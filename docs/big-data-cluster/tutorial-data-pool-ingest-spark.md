---
title: Spark ジョブを使用してデータを取り込む
titleSuffix: SQL Server big data clusters
description: このチュートリアルでは、Azure Data Studio で Spark ジョブを使用して、SQL Server 2019 ビッグ データ クラスター (プレビュー) のデータ プールにデータを取り込む方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
ms.date: 06/26/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 6d0ea6d4fb7a3aea9788c089ad68cb3bf523837f
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67957815"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>チュートリアル:Spark ジョブを使用して SQL Server のデータ プールにデータを取り込む

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このチュートリアルでは、Spark ジョブを使用して SQL Server 2019 ビッグ データ クラスター (プレビュー) の[データ プール](concept-data-pool.md)にデータを取り込む方法について説明します。 

このチュートリアルでは、次の方法を学習します。

> [!div class="checklist"]
> * データ プールに外部テーブルを作成する
> * Spark ジョブを作成して HDFS からデータを読み込む
> * 外部テーブルの結果に対してクエリを実行する

> [!TIP]
> 必要に応じて、このチュートリアルのコマンド用のスクリプトをダウンロードして実行できます。 手順については、GitHub の[データ プールのサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool)を参照してください。

## <a id="prereqs"></a> 前提条件

- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
- [ビッグ データ クラスターにサンプル データを読み込む](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>データ プールに外部テーブルを作成する

次の手順では、**web_clickstreams_spark_results** という名前のデータ プールに外部テーブルを作成します。 このテーブルは、ビッグ データ クラスターにデータを取り込むための場所として使用できます。

1. Azure Data Studio で、ビッグ データ クラスターの SQL Server マスター インスタンスに接続します。 詳細については、「[SQL Server マスター インスタンスに接続する](connect-to-big-data-cluster.md#master)」を参照してください。

1. **[サーバー]** ウィンドウで接続をダブルクリックして、SQL Server マスター インスタンスのサーバー ダッシュボードを表示します。 **[新しいクエリ]** を選択します。

   ![SQL Server マスター インスタンス クエリ](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. まだ存在しない場合は、データ プールへの外部データ ソースを作成します。

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
     CREATE EXTERNAL DATA SOURCE SqlDataPool
     WITH (LOCATION = 'sqldatapool://controller-svc/default');
   ```

1. データ プールで、**web_clickstreams_spark_results** という名前の外部テーブルを作成します。

   ```sql
   USE Sales
   GO
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstreams_spark_results')
      CREATE EXTERNAL TABLE [web_clickstreams_spark_results]
      ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. CTP 3.1 では、データ プールの作成は非同期ですが、まだ完了しているかどうかを判断する方法がありません。 データ プールが作成されたことを確認できるまで 2 分待ってから続行してください。

## <a name="start-a-spark-streaming-job"></a>Spark ストリーミング ジョブを開始する

次の手順では、ストレージ プール (HDFS) から Web クリックストリーム データを、データ プールに作成した外部テーブルに読み込む Spark ストリーミング ジョブを作成します。

1. Azure Data Studio で、ビッグ データ クラスターのマスター インスタンスに接続します。 詳細については、[ビッグ データ クラスターへの接続](connect-to-big-data-cluster.md)に関するページを参照してください。

1. **[サーバー]** ウィンドウで、HDFS/Spark ゲートウェイ接続をダブルクリックします。 次に、 **[New Spark Job]\(新しい Spark ジョブ\)** を選択します。

   ![新しい Spark ジョブ](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. **[新しいジョブ]** ウィンドウで、 **[ジョブ名]** フィールドに名前を入力します。

1. **[Jar/py ファイル]** ドロップダウンで、 **[HDFS]** を選択します。 次に、以下の jar ファイル パスを入力します。

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. **[メイン クラス]** フィールドに「`FileStreaming`」と入力します。

1. **[引数]** フィールドに、`<your_password>` プレースホルダーに SQL Server マスター インスタンスのパスワードを指定して、次のテキストを入力します。 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   次の表では、それぞれの引数について説明します。

   | 引数 | [説明] |
   |---|---|
   | サーバー名 (server name) | SQL Server によってテーブル スキーマの読み取りに使用されます |
   | ポート番号 | SQL Server でリッスンしているポート (既定値: 1433) |
   | username | SQL Server ログイン ユーザー名 |
   | パスワード | SQL Server ログイン パスワード |
   | データベース名 | [対象になるデータベース] |
   | external table name | 結果に使用するテーブル |
   | ストリーミング用のソース ディレクトリ | これは、"hdfs:///clickstream_data" などの完全な URI である必要があります |
   | input format | "csv"、"parquet"、または "json" を指定できます |
   | enable checkpoint | true または false |
   | timeout | この時間ジョブを実行したら終了します (ミリ秒単位) |

1. **[送信]** を押して、ジョブを送信します。

   ![Spark ジョブの送信](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>データにクエリを実行する

次の手順は、HDFS からデータをデータ プールに読み込む Spark ストリーミング ジョブを示しています。

1. 取り込まれたデータに対してクエリを実行する前に、タスク履歴出力を調べて、ジョブが完了したことを確認します。

   ![Spark ジョブ履歴](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. このチュートリアルで最初に開いた SQL Server マスター インスタンス クエリ ウィンドウに戻ります。

1. 次のクエリを実行して、取り込まれたデータを検査します。

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>クリーンアップ

このチュートリアルで作成されたデータベース オブジェクトを削除するには、次のコマンドを使用します。

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>次の手順

Azure Data Studio でサンプル ノートブックを実行する方法について説明します。
> [!div class="nextstepaction"]
> [サンプル ノートブックの実行](tutorial-notebook-spark.md)
