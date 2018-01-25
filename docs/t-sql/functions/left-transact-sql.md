---
title: "左 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LEFT
- LEFT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- character strings [SQL Server], LEFT
- characters [SQL Server], leftmost
- LEFT function
- leftmost character of expression
ms.assetid: 44a8c71b-63d8-458b-8b5d-99d570067c3c
caps.latest.revision: "48"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 822680e5939e628b17c15d08c3cb513ad9b348ed
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="left-transact-sql"></a>LEFT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  文字列の左端から指定された数の文字を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
LEFT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字またはバイナリ データ。 *character_expression*定数、変数、または列を指定できます。 *character_expression*を除く任意のデータ型であることができます**テキスト**または**ntext**に暗黙的に変換する**varchar**または**nvarchar**です。 それ以外の場合を使用して、[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)関数は明示的に変換する*character_expression*です。  
  
 *integer_expression*  
 文字の数を指定する正の整数、 *character_expression*が返されます。 場合*であれば、任意*は負の場合、エラーが返されます。 場合*であれば、任意*は型です**bigint** 、大きな値を含むと*character_expression*などの大規模なデータ型でなければなりません**varchar(max)**。  
  
 *であれば、任意*パラメーターは 1 文字としての utf-16 サロゲート文字をカウントします。  
  
## <a name="return-types"></a>戻り値の型  
 返します**varchar**とき*character_expression*非 Unicode 文字データ型です。  
  
 返します**nvarchar**とき*character_expression* Unicode 文字データ型です。  
  
## <a name="remarks"></a>解説  
 SC の照合順序を使用する場合、*であれば、任意*パラメーターは 1 文字としての utf-16 サロゲート ペアをカウントします。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-left-with-a-column"></a>A. 列を指定した LEFT を使用する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの `Product` テーブル内の各製品名の左端から 5 文字が返されます。  
  
```  
SELECT LEFT(Name, 5)   
FROM Production.Product  
ORDER BY ProductID;  
GO  
```  
  
### <a name="b-using-left-with-a-character-string"></a>B. 文字列を指定した LEFT を使用する  
 次の例で`LEFT`を文字の文字列の 2 つの左端の文字を返す`abcdefg`です。  
  
```  
SELECT LEFT('abcdefg',2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab   
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-left-with-a-column"></a>C. 列を指定した LEFT を使用する  
 次の例では、各製品名の左端の 5 文字を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT(EnglishProductName, 5)   
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="d-using-left-with-a-character-string"></a>D. 文字列を指定した LEFT を使用する  
 次の例で`LEFT`を文字の文字列の 2 つの左端の文字を返す`abcdefg`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab  
```  
  
## <a name="see-also"></a>参照  
 [LTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ltrim-transact-sql.md)  
 [右 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)  
 [トリム &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/trim-transact-sql.md)  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

