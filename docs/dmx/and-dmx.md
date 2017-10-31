---
title: "(DMX) |Microsoft ドキュメント"
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
- AND
dev_langs:
- DMX
helpviewer_keywords:
- AND, DMX
ms.assetid: d337b20c-f80e-48be-9354-371367e53735
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bcb67e3b5c16a9bee84271eebc2083a065e924d9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="and-dmx"></a>AND (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  2 つの数値式の論理積演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 AND Expression2  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効なデータ マイニング拡張機能 (DMX) 式です。  
  
 *Expression2*  
 有効な DMX 式、数値を返します。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターの結果が TRUE の場合は TRUE を返し、そうでない場合は FALSE を返すブール値です。  
  
## <a name="remarks"></a>解説  
 両方のパラメーターは、演算子が論理積を実行する前に、ブール値 (FALSE の場合は 0、そうでない場合は TRUE) として処理されます。 次の表は、パラメーター値のさまざまな組み合わせに基づいて返される値を示します。  
  
|Expression1|Expression2|戻り値します。|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|FALSE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 &#40;DMX"&"#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [論理演算子 &#40; DMX &#41;](../dmx/operators-logical.md)   
 [演算子 &#40;DMX"&"#41;](../dmx/operators-dmx.md)  
  
  

