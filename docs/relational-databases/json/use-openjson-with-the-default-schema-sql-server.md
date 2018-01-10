---
title: "既定のスキーマを使用する OPENJSON の使用 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.component: json
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: OPENJSON, with default schema
ms.assetid: 8e28a8f8-71a8-4c25-96b8-0bbedc6f41c4
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3da875380580bcf7151db13c0b14280a9790d5dc
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="use-openjson-with-the-default-schema-sql-server"></a>既定のスキーマを使用する OPENJSON の使用 (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  オブジェクトのプロパティごと、または配列内の要素ごとに 1 つの行が含まれたテーブルを返すには、既定のスキーマを使用して **OPENJSON** を使用します。  
  
 ここでは、既定のスキーマを使用して **OPENJSON** を使用する例をいくつか紹介します。 詳細とその他の例については、「 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」を参照してください。  
  
## <a name="example---return-each-property-of-an-object"></a>例 - オブジェクトの各プロパティを返す  
 **クエリ**  
  
```sql  
SELECT *
FROM OPENJSON('{"name":"John","surname":"Doe","age":45}') 
```  
  
 **結果**  
  
|Key|ReplTest1|  
|---------|-----------|  
|NAME|John|  
|姓|Doe|  
|age|45|  
  
## <a name="example---return-each-element-of-an-array"></a>例 - 配列の各要素を返す  
 **クエリ**  
  
```sql  
SELECT [key],value
FROM OPENJSON('["en-GB", "en-UK","de-AT","es-AR","sr-Cyrl"]') 
```  
  
 **結果**  
  
|Key|ReplTest1|  
|---------|-----------|  
|0|en-GB|  
|@shouldalert|en 英国|  
|2|de AT|  
|3|es AR|  
|4|sr という|  
  
## <a name="example---convert-json-to-a-temporary-table"></a>例 - JSON を一時テーブルに変換する  
 次のクエリのすべてのプロパティを返します、 **情報** オブジェクトです。  
  
```sql  
DECLARE @json NVARCHAR(MAX)

SET @json=N'{  
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

SELECT *
FROM OPENJSON(@json,N'lax $.info')
```  
  
 **[結果]**  
  
|Key|ReplTest1|型|  
|---------|-----------|----------|  
|型|@shouldalert|0|  
|address|{ "town":"Bristol", "county":"Avon", "country":"England" }|5|  
|タグ|[「スポーツ」、「Water ポーロ」]|4|  
  
## <a name="example---combine-relational-data-and-json-data"></a>例 - リレーショナル データと JSON データを結合する  
 次の例では、JSON 形式で SalesOrderReasons の配列を含む SalesReason テキスト列が、SalesOrderHeader テーブルにあります。 SalesOrderReasons オブジェクトには、"品質" と "製造元" のようなプロパティが含まれます。 この例では、販売理由が別個の子テーブルに含まれているかのように販売理由の JSON 配列を展開して、すべての販売注文行を関連する販売理由に結合するレポートを作成します。  
  
```sql  
SELECT SalesOrderID,OrderDate,value AS Reason
FROM Sales.SalesOrderHeader
CROSS APPLY OPENJSON(SalesReasons)
```  
  
 この例では、OPENJSON から販売理由のテーブルが返されます。このテーブルでは、販売理由が値列として示されます。 CROSS APPLY 演算子は、OPENJSON テーブル値関数によって返される行に各販売注文の行を結合します。  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>SQL Server に組み込まれている JSON サポートの詳細情報  
多くの具体的なソリューション、ユース ケース、推奨事項については、Microsoft のプログラム マネージャー Jovan Popovic による SQL Server および Azure SQL Database に[組み込まれている JSON のサポートに関するブログ投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)をご覧ください。
  
## <a name="see-also"></a>参照  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  
