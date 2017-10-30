---
title: "除算 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 9fe4a47b-d5e8-4dc7-ad4a-3e47ab463f03
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2f05c20a10b72b3c919672fd528a4222c6d204d7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="divide-mdx"></a>除算 (MDX)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

