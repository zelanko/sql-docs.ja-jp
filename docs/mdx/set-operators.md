---
title: "集合演算子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ed67b969d53eeb65009926cade623d2b87b9e175
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="set-operators"></a>セット演算子
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  多次元式 (MDX) では、セット演算子はメンバーまたはセットに対して操作を実行し、セットを返します。 MDX 式の中で集合関数の代わりにセット演算子を使用する場合があります。  
  
 MDX では、以下の表に示すセット演算子がサポートされます。  
  
|演算子|Description|  
|--------------|-----------------|  
|[-(を除く)](../mdx/except-mdx-operator.md)|2 つの集合から重複するメンバーを除去し、両者の差を返します。<br /><br /> この演算子は機能的に等価、[を除く](../mdx/except-mdx-function.md)関数。|  
|[* (クロス積)](../mdx/crossjoin-mdx-operator-reference.md)|2 つのセットのクロス積を返します。<br /><br /> この演算子は機能的に等価、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。|  
|[: (範囲)](../mdx/range-mdx.md)|自然な順序で並べた集合を返します。指定された 2 つのメンバーが終端になり、その 2 つのメンバーの間にあるすべてのメンバーが集合のメンバーに含まれます。|  
|[+ (Union)](../mdx/union-mdx-operator-reference.md)|2 つの集合から重複するメンバーを除外し、両者の和集合を返します。<br /><br /> この演算子は機能的に等価、[共用体 & #40 です。MDX と #41 です。](../mdx/union-mdx.md)関数。|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [MDX 演算子リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)   
 [演算子 & #40 です。MDX 構文 &#41;](../mdx/operators-mdx-syntax.md)  
  
  

