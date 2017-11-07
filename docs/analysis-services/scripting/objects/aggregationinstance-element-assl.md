---
title: "AggregationInstance 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AggregationInstance Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AggregationInstance element
ms.assetid: 2e77e9e1-9f2c-4df4-9aa6-5b7b911016a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f9a3840c481d63b06357fa8c76b9f3fc7c2ae6bc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
|親要素|[AggregationInstances](../../../analysis-services/scripting/collections/aggregationinstances-element-assl.md)|  
|子要素|[AggregationID](../../../analysis-services/scripting/properties/aggregationid-element-assl.md)、 [AggregationType](../../../analysis-services/scripting/properties/aggregationtype-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、[メジャー](../../../analysis-services/scripting/collections/measures-element-assl.md)、 [ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>解説  
 ときに、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素を使用して、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)要素をそのパーティションの集計を生成する各[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)で、 **AggregationDesign**そのパーティションに対してインスタンス化します。 複数のパーティションで同じ集計デザインを使用して、定義されている集計の複数のインスタンスを生成できます。 **AggregationInstance**要素が定義されている集計のインスタンスを表します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationInstance>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

