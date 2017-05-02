---
title: "AUTO モードで自動的に JSON 出力を書式設定する (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON AUTO
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a04977311f1f04171caa1de0d15373d0b3cdf15
ms.lasthandoff: 04/11/2017

---
# <a name="format-json-output-automatically-with-auto-mode-sql-server"></a>AUTO モードで自動的に JSON 出力を書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

**SELECT** ステートメントの構造に基づいて **FOR JSON** 句の出力を自動的に書式設定するには、**AUTO** オプションを指定します。  
  
**AUTO** オプションを指定すると、SELECT リストとソース テーブル内の列の順序に基づいて、JSON 出力の形式が自動的に決定されます。 この形式を変更することはできません。
 
 または、**PATH** オプションを使用して出力の制御を維持します。
 -   **PATH** オプションの詳細については、「[Format Nested JSON Output with PATH Mode](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)」 (PATH モードで入れ子になった JSON 出力を書式設定する) を参照してください。
 -   両方のオプションの概要については、「[Format Query Results as JSON with FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」(FOR JSON を使用してクエリ結果を JSON として書式設定する) を参照してください。
  
 **FOR JSON AUTO** オプションを使用するクエリには、 **FROM** 句を含める必要があります。  
  
 以下に、 **FOR JSON** 句で **AUTO** オプションを使用した例を示します。  
  
## <a name="examples"></a>使用例  
 **クエリ 1**  
  
クエリで 1 つのテーブルだけが使用される場合は、FOR JSON AUTO 句の結果は、FOR JSON PATH の結果と同様になります。 この場合、FOR JSON AUTO では、入れ子になったオブジェクトは作成されません。 唯一の違いは、FOR JSON AUTO が、入れ子になったオブジェクトではなく、ドット付きのキーとしてドット区切りの別名 (次の例では `Info.MiddleName`) を出力する点です。  
  
```tsql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON AUTO  
```  
  
 **結果 1**  
  
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
  
 **クエリ 2**  
  
 テーブルを結合すると、最初のテーブル内の列はルート オブジェクトのプロパティとして生成されます。 2 番目のテーブル内の列は、入れ子になったオブジェクトのプロパティとして生成されます。 2 番目のテーブルのテーブル名または別名 (次の例では `D`) は、入れ子になった配列の名前として使用されます。  
  
```tsql  
SELECT TOP 2 SalesOrderNumber,  
        OrderDate,  
        UnitPrice,  
        OrderQty  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON AUTO   
```  
  
 **結果 2**  
  
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
 
 **クエリ 3**  
 FOR JSON AUTO を使用せずに、次の例のように SELECT ステートメントに FOR JSON PATH サブキーを入れ子にすることができます。 この例では、前の例と同じ結果が出力されます。  
  
```tsql  
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
  
 **結果 3**  
  
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
  
## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
  
  

