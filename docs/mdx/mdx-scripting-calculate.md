---
title: CALCULATE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 389c5f470cb3bf00cfe668a9405e36cd4ac8950e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187628"
---
# <a name="mdx-scripting---calculate"></a>MDX スクリプティング - CALCULATE


  キューブの各セルに集計値を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="remarks"></a>コメント  
 使用してキューブを作成するときに、CALCULATE ステートメントは、キューブの MDX スクリプトの最初のステートメントとして自動的に含まれる[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]します。 CALCULATE ステートメントは、キューブの各セルに対して、粒度の低いセルから集計を行うよう指定します。 セルの集計後、式を使用して粒度の低いセルに値を設定すると、粒度の高いセルの集計値に反映されます。 通常はこの集計をそのまま使用しますが、CALCULATE ステートメントを削除することも、先に他のステートメントを実行することもできます。  
  
 MDX スクリプト内で入れ子になったサブキューブに CALCULATE ステートメントを含めることができません。 入れ子構造のサブキューブを定義するには、SCOPE ステートメントを使用します。 SCOPE ステートメントの詳細については、次を参照してください。 [SCOPE ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-scope.md)します。  
  
> [!NOTE]  
>  計算されるメンバーは集計されません。  
  
## <a name="see-also"></a>参照  
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [MDX スクリプティングの基礎 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [割り当てとその他のスクリプト コマンドの定義](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
