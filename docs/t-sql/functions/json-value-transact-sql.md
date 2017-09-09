---
title: "JSON_VALUE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ebb940035e4cad1ef898cfe83e1932db573848ab
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="jsonvalue-transact-sql"></a>JSON_VALUE (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON 文字列からには、スカラー値を抽出します。  
  
 スカラー値ではなく、JSON 文字列からオブジェクトまたは配列を抽出する、次を参照してください。 [JSON_QUERY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/json-query-transact-sql.md). 間の相違点について**JSON_VALUE**と**JSON_QUERY**を参照してください[JSON_VALUE の比較と JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
JSON_VALUE ( expression , path )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 式。 通常、変数またはを JSON テキストを含む列の名前。  
 
 場合**JSON_VALUE** JSON では無効ですが見つかった*式*で識別される値を検索する前に*パス*エラーを返します。 場合 **JSON_VALUE*で識別される値が検出されない*パス*, テキスト全体をスキャンし、JSON を検出した場合にエラーを返しますが、任意の場所で無効*式*です。
  
 *パス*  
 抽出するプロパティを指定する JSON のパス。 詳細については、次を参照してください。 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  
 
[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]し、[!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)]、変数の値として使用できる*パス*です。
  
 場合の形式*パス*が有効でない**JSON_VALUE**はエラーを返します。  
  
## <a name="return-value"></a>戻り値  
 型 nvarchar (4000) の 1 つのテキスト値を返します。 返される値の照合順序は、入力された式の照合順序と同じです。  
  
 値が 4,000 文字を超える場合は。  
  
-   厳密でないモード、 **JSON_VALUE**は null を返します。  
  
-   厳格モードで**JSON_VALUE**はエラーを返します。  
  
 返すスカラー値が 4,000 文字を超えていれば使用**OPENJSON**の代わりに**JSON_VALUE**です。 詳細については、「 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」をご覧ください。  
  
## <a name="remarks"></a>解説

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
  
 次の表の動作を比較して**JSON_VALUE**厳密でないモードでは厳格モードでします。 省略可能なパス モードの仕様 (lax または strict) に関する詳細については、次を参照してください。 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|[パス]|厳密でないモードでの戻り値|厳格モードでの戻り値|詳細|  
|----------|------------------------------|---------------------------------|---------------|  
|$|NULL|[エラー]|スカラー値ではありません。<br /><br /> 使用して**JSON_QUERY**代わりにします。|  
|$info.type。|N '1'|N '1'|該当なし|  
|$info.address.town。|N'Bristol'|N'Bristol'|該当なし|  
|$ .info。"アドレス|NULL|[エラー]|スカラー値ではありません。<br /><br /> 使用して**JSON_QUERY**代わりにします。|  
|$info.tags。|NULL|[エラー]|スカラー値ではありません。<br /><br /> 使用して**JSON_QUERY**代わりにします。|  
|$info.type[0]。|NULL|[エラー]|配列ではありません。|  
|$info.none。|NULL|[エラー]|プロパティが存在しません。|  
  
## <a name="examples"></a>使用例  
  
### <a name="example-1"></a>例 1  
 次の例は、JSON のプロパティの値を使用して`town`と`state`クエリの結果にします。 **JSON_VALUE**が保存されますが、ソースでは、結果の並べ替え順序の照合順序の照合順序によって異なります、`jsonInfo`列です。  
  
```sql  
SELECT FirstName,LastName,
 JSON_VALUE(jsonInfo,'$.info.address[0].town') AS Town
FROM Person.Person
WHERE JSON_VALUE(jsonInfo,'$.info.address[0].state') LIKE 'US%'
ORDER BY JSON_VALUE(jsonInfo,'$.info.address[0].town')
```  
  
### <a name="example-2"></a>例 2  
 次の例は、JSON のプロパティの値を抽出`town`ローカル変数に代入します。  
  
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
 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [JSON データ & #40 です。SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  

