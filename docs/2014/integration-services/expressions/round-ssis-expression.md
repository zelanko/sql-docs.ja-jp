---
title: ROUND (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5edad70330a5745f9d150cf8a0ad0d540132c029
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437109"
---
# <a name="round-ssis-expression"></a>ROUND (SSIS 式)
  指定された長さまたは有効桁数に丸めた数値式を返します。 length パラメーターは整数に評価される必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な数値型の式です。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
 *length*  
 整数式です。 *numeric_expression* の丸め結果とする有効桁数です。  
  
## <a name="result-types"></a>戻り値の型  
 *numeric*_*expression.* と同じ型。  
  
## <a name="remarks"></a>解説  
 *length* 引数は正の整数または 0 に評価される必要があります。  
  
 引数が NULL の場合、ROUND は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、数値リテラルを 3 桁に丸めます。 最初の結果は 137.1570 を返し、次の結果は 137.1580 を返します。  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>参照  
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
