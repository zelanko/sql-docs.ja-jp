---
title: CODEPOINT (SSIS 式) | Microsoft Docs
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
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3e531f3cca54af2bd224d1822776ddb8cb466d44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332322"
---
# <a name="codepoint-ssis-expression"></a>CODEPOINT (SSIS 式)
  文字式の一番左の文字の Unicode コード ポイントを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 一番左の文字を評価する文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_UI2  
  
## <a name="remarks"></a>コメント  
 *character_expression* は、DT_WSTR データ型である必要があります。  
  
 *character_expression* が NULL または空の文字列の場合、CODEPOINT は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、文字列リテラルを使用します。 返される結果は 77 で、Unicode コード ポイントは M です。  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 この例では、変数を使用します。 **Name** が Touring Front Wheel の場合、返される結果は 84 で、Unicode コード ポイントは T です。  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a>参照  
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  
