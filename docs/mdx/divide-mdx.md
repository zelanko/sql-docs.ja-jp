---
title: "除算 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 9fe4a47b-d5e8-4dc7-ad4a-3e47ab463f03
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7b6be129e35812c2e9f22534a0f9229ec6db6203
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="divide-mdx"></a>除算 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  除算を実行し、0 による除算の別の結果または BLANK() を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>引数  
 *分子*  
 被除数または数を分割します。  
  
 *分母*  
 除数 (割る数)。  
  
 *alternateresult*  
 (省略可能) 0 による除算でエラーが発生したときに返される値です。 指定しない場合、既定値は BLANK() です。  
  
## <a name="remarks"></a>解説  
 0 による除算の別の結果は定数である必要があります。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
