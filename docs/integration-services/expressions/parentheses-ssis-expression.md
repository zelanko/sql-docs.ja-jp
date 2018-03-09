---
title: "() (かっこ) (SSIS 式) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ae024cc0a4d8a492175ac992ed82eed34956848
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="-parentheses-ssis-expression"></a>() (かっこ) (SSIS 式)
  式の評価順序を特定します。 かっこで囲まれた式は、評価の優先順位が最も高くなります。 かっこで囲まれ、入れ子になっている式は、内側から外側の順に評価されます。  
  
 かっこは、複合式を理解しやすくするためにも使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
(expression)  
  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な式を指定します。  
  
## <a name="result-types"></a>戻り値の型  
 *expression*のデータ型。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="expression-examples"></a>式の例  
 次の例では、かっこを使用して演算子の優先順位を変更する方法を示します。 最初の式は 100 と評価され、2 番目の式は 31 と評価されます。  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
