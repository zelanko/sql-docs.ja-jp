---
title: "EXP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EXP_TSQL
- EXP
dev_langs:
- TSQL
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 5a9b8c52-6fb6-4e33-8b02-a878785b2f51
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c50757291a8f1fc3d58d8a9a131c4a24aa79a008
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した指数値を返します**float**式。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>引数  
 *float_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)型の**float**または型に暗黙的に変換できる**float**です。  
  
## <a name="return-types"></a>戻り値の型  
 **float**  
  
## <a name="remarks"></a>解説  
 定数**e** (2.718281...) は、自然対数の底です。  
  
 数値の指数は、定数**e**数値の累乗します。 たとえば、EXP(1.0) = e^1.0 = 2.71828182845905 および EXP(10) = e^10 = 22026.4657948067 になります。  
  
 数値の自然対数の指数は数自体: EXP (ログ (*n*)) =  *n*です。 数値の指数の自然対数は数自体: ログ (EXP (*n*)) =  *n*です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-finding-the-exponent-of-a-number"></a>A. 数値の指数を計算する  
 次の例は、変数を宣言し、指定された変数の指数値を返します (`10`) テキストの説明。  
  
```  
DECLARE @var float  
SET @var = 10  
SELECT 'The EXP of the variable is: ' + CONVERT(varchar,EXP(@var))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------------------------------  
The EXP of the variable is: 22026.5  
(1 row(s) affected)  
```  
  
### <a name="b-finding-exponentials-and-natural-logarithms"></a>B. 指数と自然対数を計算する  
 次の例の自然対数の指数値を返します`20`およびの指数の自然対数`20`です。 どちらの場合、戻り値は、これらの関数は互いの逆関数であるため、`20`です。  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------- ----------------------  
20                     20  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-finding-the-exponent-of-a-number"></a>C. 数値の指数を計算する  
 次の例は、指定した値の指数値を返します (`10`)。  
  
```  
SELECT EXP(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------  
22026.4657948067  
```  
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>D. 値の指数と自然対数を検索します。  
 次の例の自然対数の指数値を返します`20`およびの指数の自然対数`20`です。 どちらの場合、戻り値は、これらの関数は互いの逆関数であるため、`20`です。  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------- -----------------  
20                  20  
```  
  
## <a name="see-also"></a>参照  
 [数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [ログ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/log-transact-sql.md)   
 [Log10 関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/log10-transact-sql.md)  
  
  


