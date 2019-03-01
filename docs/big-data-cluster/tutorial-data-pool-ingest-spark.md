---
title: Spark ジョブを使用してデータを取り込む
titleSuffix: SQL Server 2019 big data clusters
description: このチュートリアルでは、Azure Data Studio で Spark ジョブを使用して SQL Server 2019 ビッグ データ クラスター (プレビュー) のデータ プールにデータを取り込む方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 28a151f00683455b582bb29a5d141a76f237caf1
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017738"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-spark-jobs"></a>チュートリアル:Spark ジョブの SQL Server のデータ プールにデータを取り込む

このチュートリアルで Spark ジョブを使用してデータを読み込む方法、[データ プール](concept-data-pool.md)の SQL Server 2019 ビッグ データ クラスター (プレビュー)。 

このチュートリアルで確認する方法。

> [!div class="checklist"]
> * データ プール内の外部テーブルを作成します。
> * HDFS からデータを読み込み、Spark ジョブを作成します。
> * 外部テーブルの結果をクエリします。

> [!TIP]
> をする場合は、ダウンロードして、このチュートリアルでは、コマンドのスクリプトを実行します。 手順については、次を参照してください。、[データ プール サンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool)GitHub でします。

## <a id="prereqs"></a> 前提条件

- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019 の拡張機能**
- [ビッグ データ クラスターにサンプル データを読み込む](tutorial-load-sample-data.md)

## <a name="create-an-external-table-in-the-data-pool"></a>データ プール内の外部テーブルを作成します。

次の手順では、外部テーブルを作成という名前のデータ プールに**web_clickstreams_spark_results**します。 このテーブルことができますし、場所としてのデータの取り込みに使用するビッグ データ クラスター。

1. Azure Data Studio では、ビッグ データ クラスターの SQL Server のマスター インスタンスに接続します。 詳細については、次を参照してください。 [master の SQL Server インスタンスへの接続](connect-to-big-data-cluster.md#master)します。

1. 内の接続をダブルクリックして、**サーバー**ウィンドウに SQL Server のマスター インスタンスのサーバー ダッシュ ボードを表示します。 選択**新しいクエリ**します。

   ![SQL Server マスター インスタンスのクエリ](./media/tutorial-data-pool-ingest-spark/sql-server-master-instance-query.png)

1. という名前の外部テーブルを作成**web_clickstreams_spark_results**データ プールにします。 `SqlDataPool`データ ソースは、ビッグ データ クラスターのマスター インスタンスから使用できる特殊なデータ ソースの種類。

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
  
1. CTP 2.3 以降でのデータ プールの作成は、非同期ですがまだ完了して確認する方法はありません。 続行する前に、データのプールが作成されたかどうかを確認する 2 分間待ちます。

## <a name="start-a-spark-streaming-job"></a>Spark ストリーミングのジョブを開始します。

次の手順は、データ プールで作成した外部テーブルに、Spark ストリーミング web クリック ストリーム データを読み込みます (HDFS) の記憶域プールからジョブを作成します。

1. Azure のデータの Studio に接続、 **HDFS/Spark ゲートウェイ**ビッグ データ クラスター。 詳細については、次を参照してください。 [HDFS/Spark ゲートウェイへの接続](connect-to-big-data-cluster.md#hdfs)します。

1. HDFS/Spark ゲートウェイ接続をダブルクリックして、**サーバー**ウィンドウ。 選び**Spark ジョブを新しい**します。

   ![新しい Spark ジョブ](media/tutorial-data-pool-ingest-spark/hdfs-new-spark-job.png)

1. **新しいジョブ** ウィンドウに名前を入力、**ジョブ名**フィールド。

1. **Jar/py ファイル**ドロップダウン リストで選択**HDFS**します。 次の jar ファイルのパスを入力します。

   ```text
   /jar/mssql-spark-lib-assembly-1.0.jar
   ```

1. **Main クラス**フィールドに、入力`FileStreaming`します。

1. **引数**フィールドに、SQL Server のマスター インスタンス内にパスワードを指定する、次のテキストを入力、`<your_password>`プレース ホルダーです。 

   ```text
   --server mssql-master-pool-0.service-master-pool --port 1433 --user sa --password <your_password> --database sales --table web_clickstreams_spark_results --source_dir hdfs:///clickstream_data --input_format csv --enable_checkpoint false --timeout 380000
   ```

   次の表では、それぞれの引数について説明します。

   | 引数 | 説明 |
   |---|---|
   | サーバー名 (server name) | テーブル スキーマを読み取るための SQL Server の使用 |
   | ポート番号 | SQL Server のポートが (既定は 1433) でリッスンしています。 |
   | username | SQL Server ログイン ユーザー名 |
   | password | SQL Server ログイン パスワード |
   | データベース名 | [対象になるデータベース] |
   | 外部テーブルの名前 | 結果を得るのために使用するテーブル |
   | ストリーミング用のソース ディレクトリ | 完全な URI をなどあるこの必要があります"hdfs:///clickstream_data" |
   | 入力の形式 | これは、"csv"、"parquet"または"json" |
   | チェックポイントを有効にします。 | true または false |
   | timeout | 時間 (ミリ秒単位) のジョブを終了する前に実行するには |

1. キーを押して**送信**ジョブを送信します。

   ![Spark ジョブの送信](media/tutorial-data-pool-ingest-spark/spark-new-job-settings.png)

## <a name="query-the-data"></a>データのクエリ

次の手順では、Spark ストリーミング ジョブが、データ プールへの HDFS からデータを読み込まれたことを示します。

1. 取り込まれたデータのクエリを実行する前に完了したジョブをタスク履歴の出力を理解することを確認します。

   ![Spark ジョブの履歴](media/tutorial-data-pool-ingest-spark/spark-task-history.png)

1. このチュートリアルの先頭に開かれた SQL Server のマスター インスタンス クエリ ウィンドウに戻ります。

1. 取り込まれたデータを検査する次のクエリを実行します。

   ```sql
   USE Sales
   GO
   SELECT count(*) FROM [web_clickstreams_spark_results];
   SELECT TOP 10 * FROM [web_clickstreams_spark_results];
   ```

## <a name="clean-up"></a>クリーンアップします。

このチュートリアルで作成されたデータベース オブジェクトを削除するのにには、次のコマンドを使用します。

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_spark_results];
```

## <a name="next-steps"></a>次のステップ

Azure Data Studio でサンプルの notebook を実行する方法について説明します。
> [!div class="nextstepaction"]
> [サンプルの notebook を実行します。](tutorial-notebook-spark.md)
