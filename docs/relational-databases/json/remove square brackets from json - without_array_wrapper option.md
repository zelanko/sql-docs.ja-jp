---
title: "WITHOUT_ARRAY_WRAPPER オプションを使用して JSON 出力から角かっこを削除する (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WITHOUT_ARRAY_WRAPPER"
ms.assetid: aa86c2d1-458e-465f-abfa-75470137d054
caps.latest.revision: 11
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# WITHOUT_ARRAY_WRAPPER オプションを使用して JSON 出力から角かっこを削除する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  既定で **FOR JSON** 句の JSON 出力を囲んでいる角かっこを削除するには、**WITHOUT_ARRAY_WRAPPER** オプションを指定します。 このオプションを使用すると、単一の JSON オブジェクトを出力として生成できます。  
  
 このオプションを指定しないと、JSON 出力が角かっこで囲まれます。  
  
## 使用例  
 **WITHOUT_ARRAY_WRAPPER** オプションを指定した場合と指定しなかった場合の **FOR JSON** 句の出力例を以下に示します。  
  
 **Query**  
  
```tsql  
SELECT 2015 as year, 12 as month, 15 as day  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使用した**結果**  
  
```json  
{ "year":2015, "month":12, "day":15 }  
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使用しない**結果**  
  
```json  
[ { "year":2015, "month":12, "day":15 } ]  
```  
  
 次に、**FOR JSON** 句で **WITHOUT_ARRAY_WRAPPER** オプションを指定した別の例を示します。  
  
 **Query**  
  
```tsql  
SELECT TOP 1 SalesOrderNumber, OrderDate, Status  
FROM Sales.SalesOrderHeader  
ORDER BY ModifiedDate  
FOR JSON PATH, WITHOUT_ARRAY_WRAPPER  
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使用した**結果**  
  
```json  
{  
    "SalesOrderNumber":"SO43660",  
    "OrderDate":"2011-05-31T00:00:00",  
    "Status":5  
}  
```  
  
 **WITHOUT_ARRAY_WRAPPER** オプションを使用しない**結果**  
  
```json  
[  
    {  
        "SalesOrderNumber":"SO43660",  
        "OrderDate":"2011-05-31T00:00:00",  
        "Status":5  
    }  
]  
```  
  
## 参照  
 [FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  