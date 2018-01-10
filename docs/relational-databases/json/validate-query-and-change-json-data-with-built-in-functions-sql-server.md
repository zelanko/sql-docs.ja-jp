---
title: "組み込み関数を使用した JSON データの検証、クエリ、変更 (SQL Server) | Microsoft Docs"
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
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: "21"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 737ed53b4c69a797a11b38c59a4939c244af7b98
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>組み込み関数を使用した JSON データの検証、クエリ、変更 (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

JSON の組み込みのサポートには、次の組み込み関数が含まれています。このトピックでは、これらの関数について簡単に説明します。  
  
-   [ISJSON](#ISJSON) 。文字列に有効な JSON が含まれているかどうかをテストします。  
  
-   [JSON_VALUE](#VALUE) 。JSON 文字列からスカラー値を抽出します。  
  
-   [JSON_QUERY](#QUERY) 。JSON 文字列からオブジェクトまたは配列を抽出します。  
  
-   [JSON_MODIFY](#MODIFY) 。JSON 文字列内のプロパティの値を更新し、更新された JSON 文字列を返します。  
 
## <a name="json-text-for-the-examples-on-this-page"></a>このページの例の JSON テキスト
このページの例では、複合要素が含まれる次の JSON テキストを使用しています。

```sql 
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
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

##  <a name="ISJSON"></a> ISJSON 関数を使用して JSON テキストを検証する  
 **ISJSON** 関数は、文字列に有効な JSON が含まれているかどうかをテストします。  
  
次の例は、列 `json_col` に有効な JSON が含まれている行を返します。  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  

詳細については、「 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)」を参照してください。  
  
##  <a name="VALUE"></a> JSON_VALUE 関数を使用して、JSON テキストから値を抽出する  
**JSON_VALUE** 関数は、JSON 文字列からスカラー値を抽出します。  
  
次の例では、入れ子になった JSON のプロパティ `town` の値をローカル変数に抽出します。  
  
```sql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
詳細については、「 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)」をご覧ください。  
  
##  <a name="QUERY"></a> JSON_QUERY 関数を使用して JSON テキストからオブジェクトまたは配列を抽出する  
**JSON_QUERY** 関数は、JSON 文字列からオブジェクトまたは配列を抽出します。  
 
次の例では、クエリの結果には JSON フラグメントを返す方法を示します。  
  
```sql  
SELECT FirstName, LastName, JSON_QUERY(jsonInfo,'$.info.address') AS Address
FROM Person.Person
ORDER BY LastName
```  
  
詳細については、「 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)」を参照してください。  
  
##  <a name="JSONCompare"></a> JSON_VALUE と JSON_QUERY を比較する  
**JSON_VALUE** と **JSON_QUERY** の主な違いは、 **JSON_VALUE** はスカラー値を返しますが、 **JSON_QUERY** はオブジェクトまたは配列を返す点です。  
  
次のようなサンプル JSON テキストがあるとします。  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
このサンプル JSON テキストでは、データ メンバー "a" と "c" は文字列値ですが、データ メンバー "b" は配列です。 **JSON_VALUE** と **JSON_QUERY** は、次の結果を返します。  
  
|[パス]|**JSON_VALUE** が返す結果|**JSON_QUERY** が返す結果|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL またはエラー|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL またはエラー|  
|**$.b**|NULL またはエラー|[1,2]|  
|**$.b[0]**|@shouldalert|NULL またはエラー|  
|**$.c**|hi|NULL またはエラー|  
  
## <a name="test-jsonvalue-and-jsonquery-with-the-adventureworks-sample-database"></a>AdventureWorks サンプル データベースを使用して JSON_VALUE と JSON_QUERY をテストする  
このトピックで説明した組み込み関数をテストするには、AdventureWorks サンプル データベースを使用して次の例を実行します。 AdventureWorks の入手先と、スクリプトを実行してテストするための JSON データの追加方法について詳しくは、「[組み込みの JSON サポートを試用する](json-data-sql-server.md#test-drive-built-in-json-support)」をご覧ください。
  
次の例では、`SalesOrder_json` テーブルの `Info` 列に JSON テキストが含まれています。  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>例 1: 標準の列と JSON データの両方を返す  
次のクエリは、標準のリレーショナル列と JSON 列の両方から値を返します。  
  
```sql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info) > 0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>例 2: JSON 値の集計とフィルター  
次のクエリは、(JSON に格納されている) 顧客名と (通常の列に格納されている) 状態別に小計を集計します。 次に、(JSON に格納されている) 市区町村と (通常の列に格納されている) OrderDate で結果をフィルターします。  
  
```sql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city
 AND OrderDate > '1/1/2015'
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="MODIFY"></a> JSON_MODIFY 関数を使用して JSON テキストのプロパティ値を更新する  
**JSON_MODIFY** 関数は、JSON 文字列内のプロパティの値を更新し、更新された JSON 文字列を返します。  
  
次の例では、JSON を格納する変数の JSON プロパティの値を更新します。  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 詳細については、「 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)」を参照してください。  
  
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
  
## <a name="see-also"></a>参照  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  
