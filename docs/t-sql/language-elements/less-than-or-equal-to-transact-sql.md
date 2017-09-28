---
title: "&lt;= (等しいまたはそれよりも小さい) (TRANSACT-SQL) |Microsoft ドキュメント"
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
- <=
- Less
- Equal To
- <=_TSQL
- Less Than
- Equal
dev_langs:
- TSQL
helpviewer_keywords:
- <= (less than or equal to operator)
- less than or equal to operator (<=)
ms.assetid: 1f05474c-0377-48cb-b567-9d85d0c40479
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c3604745940bff9695f6a961661b3ee99fe6171a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lt-less-than-or-equal-to-transact-sql"></a>&lt;= (等しいまたはそれよりも小さい) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの式を比較します (比較演算子)。 NULL でない式を比較したときに、左側のオペランドの値が右側のオペランドの値以下の場合、結果は TRUE です。それ以外の場合、結果は FALSE です。  
  
 = (等価) 比較演算子と異なり、2 つの NULL 値の >= 比較の結果は ANSI_NULLS の設定に依存しません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。 変換の規則に依存[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)です。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using--in-a-simple-query"></a>A. 使用して < 簡単なクエリで =  
 次の例では、`HumanResources.Department` テーブル内で、`DepartmentID` の値が値 3 以下の行をすべて返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT DepartmentID, Name  
FROM HumanResources.Department  
WHERE DepartmentID <= 3  
ORDER BY DepartmentID;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
DepartmentID Name  
------------ --------------------------------------------------  
1            Engineering  
2            Tool Design  
3            Sales  
  
(3 row(s) affected)  
  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
