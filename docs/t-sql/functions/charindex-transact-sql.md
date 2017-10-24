---
title: "Charindex 関数 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CHARINDEX
- CHARINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], pattern searching
- CHARINDEX function
- pattern searching [SQL Server]
- starting point of expression in character string
ms.assetid: 78c10341-8373-4b30-b404-3db20e1a3ac4
caps.latest.revision: 52
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 5467f9d98562fac8262e537887d03c1d68b25d88
ms.contentlocale: ja-jp
ms.lasthandoff: 10/12/2017

---
# <a name="charindex-transact-sql"></a>CHARINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

別の式から式を検索し、見つかった場合は開始位置を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CHARINDEX ( expressionToFind , expressionToSearch [ , start_location ] )   
```  
  
## <a name="arguments"></a>引数  
*expressionToFind*  
文字[式](../../t-sql/language-elements/expressions-transact-sql.md)を検索するシーケンスを格納しています。 *expressionToFind*は 8,000 文字に制限されます。
  
*expressionToSearch*  
検索する文字式です。
  
*start_location*  
**整数**または**bigint**検索を開始する式。 場合*start_location*が指定されていない、負の数値、または 0 の先頭から検索が開始*expressionToSearch*です。
  
## <a name="return-types"></a>戻り値の型
**bigint**場合*expressionToSearch*は、 **varchar (max)**、 **nvarchar (max)**、または**varbinary (max)**データ型です。それ以外の場合、 **int**です。
  
## <a name="remarks"></a>解説  
いずれか*expressionToFind*または*expressionToSearch*が Unicode データ型 (**nvarchar**または**nchar**) がないと、その他は、Unicode データ型に変換されます。 Charindex 関数では使用できません**テキスト**、 **ntext**、および**イメージ**データ型。
  
いずれか*expressionToFind*または*expressionToSearch*が NULL の場合、CHARINDEX は NULL を返します。
  
場合*expressionToFind*内に見つからなかった*expressionToSearch*CHARINDEX は 0 を返します。
  
CHARINDEX は、入力の照合順序に基づいて比較を行います。 指定した照合順序で比較を実行するには、COLLATE を使って入力に明示的な照合順序を適用できます。
  
開始位置は 0 ではなく 1 を基準とします。
  
0x0000 (**char (0)**) の Windows 照合順序で未定義の文字は、CHARINDEX に含めることはできません。
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
SC の照合順序を使用する場合両方*start_location*と戻り値の数のサロゲート ペアない 2 つを 1 文字として。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-starting-position-of-an-expression"></a>A. 式の開始位置を返す  
位置を返す例を次の文字のシーケンス`bicycle`でを起動、`DocumentSummary`の列、`Document`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。
  
```sql
DECLARE @document varchar(64);  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bicycle', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
48            
```  
  
### <a name="b-searching-from-a-specific-position"></a>B. 特定の位置から検索する  
次の例は、省略可能な*start_location*検索を開始するパラメーター`vital`の 5 文字で、`DocumentSummary`内の列、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('vital', @document, 5);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
-----------   
16            
  
(1 row(s) affected)  
```  
  
### <a name="c-searching-for-a-nonexistent-expression"></a>C. 存在しない式を検索する  
結果セットの場合に、次の例に示す*expressionToFind*内に見つからなかった*expressionToSearch*です。
  
```sql
DECLARE @document varchar(64);  
  
SELECT @document = 'Reflectors are vital safety' +  
                   ' components of your bicycle.';  
SELECT CHARINDEX('bike', @document);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
  
(1 row(s) affected)
```
  
### <a name="d-performing-a-case-sensitive-search"></a>D. 大文字小文字を区別する検索を実行する  
次の例は、文字列の大文字と小文字を実行`'TEST'`で`'This is a Test``'`です。
  
```sql
USE tempdb;  
GO  
--perform a case sensitive search  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
0
```  
  
次の例は、文字列の大文字と小文字を実行`'Test'`で`'This is a Test'`です。
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'Test',  
       'This is a Test'  
       COLLATE Latin1_General_CS_AS);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
### <a name="e-performing-a-case-insensitive-search"></a>E. 大文字小文字を区別しない検索を実行する  
次の例は、文字列の大文字と小文字の検索を実行`'TEST'`で`'This is a Test'`です。
  
```sql
  
USE tempdb;  
GO  
SELECT CHARINDEX ( 'TEST',  
       'This is a Test'  
       COLLATE Latin1_General_CI_AS);  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
-----------
13
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="f-searching-from-the-start-of-a-string-expression"></a>F. 文字列式の先頭から検索  
次の例の最初の位置を返します、`is`で文字列`This is a string`文字列内の位置 (最初の文字) を 1 から開始します。
  
```sql
SELECT CHARINDEX('is', 'This is a string');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
3
```  
  
### <a name="g-searching-from-a-position-other-than-the-first-position"></a>G. 最初の位置以外の位置から検索  
次の例の最初の位置を返します、`is`で文字列`This is a string`、4 番目の位置で開始します。
  
```sql
SELECT CHARINDEX('is', 'This is a string', 4);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
 6
 ```  
  
### <a name="h-results-when-the-string-is-not-found"></a>H. 文字列が見つからない場合の結果  
例を次に、戻り値のときに、 *string_pattern*検索文字列が見つかりません。
  
```sql
SELECT TOP(1) CHARINDEX('at', 'This is a string') FROM dbo.DimCustomer;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
---------
0
```  
  
## <a name="see-also"></a>参照
[文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
[+ (& a) #40 です。文字列の連結 &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/string-concatenation-transact-sql.md)  
[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)
  
  



