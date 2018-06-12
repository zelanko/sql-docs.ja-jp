---
title: 集合演算子 |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df58b5c7f6da05700f00b4ec5fd46b81926dd3bb
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742971"
---
# <a name="set-operators"></a>セット演算子


  多次元式 (MDX) では、セット演算子はメンバーまたはセットに対して操作を実行し、セットを返します。 MDX 式の中で集合関数の代わりにセット演算子を使用する場合があります。  
  
 MDX では、以下の表に示すセット演算子がサポートされます。  
  
|演算子|説明|  
|--------------|-----------------|  
|[- (を除く)](../mdx/except-mdx-operator.md)|2 つの集合から重複するメンバーを除去し、両者の差を返します。<br /><br /> この演算子は機能的に等価、[を除く](../mdx/except-mdx-function.md)関数。|  
|[* (クロス積)](../mdx/crossjoin-mdx-operator-reference.md)|2 つのセットのクロス積を返します。<br /><br /> この演算子は機能的に等価、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。|  
|[: (範囲)](../mdx/range-mdx.md)|自然な順序で並べた集合を返します。指定された 2 つのメンバーが終端になり、その 2 つのメンバーの間にあるすべてのメンバーが集合のメンバーに含まれます。|  
|[+ (和集合)](../mdx/union-mdx-operator-reference.md)|2 つの集合から重複するメンバーを除外し、両者の和集合を返します。<br /><br /> この演算子は機能的に等価、[共用体&#40;MDX&#41; ](../mdx/union-mdx.md)関数。|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
