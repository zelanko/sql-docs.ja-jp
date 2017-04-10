---
title: "組み込み関数を使用した JSON データの検証、クエリ、変更 (SQL Server) | Microsoft Docs"
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
  - "JSON、組み込み関数"
  - "関数 (JSON)"
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# 組み込み関数を使用した JSON データの検証、クエリ、変更 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON の組み込みのサポートには、次の組み込み関数が含まれています。このトピックでは、これらの関数について説明します。  
  
-   [ISJSON](#ISJSON) 。文字列に有効な JSON が含まれているかどうかをテストします。  
  
-   [JSON_VALUE](#VALUE)。JSON 文字列からスカラー値を抽出します。  
  
-   [JSON_QUERY](#QUERY)。JSON 文字列からオブジェクトまたは配列を抽出します。  
  
-   [JSON_MODIFY](#MODIFY)。JSON 文字列内のプロパティの値を更新し、更新された JSON 文字列を返します。  
  
##  <a name="ISJSON"></a> ISJSON 関数を使用して JSON テキストを検証する  
 **ISJSON** 関数は、文字列に有効な JSON が含まれているかどうかをテストします。  
  
 次の例は、列には、有効な JSON が含まれている場合に、JSON テキストを返します。  
  
```tsql  
SELECT id, json_col  
FROM tab1  
WHERE ISJSON(json_col) > 0  
```  
  
 詳細については、「[ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)」を参照してください。  
  
##  <a name="VALUE"></a> JSON_VALUE 関数を使用して、JSON テキストから値を抽出する  
 **JSON_VALUE** 関数は、JSON 文字列からスカラー値を抽出します。  
  
 次の例では、ローカル変数に JSON のプロパティの値を抽出します。  
  
```tsql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
 詳細については、「[JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)」をご覧ください。  
  
##  <a name="QUERY"></a> JSON_QUERY 関数を使用して JSON テキストからオブジェクトまたは配列を抽出する  
 **JSON_QUERY** 関数は、JSON 文字列からオブジェクトまたは配列を抽出します。  
  
 次のサンプル JSON テキストには、複合型の要素が含まれています。  
  
```json  
DECLARE @jsonInfo VARCHAR(MAX)  
SET @jsonInfo = N'{  
    "info":{    
      "type":1,  
      "address":{    
        "town":"Bristol",  
        "county":"Avon",  
        "country":"England"  
      },  
      "tags":["Sport", "Water polo"]  
   },  
   "type":"Basic"  
}'  
```  
  
 次の例では、クエリの結果には JSON フラグメントを返す方法を示します。  
  
```tsql  
SELECT FirstName, LastName,   
       JSON_QUERY(jsonInfo, '$.info.address') AS Address  
FROM Person.Person  
ORDER BY LastName  
```  
  
 詳細については、「[JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)」をご覧ください。  
  
##  <a name="JSONCompare"></a> JSON_VALUE と JSON_QUERY を比較する  
 **JSON_VALUE** と **JSON_QUERY** の主な違いは、**JSON_VALUE** はスカラー値を返しますが、**JSON_QUERY** はオブジェクトまたは配列を返す点です。  
  
 次のようなサンプル JSON テキストがあるとします。  
  
```json  
{ "a": "[1,2]", "b": [1,2], "c": "hi" }  
```  
  
 このサンプル JSON テキストでは、データ メンバー "a" と "c" は文字列値ですが、データ メンバー "b" は配列です。 **JSON_VALUE** と **JSON_QUERY** は、次の結果を返します。  
  
|Query|**JSON_VALUE** が返す結果|**JSON_QUERY** が返す結果|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL またはエラー|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL またはエラー|  
|**$.b**|NULL またはエラー|[1,2]|  
|**$.b[0]**|1|NULL またはエラー|  
|**$.c**|hi|NULL またはエラー|  
  
## AdventureWorks サンプル データベースを使用して JSON_VALUE と JSON_QUERY をテストする  
 このトピックで説明した組み込み関数をテストするには、JSON データが含まれている AdventureWorks サンプル データベースを使用して次の例を実行します。 AdventureWorks サンプル データベースを入手するには、 [こちらをクリック](http://www.microsoft.com/en-us/download/details.aspx?id=49502)してください。  
  
 次の例では、SalesOrder_json テーブルの Info 列に JSON テキストが含まれています。  
  
### 例 1: 標準の列と JSON データの両方を返す  
 次のクエリは、標準のリレーショナル列と JSON 列の値の両方を返します。  
  
```tsql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,  
             JSON_QUERY(Info, '$.ShippingInfo') ShippingInfo,  
             JSON_QUERY(Info, '$.BillingInfo') BillingInfo,  
             JSON_VALUE(Info, '$.SalesPerson.Name') SalesPerson,  
             JSON_VALUE(Info, '$.ShippingInfo.City') City,  
             JSON_VALUE(Info, '$.Customer.Name') Customer,  
             JSON_QUERY(OrderItems, '$') OrderItems  
FROM Sales.SalesOrder_json  
WHERE ISJSON(Info) > 0  
  
```  
  
### 例 2: JSON 値の集計とフィルター  
 次のクエリは、(JSON に格納されている) 顧客名と (通常の列に格納されている) 状態別に小計を集計します。 次に、(JSON に格納されている) 市区町村と (通常の列に格納されている) OrderDate で結果をフィルターします。  
  
```tsql  
SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total  
FROM Sales.SalesOrder_json  
WHERE TerritoryID = @territoryid  
AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city  
AND OrderDate > '1/1/2015'  
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status  
HAVING SUM(SubTotal) > 1000  
  
```  
  
##  <a name="MODIFY"></a> JSON_MODIFY 関数を使用して JSON テキストのプロパティ値を更新する  
 **JSON_MODIFY** 関数は、JSON 文字列内のプロパティの値を更新し、更新された JSON 文字列を返します。  
  
 次の例では、JSON を格納する変数のプロパティの値を更新します。  
  
```tsql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')  
```  
  
 詳細については、「[JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)」をご覧ください。  
  
## SQL Server に組み込まれている JSON サポートの詳細情報  
 [Microsoft のプログラム マネージャー Jovan Popovic によるブログ記事](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## 参照  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  