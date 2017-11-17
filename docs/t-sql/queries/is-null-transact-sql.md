---
title: "NULL (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NULL_TSQL
- IS_[NOT]_NULL_TSQL
- IS_NULL_TSQL
- NULL
- '[NOT]_TSQL'
- IS
- IS_TSQL
- IS NULL
- IS [NOT] NULL
- '[NOT]'
dev_langs:
- TSQL
helpviewer_keywords:
- verifying nullability
- IS NOT NULL clause
- null values [SQL Server], verifying
- null values [SQL Server], IS [NOT] NULL
- IS [NOT] NULL clause
- testing nullability
- checking nullability
ms.assetid: cdc45cd8-e9b6-4648-8417-892fbeab15af
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 047e4fd57b91155485fddc2459e94247bb923c7e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="is-null-transact-sql"></a>NULL (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した式が NULL かどうかを判定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 [NOT]  
 ブール値の結果を否定するよう指定します。 この述語によって返される値は反転されるので、値が NULL でない場合は TRUE、NULL の場合は FALSE が返されます。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="return-code-values"></a>リターン コードの値  
 場合の値*式*は NULL、IS NULL、TRUE を返します。 それ以外の場合は FALSE を返します。  
  
 場合の値*式*は NULL、IS NOT NULL、FALSE を返します。 それ以外の場合、TRUE を返します。  
  
## <a name="remarks"></a>解説  
 式が NULL かどうかを判定するには、= や != などの比較演算子の代わりに、IS NULL または IS NOT NULL を使用してください。 比較演算子では、引数のいずれかまたは両方が NULL の場合、UNKNOWN が返されます。  
  
## <a name="examples"></a>使用例  
 次の例は、名前と重量、重みは、すべての製品のいずれかを返しますより小さい`10`ポンドまたは色が不明、または`NULL`です。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight, Color  
FROM Production.Product  
WHERE Weight < 10.00 OR Color IS NULL  
ORDER BY Name;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、すべての従業員のミドル ネームの頭文字との完全名を返します。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, MiddleName  
FROM DIMEmployee  
WHERE MiddleName IS NOT NULL  
ORDER BY LastName DESC;  
```  
  
## <a name="see-also"></a>参照  
 [場合 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [ような & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [論理演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/logical-operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [ここで & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  


