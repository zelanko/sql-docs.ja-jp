---
title: "PATINDEX (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/19/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PATINDEX
- PATINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- first occurrence of pattern [SQL Server]
- searches [SQL Server], pattern starting position
- starting position of patten search
- pattern searching [SQL Server]
- PATINDEX function
ms.assetid: c0dfb17f-2230-4e36-98da-a9b630bab656
caps.latest.revision: 53
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: abf357840512c1447f0977a151ca742b148f45d2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="patindex-transact-sql"></a>PATINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  すべて有効なテキスト データ型と文字データ型で指定された式の中で、パターンが最初に現れる先頭位置を返します。パターンが見つからない場合は、0 を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
PATINDEX ( '%pattern%' , expression )  
```  
  
## <a name="arguments"></a>引数  
 *パターン*  
 検索するシーケンスを含む文字式です。 ワイルドカード文字を使用できます。ただし、% 文字が前にし、次の必要があります*パターン*を除く最初と最後の文字を検索する場合)。 *パターン*文字の文字列データ型カテゴリの式を指定します。 *パターン*は 8,000 文字に制限されます。  
  
 *式 (expression)*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)通常は、指定したパターンの検索条件となる列。 *式*は、文字列データ型に分類します。  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**場合*式*は、 **varchar (max)**または**nvarchar (max)**データ型以外の場合**int**です。  
  
## <a name="remarks"></a>解説  
 いずれか*パターン*または*式*が NULL の場合、PATINDEX は NULL を返します。  
  
 PATINDEX では、入力の照合順序に基づいて比較が行われます。 指定した照合順序で比較を実行するには、COLLATE を使って入力に明示的な照合順序を適用できます。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 SC の照合順序を使用する場合、戻り値内、utf-16 のサロゲート ペアの数が、*式*パラメーターを 1 つの文字として。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
 0x0000 (**char (0)**) の Windows 照合順序で未定義の文字は、PATINDEX に含めることはできません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-patindex-example"></a>A. PATINDEX の簡単な例  
 次の例では、短い文字列 (`interesting data`) 文字の開始位置の`ter`します。  
  
```  
SELECT PATINDEX('%ter%', 'interesting data');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `3`  
  
### <a name="b-using-a-pattern-with-patindex"></a>B. PATINDEX でパターンを使用する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの `ensure` テーブルにある `DocumentSummary` 列の特定の行で、パターン `Document` が始まる位置を検出します。  
  
```  
SELECT PATINDEX('%ensure%',DocumentSummary)  
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
GO   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-----------  
64  
(1 row(s) affected)
```  
  
 使用して検索する行を制限しないかどうか、`WHERE`句、クエリは、テーブル内のすべての行を返し、パターンが検出された行は 0 以外の値とをパターンが見つからなかったすべての行に 0 を報告します。  
  
### <a name="c-using-wildcard-characters-with-patindex"></a>C. PATINDEX でワイルドカード文字を使用する  
 次の例では、% と _ ワイルドカード文字を使用する位置を検索するパターン`'en'`任意の 1 文字と、その後、 `'ure'` (インデックスは 1 から開始) の指定された文字列の開始。  
  
```  
SELECT PATINDEX('%en_ure%', 'please ensure the door is locked');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-----------  
8  
```  
  
 `PATINDEX`同様に動作します`LIKE`、任意のワイルドカードを使用できるようにします。 パターンを % で囲む必要はありません。 `PATINDEX('a%', 'abc')` は 1 を返し、`PATINDEX('%a', 'cba')` は 3 を返します。  
  
 異なり`LIKE`、`PATINDEX`と同様の位置を返します`CHARINDEX`はします。  
  
### <a name="d-using-collate-with-patindex"></a>D. PATINDEX で COLLATE を使用する  
 次の例では、`COLLATE`関数を明示的に検索する式の照合順序を指定します。  
  
```  
USE tempdb;  
GO  
SELECT PATINDEX ( '%ein%', 'Das ist ein Test'  COLLATE Latin1_General_BIN) ;  
GO  
```  
  
### <a name="e-using-a-variable-to-specify-the-pattern"></a>E. 変数を使用してパターンを指定する  
 次の例では、変数を使用して、値を渡す、*パターン*パラメーター。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
DECLARE @MyValue varchar(10) = 'safety';   
SELECT PATINDEX('%' + @MyValue + '%', DocumentSummary)   
FROM Production.Document  
WHERE DocumentNode = 0x7B40;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ------------  
 22
 ```  
  

  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
 [& #40 です。ワイルドカード - 文字 (&) #40; s &#41;一致と #41 です。& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [& #40 です。ワイルドカード - 文字 (&) #40; s &#41;一致と #41 です。& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-character-s-not-to-match-transact-sql.md)   
 [_ & #40 です。ワイルドカード - 一致する 1 文字 &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)   
 [パーセント記号と #40 です。ワイルドカード - 文字 (&) #40; s &#41;一致と #41 です。& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)  
  
  



