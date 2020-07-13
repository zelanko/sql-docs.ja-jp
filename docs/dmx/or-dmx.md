---
title: OR (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 9ce963b2322e19e4e3a98982a88f99d3546cabc2
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83668728"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2つの数値式の論理和を実行する論理演算子です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効なデータマイニング拡張機能 (DMX) 式です。  
  
 *Expression2*  
 数値を返す有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 いずれかまたは両方の引数が TRUE に評価される場合に TRUE を返すブール値です。それ以外の場合は FALSE。  
  
## <a name="remarks"></a>Remarks  
 両方の引数は、演算子が論理和を実行する前に、ブール値 (FALSE の場合は0、それ以外の場合は TRUE) として扱われます。 いずれかの引数または両方の引数が TRUE に評価された場合、演算子は TRUE を返します。 *Expression1*が true と評価され、 *Expression2*が FALSE と評価された場合、演算子は true を返します。  
  
 次の表は、論理和の実行方法を示しています。  
  
|Expression1|Expression2|戻り値はです。|  
|-----------------------|-----------------------|---------------------|  
|true|true|true|  
|true|FALSE|TRUE|  
|FALSE|TRUE|true|  
|false|false|false|  
  
## <a name="see-also"></a>参照  
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;論理演算子](../dmx/operators-logical.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
