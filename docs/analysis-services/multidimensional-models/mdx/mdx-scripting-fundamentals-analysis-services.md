---
title: "MDX スクリプティングの基礎 (Analysis Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 11d9dd08521f271284c13a3d93e37fe32d8850b5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-scripting-fundamentals-analysis-services"></a>MDX スクリプティングの基礎 (Analysis Services)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]の多次元式 (MDX) スクリプトは、計算結果をキューブに格納する 1 つまたは複数の MDX 式またはステートメントから構成されます。  
  
 MDX スクリプトはキューブの計算プロセスを定義します。 また、MDX スクリプト自体がキューブの一部分だと考えることもできます。 したがって、キューブに関連した MDX スクリプトの内容を変更すると、即座にキューブの計算プロセスが変更されることになります。  
  
 MDX スクリプトを生成するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でキューブ デザイナーを使用できます。 詳細については、「 [割り当てとその他のスクリプト コマンドの定義](../../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md) 」および「 [Microsoft SQL Server 2005 の MDX スクリプトの紹介](http://go.microsoft.com/fwlink/?LinkId=81892)」を参照してください。  
  
 MDX クエリおよび計算に関するパフォーマンス問題については、「 [SQL Server Analysis Services パフォーマンス ガイド](http://go.microsoft.com/fwlink/p/?LinkId=399050)」の MDX 最適化のセクションを参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[基本的な MDX スクリプト &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)|MDX スクリプトの基礎を詳しく説明します。各キューブに付属している既定の MDX スクリプトについて、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のキューブ内で MDX スクリプトが一般的にどのように機能するかについての説明が含まれます。|  
|[スコープとコンテキストの管理 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/managing-scope-and-context-mdx.md)|MDX スクリプト内でコンテキストとスコープを管理するために [CALCULATE](../../../mdx/mdx-scripting-calculate.md) ステートメント、 [SCOPE](../../../mdx/mdx-scripting-scope.md) ステートメント、および [This](../../../mdx/this-mdx.md) 関数を使用する方法について説明します。|  
|[変数とパラメーターの使用 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-variables-and-parameters-mdx.md)|MDX スクリプト内で変数やパラメーターを使用する方法について説明します。|  
|[エラー処理 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/error-handling-mdx.md)|MDX スクリプト内でのエラー処理について説明します。|  
|[サポートされる MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/supported-mdx-mdx.md)|MDX スクリプト内でサポートされる MDX 演算子、ステートメント、関数の一覧を示します。|  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;MDX&#41;](../../../mdx/mdx-language-reference-mdx.md)  
  
  

