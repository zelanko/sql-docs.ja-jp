---
title: "(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
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
- AND_TSQL
- AND
dev_langs: TSQL
helpviewer_keywords:
- values [SQL Server], TRUE
- TRUE
- AND, about AND operators
- AND
- combining expressions
ms.assetid: b61d7f8d-5a51-49b7-91dd-f6190a5a0fb9
caps.latest.revision: "26"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f85ca8eceabd8e07a376be0b9d958190cb663de0
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="and-transact-sql"></a>AND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つのブール式を結合し、返します**TRUE**ときに両方の式が**TRUE**です。 ステートメントでは、1 つ以上の論理演算子を使用すると、 **AND**演算子が最初に評価されます。 かっこを使うと、演算の順序を変更することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
boolean_expression AND boolean_expression  
```  
  
## <a name="arguments"></a>引数  
 *boolean_expression*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)ブール値を返す: **TRUE**、 **FALSE**、または**不明な**します。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="result-value"></a>結果の値  
 両方の式が TRUE の場合、TRUE を返します。  
  
## <a name="remarks"></a>解説  
 次の表は、TRUE 値と FALSE 値を AND 演算子を使用して比較する場合の結果です。  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**TRUE**|TRUE|FALSE|UNKNOWN|  
|**FALSE**|FALSE|FALSE|FALSE|  
|**不明**|UNKNOWN|FALSE|UNKNOWN|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-the-and-operator"></a>A. AND 演算子の使用  
 次の例は、両方のタイトルを持つ従業員に関する情報を選択の`Marketing Assistant`と複数の`41`休暇時間使用できます。  
  
```  
-- Uses AdventureWorks  
  
SELECT  BusinessEntityID, LoginID, JobTitle, VacationHours   
FROM HumanResources.Employee  
WHERE JobTitle = 'Marketing Assistant'  
AND VacationHours > 41 ;  
```  
  
### <a name="b-using-the-and-operator-in-an-if-statement"></a>B. IF ステートメントでの AND 演算子の使用  
 次の例は、IF ステートメントでの AND の使用方法を示しています。 最初のステートメントでは、両方とも`1 = 1`と`2 = 2`も true であるため、結果は true です。 2 つ目の例では、引数 `2 = 17` が false であるため、結果は false です。  
  
```  
IF 1 = 1 AND 2 = 2  
BEGIN  
   PRINT 'First Example is TRUE'  
END  
ELSE PRINT 'First Example is FALSE';  
GO  
  
IF 1 = 1 AND 2 = 17  
BEGIN  
   PRINT 'Second Example is TRUE'  
END  
ELSE PRINT 'Second Example is FALSE' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  
