---
title: "電源 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- POWER_TSQL
- POWER
dev_langs:
- TSQL
helpviewer_keywords:
- POWER function
ms.assetid: 0fd34494-90b9-4559-8011-a8c1b9f40239
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cb1f3ca862c070888a8e8cb5265f582dcf47d4aa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="power-transact-sql"></a>POWER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定された式の指定されたべき乗値を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
POWER ( float_expression , y )  
```  
  
## <a name="arguments"></a>引数  
 *float_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)型の**float**または型に暗黙的に変換できる**float**です。  
  
 *y*  
 のべき乗値を指定*float_expression*です。 *y*を除く、真数または概数数値の正確なデータ型カテゴリの式を指定できます、**ビット**データ型。  
  
## <a name="return-types"></a>戻り値の型  
 送信するときと同じ型を返します*float_expression*です。 たとえば場合、 **10 進**(2, 0) として送信された*float_expression*、結果が返されます**decimal**(2, 0) です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-power-to-return-the-cube-of-a-number"></a>A. POWER を使用して数値の 3 乗を返す  
 次の例は、数値を 3 乗する方法を示しています。  
  
```  
DECLARE @input1 float;  
DECLARE @input2 float;  
SET @input1= 2;  
SET @input2 = 2.5;  
SELECT POWER(@input1, 3) AS Result1, POWER(@input2, 3) AS Result2;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result1                Result2  
---------------------- ----------------------  
8                      15.625  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-power-to-show-results-of-data-type-conversion"></a>B. POWER を使用してデータ型変換の結果を示す  
 例を次にどのように*float_expression*予期しない結果を返す可能性のあるデータ型を保持します。  
  
```  
SELECT   
POWER(CAST(2.0 AS float), -100.0) AS FloatResult,  
POWER(2, -100.0) AS IntegerResult,  
POWER(CAST(2.0 AS int), -100.0) AS IntegerResult,  
POWER(2.0, -100.0) AS Decimal1Result,  
POWER(2.00, -100.0) AS Decimal2Result,  
POWER(CAST(2.0 AS decimal(5,2)), -100.0) AS Decimal2Result;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FloatResult            IntegerResult IntegerResult Decimal1Result Decimal2Result Decimal2Result  
---------------------- ------------- ------------- -------------- -------------- --------------  
7.88860905221012E-31   0             0             0.0            0.00           0.00  
```  
  
### <a name="c-using-power"></a>C. POWER を使用する  
 次の例を返します`POWER`結果`2`です。  
  
```  
DECLARE @value int, @counter int;  
SET @value = 2;  
SET @counter = 1;  
  
WHILE @counter < 5  
   BEGIN  
      SELECT POWER(@value, @counter)  
      SET NOCOUNT ON  
      SET @counter = @counter + 1  
      SET NOCOUNT OFF  
   END;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
2             
  
(1 row(s) affected)  
  
-----------   
4             
  
(1 row(s) affected)  
  
-----------   
8             
  
(1 row(s) affected)  
  
-----------   
16            
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-power-to-return-the-cube-of-a-number"></a>D: では、電源を使用して、数値のキューブを取得するには  
 次の例を返します`POWER`結果`2.0`第 3 の電源をします。  
  
```  
SELECT POWER(2.0, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
------------ 
8.0
```  
  
## <a name="see-also"></a>参照  
 [decimal および numeric 型 &#40;TRANSACT-SQL と #41 です。](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)   
 [float、real および #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/float-and-real-transact-sql.md)   
 [int、bigint、smallint 型、および tinyint (&) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)   
 [数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [money および smallmoney & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)  
  
  


