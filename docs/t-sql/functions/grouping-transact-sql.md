---
title: "グループ化 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GROUPING
- GROUPING_TSQL
dev_langs: TSQL
helpviewer_keywords:
- null values [SQL Server], GROUPING function
- grouping columns
- ROLLUP operator
- GROUP BY clause, GROUPING function
- GROUPING function
- CUBE operator
ms.assetid: 4efa3868-1fc4-4626-8fb1-e863cc03e422
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: cb9c9e7f4e5fe4a82c6f7a451614fde82e730e08
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-transact-sql"></a>GROUPING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  GROUP BY リストの指定された列式が集計されるかどうかを示します。 GROUPING は、集計される場合に 1、集計されない場合に 0 を結果セットで返します。 グループ化は、選択でのみ使用できます\<選択 > リスト、HAVING、および GROUP BY が指定されている場合は、ORDER BY 句。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GROUPING ( <column_expression> )  
```  
  
## <a name="arguments"></a>引数  
 \<column_expression >  
 列または式で列を含む、 [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md)句。  
  
## <a name="return-types"></a>戻り値の型  
 **tinyint**  
  
## <a name="remarks"></a>解説  
 GROUPING を使用して、ROLLUP、CUBE、または GROUPING SETS から返される NULL 値と標準的な NULL 値を区別します。 ROLLUP、CUBE、または GROUPING SETS の演算結果として返される NULL 値は、NULL の特別な用途です。 結果セット内の列のプレースホルダーとして動作し、すべてという意味を持ちます。  
  
## <a name="examples"></a>使用例  
 次の例のグループ`SalesQuota`と集計`SaleYTD`額、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。 `GROUPING`に関数が適用される、`SalesQuota`列です。  
  
```  
SELECT SalesQuota, SUM(SalesYTD) 'TotalSalesYTD', GROUPING(SalesQuota) AS 'Grouping'  
FROM Sales.SalesPerson  
GROUP BY SalesQuota WITH ROLLUP;  
GO  
```  
  
 結果セットは、`SalesQuota` の下に 2 つの NULL 値を示します。 最初の`NULL`テーブル内のこの列から null 値のグループを表します。 2 番目`NULL`はプログラムのロールアップの操作によって追加された概要の行にします。 概要の行の表示、`TotalSalesYTD`すべて金額`SalesQuota`グループ化されで示される`1`で、`Grouping`列です。  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 SalesQuota     TotalSalesYTD       Grouping  
------------   -----------------   --------  
NULL           1533087.5999          0  
250000.00      33461260.59           0  
300000.00      9299677.9445          0  
NULL           44294026.1344         1  

(4 row(s) affected)
```  
  
## <a name="see-also"></a>参照  
 [GROUPING_ID &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/grouping-id-transact-sql.md)   
 [GROUP BY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  
