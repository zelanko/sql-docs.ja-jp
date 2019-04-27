---
title: または (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a57d0b1c7f1fa75504e786712029326fc958135
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62501813"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  論理演算子には、2 つの数値式に対して論理和演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値の値を返す有効なデータ マイニング拡張機能 (DMX) 式。  
  
 *Expression2*  
 数値の値を返す有効な DMX 式。  
  
## <a name="return-value"></a>戻り値  
 True の場合、いずれかまたは両方の引数が評価されるを TRUE にするブール値それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>コメント  
 両方の引数がブール値として扱われます (0 FALSE の場合それ以外の場合 TRUE) 論理和演算を実行します。 いずれかまたは両方の引数が TRUE と評価される、演算子は TRUE を返します。 場合*Expression1*を TRUE に評価および*Expression2*を FALSE に評価される、演算子は TRUE を返します。  
  
 次の表は、論理和演算を実行する方法を示しています。  
  
|Expression1|Expression2|戻り値は|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [論理演算子&#40;DMX&#41;](../dmx/operators-logical.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
