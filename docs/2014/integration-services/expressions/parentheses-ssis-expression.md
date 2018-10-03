---
title: () (かっこ) (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- () (parentheses operator)
- evaluation order [Integration Services]
- parentheses operator ()
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3cfcad949dd07d4eec4513b09a19cf262bd5c787
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101982"
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
 *expression*のデータ型。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="expression-examples"></a>式の例  
 次の例では、かっこを使用して演算子の優先順位を変更する方法を示します。 最初の式は 100 と評価され、2 番目の式は 31 と評価されます。  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)   
 [演算子&#40;SSIS 式&#41;](operators-ssis-expression.md)  
  
  
