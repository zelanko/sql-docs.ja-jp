---
title: DiscretizationMethod 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DiscretizationMethod Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DiscretizationMethod
helpviewer_keywords:
- DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75308b5270eb762236be22fc0838a480474898dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200478"
---
# <a name="discretizationmethod-element-assl"></a>DiscretizationMethod 要素 (ASSL)
  分離に使用するメソッドを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `DiscretizationMethod` 要素の値は、`DimensionAttribute` または `ScalarMiningStructureColumn` の値が特定のグループ セットにどのように分離されるか (編成されるか) を決定します。 分離メソッドの詳細については、次を参照してください。[分離メソッド&#40;データ マイニング&#41;](../../data-mining/discretization-methods-data-mining.md)します。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*自動*|マイニング構造列における AUTOMATIC 分離メソッドに相当します。|  
|*EqualAreas*|マイニング構造列における EQUAL_AREAS 分離メソッドに相当します。|  
|*クラスター*|マイニング構造列における CLUSTERS 分離メソッドに相当します。|  
|*しきい値*|マイニング構造列における THRESHOLDS 分離メソッドに相当します。|  
|*EqualRanges*|マイニング構造列における EQUAL_RANGES 分離メソッドに相当します。|  
  
 許容された値に対応する列挙`DiscretizationMethod`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.DiscretizationMethod>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
