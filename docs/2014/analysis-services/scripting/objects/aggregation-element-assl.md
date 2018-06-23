---
title: Aggregation 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Aggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Aggregation
helpviewer_keywords:
- Aggregation element
ms.assetid: f37af388-b2b3-4234-a1d6-936ee9b7f2ae
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 59f33b45653f614702b1472e57fe4464cf172b73
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163948"
---
# <a name="aggregation-element-assl"></a>Aggregation 要素 (ASSL)
  1 つの集計を定義、[パーティション](partition-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Aggregations>  
      <Aggregation>  
      <ID>...</ID>  
      <Name>...</Name>  
      <Dimensions>...</Dimensions>  
            <Annotations>...</Annotations>  
      <Description>...</Description>  
   </Aggregation>  
</Aggregations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[集計](../collections/aggregations-element-assl.md)|  
|子要素|[注釈](../collections/annotations-element-assl.md)、[説明](../properties/description-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、 [ID](../properties/id-element-assl.md)、[名](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Aggregation>します。  
  
## <a name="see-also"></a>参照  
 [要素をパーティション分割&#40;ASSL&#41;](partition-element-assl.md)   
 [AggregationDesign 要素&#40;ASSL&#41;](aggregationdesign-element-assl.md)   
 [MeasureGroup 要素&#40;ASSL&#41;](group-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  