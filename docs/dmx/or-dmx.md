---
title: または (DMX) |Microsoft ドキュメント
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
- OR
dev_langs:
- DMX
helpviewer_keywords:
- OR operator
ms.assetid: 727a38a9-7f75-4963-8e8a-aa703c129d30
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17e7f7119125359a12690b3cb9140ae2ac382419
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 つの数値式の論理和を実行する論理演算子です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効なデータ マイニング拡張機能 (DMX) 式です。  
  
 *Expression2*  
 有効な DMX 式、数値を返します。  
  
## <a name="return-value"></a>戻り値  
 どちらかまたは両方の引数の結果が TRUE の場合に TRUE を、そうでない場合は FALSE を返すブール値です。  
  
## <a name="remarks"></a>解説  
 両方の引数は、演算子が論理和を実行する前に、ブール値 (FALSE の場合は 0、そうでない場合は TRUE) として処理されます。 どちらかまたは両方の引数の結果が TRUE の場合、演算子は TRUE を返します。 場合*Expression1*を TRUE に評価および*Expression2*が FALSE と評価、演算子は TRUE を返します。  
  
 次の表は、論理和の実行方法について示しています。  
  
|Expression1|Expression2|戻り値します。|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX&#41; 演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [論理演算子 &#40;DMX&#41;](../dmx/operators-logical.md)   
 [演算子 &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
