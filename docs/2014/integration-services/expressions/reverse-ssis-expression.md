---
title: REVERSE (SSIS 式) | Microsoft Docs
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
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 02175d277793a1be7ca7d82edc4fd47b862d26f3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174205"
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
  
## <a name="remarks"></a>コメント  
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
  
## <a name="see-also"></a>参照  
 [関数&#40;SSIS 式&#41;](functions-ssis-expression.md)  
  
  