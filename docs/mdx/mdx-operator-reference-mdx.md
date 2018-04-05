---
title: MDX 演算子リファレンス (MDX) |Microsoft ドキュメント
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
dev_langs:
- kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], operators
- operators [MDX]
- MDX [Analysis Services], operators
ms.assetid: 1cdb8c31-a5f6-4430-b509-f81344f4622a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 5e80abbfc587b66c0059b2ae329e2ddfd009bf10
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-operator-reference-mdx"></a>MDX 演算子リファレンス (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  多次元式 (MDX) 言語は、算術演算子、論理演算子、比較演算子、セット演算子、文字列演算子、単項演算子をサポートしています。 次の表は、サポートされている演算子とその説明の一覧です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[--&#40;です。コメント &#41;&#40;です。MDX と #41 です。](../mdx/comment-mdx-operator-reference.md)|ユーザーが指定したコメントのテキストを示します。|  
|[-(& a) #40 です。除く (& a) #41;&#40;です。MDX と #41 です。](../mdx/except-mdx-operator.md)|2 つのセットの重複メンバーを削除して差集合を返すセット演算を実行します。|  
|[-(& a) #40 です。負の値&#41;&#40;です。MDX と #41 です。](../mdx/negative-mdx.md)|数値式の負の値を返す単項演算を実行します。|  
|[-(& a) #40 です。減算 (& a) #41;&#40;です。MDX と #41 です。](../mdx/subtract-mdx.md)|1 つの数から別の数を減算する算術演算を実行します。|  
|[&#42;です。&#40;です。クロス結合&#41;&#40;です。MDX と #41 です。](../mdx/crossjoin-mdx-operator-reference.md)|2 つのセットのクロス積を返すセット演算を実行します。|  
|[&#42;です。&#40;です。乗算 (& a) #41;&#40;です。MDX と #41 です。](../mdx/multiply-mdx.md)|2 つの数を乗算する算術演算を実行します。|  
|[& # #40; 除算 &#41;&#40;です。MDX と #41 です。](../mdx/divide-mdx-operator-reference.md)|1 つの数を別の数で除算する算術演算を実行します。|  
|[^ (& a) #40 です。電源 &#41;&#40;です。MDX と #41 です。](../mdx/power-mdx.md)|1 つの数を別の数で累乗する算術演算を実行します。|  
|[コメント &#40;です。MDX と #41 です。](../mdx/comment-mdx.md)|ユーザーが指定したコメントのテキストを示します。|  
|[&#40;です。コメント &#41;&#40;です。MDX と #41 です。](../mdx/comment-mdx-double-slash.md)|ユーザーが入力したテキストを示します。|  
|[: &#40;です。範囲&#41;&#40;です。MDX と #41 です。](../mdx/range-mdx.md)|自然な順序で並べたセットを返すセット演算を実行します。指定された 2 つのメンバーが終端になり、その 2 つのメンバーの間にあるすべてのメンバーがセットのメンバーに含まれます。|  
|[+ (& a) #40 です。追加 (& a) #41;&#40;です。MDX と #41 です。](../mdx/add-mdx.md)|2 つの数を加算する算術演算を実行します。|  
|[+ (& a) #40 です。正の値&#41;&#40;です。MDX と #41 です。](../mdx/positive-mdx.md)|数値式の正の値を返す単項演算を実行します。|  
|[+ (& a) #40 です。文字列の連結 &#41;&#40;です。MDX と #41 です。](../mdx/string-concatenation-mdx.md)|2 つ以上の文字列、組、または文字列と組の組み合わせを連結する文字列演算を実行します。|  
|[+ (& a) #40 です。共用体&#41;&#40;です。MDX と #41 です。](../mdx/union-mdx-operator-reference.md)|2 つのセットの重複部分を削除して和集合を返すセット演算を実行します。|  
|[(& m); 60&#40;です。小さい (& a) #41;&#40;です。MDX と #41 です。](../mdx/less-than-mdx.md)|1 つの MDX 式の値が別の MDX 式の値よりも小さいかどうかを判別する比較演算を実行します。|  
|[(& m); 60 = (& a) #40 です。以下に &#41;&#40;です。MDX と #41 です。](../mdx/less-than-or-equal-to-mdx.md)|1 つの MDX 式の値が別の MDX 式の値以下であるかどうかを判別する比較演算を実行します。|  
|[(& m); 60 &#62;。&#40;です。等しい &#41; されません。&#40;です。MDX と #41 です。](../mdx/not-equal-to-mdx.md)|1 つの MDX 式の値が別の MDX 式の値と等しくないかどうかを判別する比較演算を実行します。|  
|[= (& a) #40 です。等しいと #41 です。&#40;です。MDX と #41 です。](../mdx/equal-to-mdx.md)|1 つの MDX 式の値が別の MDX 式の値と等しいかどうかを判別する比較演算を実行します。|  
|[&#62;です。&#40;です。大きい (& a) #41;&#40;です。MDX と #41 です。](../mdx/greater-than-mdx.md)|1 つの MDX 式の値が別の MDX 式の値よりも大きいかどうかを判別する比較演算を実行します。|  
|[&#62; = (& a) #40 です。大きいまたは等しい &#41;&#40;です。MDX と #41 です。](../mdx/greater-than-or-equal-to-mdx.md)|1 つの MDX 式の値が別の MDX 式の値以上であるかどうかを判別する比較演算を実行します。|  
|[および &#40;です。MDX と #41 です。](../mdx/and-mdx.md)|2 つの数値式の論理積演算を実行します。|  
|[&#40;です。MDX と #41 です。](../mdx/is-mdx.md)|2 つのオブジェクト式の論理比較を実行します。|  
|[いない &#40;です。MDX と #41 です。](../mdx/not-mdx.md)|1 つの数値式の論理否定を実行します。|  
|[または &#40;です。MDX と #41 です。](../mdx/or-mdx.md)|2 つの数値式の論理和を実行します。|  
|[XOR &#40;です。MDX と #41 です。](../mdx/xor-mdx.md)|2 つの数値式の排他的論理和演算を実行します。|  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-language-reference-mdx.md)  
  
  
