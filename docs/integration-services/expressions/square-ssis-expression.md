---
title: SQUARE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4894a3fea551a6ca428920910900164d7f94a62
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913505"
---
# <a name="square-ssis-expression"></a>SQUARE (SSIS 式)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  数値式の 2 乗値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 任意の数値データ型の数値式です。 詳細については、「 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## <a name="result-types"></a>戻り値の型  
 DT_R8  
  
## <a name="remarks"></a>解説  
 引数が NULL の場合、SQUARE は NULL を返します。  
  
 2 乗演算の前に、引数は DT_R8 データ型にキャストされます。  
  
## <a name="expression-examples"></a>式の例  
 この例では、12 の 2 乗が返されます。 返される結果は 144 です。  
  
```  
SQUARE(12)  
```  
  
 この例では、2 つの列の値を減算した結果の 2 乗が返されます。 **Value1** が 12 で **Value2** が 4 の場合、SQUARE 関数は 64 を返します。  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 この例では、SQUARE 関数を 2 つの変数に適用して、その合計の平方根を計算することにより、直角三角形の 3 番目の辺の長さが返されます。 **Side1** の値が 3、 **Side2** の値が 4 の場合、SQRT 関数は 5 を返します。  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  式に含まれる変数名には、常にプレフィックス \@ を付けます。  
  
## <a name="see-also"></a>参照  
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
