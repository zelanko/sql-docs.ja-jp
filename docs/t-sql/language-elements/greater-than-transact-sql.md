---
title: "&gt;(より大きい)(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Greater
- Than
- '> (Greater Than)'
- '>_TSQL'
- Greater Than
- '>'
dev_langs: TSQL
helpviewer_keywords:
- greater than operator (>)
- '> (greater than operator)'
ms.assetid: 50a7b098-a3fb-4df6-ae42-1272d6346338
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5ca1c189b4548175fd1038b2c83bed87d768a776
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="gt-greater-than-transact-sql"></a>&gt;(より大きい)(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で 2 つの式を比較します (比較演算子)。 NULL でない式を比較したときに、左側のオペランドの値が右側のオペランドの値よりも大きい場合、結果は TRUE です。それ以外の場合、結果は FALSE です。 いずれかまたは両方のオペランドが NULL の場合は、トピックを参照してください。 [SET ANSI_NULLS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-nulls-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。 変換の規則に依存[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)です。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using--in-a-simple-query"></a>A. 簡単なクエリで > を使用する  
 次の例では、`HumanResources.Department` テーブル内で、`DepartmentID` の値が値 13 を超えるすべての行を返します。  
  
```  
--Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID > 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(3 row(s) affected)  
  
```  
  
### <a name="b-using--to-compare-two-variables"></a>B. > を使用して 2 つの変数を比較する  
  
```  
DECLARE @a int = 45, @b int = 40;  
SELECT IIF ( @a > @b, 'TRUE', 'FALSE' ) AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
------  
TRUE  
  
(1 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照  
 [Iif 関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/logical-functions-iif-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
