---
title: AND (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea3cacd8fe2d80e6037cf83df9eea1fd112a4b05
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971831"
---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  2つの数値式の論理積を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効なデータマイニング拡張機能 (DMX) 式です。  
  
 *Expression2*  
 数値を返す有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが TRUE と評価される場合に TRUE を返すブール値です。それ以外の場合は FALSE。  
  
## <a name="remarks"></a>注釈  
 どちらのパラメーターもブール値として処理されます (FALSE の場合は0、それ以外の場合は TRUE)。 次の表に、パラメーター値のさまざまな組み合わせに基づいて返される値を示します。  
  
|Expression1|Expression2|戻り値はです。|  
|-----------------------|-----------------------|---------------------|  
|true|true|true|  
|TRUE|FALSE|false|  
|FALSE|TRUE|FALSE|  
|false|false|false|  
  
## <a name="see-also"></a>参照  
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;論理演算子](../dmx/operators-logical.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
