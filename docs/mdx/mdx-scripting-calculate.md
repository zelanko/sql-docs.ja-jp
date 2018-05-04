---
title: CALCULATE ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CALCULATE
dev_langs:
- kbMDX
helpviewer_keywords:
- CALCULATE statement
ms.assetid: 41e196a1-d49e-487b-a42a-73e5d441ed1b
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 9be6ad404ade5784ab86845b90cda51b2b939bdf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-scripting---calculate"></a>MDX スクリプティングの計算
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  キューブの各セルに集計値を格納します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CALCULATE  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="remarks"></a>解説  
 使用してキューブを作成するときに、CALCULATE ステートメントは、キューブの MDX スクリプト内の最初のステートメントとして自動的に含まれる[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]です。 CALCULATE ステートメントは、キューブの各セルに対して、粒度の低いセルから集計を行うよう指定します。 セルの集計後、式を使用して粒度の低いセルに値を設定すると、粒度の高いセルの集計値に反映されます。 通常はこの集計をそのまま使用しますが、CALCULATE ステートメントを削除することも、先に他のステートメントを実行することもできます。  
  
 MDX スクリプト内で入れ子になっているサブキューブに CALCULATE ステートメントを含めることはできません。 入れ子構造のサブキューブは、SCOPE ステートメントを使用して定義します。 SCOPE ステートメントの詳細については、次を参照してください。 [SCOPE ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-scope.md)です。  
  
> [!NOTE]  
>  計算されるメンバーは集計されません。  
  
## <a name="see-also"></a>参照  
 [MDX スクリプト ステートメント&#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [MDX スクリプティングの基礎と #40 です。Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [割り当てとその他のスクリプト コマンドの定義](../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md)  
  
  
