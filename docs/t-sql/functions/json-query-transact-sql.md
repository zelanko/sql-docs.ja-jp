---
title: JSON_QUERY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: douglasl
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- JSON_QUERY
- JSON_QUERY_TSQL
helpviewer_keywords:
- JSON, extracting
- JSON, querying
- JSON_QUERY function
ms.assetid: 1ab0d90f-19b6-4988-ab4f-22fdf28b7c79
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: 5b2436f7ed1f8c32ba0d9b69f9d98e7092d340f7
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38022827"
---
# <a name="jsonquery-transact-sql"></a>JSON_QUERY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 オブジェクトまたは配列を JSON 文字列から抽出します。  
  
 オブジェクトまたは配列ではなく JSON 文字列からスカラー値を抽出する場合は、「[JSON_VALUE &#40;TRANSACT-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)」を参照してください。 **JSON_VALUE** と **JSON_QUERY** の違いについては、「[JSON_VALUE と JSON_QUERY を比較する](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
JSON_QUERY ( expression [ , path ] )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 式。 通常、変数またはを JSON テキストを含む列の名前。  
  
 **JSON_QUERY** が、*path* によって識別される値を検出する前に *expression* で無効な JSON を検出した場合、関数はエラーを返します。 **JSON_QUERY** が *path* によって識別される値を検出できない場合、テキスト全体がスキャンされ、*expression* のどこかで無効な JSON を検出した場合はエラーを返します。  
  
 *path*  
 オブジェクトまたは抽出先の配列を指定する JSON のパス。

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] と [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)] では、*path* の値として変数を指定できます。

JSON のパスを解析するための厳密でないまたは strict モードを指定できます。 解析モードの指定がない場合は、厳密でないモードが既定で指定されます。 詳細については、「[JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)」を参照してください。  

*path* の既定値は '$' です。 この結果、*path* の値を指定しない場合、**JSON_QUERY** は、入力された *expression* を返します。

*path* の書式が有効でない場合、**JSON_QUERY** はエラーを返します。  
  
## <a name="return-value"></a>戻り値  
 型 nvarchar (max) の JSON フラグメントを返します。 返される値の照合順序は、入力された式の照合順序と同じです。  
  
 場合は、値は、オブジェクトまたは配列には。  
  
-   厳密でないモードで **JSON_QUERY** は null を返します。  
  
-   厳格モードで **JSON_QUERY** はエラーを返します。  
  
## <a name="remarks"></a>Remarks  

### <a name="lax-mode-and-strict-mode"></a>厳密でないモードと厳格モード

 次の JSON テキストを考慮してください。  
  
```json  
{
    "info": {
        "type": 1,
        "address": {
            "town": "Bristol",
            "county": "Avon",
            "country": "England"
        },
        "tags": ["Sport", "Water polo"]
    },
    "type": "Basic"
} 
```  
  
 次の表は、lax モードと strict モードでの **JSON_MODIFY** の動作を比較します。 省略可能なパス モード (厳密でない、または厳格) の指定について詳しくは、「[JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)」を参照してください。  
  
|[パス]|厳密でないモードでの戻り値|厳格モードでの戻り値|詳細|  
|----------|------------------------------|---------------------------------|---------------|  
|$|全体の JSON テキストを返します|全体の JSON テキストを返します|該当なし|  
|$info.type。|NULL|[エラー]|オブジェクトまたは配列されません。<br /><br /> 代わりに **JSON_VALUE** を使用します。|  
|$.info.address.town|NULL|[エラー]|オブジェクトまたは配列されません。<br /><br /> 代わりに **JSON_VALUE** を使用します。|  
|$ .info。"アドレス|N'{ "town":"Bristol", "county":"Avon", "country":"England" }'|N'{ "town":"Bristol", "county":"Avon", "country":"England" }'|該当なし|  
|$info.tags。|N'[ "Sport", "Water polo"]'|N'[ "Sport", "Water polo"]'|該当なし|  
|$info.type[0]。|NULL|[エラー]|配列ではありません。|  
|$info.none。|NULL|[エラー]|プロパティが存在しません。|  

### <a name="using-jsonquery-with-for-json"></a>JSON_QUERY と FOR JSON の使用

**JSON_QUERY** は、有効な JSON フラグメントを返します。 その結果、**FOR JSON** は、**JSON_QUERY** 戻り値内の特殊文字をエスケープしません。

FOR JSON を使用して結果を返すときに (列内または式の結果として) 既に JSON 形式になっているデータを含める場合は、*path* パラメーターなしで **JSON_QUERY** を使用して JSON データをラップします。

## <a name="examples"></a>使用例  
  
### <a name="example-1"></a>例 1  
 次の例では、クエリの結果内の `CustomFields` 列から JSON フラグメントを返す方法を示します。  
  
```sql  
SELECT PersonID,FullName,
 JSON_QUERY(CustomFields,'$.OtherLanguages') AS Languages
FROM Application.People
```  
  
### <a name="example-2"></a>例 2  
次の例では、JSON の FOR 句の出力に JSON フラグメントを含める方法を示します。  
  
```sql  
SELECT StockItemID, StockItemName,
         JSON_QUERY(Tags) as Tags,
         JSON_QUERY(CONCAT('["',ValidFrom,'","',ValidTo,'"]')) ValidityPeriod
FROM Warehouse.StockItems
FOR JSON PATH
```  
  
## <a name="see-also"></a>参照  
 [JSON パス式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [JSON データ &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
