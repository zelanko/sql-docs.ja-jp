---
title: "PATH モードで入れ子になった JSON 出力を書式設定する (SQL Server) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 115bc1104c4da33158d4c8de131e2e3fc021c94e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>PATH モードで入れ子になった JSON 出力を書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

**FOR JSON** 句の出力を完全に制御するには、**PATH** オプションを指定します。  
  
**PATH** モードでは、ラッパー オブジェクトを作成し、複雑なプロパティを入れ子にすることができます。 結果は JSON オブジェクトの配列として書式設定されます。  
  
または、**AUTO** オプションを使用して、**SELECT** ステートメントの構造に基づいて出力を自動的に書式設定する方法があります。
 -   **AUTO** オプションの詳細については、「[Format JSON Output Automatically with AUTO Mode](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md)」 (AUTO モードで自動的に JSON 出力を書式設定する) を参照してください。
 -   両方のオプションの概要については、「[Format Query Results as JSON with FOR JSON](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」 (FOR JSON を使用してクエリ結果を JSON として書式設定する) を参照してください。
 
以下に、 **FOR JSON** 句で **PATH** オプションを使用した例を示します。 次の例に示すように、ドット区切りの列名を使用するか、入れ子になったクエリを使用して、入れ子になった結果を書式設定します。 既定では、**FOR JSON** 出力に null 値は含まれません。  

## <a name="example---dot-separated-column-names"></a>例: ドット区切りの列名  
次のクエリは、AdventureWorks `Person` テーブルの最初の 5 行を JSON として書式設定します。  

**FOR JSON PATH** 句は、列の別名または列の名前を使用して JSON 出力のキー名を決定します。 別名にドットが含まれている場合、PATH オプションで入れ子になったオブジェクトが作成されます。  

 **Query**  
  
```sql  
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
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sanchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
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
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  
   
## <a name="example---multiple-tables"></a>例 - 複数のテーブル  
クエリで複数のテーブルを参照すると、**FOR JSON PATH** でその別名を使用して各列が入れ子にされます。 次のクエリは、クエリで結合される (OrderHeader、OrderDetails) ペアごとに 1 つの JSON オブジェクトを作成します。 
  
 **Query**  
  
```sql  
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
[{
    "Order": {
        "Number": "SO43659",
        "Date": "2011-05-31T00:00:00"
    },
    "Product": {
        "Price": 2024.9940,
        "Quantity": 1
    }
}, {
    "Order": {
        "Number": "SO43659"
    },
    "Product": {
        "Price": 2024.9940
    }
}]
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。

## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
