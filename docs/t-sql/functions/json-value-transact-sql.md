---
title: JSON_VALUE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- JSON_VALUE
- JSON_VALUE_TSQL
helpviewer_keywords:
- JSON_VALUE function
- JSON, extracting
- JSON, querying
ms.assetid: cd016e14-11eb-4eaf-bf05-c7cfcc820a10
caps.latest.revision: 18
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: 9bbd4dd23c4c536fa70f679ceabf6d96ddde121c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="jsonvalue-transact-sql"></a>JSON_VALUE (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON 文字列からには、スカラー値を抽出します。  
  
 JSON 文字列からスカラー値ではなくオブジェクトまたは配列を抽出する場合は、「[JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)」を参照してください。 **JSON_VALUE** と **JSON_QUERY** の違いについては、「[JSON_VALUE と JSON_QUERY を比較する](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
JSON_VALUE ( expression , path )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 式。 通常、変数またはを JSON テキストを含む列の名前。  
 
 **JSON_VALUE** が、*path* によって識別される値を検出する前に *expression* で無効な JSON を検出した場合、関数はエラーを返します。 **JSON_VALUE* が *path* によって識別される値を検出できない場合、テキスト全体がスキャンされ、*expression* のどこかで無効な JSON を検出した場合はエラーを返します。
  
 *path*  
 抽出するプロパティを指定する JSON のパス。 詳細については、「[JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)」を参照してください。  
 
[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] と [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)] では、*path* の値として変数を指定できます。
  
 *path* の書式が有効でない場合、**JSON_VALUE** はエラーを返します。  
  
## <a name="return-value"></a>戻り値  
 型 nvarchar (4000) の 1 つのテキスト値を返します。 返される値の照合順序は、入力された式の照合順序と同じです。  
  
 値が 4,000 文字を超える場合は。  
  
-   厳密でないモードでは、**JSON_VALUE** は null を返します。  
  
-   厳格モードでは、**JSON_VALUE** はエラーを返します。  
  
 4,000 文字を超えるスカラー値を返す必要がある場合は、**JSON_VALUE** の代わりに **OPENJSON** を使用します。 詳細については、「 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」をご覧ください。  
  
## <a name="remarks"></a>Remarks

### <a name="lax-mode-and-strict-mode"></a>厳密でないモードと厳格モード

 次の JSON テキストを考慮してください。  
  
```json  
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
  
 次の表は、厳密でないモードと厳格モードでの **JSON_VALUE** の動作を比較します。 省略可能なパス モード (厳密でない、または厳格) の指定について詳しくは、「[JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)」を参照してください。  
  
|[パス]|厳密でないモードでの戻り値|厳格モードでの戻り値|詳細|  
|----------|------------------------------|---------------------------------|---------------|  
|$|NULL|[エラー]|スカラー値ではありません。<br /><br /> 代わりに **JSON_QUERY** を使用します。|  
|$info.type。|N '1'|N '1'|該当なし|  
|$.info.address.town|N'Bristol'|N'Bristol'|該当なし|  
|$ .info。"アドレス|NULL|[エラー]|スカラー値ではありません。<br /><br /> 代わりに **JSON_QUERY** を使用します。|  
|$info.tags。|NULL|[エラー]|スカラー値ではありません。<br /><br /> 代わりに **JSON_QUERY** を使用します。|  
|$info.type[0]。|NULL|[エラー]|配列ではありません。|  
|$info.none。|NULL|[エラー]|プロパティが存在しません。|  
  
## <a name="examples"></a>使用例  
  
### <a name="example-1"></a>例 1  
 次の例では、クエリの結果に JSON のプロパティの値 `town` と `state` を使用します。 **JSON_VALUE** がソースの照合順序を保持するため、結果の並べ替え順序が `jsonInfo` 列の照合順序に依存します。 

> [!NOTE]
> (この例では、`Person.Person` という名前のテーブルが JSON テキストの `jsonInfo` 列を含み、またこの列が、前の厳密でないモードと厳格モードの説明で示した構造を持っていることを前提としています。 AdventureWorks サンプル データベースでは、`Person` テーブルは実は `jsonInfo` 列を含んでいません。)
  
```sql  
SELECT FirstName, LastName,
 JSON_VALUE(jsonInfo,'$.info.address[0].town') AS Town
FROM Person.Person
WHERE JSON_VALUE(jsonInfo,'$.info.address[0].state') LIKE 'US%'
ORDER BY JSON_VALUE(jsonInfo,'$.info.address[0].town')
```  
  
### <a name="example-2"></a>例 2  
 次の例では、ローカル変数に JSON プロパティの値 `town` を抽出します。  
  
```sql  
DECLARE @jsonInfo NVARCHAR(MAX)
DECLARE @town NVARCHAR(32)

SET @jsonInfo=N'<array of address info>'

SET @town=JSON_VALUE(@jsonInfo,'$.info.address.town')
```  
  
### <a name="example-3"></a>例 3  
 次の例では、JSON のプロパティの値に基づいて、計算列を作成します。  
  
```sql  
CREATE TABLE dbo.Store
 (
  StoreID INT IDENTITY(1,1) NOT NULL,
  Address VARCHAR(500),
  jsonContent NVARCHAR(8000),
  Longitude AS JSON_VALUE(jsonContent, '$.address[0].longitude'),
  Latitude AS JSON_VALUE(jsonContent, '$.address[0].latitude')
 )
```  
  
## <a name="see-also"></a>参照  
 [JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [JSON データ &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  
