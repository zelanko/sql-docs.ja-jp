---
title: NOT (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b4a28c6be2c956636f303ccc561936f799c63b64
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68008253"
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  数値式の論理否定を実行する論理演算子です。  
  
## <a name="syntax"></a>構文  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 引数の結果が TRUE の場合は FALSE を返し、そうでない場合は TRUE を返すブール値です。  
  
## <a name="remarks"></a>Remarks  
 引数は、演算子が論理否定を実行する前に、ブール値 (FALSE の場合は0、それ以外の場合は TRUE) として処理されます。 *Expression1*が TRUE の場合、演算子は FALSE を返します。 *Expression1*が FALSE の場合、演算子は TRUE を返します。 次の表は、論理積の実行方法を示しています。  
  
|Expression1|戻り値はです。|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>参照  
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;論理演算子](../dmx/operators-logical.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
