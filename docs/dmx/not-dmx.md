---
title: NOT (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 98c40dba282c82f124d4e4ac009a046a44a283cb
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971635"
---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
## <a name="remarks"></a>注釈  
 引数は、演算子が論理否定を実行する前に、ブール値 (FALSE の場合は0、それ以外の場合は TRUE) として処理されます。 *Expression1*が TRUE の場合、演算子は FALSE を返します。 *Expression1*が FALSE の場合、演算子は TRUE を返します。 次の表は、論理積の実行方法を示しています。  
  
|Expression1|戻り値はです。|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>参照  
 [DMX&#41; オペレーターリファレンス &#40;データマイニング拡張機能](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [DMX&#41;&#40;論理演算子](../dmx/operators-logical.md)   
 [DMX&#41;&#40;オペレーター](../dmx/operators-dmx.md)  
  
  
