---
title: ビッグ データの SQL Server クラスターで HDFS をクエリする方法 |Microsoft Docs
description: このチュートリアルでは、SQL Server 2019 ビッグ データ クラスター (プレビュー) での HDFS データを照会する方法を示します。 記憶域プール内のデータに対して外部テーブルを作成してクエリを実行しています。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/11/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: c6f0f01936d5b6e570c2bff53d19ae7a64f151ab
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644245"
---
# <a name="tutorial-query-hdfs-in-a-sql-server-big-data-cluster"></a>チュートリアル: SQL Server のビッグ データ クラスターで HDFS を照会します。

このチュートリアルでは、SQL Server 2019 ビッグ データ クラスターで HDFS のデータを照会する方法を示します。

このチュートリアルで確認する方法。

> [!div class="checklist"]
> * ビッグ データ クラスターで HDFS のデータを指す外部テーブルを作成します。
> * マスター インスタンスで価値の高いデータを持つこのデータを結合します。

> [!TIP]
> をする場合は、ダウンロードして、このチュートリアルでは、コマンドのスクリプトを実行します。 手順については、次を参照してください。、[データ仮想化のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization)GitHub でします。

## <a name="prerequisites"></a>前提条件

- [Kubernetes でのビッグ データ クラスター デプロイ](deployment-guidance.md)します。
- [Azure Data Studio と SQL Server 2019 拡張機能をインストール](deploy-big-data-tools.md)します。
- [クラスターにサンプル データを読み込む](#sampledata)します。

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-to-hdfs"></a>HDFS に外部テーブルを作成します。

記憶域プールには、HDFS に格納されている CSV ファイルでは、web クリック ストリーム データが含まれています。 次の手順を使用すると、そのファイル内のデータにアクセスできる外部テーブルを定義します。

1. Azure Data Studio では、ビッグ データ クラスターの SQL Server のマスター インスタンスに接続します。 詳細については、次を参照してください。 [master の SQL Server インスタンスへの接続](deploy-big-data-tools.md#master)します。

2. 内の接続をダブルクリックして、**サーバー**ウィンドウに SQL Server のマスター インスタンスのサーバー ダッシュ ボードを表示します。 選択**新しいクエリ**します。

   ![SQL Server マスター インスタンスのクエリ](./media/tutorial-query-hdfs-storage-pool/sql-server-master-instance-query.png)

3. コンテキストを変更するのには、次の TRANSACT-SQL コマンドを実行、 **Sales**マスター インスタンス内のデータベース。

   ```sql
   USE Sales
   GO
   ```

4. HDFS からの読み取り、CSV ファイルの形式を定義します。 F5 キーを押して、ステートメントを実行します。

   ```sql
   CREATE EXTERNAL FILE FORMAT csv_file
   WITH (
       FORMAT_TYPE = DELIMITEDTEXT,
       FORMAT_OPTIONS(
           FIELD_TERMINATOR = ',',
           STRING_DELIMITER = '"',
           FIRST_ROW = 2,
           USE_TYPE_DEFAULT = TRUE)
   );
   ```

5. 読み取ることができる外部テーブルを作成、`/clickstream_data`記憶域プールから。 **SqlStoragePool**はビッグ データ クラスターのマスター インスタンスからアクセスできます。

   ```sql
   CREATE EXTERNAL TABLE [web_clickstreams_hdfs]
   ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
   WITH
   (
       DATA_SOURCE = SqlStoragePool,
       LOCATION = '/clickstream_data',
       FILE_FORMAT = csv_file
   );
   GO
   ```

## <a name="query-the-data"></a>データのクエリ

HDFS データに結合する次のクエリ実行、`web_clickstream_hdfs`ローカル リレーショナル データを外部テーブル`Sales`データベース。

```sql
SELECT  
    wcs_user_sk,
    SUM( CASE WHEN i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
    SUM( CASE WHEN i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
    SUM( CASE WHEN i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
    SUM( CASE WHEN i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
    SUM( CASE WHEN i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
    SUM( CASE WHEN i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
    SUM( CASE WHEN i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
    SUM( CASE WHEN i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
    SUM( CASE WHEN i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
    SUM( CASE WHEN i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
  FROM [dbo].[web_clickstreams_hdfs]
  INNER JOIN item it ON (wcs_item_sk = i_item_sk
                        AND wcs_user_sk IS NOT NULL)
GROUP BY  wcs_user_sk;
GO
```

## <a name="clean-up"></a>クリーンアップします。

このチュートリアルで使用する外部テーブルを削除するのにには、次のコマンドを使用します。

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_hdfs];
GO
```

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターから Oracle クエリを実行する方法については、次の記事に進んでください。
> [!div class="nextstepaction"]
> [Oracle の外部のデータを照会します。](tutorial-query-oracle.md)
