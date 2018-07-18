---
title: CEILING (SSIS 式) | Microsoft Docs
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
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d50b8c181eb600003ccad22bc6a968b3898477f5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256798"
---
# <a name="ceiling-ssis-expression"></a>CEILING (SSIS 式)
  数値式以上で最小の整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 関数に送信された数値式のデータ型です。  
  
## <a name="remarks"></a>コメント  
 引数が NULL の場合、CEILING は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、正の値、負の値、および 0 に CEILING 関数を適用します。  
  
```  
CEILING(123.74)  
```  
  
 124.00 を返します。  
  
```  
CEILING(-124.27)  
```  
  
 -124.00 を返します。  
  
```  
CEILING(0.00)  
```  
  
 0.00 を返します。  
  
## <a name="see-also"></a>参照  
 [FLOOR &#40;SSIS 式&#41;](floor-ssis-expression.md)   
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  
