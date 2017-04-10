---
title: "PATH モードで入れ子になった JSON 出力を書式設定する (SQL Server) | Microsoft Docs"
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
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# PATH モードで入れ子になった JSON 出力を書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON 出力の形式を完全に制御するには、 **FOR JSON** 句で **PATH** オプションを指定します。  
  
 **PATH** モードでは、ラッパー オブジェクトを作成し、複雑なプロパティを入れ子にすることができます。 結果は JSON オブジェクトの配列として書式設定されます。  
  
 以下に、 **FOR JSON** 句で **PATH** オプションを使用した例を示します。 次の例に示すように、ドット区切りの列名を使用するか、入れ子になったクエリを使用して、入れ子になった結果を書式設定します。 既定では、null 値は出力に含まれません。  
  
## 例: ドット区切りの列名  
 次のクエリは、AdventureWorks Person テーブルの最初の 5 行を JSON として書式設定します。  
  
 **Query**  
  
```tsql  
SELECT TOP 5   
      BusinessEntityID As Id,  
      FirstName, LastName,  
      Title As 'Info.Title',  
      MiddleName As 'Info.MiddleName'  
  FROM Person.Person  
  FOR JSON PATH  
```  
  
 **結果**  
  
```json  
[  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
```  
  
 FOR JSON PATH 句は、列の別名または列の名前を使用して JSON 出力のキー名を決定します。 一部の別名にドットが含まれている場合、FOR JSON PATH 句は入れ子になったオブジェクトを作成します。 NULL 値のセルは出力で生成されないことに注意してください。  
  
## 例 - 複数のテーブル  
 クエリで複数のテーブルが参照されている場合は、結果が単純なリストとして表された後、FOR JSON PATH によりその別名が使用され、各列が入れ子にされます。 次のクエリは、クエリで結合される (OrderHeader,OrderDetails) ペアごとに 1 つの JSON オブジェクトを作成します。  
  
 **Query**  
  
```tsql  
SELECT TOP 2 SalesOrderNumber AS 'Order.Number',  
       OrderDate AS 'Order.Date',  
       UnitPrice AS 'Product.Price',  
       OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
  INNER JOIN Sales.SalesOrderDetail D  
    ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH  
```  
  
 **結果**  
  
```json  
[  
  {  
    "Order":{  
        "Number":"SO43659",  
        "Date":"2011-05-31T00:00:00"  
      },  
    "Product":{  
         "Price":2024.9940,  
         "Quantity":1  
     }  
  },  
  {  
    "Order":{ "Number":"SO43659“ },  
    "Product":{"Price":2024.9940}  
  }  
]  
```  
  
## 参照  
 [FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  