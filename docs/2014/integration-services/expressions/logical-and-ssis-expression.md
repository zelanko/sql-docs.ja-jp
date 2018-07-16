---
title: '&amp;&amp; (論理 AND) (SSIS 式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- '&& (logical AND)'
- AND, logical AND
- logical AND (&&)
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0185c28d970a1698a4159daefbbca9338b2a66cb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302262"
---
# <a name="ampamp-logical-and-ssis-expression"></a>&amp;&amp; (論理 AND) (SSIS 式)
  論理 AND 演算を実行します。 両方の条件が TRUE の場合、式は TRUE に評価されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## <a name="arguments"></a>引数  
 *boolean _expression1, boolean_expression2*  
 TRUE、FALSE、または NULL に評価される、任意の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="remarks"></a>コメント  
 次の表は、&& 演算子の結果を示します。  
  
|結果|式|式|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## <a name="expression-examples"></a>式の例  
 この例では、 **StandardCost** 列と **ListPrice** 列を使用しています。 **StandardCost** 列の値が 300 より小さく、かつ **ListPrice** 列の値が 500 より大きい場合、式は TRUE に評価されます。  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 この例では、リテラルの代わりに変数 **SPrice** と **LPrice** を使用しています。  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## <a name="see-also"></a>参照  
 [&&#40;ビットごとの AND&#41; &#40;SSIS 式&#41;](bitwise-and-ssis-expression.md)   
 [演算子の優先順位と結合規則](operator-precedence-and-associativity.md)   
 [演算子&#40;SSIS 式&#41;](operators-ssis-expression.md)  
  
  
