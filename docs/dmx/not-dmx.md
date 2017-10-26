---
title: "されません (DMX) |Microsoft ドキュメント"
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 947d066f9dd13d7f4af15407987fcf218c275cc2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="not-dmx"></a>NOT (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

