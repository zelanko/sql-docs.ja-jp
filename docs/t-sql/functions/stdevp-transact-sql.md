---
title: "STDEVP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
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
- STDEVP
- STDEVP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STDEVP function [Transact-SQL]
- expressions [SQL Server], statistical standard deviation
- statistical standard deviation
ms.assetid: 29f2a906-d084-4464-abc3-4b275ed19442
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: af2c89686b804e263d0a7e576a3c91e926a65644
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="stdevp-transact-sql"></a>STDEVP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定された式のすべての値を母集団として標準偏差を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
STDEVP ( [ ALL | DISTINCT ] expression )   
   OVER ( [ partition_by_clause ] order_by_clause )    
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
-- Aggregate Function Syntax   
STDEVP ( [ ALL | DISTINCT ] expression )  
  
-- Analytic Function Syntax   
STDEVP (expression) OVER ( [ partition_by_clause ] order_by_clause)  
```  
  
## <a name="arguments"></a>引数  
 **ALL**  
 すべての値にこの関数を適用します。 ALL が既定値です。  
  
 DISTINCT  
 重複する値は 1 つだけカウントします。  
  
 *式 (expression)*  
 数値[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 集計関数とサブクエリは使用できません。 *式*が、正確な型または概数の数値データ型カテゴリの式を除く、**ビット**データ型。  
  
 経由で**(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause*関数を適用するパーティションに FROM 句で生成される結果セットに分割します。 指定しない場合、関数ではクエリ結果セットのすべての行を 1 つのグループとして扱います。 *order_by_clause*操作が実行される論理的順序を決定します。 *order_by_clause*が必要です。 詳細については、次を参照してください。 [OVER 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>戻り値の型  
 **float**  
  
## <a name="remarks"></a>解説  
 SELECT ステートメントの中のすべての項目に対して STDEVP を使用すると、結果セット内のすべての値が計算に含まれます。 STDEVP は、数値型列に対して使用できます。 NULL 値は無視されます。  
  
 STDEVP は、OVER 句や ORDER BY 句なしで使用される場合は決定的関数です。 OVER 句や ORDER BY 句と共に使用される場合は、非決定的関数です。 詳細については、「 [決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-stdevp"></a>A: STDEVP を使用します。  
 次の例は、すべてのボーナス値の母集団に対する標準偏差を返します、`SalesPerson`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT STDEVP(Bonus)  
FROM Sales.SalesPerson;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-using-stdevp"></a>B: STDEVP を使用します。  
 次の例を返します、 `STDEVP` 、テーブルの販売ノルマの値の`dbo.FactSalesQuota`します。 最初の列を含むすべての個別の値の標準偏差と 2 番目の列に重複値も含めてすべての値の標準偏差が含まれています。  
  
```  
-- Uses AdventureWorks  
  
SELECT STDEVP(DISTINCT SalesAmountQuota)AS Distinct_Values, STDEVP(SalesAmountQuota) AS All_Values  
FROM dbo.FactSalesQuota;SELECT STDEVP(DISTINCT Quantity)AS Distinct_Values, STDEVP(Quantity) AS All_Values  
FROM ProductInventory;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Distinct_Values   All_Values  
----------------  ----------------  
397676.79         397226.44
```  
  
### <a name="c-using-stdevp-with-over"></a>C. OVER で STDEVP を使用します。  
 次の例を返します、`STDEVP`のカレンダー年度の四半期ごとの販売ノルマの値。 `ORDER BY` 句の `OVER` によって `STDEVP` が順序付けされ、`ORDER BY` ステートメントの `SELECT` によって結果セットが順序付けされることに注目してください。  
  
```  
-- Uses AdventureWorks  
  
SELECT CalendarYear AS Year, CalendarQuarter AS Quarter, SalesAmountQuota AS SalesQuota,  
       STDEVP(SalesAmountQuota) OVER (ORDER BY CalendarYear, CalendarQuarter) AS StdDeviation  
FROM dbo.FactSalesQuota  
WHERE EmployeeKey = 272 AND CalendarYear = 2002  
ORDER BY CalendarQuarter;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Year  Quarter  SalesQuota              StdDeviation  
----  -------  ----------------------  -------------------  
2002  1         91000.0000             0.00  
2002  2        140000.0000             24500.00  
2002  3         70000.0000             29329.55  
2002  4        154000.0000             34426.55
```  
  
## <a name="see-also"></a>参照  
 [集計関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [句 &#40; 経由TRANSACT-SQL と #41 です。](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  

