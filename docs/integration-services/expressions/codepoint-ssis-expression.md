---
title: CODEPOINT (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
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
ms.openlocfilehash: d0cf07cf0764ee54159b930428334e67ce4bedaa
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35409944"
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
  
## <a name="remarks"></a>Remarks  
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
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
