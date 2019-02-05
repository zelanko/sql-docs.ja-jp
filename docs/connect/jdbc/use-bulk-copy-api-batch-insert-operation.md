---
title: MSSQL JDBC ドライバーのバッチ挿入操作の一括コピー API を使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c3d3c7cc4d8dd7beeb620a211b2f41a1d1105a04
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737103"
---
# <a name="using-bulk-copy-api-for-batch-insert-operation"></a>バッチ挿入操作に一括コピー API を使用する

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

バッチの一括コピー API を使用して SQL Server サポート用の Microsoft JDBC Driver 7.0 では、Azure Data Warehouse の操作を挿入します。 この機能では、挿入操作のバッチを実行するときに下にある一括コピー操作を実行するドライバーを有効にすることができます。 正規表現のバッチである、ドライバーと同じデータの挿入中にパフォーマンスの向上を実現するためにドライバーの目的は、操作を挿入します。 ドライバーは、通常のバッチ挿入操作の代わりの一括コピー API を利用するユーザーの SQL クエリを解析します。 バッチの一括コピー API を有効にするさまざまな方法は挿入機能と制限事項の一覧を次に示します。 このページには、使用状況とパフォーマンスの向上を説明する小規模なサンプル コードも含まれています。

この機能は、PreparedStatement および CallableStatement ののみ`executeBatch()`  &  `executeLargeBatch()` Api。

## <a name="pre-requisites"></a>前提条件

一括挿入を一括コピー API を有効にする 2 つの前提条件があります。

* サーバーは、Azure Data Warehouse である必要があります。
* クエリは、insert クエリである必要があります (クエリは、コメントを含めることができますが、この機能を有効になる INSERT キーワードを使用してクエリを開始する必要があります)。

## <a name="enabling-bulk-copy-api-for-batch-insert"></a>一括挿入の一括コピー API を有効にします。

一括挿入を一括コピー API を有効にする 3 つの方法はあります。

### <a name="1-enabling-with-connection-property"></a>1.接続プロパティを有効にします。

追加**useBulkCopyForBatchInsert = true;** 接続文字列がこの機能を有効します。

```java
Connection connection = DriverManager.getConnection("jdbc:sqlserver://<server>:<port>;userName=<user>;password=<password>;database=<database>;useBulkCopyForBatchInsert=true;");
```

### <a name="2-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverconnection-object"></a>2.SQLServerConnection オブジェクトから setUseBulkCopyForBatchInsert() メソッドを使用して有効にします。

呼び出す**SQLServerConnection.setUseBulkCopyForBatchInsert(true)** この機能を有効にします。

**SQLServerConnection.getUseBulkCopyForBatchInsert()** の現在の値を取得します。 **useBulkCopyForBatchInsert**接続プロパティです。

値は、 **useBulkCopyForBatchInsert**の初期化時に各 PreparedStatement の定数を保持します。 呼び出す**SQLServerConnection.setUseBulkCopyForBatchInsert()** 作成済みの PreparedStatement に関しては、その値には影響しません。

### <a name="3-enabling-with-setusebulkcopyforbatchinsert-method-from-sqlserverdatasource-object"></a>3.SQLServerDataSource オブジェクトから setUseBulkCopyForBatchInsert() メソッドを使用して有効にします。

上記に似ていますが SQLServerDataSource を使用して、SQLServerConnection オブジェクトを作成します。 どちらの方法も、同じ結果が得られます。

## <a name="known-limitations"></a>既知の制限事項

現在、この機能に適用されるこれらの制限は。

* パラメーター化されていない値を含むクエリの挿入 (たとえば、 `INSERT INTO TABLE VALUES (?, 2`)) はサポートされていません。 ワイルドカード (?) は、この関数でのみサポートされているパラメーターです。
* 挿入 INSERT SELECT 式が含まれるクエリ (たとえば、 `INSERT INTO TABLE SELECT * FROM TABLE2`) ではサポートされていません。
* 複数値の式を含むクエリの挿入 (たとえば、 `INSERT INTO TABLE VALUES (1, 2) (3, 4)`) はサポートされていません。
* OPTION 句の後に、複数のテーブルと結合または後に別のクエリの挿入クエリはサポートされていません。
* 一括コピーの API の制限により`MONEY`、 `SMALLMONEY`、 `DATE`、 `DATETIME`、 `DATETIMEOFFSET`、 `SMALLDATETIME`、 `TIME`、 `GEOMETRY`、および`GEOGRAPHY`データ型は現在サポートされていませんこの機能です。

以外のため、クエリが失敗した場合"SQL server"関連のエラー、ドライバーは一括挿入を元のロジックにエラー メッセージとフォールバックが記録されます。

## <a name="example"></a>例

ユース ケースをバッチ挿入操作の Azure の DW に対して、1000 を超える数の行の両方 (正規表現と一括コピー API) のシナリオを示すコードの例を次に示します。

```java
    public static void main(String[] args) throws Exception
    {
        String tableName = "batchTest";
        String tableNameBulkCopyAPI = "batchTestBulk";

        String azureDWconnectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl); // connects to an Azure Data Warehouse.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableName + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableName + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableName + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableName + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using regular batch insert operation.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }

        try (Connection con = DriverManager.getConnection(azureDWconnectionUrl + ";useBulkCopyForBatchInsert=true"); // connects to an Azure Data Warehouse, with useBulkCopyForBatchInsert connection property set to true.
                Statement stmt = con.createStatement();
                PreparedStatement pstmt = con.prepareStatement("insert into " + tableNameBulkCopyAPI + " values (?, ?)");) {

            String dropSql = "if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[" + tableNameBulkCopyAPI + "]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) DROP TABLE [" + tableNameBulkCopyAPI + "]";
            stmt.execute(dropSql);

            String createSql = "create table " + tableNameBulkCopyAPI + " (c1 int, c2 varchar(20))";
            stmt.execute(createSql);

            System.out.println("Starting batch operation using Bulk Copy API.");
            long start = System.currentTimeMillis();
            for (int i = 0; i < 1000; i++) {
                pstmt.setInt(1, i);
                pstmt.setString(2, "test" + i);
                pstmt.addBatch();
            }
            pstmt.executeBatch();

            long end = System.currentTimeMillis();

            System.out.println("Finished. Time taken : " + (end - start) + " milliseconds.");
        }
    }
```

結果:

```bash
Starting batch operation using regular batch insert operation.
Finished. Time taken : 104132 milliseconds.
Starting batch operation using Bulk Copy API.
Finished. Time taken : 1058 milliseconds.
```

## <a name="see-also"></a>参照

[JDBC ドライバーによるパフォーマンスと信頼性の強化](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
