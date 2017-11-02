---
title: "データ マイニング拡張機能 (DMX) 演算子リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- operators [DMX]
- DMX [Analysis Services], operators
- Data Mining Extensions [Analysis Services], operators
ms.assetid: a6d747c0-9ff0-475f-86cd-34bebd79c21a
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d4958e829a3b857d9aff25dff8d38e49b88f9b3c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="data-mining-extensions-dmx-operator-reference"></a>データ マイニング拡張機能 (DMX) 演算子リファレンス
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ マイニング拡張機能 (DMX) 言語で[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]算術演算子、代入、比較、論理、および単項演算子をサポートしています。 次の表は、DMX がサポートする演算子について示しています。  
  
|演算子|Description|  
|--------------|-----------------|  
|[+ (& a) #40 です。追加 (& a) #41;& # #40; DMX &#41;](../dmx/add-dmx.md)|2 つの数値を加算する算術演算子です。|  
|[-(& a) #40 です。減算 (& a) #41;& # #40; DMX &#41;](../dmx/subtract-dmx.md)|ある数値を別の数値から減算する算術演算子です。|  
|[&#42;です。&#40;です。乗算 (& a) #41;& # #40; DMX &#41;](../dmx/multiply-dmx.md)|ある数値を別の数値によって乗算する算術演算子です。|  
|[& # #40; 除算 &#41;& # #40; DMX &#41;](../dmx/divide-dmx.md)|ある数値を別の数値によって除算する算術演算子です。|  
|[(& m); 60&#40;です。小さい (& a) #41;& # #40; DMX &#41;](../dmx/less-than-dmx.md)|比較演算子です。 Null 以外の値に評価される引数の場合は TRUE を返します、左の引数の値が右の引数の値より小さい場合それ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[&#62;です。&#40;です。大きい (& a) #41;& # #40; DMX &#41;](../dmx/greater-than-dmx.md)|比較演算子です。 Null 以外の値に評価される引数の場合は TRUE を返しますの左側の引数の値が右の引数の値より大きい場合それ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[= (& a) #40 です。等しいと #41 です。& # #40; DMX &#41;](../dmx/equal-to-dmx.md)|比較演算子です。 Null 以外の値に評価される引数の場合は TRUE を返しますの左側の引数の値が右の引数の値に等しい場合それ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[(& m); 60 &#62;。&#40;です。等しい &#41; されません。& # #40; DMX &#41;](../dmx/not-equal-to-dmx.md)|比較演算子です。 NULL 以外の値として評価される引数では、左の引数の値が右の引数の値と等しくない場合に TRUE を返します。そうでない場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[(& m); 60 = (& a) #40 です。以下に &#41;& # #40; DMX &#41;](../dmx/less-than-or-equal-to-dmx.md)|比較演算子です。 Null 以外の値に評価される引数を左の引数の値が右の引数の値に等しいまたはそれよりも小さい場合に TRUE を返しますそれ以外の場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[&#62; = (& a) #40 です。大きいまたは等しい &#41;& # #40; DMX &#41;](../dmx/greater-than-or-equal-to-dmx.md)|比較演算子です。 NULL 以外の値として評価される引数では、左の引数の値が右の引数の値以上の場合に TRUE を返します。そうでない場合は FALSE を返します。 どちらかまたは両方の引数の結果が NULL 値の場合、演算子は NULL 値を返します。|  
|[および & # #40; DMX &#41;](../dmx/and-dmx.md)|2 つの数値式の積を実行する論理演算子です。|  
|[いない & # #40; DMX &#41;](../dmx/not-dmx.md)|数値式の否定を実行する論理演算子です。|  
|[または & # #40; DMX &#41;](../dmx/or-dmx.md)|2 つの数値式の和を実行する論理演算子です。|  
|[+ (& a) #40 です。正の値&#41;& # #40; DMX &#41;](../dmx/positive-dmx.md)|数値式の正の値を返す単項演算子です。|  
|[-(& a) #40 です。負の値&#41;& # #40; DMX &#41;](../dmx/negative-dmx.md)|数値式の負の値を返す単項演算子です。|  
|[2 つのスラッシュ &#40;です。コメント &#41;& # #40; DMX &#41;](../dmx/double-slash-comment-dmx.md)|テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、DMX ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。|  
|[--&#40;です。コメント &#41;& # #40; DMX &#41;概要](../dmx/comment-dmx-summary.md)|テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、DMX ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。|  
|[スラッシュ スター &#40;です。コメント &#41;& # #40; DMX &#41;](../dmx/slash-star-comment-dmx.md)|テキストを示す文字列を[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]実行する必要があります。 コメントは、DMX ステートメント内で入れ子にしたり、コード行の最後に含めたり、別の行に挿入したりすることができます。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能 &#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  

