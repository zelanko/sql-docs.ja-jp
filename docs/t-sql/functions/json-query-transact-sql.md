---
title: "JSON_QUERY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JSON_QUERY
- JSON_QUERY_TSQL
helpviewer_keywords:
- JSON, extracting
- JSON, querying
- JSON_QUERY function
ms.assetid: 1ab0d90f-19b6-4988-ab4f-22fdf28b7c79
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 56b50c0497a2e0ee40f9cf086124eba8e55bdd03
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="jsonquery-transact-sql"></a>JSON_QUERY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 オブジェクトまたは配列を JSON 文字列から抽出します。  
  
 オブジェクトまたは配列ではなく、JSON 文字列からスカラー値を抽出する、次を参照してください。 [JSON_VALUE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/json-value-transact-sql.md). 間の相違点について**JSON_VALUE**と**JSON_QUERY**を参照してください[JSON_VALUE の比較と JSON_QUERY](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md#JSONCompare)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
JSON_QUERY ( expression [ , path ] )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 式。 通常、変数またはを JSON テキストを含む列の名前。  
  
 場合**JSON_QUERY** JSON では無効ですが見つかった*式*で識別される値を検索する前に*パス*エラーを返します。 場合**JSON_QUERY**で識別される値が検出されない*パス*, テキスト全体をスキャンし、JSON を検出した場合にエラーを返しますが、任意の場所で無効*式*です。  
  
 *パス*  
 オブジェクトまたは抽出先の配列を指定する JSON のパス。

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]し、[!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)]、変数の値として使用できる*パス*です。

JSON のパスを解析するための lax または strict モードを指定できます。 解析モードを指定しない場合は、既定値は lax モードです。 詳細については、次を参照してください。 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  

既定値*パス*'$' がします。 値を指定しない場合、結果として*パス*、 **JSON_QUERY** 、入力を返します*式*です。

場合の形式*パス*が有効でない**JSON_QUERY**はエラーを返します。  
  
## <a name="return-value"></a>戻り値  
 型 nvarchar (max) の JSON フラグメントを返します。 返される値の照合順序は、入力された式の照合順序と同じです。  
  
 場合は、値は、オブジェクトまたは配列には。  
  
-   厳密でないモード、 **JSON_QUERY**は null を返します。  
  
-   厳格モードで**JSON_QUERY**はエラーを返します。  
  
## <a name="remarks"></a>解説  

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
  
 次の表の動作を比較して**JSON_QUERY**厳密でないモードでは厳格モードでします。 省略可能なパス モードの仕様 (lax または strict) に関する詳細については、次を参照してください。 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|[パス]|厳密でないモードでの戻り値|厳格モードでの戻り値|詳細|  
|----------|------------------------------|---------------------------------|---------------|  
|$|全体の JSON テキストを返します。|全体の JSON テキストを返します。|該当なし|  
|$info.type。|NULL|[エラー]|いないオブジェクトまたは配列。<br /><br /> 使用して**JSON_VALUE**代わりにします。|  
|$info.address.town。|NULL|[エラー]|いないオブジェクトまたは配列。<br /><br /> 使用して**JSON_VALUE**代わりにします。|  
|$ .info。"アドレス|N'{「町」:「板紙」で、"郡": ある"Avon"、「国」:"England"}'|N'{「町」:「板紙」で、"郡": ある"Avon"、「国」:"England"}'|該当なし|  
|$info.tags。|N '[「スポーツ」、「Water ポーロ」]'|N '[「スポーツ」、「Water ポーロ」]'|該当なし|  
|$info.type[0]。|NULL|[エラー]|配列ではありません。|  
|$info.none。|NULL|[エラー]|プロパティが存在しません。|  

### <a name="using-jsonquery-with-for-json"></a>FOR JSON と JSON_QUERY を使用します。

**JSON_QUERY**有効な JSON フラグメントを返します。 その結果、 **FOR JSON**内の特殊文字をエスケープしない、 **JSON_QUERY**値を返します。

FOR JSON で結果を返す場合、(列または式の結果として) の JSON 形式では既にデータを含むしている場合は、ラップを使用して JSON データ**JSON_QUERY**せず、*パス*パラメーター。

## <a name="examples"></a>使用例  
  
### <a name="example-1"></a>例 1  
 次の例からの JSON フラグメントを返す方法を示しています、`CustomFields`クエリ結果内の列です。  
  
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
 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [JSON データ & #40 です。SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  

