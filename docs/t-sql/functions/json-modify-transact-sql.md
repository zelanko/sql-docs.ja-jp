---
title: "JSON_MODIFY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 96bc8255-a037-4907-aec4-1a9c30814651
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70f2c1456da6469c39389fada6a74ccf46383582
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="jsonmodify-transact-sql"></a>JSON_MODIFY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON 文字列内のプロパティの値を更新し、更新された JSON 文字列を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
JSON_MODIFY ( expression , path , newValue )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 式。 通常、変数またはを JSON テキストを含む列の名前。  
  
 **JSON_MODIFY**エラーが返されます*式*有効な JSON が含まれていません。  
  
 *パス*  
 JSON のパスを指定する式を更新するプロパティです。

 *パス*に次の構文があります。  
  
 `[append] [ lax | strict ] $.<json path>`  
  
-   *追加します。*  
    によって参照される配列を新しい値を追加することを指定する省略可能な修飾子 *\<json のパス >*です。  
  
-   *厳密でないです。*  
    プロパティによって参照されることを示す *\<json のパス >*が存在する必要はありません。 プロパティが存在しない場合、JSON_MODIFY は指定されたパスに新しい値を挿入しようとします。 プロパティは、パスを挿入することはできない場合に、挿入が失敗する可能性があります。 指定しない場合は*lax*または*厳密な*、 *lax*既定モードです。  
  
-   *厳密です*  
    プロパティによって参照されることを示す *\<json のパス >* JSON 式である必要があります。 プロパティが存在しない場合、JSON_MODIFY はエラーを返します。  
  
-   *\<json のパス >*  
    更新するプロパティのパスを指定します。 詳細については、次を参照してください。 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]し、[!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)]、変数の値として使用できる*パス*です。

**JSON_MODIFY**エラーが返されますの形式*パス*が無効です。  
  
 *newValue*  
 指定されたプロパティの新しい値*パス*です。  
  
 厳密でないモードでは、JSON_MODIFY は、新しい値が NULL の場合に、指定したキーを削除します。  
  
JSON_MODIFY は、値の型が NVARCHAR または VARCHAR の場合、新しい値のすべての特殊文字をエスケープします。 適切である場合、テキスト値がエスケープされていない FOR JSON、JSON_QUERY、または JSON_MODIFY によって生成された JSON を書式設定します。  
  
## <a name="return-value"></a>戻り値  
 更新された値を返します*式*として正しく JSON テキストを書式設定します。  
  
## <a name="remarks"></a>解説  
 JSON_MODIFY 関数では、既存のプロパティの値を更新して、新しいキーと値のペアを挿入またはモードの組み合わせに基づいており、値を提供したキーを削除することができます。  
  
 次の表の動作を比較して**JSON_MODIFY**厳密でないモードでは厳格モードでします。 省略可能なパス モードの仕様 (lax または strict) に関する詳細については、次を参照してください。 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|既存の値|パスが存在します。|厳密でないモード|厳格モード|  
|--------------------|-----------------|--------------|-----------------|  
|NULL でないです。|はい|既存の値を更新します。|既存の値を更新します。|  
|NULL でないです。|不可|指定したパスに新しいキーと値のペアを作成しようとしてください。<br /><br /> これが失敗する可能性があります。 たとえば、パスを指定する場合`$.user.setting.theme`、JSON_MODIFY がキーを挿入できません`theme`場合、`$.user`または`$.user.settings`オブジェクトが存在しないかどうかの設定は、配列またはスカラー値またはします。|Error – INVALID_PROPERTY|  
|NULL|はい|既存のプロパティを削除します。|既存の値を null に設定します。|  
|NULL|不可|操作はありません。 最初の引数は、結果として返されます。|Error – INVALID_PROPERTY|  
  
 厳密でないモードでは、JSON_MODIFY は、新しいキーと値のペアを作成しようとしていますが、場合によっては失敗する可能性があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="example---basic-operations"></a>例 - 基本的な操作  
 次の例では、JSON テキストを実行する基本的な操作を示します。  
  
 **Query**  
  
```sql  

DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update name  

SET @info=JSON_MODIFY(@info,'$.name','Mike')

PRINT @info

-- Insert surname  

SET @info=JSON_MODIFY(@info,'$.surname','Smith')

PRINT @info

-- Delete name  

SET @info=JSON_MODIFY(@info,'$.name',NULL)

PRINT @info

-- Add skill  

SET @info=JSON_MODIFY(@info,'append $.skills','Azure')

PRINT @info
```  
  
 **[結果]**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---multiple-updates"></a>例 - 複数の更新プログラム  
 JSON_MODIFY では、1 つのプロパティを更新できます。 複数の更新プログラムを実行していれば、JSON_MODIFY の複数の呼び出しを使用できます。  
  
 **Query**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Multiple updates  

SET @info=JSON_MODIFY(JSON_MODIFY(JSON_MODIFY(@info,'$.name','Mike'),'$.surname','Smith'),'append $.skills','Azure')

PRINT @info
```  
  
 **[結果]**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---rename-a-key"></a>例 - 名前、キーの変更  
 次の例では、JSON_MODIFY 関数を含む JSON テキストでは、プロパティの名前を変更する方法を示します。 最初に既存のプロパティの値を取得し、新しいキーと値のペアとして挿入できます。 古いプロパティの値を NULL に設定して、以前のキーを削除することができます。  
  
 **Query**  
  
```sql  
DECLARE @product NVARCHAR(100)='{"price":49.99}'

PRINT @product

-- Rename property  

SET @product=
 JSON_MODIFY(
  JSON_MODIFY(@product,'$.Price',CAST(JSON_VALUE(@product,'$.price') AS NUMERIC(4,2))),
  '$.price',
  NULL
 )

PRINT @product
```  
  
 **[結果]**  
  
```json  
{
    "price": 49.99
} {
    "Price": 49.99
}
```  
  
 数値型に新しい値をキャストしない、JSON_MODIFY はテキストとして扱われ、二重引用符で囲みます。  
  
### <a name="example---increment-a-value"></a>増分値の使用例  
 次の例では、JSON_MODIFY 関数を含む JSON テキスト内のプロパティの値をインクリメントする方法を示します。 まず、既存のプロパティの値を取得し、新しいキーと値のペアとして挿入できます。 古いプロパティの値を NULL に設定して、以前のキーを削除することができます。  
  
 **Query**  
  
```sql  
DECLARE @stats NVARCHAR(100)='{"click_count": 173}'

PRINT @stats

-- Increment value  

SET @stats=JSON_MODIFY(@stats,'$.click_count',
 CAST(JSON_VALUE(@stats,'$.click_count') AS INT)+1)

PRINT @stats
```  
  
 **[結果]**  
  
```json  
{
    "click_count": 173
} {
    "click_count": 174
}
```  
  
### <a name="example---modify-a-json-object"></a>例 - JSON オブジェクトの変更  
 JSON_MODIFY の処理、 *newValue*引数を正しく含まれている場合でもプレーン テキストとして JSON テキストを書式設定します。 その結果、関数の JSON の出力は、二重引用符で囲まれてし、次の例で示すように、すべての特殊文字をエスケープします。  
  
 **Query**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array

SET @info=JSON_MODIFY(@info,'$.skills','["C#","T-SQL","Azure"]')

PRINT @info
```  
  
 **[結果]**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": "["C#","T-SQL","Azure"]"
}
```  
  
 自動エスケープを回避するには、 *newValue* JSON_QUERY 関数を使用しています。 JSON_MODIFY 認識 JSON_MODIFY によって返される値が適切に値をエスケープしないために、JSON を書式設定します。  
  
 **Query**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array  

SET @info=JSON_MODIFY(@info,'$.skills',JSON_QUERY('["C#","T-SQL","Azure"]'))

PRINT @info
```  
  
 **[結果]**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": ["C#", "T-SQL", "Azure"]
}
```  
  
### <a name="example---update-a-json-column"></a>例 - JSON 列の更新  
 次の例では、JSON を含むテーブル列のプロパティの値を更新します。  
  
```sql  
UPDATE Employee
SET jsonCol=JSON_MODIFY(jsonCol,"$.info.address.town",'London')
WHERE EmployeeID=17
 
```  
  
## <a name="see-also"></a>参照  
 [JSON パス式 & #40 です。SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [JSON データ & #40 です。SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  

