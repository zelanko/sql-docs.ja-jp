---
title: "! (論理 Not)(SSIS 式) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 003e0fcc98a267342aaf7c77bf344cdfdc71880b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="-logical-not-ssis-expression"></a>! (論理 Not) (SSIS 式)
  ブール型のオペランドを否定します。  
  
> [!NOTE]  
>  ! 演算子は、他の演算子と組み合わせて使用することはできません。 たとえば、!  演算子と > 演算子を組み合わせて !>  演算子にすることはできません。  
  
## <a name="syntax"></a>構文  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a>引数  
 *boolean_expression*  
 ブール型に評価される任意の有効な式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="remarks"></a>解説  
 次の表は、! 指定します。  
  
|元のブール式|! 演算子の適用後 演算子 (operator)|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## <a name="expression-examples"></a>式の例  
 **Color** 列の値が "red" の場合、この例は FALSE に評価されます。  
  
```  
!(Color == "red")  
```  
  
 **MonthNumber** 変数の値が現在の月を示す整数と同じ場合、この例は TRUE に評価されます。 詳細については、「[MONTH &#40;SSIS 式&#41;](../../integration-services/expressions/month-ssis-expression.md)」および「[GETDATE &#40;SSIS 式&#41;](../../integration-services/expressions/getdate-ssis-expression.md)」をご覧ください。  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40; です。SSIS 式と &#41; です。](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
