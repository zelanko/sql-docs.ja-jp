---
title: "集合演算子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 55d5b2c2b28a644221673c7104881d5864fbbfa7
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="set-operators"></a>セット演算子
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) では、セット演算子はメンバーまたはセットに対して操作を実行し、セットを返します。 MDX 式の中で集合関数の代わりにセット演算子を使用する場合があります。  
  
 MDX では、以下の表に示すセット演算子がサポートされます。  
  
|演算子|Description|  
|--------------|-----------------|  
|[- (を除く)](../mdx/except-mdx-operator.md)|2 つの集合から重複するメンバーを除去し、両者の差を返します。<br /><br /> この演算子は機能的に等価、[を除く](../mdx/except-mdx-function.md)関数。|  
|[* (クロス積)](../mdx/crossjoin-mdx-operator-reference.md)|2 つのセットのクロス積を返します。<br /><br /> この演算子は機能的に等価、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。|  
|[: (範囲)](../mdx/range-mdx.md)|自然な順序で並べた集合を返します。指定された 2 つのメンバーが終端になり、その 2 つのメンバーの間にあるすべてのメンバーが集合のメンバーに含まれます。|  
|[+ (和集合)](../mdx/union-mdx-operator-reference.md)|2 つの集合から重複するメンバーを除外し、両者の和集合を返します。<br /><br /> この演算子は機能的に等価、[共用体 &#40;です。MDX と #41 です。](../mdx/union-mdx.md)関数。|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)   
 [演算子 &#40;です。MDX 構文 &#41;](../mdx/operators-mdx-syntax.md)  
  
  
