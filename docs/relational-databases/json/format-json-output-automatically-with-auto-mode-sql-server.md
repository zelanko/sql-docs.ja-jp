---
title: "AUTO モードで自動的に JSON 出力を書式設定する (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aef9d09f6f8a9606a742be05a2076bf65aeb9a40
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>AUTO モードで自動的に JSON 出力を書式設定する (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

**SELECT** ステートメントの構造に基づいて **FOR JSON** 句の出力を自動的に書式設定するには、**AUTO** オプションを指定します。  
  
**AUTO** オプションを指定すると、SELECT リストとソース テーブル内の列の順序に基づいて、JSON 出力の形式が自動的に決定されます。 この形式を変更することはできません。
 
または、**PATH** オプションを使用して出力の制御を維持します。
-   **PATH** オプションの詳細については、「[Format Nested JSON Output with PATH Mode](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)」 (PATH モードで入れ子になった JSON 出力を書式設定する) を参照してください。
-   両方のオプションの概要については、「[Format Query Results as JSON with FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」(FOR JSON を使用してクエリ結果を JSON として書式設定する) を参照してください。

**FOR JSON AUTO** オプションを使用するクエリには、 **FROM** 句を含める必要があります。  
  
以下に、 **FOR JSON** 句で **AUTO** オプションを使用した例を示します。  
  
## <a name="examples"></a>使用例

### <a name="example-1"></a>例 1
 **クエリ**  
  
クエリで 1 つのテーブルだけが参照されている場合、FOR JSON AUTO 句の結果は、FOR JSON PATH の結果と同様になります。 この場合、FOR JSON AUTO では、入れ子になったオブジェクトは作成されません。 唯一の違いは、FOR JSON AUTO が、入れ子になったオブジェクトではなく、ドット付きのキーとしてドット区切りの別名 (次の例では `Info.MiddleName`) を出力する点です。  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **結果**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sánchez",
    "Info.MiddleName": "J"
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info.MiddleName": "Lee"
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info.Title": "Ms.",
    "Info.MiddleName": "A"
}]
```  

### <a name="example-2"></a>例 2

**クエリ**  
  
テーブルを結合すると、最初のテーブル内の列はルート オブジェクトのプロパティとして生成されます。 2 番目のテーブル内の列は、入れ子になったオブジェクトのプロパティとして生成されます。 2 番目のテーブルのテーブル名または別名 (次の例では `D`) は、入れ子になった配列の名前として使用されます。  
  
```sql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
**結果**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO43659",
    "D": [{
        "UnitPrice": 34.40
    }, {
        "UnitPrice": 134.24,
        "OrderQty": 5
    }]
}]
```  

### <a name="example-3"></a>例 3
 
**クエリ**  
FOR JSON AUTO を使用せずに、次の例のように SELECT ステートメントに FOR JSON PATH サブキーを入れ子にすることができます。 この例では、前の例と同じ結果が出力されます。  
  
```sql  
SELECT TOP 2  
    SalesOrderNumber,  
    OrderDate,  
    (SELECT UnitPrice, OrderQty  
      FROM Sales.SalesOrderDetail AS D  
      WHERE H.SalesOrderID = D.SalesOrderID  
     FOR JSON PATH) AS D  
FROM Sales.SalesOrderHeader AS H  
FOR JSON PATH  
```  
  
**結果**  
  
```json  
[{
    "SalesOrderNumber": "SO43659",
    "OrderDate": "2011-05-31T00:00:00",
    "D": [{
        "UnitPrice": 24.99,
        "OrderQty": 1
    }]
}, {
    "SalesOrderNumber": "SO4390",
    "D": [{
        "UnitPrice": 24.99
    }]
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。

## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
