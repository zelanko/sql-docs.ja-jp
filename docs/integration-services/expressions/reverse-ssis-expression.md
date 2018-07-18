---
title: REVERSE (SSIS 式) | Microsoft Docs
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
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f5d213179d88a70c2f02436e5b1d0b1f2674bce4
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406704"
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
  
## <a name="see-also"></a>参照  
 [関数 (SSIS 式)](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
