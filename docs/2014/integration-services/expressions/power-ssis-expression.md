---
title: POWER (SSIS 式) | Microsoft Docs
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
- POWER function
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b949c3191e00d3c6f1fc30f46ababfa2fd868d2f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245202"
---
# <a name="power-ssis-expression"></a>POWER (SSIS 式)
  指定された数値式の結果をべき乗値で返します。 power パラメーターは整数に評価される必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な数値式です。  
  
 *power*  
 有効な数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_R8  
  
## <a name="remarks"></a>コメント  
 *numeric_expression* 引数と *power* 引数は、べき乗値の計算前に DT_R8 データ型にキャストされます。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
 *numeric_expression* が 0 に評価され、 *power* が負の値の場合、式エバリュエーターはエラーを返し、返される結果を NULL に設定します。  
  
 *numeric_expression* または *power* の結果が不確定に評価される場合、返される結果は NULL になります。  
  
 *power* 引数には小数を使用できます。 たとえば、power 引数として値 0.5 を使用できます。  
  
## <a name="expression-examples"></a>式の例  
 この例では、数値リテラルを使用しています。 関数は、4 を 3 乗して 64 を返します。  
  
```  
POWER(4,3)  
```  
  
 この例では、 **Length** 列と **DimensionCount** 変数を使用します。 **Length** が 8、 **DimensionCount** が 2 の場合、返される結果は 64 になります。  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## <a name="see-also"></a>参照  
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  
