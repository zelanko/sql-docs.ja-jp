---
title: 除算 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 86b4d8c97996733396e3062e134b2e31d2819ec0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62471313"
---
# <a name="divide-mdx"></a>除算 (MDX)


  除算を実行し、0 による除算の別の結果または BLANK() を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>引数  
 *numerator*  
 分割する被除数または数。  
  
 *denominator*  
 除算する除数または数。  
  
 *alternateresult*  
 (省略可能) 0 による除算でエラーが発生したときに返される値です。 指定しない場合、既定値は BLANK() です。  
  
## <a name="remarks"></a>コメント  
 0 による除算の別の結果は定数である必要があります。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
