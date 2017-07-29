---
title: "明示的なスキーマで OPENJSON を使用する (SQL Server) | Microsoft Docs"
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
- OPENJSON, with explicit schema
ms.assetid: 9c1c3bfb-e1ad-4659-b94f-722b0848d5a2
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: c96f36b9f59f5cd091dfa3e61be9e1cf7e744f3d
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="use-openjson-with-an-explicit-schema-sql-server"></a>明示的なスキーマで OPENJSON を使用する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **OPENJSON** と共に明示的なスキーマを使用し、WITH 句で指定した書式設定のテーブルを返します。  
  
 ここでは、 **OPENJSON** と明示的なスキーマを使用する例をいくつか紹介します。 詳細とその他の例については、 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)を参照してください。  
  
## <a name="example---use-the-with-clause-to-format-the-output"></a>例 - WITH 句を使用し、出力を書式設定する  
 次のクエリでは、次の表に示すように結果を返します。 JSON の AS 句が col5 および array_element でスカラー値ではなく、JSON オブジェクトとして返される値がどのように発生する方法に注意してください。  
  
```sql  
DECLARE @json NVARCHAR(MAX) =
N'{"someObject":   
    {"someArray":  
      [  
          {"k1": 11, "k2": null, "k3": "text"},  
          {"k1": 21, "k2": "text2", "k4": { "data": "text4" }},  
          {"k1": 31, "k2": 32},  
          {"k1": 41, "k2": null, "k4": { "data": false }}     
       ]  
    }  
 }'  
   
SELECT * FROM  
 OPENJSON(@json, N'lax $.someObject.someArray')  
WITH ( k1 int,   
        k2 varchar(100),  
        col3 varchar(6) N'$.k3',  
        col4 varchar(10) N'lax $.k4.data',  
        col5 nvarchar(MAX) N'lax $.k4' AS JSON, 
        array_element nvarchar(MAX) N'$' AS JSON  
 )  
```  
  
 **[結果]**  
  
|k1|k2|col3|col4|col5|array_element|  
|--------|--------|----------|----------|----------|--------------------|  
|11|*NULL*|"text"|*NULL*|*NULL*|{"k1": 11、"k2": null の場合、"k3":"text"}|  
|21|テキスト「2」|*NULL*|テキスト「4」|{「データ」:"テキスト"が 4}|{"k1": true,"k2":"text2"、"k4": {「データ」: テキスト「4」}}|  
|31|"32"|*NULL*|*NULL*|*NULL*|{"k1": 31 日"k2": 32}|  
|41|*NULL*|*NULL*|オプション|{「データ」: false}|{"k1": 41、"k2": null の場合、"k4": {「データ」: false}}|  
  
## <a name="example---load-json-into-a-includessnoversionincludesssnoversion-mdmd-table"></a>例 - JSON を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに読み込む。  
 次の例では、全体の JSON オブジェクトを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルです。  
  
```sql  
DECLARE @json NVARCHAR(MAX) = '{  
  "id" : 2,  
  "firstName": "John",  
  "lastName": "Smith",  
  "isAlive": true,  
  "age": 25,  
  "dateOfBirth": "2015-03-25T12:00:00",  
  "spouse": null  
  }';  
   
  INSERT INTO Person  
  SELECT *   
  FROM OPENJSON(@json)  
  WITH (id int,  
        firstName nvarchar(50), lastName nvarchar(50),   
        isAlive bit, age int,  
        dateOfBirth datetime2, spouse nvarchar(50))  
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>詳細については、組み込みの JSON が SQL Server のサポート  
特定のソリューションの多くは、ケース、および推奨事項を使用して、参照してください、[組み込みの JSON サポートに関するブログの投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)SQL Server および Microsoft のプログラム マネージャー Jovan Popovic による Azure SQL データベースでします。
  
## <a name="see-also"></a>参照  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)  
  
  

