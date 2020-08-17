---
description: 集合演算子
title: Set 演算子 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: eb4434c9fe1991e1398baaa9c7bfd9602995652d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341238"
---
# <a name="set-operators"></a>集合演算子


  多次元式 (MDX) では、セット演算子はメンバーまたはセットに対して操作を実行し、セットを返します。 多くの場合、MDX 式でいくつかのセット関数の代わりに set 演算子を使用します。  
  
 MDX では、以下の表に示すセット演算子がサポートされます。  
  
|演算子|説明|  
|--------------|-----------------|  
|[- (を除く)](../mdx/except-mdx-operator.md)|重複したメンバーを削除する2つのセットの差を返します。<br /><br /> この演算子は、機能的には [Except](../mdx/except-mdx-function.md) 関数と同等です。|  
|[* (クロス積)](../mdx/crossjoin-mdx-operator-reference.md)|2つのセットのクロス積を返します。<br /><br /> この演算子は、機能的には [Crossjoin](../mdx/crossjoin-mdx.md) 関数に相当します。|  
|[: (範囲)](../mdx/range-mdx.md)|指定された2つのメンバーをエンドポイントとして持ち、指定された2つのメンバー間のすべてのメンバーがセットのメンバーとして含まれる、自然な順序付きセットを返します。|  
|[+ (和集合)](../mdx/union-mdx-operator-reference.md)|重複するメンバーを除外して、2つのセットの和集合を返します。<br /><br /> この演算子は、機能的に [Union &#40;MDX&#41;](../mdx/union-mdx.md) 関数と同等です。|  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [MDX 構文 &#40;の演算子&#41;](../mdx/operators-mdx-syntax.md)  
  
  
