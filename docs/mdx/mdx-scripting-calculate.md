---
description: CALCULATE ステートメント (MDX)
title: CALCULATE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6ec4d0e86c2719613527ec7ea8206f980deebc3a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429764"
---
# <a name="mdx-scripting---calculate"></a>MDX スクリプティング - CALCULATE


  キューブの各セルに集計値を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="remarks"></a>解説  
 を使用してキューブを作成すると、CALCULATE ステートメントがキューブの MDX スクリプトの最初のステートメントとして自動的に含まれ [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ます。 CALCULATE ステートメントは、キューブの各セルに対して、粒度の低いセルから集計を行うよう指定します。 セルの集計後、式を使用して粒度の低いセルに値を設定すると、粒度の高いセルの集計値に反映されます。 通常はこの集計をそのまま使用しますが、CALCULATE ステートメントを削除することも、先に他のステートメントを実行することもできます。  
  
 CALCULATE ステートメントは、MDX スクリプト内の入れ子になったサブキューブに含めることはできません。 入れ子になったサブキューブは、SCOPE ステートメントを使用して定義されます。 SCOPE ステートメントの詳細については、「 [Scope ステートメント &#40;MDX&#41;](../mdx/mdx-scripting-scope.md)」を参照してください。  
  
> [!NOTE]  
>  計算されるメンバーは集計されません。  
  
## <a name="see-also"></a>参照  
 [Mdx&#41;&#40;MDX スクリプトステートメント ](../mdx/mdx-scripting-statements-mdx.md)   
 [MDX スクリプティングの基礎 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services)   
 [割り当てとその他のスクリプト コマンドの定義](https://docs.microsoft.com/analysis-services/multidimensional-models/define-assignments-and-other-script-commands)  
  
  
