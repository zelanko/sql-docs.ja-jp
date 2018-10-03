---
title: LN (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- LN function
- natural logarithm of expression [Integration Services]
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cf836d26c67276b6780392bef44e1d4e5a470f86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140239"
---
# <a name="ln-ssis-expression"></a>LN (SSIS 式)
  数値式の自然対数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
LN(numeric_expression)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 0 でなく、かつ負の値でない有効な数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_R8  
  
## <a name="remarks"></a>コメント  
 この数値式は、対数の計算前に DT_R8 データ型にキャストされます。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
 *numeric_expression* が 0 または負の値に評価される場合、返される結果は NULL になります。  
  
## <a name="expression-examples"></a>式の例  
 この例では、数値リテラルを使用しています。 この関数は、値 3.737766961828337 を返します。  
  
```  
LN(42)  
```  
  
 この例では、列 **Length**を使用しています。 列の値が 53.99 の場合、この関数は 3.9887988442302 を返します。  
  
```  
LN(Length)   
```  
  
 この例では、変数 **Length**を使用しています。 変数は数値データ型である必要があります。または式に、数値データ型への明示的なキャストが含まれている必要があります。 **Length** が 234.567 の場合、関数は 5.45774126708797 を返します。  
  
```  
LN(@Length)   
```  
  
## <a name="see-also"></a>参照  
 [ログ&#40;SSIS 式&#41;](log-ssis-expression.md)   
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  
