---
title: データ マイニング拡張機能 (DMX) 演算子リファレンス |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a85644328591f037ee342866ca7dfb5e887ed17
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842765"
---
# <a name="data-mining-extensions-dmx-operator-reference"></a>データ マイニング拡張機能 (DMX) 演算子リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング拡張機能 (DMX) 言語で[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]算術演算子、代入、比較、論理、および単項演算子をサポートしています。 次の表は、DMX がサポートする演算子について示しています。  
  
|演算子|説明|  
|--------------|-----------------|  
|[+&#40;追加&#41; &#40;DMX&#41;](../dmx/add-dmx.md)|2 つの数値を加算する算術演算子です。|  
|[-&#40;減算&#41; &#40;DMX&#41;](../dmx/subtract-dmx.md)|ある数値を別の数値から減算する算術演算子です。|  
|[&#42;&#40;乗算&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|ある数値を別の数値によって乗算する算術演算子です。|  
|[&#40;分割&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|ある数値を別の数値によって除算する算術演算子です。|  
|[&#60;&#40;より小さい&#41; &#40;DMX&#41;](../dmx/less-than-dmx.md)|比較演算子です。 Null 以外の値に評価される引数の場合は TRUE を返します、左の引数の値が右の引数の値より小さい場合それ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[&#62;&#40;より大きい&#41; &#40;DMX&#41;](../dmx/greater-than-dmx.md)|比較演算子です。 Null 以外の値に評価される引数の場合は TRUE を返しますの左側の引数の値が右の引数の値より大きい場合それ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[=&#40;と等しい&#41; &#40;DMX&#41;](../dmx/equal-to-dmx.md)|比較演算子です。 Null 以外の値に評価される引数の場合は TRUE を返しますの左側の引数の値が右の引数の値に等しい場合それ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[&#60;&#62;&#40;等しくない&#41; &#40;DMX&#41;](../dmx/not-equal-to-dmx.md)|比較演算子です。 NULL 以外の値として評価される引数では、左の引数の値が右の引数の値と等しくない場合に TRUE を返します。そうでない場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[&#60;=&#40;以下に&#41; &#40;DMX&#41;](../dmx/less-than-or-equal-to-dmx.md)|比較演算子です。 Null 以外の値に評価される引数を左の引数の値が右の引数の値に等しいまたはそれよりも小さい場合に TRUE を返しますそれ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[&#62;=&#40;より大きいか等しい&#41; &#40;DMX&#41;](../dmx/greater-than-or-equal-to-dmx.md)|比較演算子です。 NULL 以外の値として評価される引数では、左の引数の値が右の引数の値以上の場合に TRUE を返します。そうでない場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[および&AMP;#40;DMX&AMP;#41;](../dmx/and-dmx.md)|2 つの数値式の積を実行する論理演算子です。|  
|[いない&AMP;#40;DMX&AMP;#41;](../dmx/not-dmx.md)|数値式の否定を実行する論理演算子です。|  
|[または&AMP;#40;DMX&AMP;#41;](../dmx/or-dmx.md)|2 つの数値式の和を実行する論理演算子です。|  
|[+&#40;正&#41; &#40;DMX&#41;](../dmx/positive-dmx.md)|数値式の正の値を返す単項演算子です。|  
|[-&#40;負&#41; &#40;DMX&#41;](../dmx/negative-dmx.md)|数値式の負の値を返す単項演算子です。|  
|[2 つのスラッシュ&#40;コメント&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)|テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、DMX ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。|  
|[--&#40;コメント&#41; &#40;DMX&#41;の概要](../dmx/comment-dmx-summary.md)|テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、DMX ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。|  
|[星をスラッシュ&#40;コメント&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)|テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、DMX ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
