---
title: '- (負数化) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6a10ddc0db0edf2509b6b74b5f3d3c394dab0ad2
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272063"
---
# <a name="--negate-ssis-expression"></a>- (負数化) (SSIS 式)
  数値式を負数化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 任意の数値データ型の有効な式です。 サポートされるデータ型は、符号付き数値データ型のみです。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="result-types"></a>戻り値の型  
 データ型を返す *numeric_expression*です。  
  
## <a name="expression-examples"></a>式の例  
 この例では、変数 **Counter** の値を負数化して、数値リテラル 50 を加算します。  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a>参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
