---
title: "- (減算)(SSIS 式) |Microsoft ドキュメント"
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
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d185d99f8ebd22d05446eadb556bd7ebcb95cb2f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="--subtract-ssis-expression"></a>- (減算) (SSIS 式)
  最初の数値式から 2 番目の数値式を減算します。  
  
## <a name="syntax"></a>構文  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression1、numeric_expression2*  
 数値データ型の有効な式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数のデータ型によって決まります。 詳細については、「 [式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 式が正しい順序で評価されるようにするために、マイナス単項式はかっこで囲みます。  
  
## <a name="remarks"></a>解説  
 オペランドのいずれかが NULL の場合、結果は NULL になります。  
  
## <a name="expression-examples"></a>式の例  
 この例では、数値リテラルを減算します。  
  
```  
5 - 6.09  
```  
  
 この例では、 **ListPrice** 列の値から **StandardCost** 列の値を減算します。  
  
```  
ListPrice - StandardCost  
```  
  
 この例では、計算した値を **ListPrice** 列から減算します。 変数 **Discount%** は、名前に % 文字が含まれているため、角かっこで囲む必要があります。 詳細については、「[識別子 &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md)」を参照してください。  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40; です。SSIS 式と &#41; です。](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
