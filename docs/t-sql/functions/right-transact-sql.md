---
title: "右 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- RIGHT_TSQL
- RIGHT
dev_langs: TSQL
helpviewer_keywords:
- rightmost character of expression
- RIGHT function
- character strings [SQL Server], RIGHT
ms.assetid: 43f1fe1f-aa18-47e3-ba20-e03e32254a6d
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: b6680078aff2e103655a94ec157371a0d09f79be
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="right-transact-sql"></a>RIGHT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  文字列の右端から指定された数の文字を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
RIGHT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の文字またはバイナリ データ。 *character_expression*定数、変数、または列を指定できます。 *character_expression*を除く任意のデータ型であることができます**テキスト**または**ntext**に暗黙的に変換する**varchar**または**nvarchar**です。 それ以外の場合を使用して、[キャスト](../../t-sql/functions/cast-and-convert-transact-sql.md)関数は明示的に変換する*character_expression*です。  
  
 *integer_expression*  
 文字の数を指定する正の整数*character_expression*が返されます。 場合*であれば、任意*は負の場合、エラーが返されます。 場合*であれば、任意*は型です**bigint** 、大きな値を含むと*character_expression*などの大規模なデータ型でなければなりません**varchar(max)**。  
  
## <a name="return-types"></a>戻り値の型  
 返します**varchar**とき*character_expression*非 Unicode 文字データ型です。  
  
 返します**nvarchar**とき*character_expression* Unicode 文字データ型です。  
  
## <a name="supplementary-characters-surrogate-pairs"></a>補助文字 (サロゲート ペア)  
 SC の照合順序を使用する場合、RIGHT 関数では、UTF-16 のサロゲート ペアが 1 文字としてカウントされます。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-right-with-a-column"></a>A: 権限を使用して列を含む  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の各担当者の名前の右端から 5 文字が返されます。  
  
```  
SELECT RIGHT(FirstName, 5) AS 'First Name'  
FROM Person.Person  
WHERE BusinessEntityID < 5  
ORDER BY FirstName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
First Name  
----------  
Ken  
Terri  
berto  
Rob  
  
(4 row(s) affected)  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-right-with-a-column"></a>B. 列での右の使用  
 次の例は、各に姓の 5 つの右端の文字を返します、`DimEmployee`テーブル。  
  
```  
-- Uses AdventureWorks  
  
SELECT RIGHT(LastName, 5) AS Name  
FROM dbo.DimEmployee  
ORDER BY EmployeeKey;  
```  
  
 部分的な結果セットを次に示します。  
  
 ```
Name
-----
lbert
Brown
rello
lters
 ```  
  
### <a name="c-using-right-with-a-character-string"></a>C. 文字の文字列での右の使用  
 次の例で`RIGHT`を文字の文字列の 2 つの右端の文字を返す`abcdefg`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT TOP(1) RIGHT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
-------  
fg
```  
  
## <a name="see-also"></a>参照  
 [左と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ltrim-transact-sql.md)  
 [RTRIM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)  
 [トリム &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/trim-transact-sql.md)  
 [CAST および CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [文字列関数 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

