---
title: REVERSE (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 42b74657402e3e4b8ade0deaf2505217ceb0c0de
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093648"
---
# <a name="reverse-ssis-expression"></a>REVERSE (SSIS 式)
  文字式を逆に並べ替えたものを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 逆に並べ替える対象となる文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 *character_expression* 引数は、DT_WSTR データ型である必要があります。  
  
 *character_expression* が NULL の場合、REVERSE は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、文字列リテラルを使用します。 返される結果は "ekiB niatnuoM" です。  
  
```  
REVERSE("Mountain Bike")  
```  
  
 この例では、変数を使用します。 **Name** に Touring Bike が含まれる場合、返される結果は "ekiB gniruoT" です。  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a>関連項目  
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  
