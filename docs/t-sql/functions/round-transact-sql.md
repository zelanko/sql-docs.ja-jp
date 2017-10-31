---
title: "ROUND (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ROUND_TSQL
- ROUND
dev_langs:
- TSQL
helpviewer_keywords:
- rounding expressions
- ROUND function [Transact-SQL]
ms.assetid: 23921ed6-dd6a-4c9e-8c32-91c0d44fe4b7
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: cba8b5a9b62a21fc810ff9bb5fcd3d0c6429f9f5
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="round-transact-sql"></a>ROUND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定された長さまたは有効桁数に丸めた数値を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ROUND ( numeric_expression , length [ ,function ] )  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ROUND (numeric_expression , length )  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)の正確な型または概数の数値データのカテゴリを除く入力、**ビット**データ型。  
  
 *length*  
 有効桁数を*numeric_expression*丸めた後です。 *長さ*型の式を指定する必要があります**tinyint**、 **smallint**、または**int**です。ときに*長さ*正の整数*numeric_expression*で指定された小数点以下桁数に丸められます*長さ*です。 ときに*長さ*、負の値は、 *numeric_expression*で指定したとおり、小数点の左側にあるで丸められます*長さ*です。  
  
 *関数 (function)*  
 実行する操作の種類です。 *関数*する必要があります**tinyint**、 **smallint**、または**int**です。ときに*関数*を省略するか、0 (既定値) の値を持つ*numeric_expression*は丸められます。 以外の値 0 が指定した場合、 *numeric_expression*が切り詰められています。  
  
## <a name="return-types"></a>戻り値の型  
 次のデータ型を返します。  
  
|式の結果|戻り値の型|  
|-----------------------|-----------------|  
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**ssNoversion**|**int**|  
|**bigint**|**bigint**|  
|**10 進**と**数値**型 (p, s)|**decimal (p, s)**|  
|**money**と**smallmoney**カテゴリ|**money**|  
|**float**と**実際**カテゴリ|**float**|  
  
## <a name="remarks"></a>解説  
 ROUND は常に値を返します。 場合*長さ*は負の値であり、小数点の前に数字の数よりも大きい、ROUND は 0 を返します。  
  
|例|結果|  
|-------------|------------|  
|ROUND (748.58、-4)|0|  
  
 ラウンドは、角の丸いを返します*numeric_expression*データ型に関係なく、ときに*長さ*負の数値します。  
  
|使用例|結果|  
|--------------|------------|  
|ROUND (748.58,-1)|750.00|  
|ROUND (748.58、-2)|700.00|  
|ROUND(748.58, -3)|748.58 の既定値は decimal(5,2) となり、1000.00 を返すことができないため、結果は算術オーバーフローになります。|  
|4 桁までに丸めるには、入力のデータ型を変更します。 例:<br /><br /> `SELECT ROUND(CAST (748.58 AS decimal (6,2)),-3);`|1000.00|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-round-and-estimates"></a>A. ROUND と概数を使用する  
 次の例では、`ROUND` を使用することにより最後の桁が常に概数になることを表す 2 つの式を示します。  
  
```  
SELECT ROUND(123.9994, 3), ROUND(123.9995, 3);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------- -----------  
123.9990    124.0000      
```  
  
### <a name="b-using-round-and-rounding-approximations"></a>B. ROUND を使用して概数を丸める  
 次の例では、数値を丸めて概数化します。  
  
```  
SELECT ROUND(123.4545, 2), ROUND(123.45, -2);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ----------
123.45    100.00
```
  
### <a name="c-using-round-to-truncate"></a>C. ROUND を使用して切り捨てを行う  
 次の例を使用して 2 つ`SELECT`ステートメントを丸め処理と切り捨ての違いを示します。 最初のステートメントは、結果を丸めます。 2 番目のステートメントは、結果を切り捨てます。  
  
```  
SELECT ROUND(150.75, 0);  
GO  
SELECT ROUND(150.75, 0, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
151.00  
  
(1 row(s) affected)  
  
--------  
150.00  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-round-and-estimates"></a>D. ROUND と概数を使用する  
 次の例では、`ROUND` を使用することにより最後の桁が常に概数になることを表す 2 つの式を示します。  
  
```  
SELECT ROUND(123.994999, 3), ROUND(123.995444, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

 ```
--------  ---------
123.995000    123.995444
```
  
## <a name="see-also"></a>参照  
 [CEILING & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ceiling-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FLOOR & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/floor-transact-sql.md)   
 [数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  


