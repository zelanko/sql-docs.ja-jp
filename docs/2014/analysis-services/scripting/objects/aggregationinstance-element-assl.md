---
title: AggregationInstance 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AggregationInstance Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aef7afde2cf93d18ad0a567f5a5e1071b7e42ebf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177902"
---
# <a name="aggregationinstance-element-assl"></a>AggregationInstance 要素 (ASSL)
  パーティションに対して集計インスタンスを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationInstances>  
   <AggregationInstance>  
      <AggregationType>...</AggregationType>  
      <AggregationID>...</AggregationID>  
      <Source>...</Source>  
      <Dimensions>...</Dimensions>  
      <Measures>...</Measures>  
      <Annotations>...</Annotations>  
   </AggregationInstance>  
</AggregationInstances>  
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
|親要素|[AggregationInstances](../collections/aggregationinstances-element-assl.md)|  
|子要素|[AggregationID](../properties/id-element-assl.md)、 [AggregationType](../properties/aggregationtype-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、[メジャー](../collections/measures-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>コメント  
 ときに、[パーティション](partition-element-assl.md)要素を使用して、 [AggregationDesign](aggregationdesign-element-assl.md)要素、そのパーティションの集計を生成する各[集計](aggregation-element-assl.md)で、`AggregationDesign`はそのパーティションに対してインスタンス化します。 複数のパーティションで同じ集計デザインを使用して、定義されている集計の複数のインスタンスを生成できます。 `AggregationInstance` 要素は、定義されている集計のインスタンスを表します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationInstance>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
