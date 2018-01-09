---
title: "Aggregation 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Aggregation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Aggregation
helpviewer_keywords: Aggregation element
ms.assetid: f37af388-b2b3-4234-a1d6-936ee9b7f2ae
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e4d6801123ab0a07ff4243d1147673f3baedb07d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="aggregation-element-assl"></a>Aggregation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]1 つの集計を定義、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)要素。  
  
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
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[集計](../../../analysis-services/scripting/collections/aggregations-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[名](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Aggregation>します。  
  
## <a name="see-also"></a>参照  
 [Partition 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)   
 [AggregationDesign 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [MeasureGroup 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
