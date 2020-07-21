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
ms.openlocfilehash: 564f09564349fa5709cefa87eca8fe847638b9b6
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669859"
---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>Remarks  
 どちらのパラメーターもブール値として処理されます (FALSE の場合は0、それ以外の場合は TRUE)。 次の表に、パラメーター値のさまざまな組み合わせに基づいて返される値を示します。  
  
|Expression1|Expression2|戻り値はです。|  
|-----------------------|-----------------------|---------------------|  
|true|true|true|  
|true|false|false|  
|FALSE|TRUE|false|  
|false|false|false|  
  
## <a name="see-also"></a>参照  
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;論理演算子](../dmx/operators-logical.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
