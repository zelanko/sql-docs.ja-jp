---
title: "AUTO モードで自動的に JSON 出力を書式設定する (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FOR JSON AUTO"
ms.assetid: 178a2a4e-e0f6-49b9-9895-396956d3c7d9
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# AUTO モードで自動的に JSON 出力を書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **SELECT** ステートメントの構造に基づいて自動的に JSON 出力を書式設定するには、  **FOR JSON** 句で **AUTO** オプションを指定します。  
  
 **AUTO** オプションを指定すると、SELECT リストとソース テーブル内の列の順序に基づいて、JSON 出力の形式が自動的に決定されます。 この形式を変更することはできません。  
  
 **FOR JSON AUTO** オプションを使用するクエリには、 **FROM** 句を含める必要があります。  
  
 以下に、 **FOR JSON** 句で **AUTO** オプションを使用した例を示します。  
  
## 使用例  
 **クエリ 1**  
  
 クエリで 1 つのテーブルだけが使用される場合は、FOR JSON AUTO 句の結果は、FOR JSON PATH と同様になります。 この場合、FOR JSON AUTO では、入れ子になったオブジェクトは作成されません。 唯一の違いは、ドット区切りのエイリアスがドット付きのキーとして生成されることです (つまり FOR JSON AUTO で列の別名が書式設定に使用されません)。  
  
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
[  
      {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info.MiddleName":"J"},  
      {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info.MiddleName":"Lee"},  
      {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
      {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
      {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info.Title":"Ms.","Info.MiddleName":"A"}  
]  
```  
  
 **クエリ 2**  
  
 テーブルを結合すると、最初のテーブル内の列はルート オブジェクトのプロパティとして生成されます。 2 番目のテーブル内の列は、入れ子になったオブジェクトのプロパティとして生成されます。 2 番目のテーブルのテーブル名またはエイリアスは、入れ子になった配列の名前として使用されます。  
  
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
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            {"UnitPrice":24.99, "OrderQty":1  }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO43659" ,  
       "D":[  
          { "UnitPrice":34.40  },  
          { "UnitPrice":134.24, "OrderQty":5 }  
        ]  
  }  
]  
  
```  
  
## 例 - 入れ子になった JSON 出力の生成  
 FOR JSON AUTO ではなく、次の例に示すように、FOR JSON PATH 句を使用してメインのクエリの SELECT 部分に入れ子になった FOR JSON クエリを記述できます。  
  
 **クエリ 1**  
  
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
  
 **結果 1**  
  
```json  
[  
  {  
       "SalesOrderNumber":"SO43659",  
        "OrderDate":"2011-05-31T00:00:00",  
        "D":[  
            { "UnitPrice":24.99,  "OrderQty":1 }  
         ]  
  },  
  {  
       "SalesOrderNumber":"SO4390" ,  
       "D":[  
            { "UnitPrice":24.99 }  
        ]  
  }  
]  
  
```  
  
## 参照  
 [FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  