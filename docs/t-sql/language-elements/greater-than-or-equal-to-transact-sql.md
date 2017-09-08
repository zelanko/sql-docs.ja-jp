---
title: "&gt;= (より大きいか等しい) (TRANSACT-SQL) |Microsoft ドキュメント"
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
- Greater
- '>='
- '>= (Greater Than or Equal To)'
- Equal To
- '>=_TSQL'
- Greater Than
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- greater than or equal to operator (>=)
- '>= (greater than or equal to operator)'
ms.assetid: 641ee28d-7536-46dd-a48a-6c63c2d59278
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3d062fde7d244e2b5697d68701315faa31671f57
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="gt-greater-than-or-equal-to-transact-sql"></a>&gt;= (より大きいか等しい) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの式を比較して "以上" であるかどうかを判定します (比較演算子)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
expression >= expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。 変換の規則に依存[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)です。  
  
## <a name="result-types"></a>戻り値の型  
 ブール値  
  
## <a name="remarks"></a>解説  
 NULL 以外の式を比較したときに、左側のオペランドの値が右側のオペランドの値以上の場合、結果は TRUE です。それ以外の場合、結果は FALSE です。  
  
 = (等価) 比較演算子と異なり、2 つの NULL 値の >= 比較の結果は ANSI_NULLS の設定に依存しません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using--in-a-simple-query"></a>A. 簡単なクエリで >= を使用する  
 次の例では、`HumanResources.Department` テーブル内で、`DepartmentID` の値が値 13 以上の行をすべて返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID >= 13  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
13           Quality Assurance  
14           Facilities and Maintenance  
15           Shipping and Receiving  
16           Executive  
  
(4 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [= (& a) #40 です。等しい &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/equals-transact-sql.md)   
 [& #62 です。& #40 です。大きい (& a) #41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/greater-than-transact-sql.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
