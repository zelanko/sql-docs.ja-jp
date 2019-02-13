---
title: Sql_variant データ型を使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8df6fcee7b79f0c85f1182442195eb2cdf8d7ac9
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737350"
---
# <a name="using-sqlvariant-data-type"></a>Sql_variant データ型の使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

バージョン 6.3.0 の時点では、JDBC ドライバーは、sql_variant データ型をサポートします。 Sql_variant は、後でこのページに記載いくつかの制限とテーブル値パラメーターと BulkCopy などの機能を使用するときにもサポートされます。 すべてのデータ型は、sql_variant データ型に格納できます。 Sql_variant 型でサポートされるデータ型の一覧は、SQL Server を確認[Docs](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql)します。

##  <a name="populating-and-retrieving-a-table"></a>設定、テーブルを取得します。
1 つと仮定すると、として sql_variant 列を持つテーブルがあります。

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

ステートメントを使用して値を挿入するサンプル スクリプトです。

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

挿入する値を使用してステートメントを準備します。

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

渡されるデータの基になる型が既知の場合は、それぞれの set アクセス操作子を使用できます。 たとえば、`preparedStatement.setInt()`整数値を挿入するときに使用できます。

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

テーブルから値の読み取り、それぞれの get アクセス操作子を使用していることができます。 たとえば、`getInt()`または`getString()`サーバーからの値がわかっている場合、メソッドを使用できます。    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sqlvariant"></a>Sql_variant でストアド プロシージャを使用します。   
ストアド プロシージャをなどあります。     

```java
String sql = "CREATE PROCEDURE " + inputProc + " @p0 sql_variant OUTPUT AS SELECT TOP 1 @p0=col1 FROM sampleTable ";
``` 
    
出力パラメーターを登録する必要があります。

```java
try (CallableStatement callableStatement = con.prepareCall(" {call " + inputProc + " (?) }")) {
    callableStatement.registerOutParameter(1, microsoft.sql.Types.SQL_VARIANT);      
    callableStatement.execute();
}
```

## <a name="limitations-of-sqlvariant"></a>Sql_variant 型の制限事項:
- TVP を使用してテーブルに設定する場合、 `datetime` / `smalldatetime` / `date` 、sql_variant に格納された値を呼び出す`getDateTime()` / `getSmallDateTime()` / `getDate()`で、結果セットは行われず、次の例外をスローします。
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    回避策: 使用`getString()`または`getObject()`代わりにします。 
    
- TVP を使用してテーブルを設定して、sql_variant 型で null 値を送信することはできず、例外をスローします。
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>参照

[JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
