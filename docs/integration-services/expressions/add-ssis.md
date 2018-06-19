---
title: + (加算) (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 127f311e284cec40bf1fda3e38398a1959e0226b
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411774"
---
# <a name="-add-ssis"></a>+ (加算) (SSIS)
  2 つの数値式を加算します。  
  
## <a name="syntax"></a>構文  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression1、numeric_ expression2*  
 数値データ型の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数のデータ型によって決まります。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
 オペランドのいずれかが NULL の場合、結果は NULL になります。  
  
## <a name="expression-examples"></a>式の例  
 この例では、数値リテラルを加算します。  
  
```  
5 + 6.09 + 7.0  
```  
  
 この例では、 **VacationHours** 列と **SickLeaveHours** 列の値を加算します。  
  
```  
VacationHours + SickLeaveHours  
```  
  
 この例では、計算した値を **StandardCost** 列に加算します。 変数 **Profit%** は、名前に % 文字が含まれているため、角かっこで囲む必要があります。 詳細については、「[識別子 (SSIS)](../../integration-services/expressions/identifiers-ssis.md)」を参照してください。  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
