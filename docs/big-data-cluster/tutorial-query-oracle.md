---
title: SQL Server のビッグ データ クラスターから Oracle を照会する方法 |Microsoft Docs
description: このチュートリアルでは、SQL Server 2019 ビッグ データ クラスター (プレビュー) から Oracle データを照会する方法を示します。 Oracle のデータに対して外部テーブルを作成してクエリを実行しています。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/12/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 7f5383a6faf13f0454439a42efb7524eaeda7c76
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644252"
---
# <a name="tutorial-query-oracle-from-a-sql-server-big-data-cluster"></a>チュートリアル: SQL Server のビッグ データ クラスターから Oracle を照会します。

このチュートリアルでは、SQL Server 2019 のビッグ データ クラスターから Oracle データを照会する方法を示します。 このチュートリアルを実行するには、Oracle サーバーにアクセスする必要があります。 このチュートリアルがアクセスできない場合は、ビッグ データの SQL Server クラスター内の外部データ ソースのデータ仮想化のしくみを把握付与します。

このチュートリアルで確認する方法。

> [!div class="checklist"]
> * 外部の Oracle データベースでデータの外部テーブルを作成します。
> * マスター インスタンスで価値の高いデータを持つこのデータを結合します。

> [!TIP]
> をする場合は、ダウンロードして、このチュートリアルでは、コマンドのスクリプトを実行します。 手順については、次を参照してください。、[データ仮想化のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization)GitHub でします。

## <a id="prereqs"></a> 前提条件

* [Kubernetes でのビッグ データ クラスター デプロイ](deployment-guidance.md)します。
* [Azure Data Studio と SQL Server 2019 拡張機能をインストール](deploy-big-data-tools.md)します。
* [クラスターにサンプル データを読み込む](#sampledata)します。

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-oracle-table"></a>Oracle テーブルを作成します。

次の手順は、という名前のサンプル テーブルを作成`INVENTORY`Oracle でします。

1. Oracle インスタンスとこのチュートリアルで使用するデータベースに接続します。

1. 作成する次のステートメントを実行して、`INVENTORY`テーブル。

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. コンテンツをインポート、 **inventory.csv**ファイルをこのテーブルにします。 このファイルは、サンプルの作成スクリプトで作成された、[の前提条件](#prereqs)セクション。

## <a name="create-an-external-data-source"></a>外部データ ソースを作成します。

最初の手順では、Oracle サーバーにアクセスできる外部データ ソースを作成します。

1. Azure Data Studio では、ビッグ データ クラスターの SQL Server のマスター インスタンスに接続します。 詳細については、次を参照してください。 [master の SQL Server インスタンスへの接続](deploy-big-data-tools.md#master)します。

1. 内の接続をダブルクリックして、**サーバー**ウィンドウに SQL Server のマスター インスタンスのサーバー ダッシュ ボードを表示します。 選択**新しいクエリ**します。

   ![SQL Server マスター インスタンスのクエリ](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. コンテキストを変更するのには、次の TRANSACT-SQL コマンドを実行、 **Sales**マスター インスタンス内のデータベース。

   ```sql
   USE Sales
   GO
   ```

1. Oracle サーバーに接続するデータベース スコープ資格情報を作成します。 次のステートメントで Oracle サーバーに適切な資格情報を提供します。

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Oracle サーバーを指す外部データ ソースを作成します。

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

## <a name="create-an-external-table"></a>外部テーブルを作成します。

次に、という名前の外部テーブルを作成**iventory_ora**経由で、 `INVENTORY` Oracle サーバー上のテーブル。

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> Oracle に対してクエリを実行中に識別子を引用符で囲まれた、ANSI SQL は、テーブル名と列名が使用されます。 その結果、名前は大文字小文字を区別します。 Oracle のメタデータのテーブルおよび列名の大文字と小文字の一致する外部テーブル定義の名前を指定する重要です。

## <a name="query-the-data"></a>データのクエリ

データを結合する次のクエリ実行、`iventory_ora`ローカル テーブルと外部テーブル`Sales`データベース。

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>クリーンアップします。

このチュートリアルで作成されたデータベース オブジェクトを削除するのにには、次のコマンドを使用します。

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>次の手順

データのプールにデータを取り込む方法について説明します。
> [!div class="nextstepaction"]
> [データのプールにデータを読み込む](tutorial-data-pool-ingest-sql.md)
