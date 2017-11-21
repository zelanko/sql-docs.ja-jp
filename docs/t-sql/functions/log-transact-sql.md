---
title: "ログ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOG
- LOG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- logarithm of expression
- LOG function
ms.assetid: f7c39511-cd84-4362-93ba-0d93655217ee
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 7918cb0d2832e88f3e4218b98c7f606f559f2e4e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="log-transact-sql"></a>LOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定したの自然対数を返します**float**式[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
LOG ( float_expression [, base ] )  
```  
  
```  
-- Syntax for Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
LOG ( float_expression )  
```  
  
## <a name="arguments"></a>引数  
 *float_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)型の**float**または型に暗黙的に変換できる**float**です。  
  
 *ベース*  
 対数の底を設定するオプションの整数引数です。  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
## <a name="return-types"></a>戻り値の型  
 **float**  
  
## <a name="remarks"></a>解説  
 既定では、 **LOG()**自然対数を返します。 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、対数の底を別の値に変更するには、オプションを使用して*基本*パラメーター。  
  
 自然対数を底とする対数**e**ここで、 **e** 2.718281828 にほぼ等しい無理定数がします。  
  
 数値の指数の自然対数は数自体: ログ (EXP (  *n*  )) =  *n*です。 数値の自然対数の指数は数自体: EXP (ログ (  *n*  )) =  *n*です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-calculating-the-logarithm-for-a-number"></a>A. 数値の自然対数を計算する  
 次の例では、計算、 `LOG` 、指定された**float**式。  
  
```  
DECLARE @var float = 10;  
SELECT 'The LOG of the variable is: ' + CONVERT(varchar, LOG(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------  
The LOG of the variable is: 2.30259  
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-logarithm-of-the-exponent-of-a-number"></a>B. 数値の指数の自然対数を計算する  
 次の例では、数値の指数の `LOG` を計算します。  
  
```  
SELECT LOG (EXP (10));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------  
10  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-logarithm-for-a-number"></a>C. 数値の自然対数を計算します。  
 次の例では、計算、 `LOG` 、指定された**float**式。  
  
```  
SELECT LOG(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ----------------`  
  
 2.30
 ```  
  
## <a name="see-also"></a>参照  
 [数学関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [Exp 関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/exp-transact-sql.md)   
 [Log10 関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/log10-transact-sql.md)  
  
  


