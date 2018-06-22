---
title: FLOOR (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: cae43e01a262258fa2fce824797b3d20682c3829
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076258"
---
# <a name="floor-ssis-expression"></a>FLOOR (SSIS 式)
  数値式以下で最大の整数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 引数の式の数値データ型です。 結果は、 *numeric_expression*と同じデータ型の、計算値の整数部分になります。  
  
## <a name="remarks"></a>コメント  
 引数が NULL の場合、FLOOR は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 次の例では、正の値、負の値、および 0 に FLOOR 関数を適用します。  
  
```  
FLOOR(123.45)  
```  
  
 123.00 を返します  
  
```  
FLOOR(-123.45)  
```  
  
 -124.00 を返します  
  
```  
FLOOR(0.00)  
```  
  
 0.00 を返します。  
  
## <a name="see-also"></a>参照  
 [CEILING &#40;SSIS 式&#41;](ceiling-ssis-expression.md)   
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  