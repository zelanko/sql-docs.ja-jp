---
title: 集合演算子 |Microsoft Docs
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150167"
---
# <a name="set-operators"></a>セット演算子


  多次元式 (MDX) では、セット演算子はメンバーまたはセットに対して操作を実行し、セットを返します。 多くの場合、セット演算子を使用するには、代わりに、MDX 式内でいくつかのセット関数。  
  
 MDX では、以下の表に示すセット演算子がサポートされます。  
  
|演算子|説明|  
|--------------|-----------------|  
|[- (を除く)](../mdx/except-mdx-operator.md)|重複するメンバーを削除する 2 つのセット間の差を返します。<br /><br /> この演算子は機能的に等価、[を除く](../mdx/except-mdx-function.md)関数。|  
|[* (クロス積)](../mdx/crossjoin-mdx-operator-reference.md)|2 つのセットのクロス積を返します。<br /><br /> この演算子は機能的に等価、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。|  
|[:(範囲)](../mdx/range-mdx.md)|エンドポイントとして指定した 2 つのメンバーと、すべてのメンバー、セットのメンバーとして含まれている 2 つの指定したメンバーの間の自然順序のセットを返します。|  
|[+ (和集合)](../mdx/union-mdx-operator-reference.md)|重複するメンバーを除く、2 つのセットの和集合を返します。<br /><br /> この演算子は機能的に等価、[共用体&#40;MDX&#41; ](../mdx/union-mdx.md)関数。|  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
