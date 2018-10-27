---
title: Transact SQL を使用した SQL Server のデータ プールにデータを取り込む方法 |Microsoft Docs
description: このチュートリアルでは、sp_data_pool_table_insert_data ストアド プロシージャを含む SQL Server 2019 ビッグ データ クラスター (プレビュー) のデータ プールにデータを取り込む方法を示します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/16/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: c909379c92b2eb9a98c1c191987570946a8cc002
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644237"
---
# <a name="tutorial-ingest-data-into-a-sql-server-data-pool-with-transact-sql"></a>チュートリアル: は、Transact SQL を使用した SQL Server のデータ プールにデータを取り込む

このチュートリアルで TRANSACT-SQL を使用してデータを読み込む方法、[データ プール](concept-data-pool.md)の SQL Server 2019 ビッグ データ クラスター (プレビュー)。 ビッグ データの SQL Server クラスターでのさまざまなソースからデータを取り込み、データ プール インスタンスに分散します。

このチュートリアルで確認する方法。

> [!div class="checklist"]
> * データ プール内の外部テーブルを作成します。
> * サンプル web クリック ストリーム データをデータ プール テーブルに挿入します。
> * ローカル テーブルのデータ プール テーブル内のデータを結合します。

> [!TIP]
> をする場合は、ダウンロードして、このチュートリアルでは、コマンドのスクリプトを実行します。 手順については、次を参照してください。、[データ プール サンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-pool)GitHub でします。

## <a id="prereqs"></a> 前提条件

* [Kubernetes でのビッグ データ クラスター デプロイ](deployment-guidance.md)します。
* [Azure Data Studio と SQL Server 2019 拡張機能をインストール](deploy-big-data-tools.md)します。
* [クラスターにサンプル データを読み込む](#sampledata)します。

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-in-the-data-pool"></a>データ プール内の外部テーブルを作成します。

次の手順では、外部テーブルを作成という名前のデータ プールに**web_clickstream_clicks_data_pool**します。 このテーブルことができますし、場所としてのデータの取り込みに使用するビッグ データ クラスター。

1. Azure Data Studio では、ビッグ データ クラスターの SQL Server のマスター インスタンスに接続します。 詳細については、次を参照してください。 [master の SQL Server インスタンスへの接続](deploy-big-data-tools.md#master)します。

1. 内の接続をダブルクリックして、**サーバー**ウィンドウに SQL Server のマスター インスタンスのサーバー ダッシュ ボードを表示します。 選択**新しいクエリ**します。

   ![SQL Server マスター インスタンスのクエリ](./media/tutorial-data-pool-ingest-sql/sql-server-master-instance-query.png)

1. コンテキストを変更するのには、次の TRANSACT-SQL コマンドを実行、 **Sales**マスター インスタンス内のデータベース。

   ```sql
   USE Sales
   GO
   ```

1. という名前の外部テーブルを作成**web_clickstream_clicks_data_pool**データ プールにします。 `SqlDataPool`データ ソースは、ビッグ データ クラスターのマスター インスタンスから使用できる特殊なデータ ソースの種類。

   ```sql
   IF NOT EXISTS(SELECT * FROM sys.external_tables WHERE name = 'web_clickstream_clicks_data_pool')
      CREATE EXTERNAL TABLE [web_clickstream_clicks_data_pool]
      ("wcs_user_sk" BIGINT , "i_category_id" BIGINT , "clicks" BIGINT)
      WITH
      (
         DATA_SOURCE = SqlDataPool,
         DISTRIBUTION = ROUND_ROBIN
      );
   ```
  
1. CTP 2.0 でのデータ プールの作成は、非同期ですがまだ完了して確認する方法はありません。 続行する前に、データのプールが作成されたかどうかを確認する 2 分間待ちます。

## <a name="load-data"></a>データの読み込み

次の手順では、前の手順で作成された外部テーブルを使用してデータ プールにサンプル web クリック ストリーム データを取り込みます。

1. 使用してデータ プールにデータを挿入するクエリの変数を定義します。 使用して、**モデル.sp_data_pool_table_insert_data**ストアド プロシージャのデータ プールに、クエリから結果を挿入する (、 **web_clickstream_clicks_data_pool**外部テーブル)。

   ```sql
   DECLARE @db_name SYSNAME = 'Sales'
   DECLARE @schema_name SYSNAME = 'dbo'
   DECLARE @table_name SYSNAME = 'web_clickstream_clicks_data_pool'
   DECLARE @query NVARCHAR(MAX) = '
   SELECT wcs_user_sk, i_category_id, COUNT_BIG(*) as clicks
   FROM sales.dbo.web_clickstreams
   INNER JOIN sales.dbo.item it ON (wcs_item_sk = i_item_sk
      AND wcs_user_sk IS NOT NULL)
   GROUP BY wcs_user_sk, i_category_id
   HAVING COUNT_BIG(*) > 100;'

   EXEC model..sp_data_pool_table_insert_data @db_name, @schema_name, @table_name, @query
   ```

1. 2 つの SELECT クエリで挿入されたデータを検査します。

   ```sql
   SELECT count(*) FROM [dbo].[web_clickstream_clicks_data_pool]
   SELECT TOP 10 * FROM [dbo].[web_clickstream_clicks_data_pool]  
   ```

## <a name="query-the-data"></a>データのクエリ

格納されたデータ プール内でローカル データのクエリから結果を結合、 **Sales**テーブル。

```sql
SELECT TOP (100)
   w.wcs_user_sk,
   SUM( CASE WHEN i.i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
   SUM( CASE WHEN w.i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
   SUM( CASE WHEN w.i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
   SUM( CASE WHEN w.i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
   SUM( CASE WHEN w.i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
   SUM( CASE WHEN w.i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
   SUM( CASE WHEN w.i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
   SUM( CASE WHEN w.i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
   SUM( CASE WHEN w.i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
   SUM( CASE WHEN w.i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
FROM [dbo].[web_clickstream_clicks_data_pool] as w
INNER JOIN (SELECT DISTINCT i_category_id, i_category FROM item) as i
   ON i.i_category_id = w.i_category_id
GROUP BY w.wcs_user_sk;
```

## <a name="clean-up"></a>クリーンアップします。

このチュートリアルで作成されたデータベース オブジェクトを削除するのにには、次のコマンドを使用します。

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstream_clicks_data_pool];
```

## <a name="next-steps"></a>次の手順

Spark ジョブのデータ プールにデータを取り込む方法について説明します。
> [!div class="nextstepaction"]
> [Spark ジョブを使用してデータを取り込む](tutorial-data-pool-ingest-spark.md)
