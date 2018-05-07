---
title: されません (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NOT
dev_langs:
- DMX
helpviewer_keywords:
- NOT operator [DMX]
ms.assetid: 6d91b3d9-270c-4a68-b41f-169cff5faa0e
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 155dbc89f38ad39a87bbf2e69171e741735ec8a0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
 有効な DMX 式、数値を返します。  
  
## <a name="return-value"></a>戻り値  
 引数の結果が TRUE の場合は FALSE を返し、そうでない場合は TRUE を返すブール値です。  
  
## <a name="remarks"></a>解説  
 引数は、演算子が論理否定を実行する前に、ブール値 (FALSE の場合は 0、そうでない場合は TRUE) として処理されます。 場合*Expression1* TRUE の場合は、演算子は FALSE を返します。 場合*Expression1* FALSE が使用され、演算子は TRUE を返します。 次の表は、論理積の実行方法について示しています。  
  
|Expression1|戻り値します。|  
|-----------------------|---------------------|  
|TRUE|FALSE|  
|FALSE|TRUE|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41; 演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [論理演算子 &#40;DMX&#41;](../dmx/operators-logical.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
