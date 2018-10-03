---
title: Kpi 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Kpi Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Kpi
helpviewer_keywords:
- Kpi element
ms.assetid: 1979a58f-97a8-4c1a-aa65-dcfb6d2404cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 63b7947785976d41cda112b1c14b3829e3f98e3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124152"
---
# <a name="kpi-element-assl"></a>Kpi 要素 (ASSL)
  内で主要業績評価指標 (KPI) を定義する、[キューブ](cube-element-assl.md)要素または[パースペクティブ](perspective-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Kpis>  
   <Kpi> <!-- ancestor: Cube -->  
            <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DisplayFolder>...</DisplayFolder>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <Value>...</Value>  
            <Goal>...</Goal>  
      <Status>...</Status>  
      <Trend>...</Trend>  
      <TrendGraphic>...</TrendGraphic>  
      <StatusGraphic>...</StatusGraphic>  
      <CurrentTimeMember>...</CurrentTimeMember>  
      <Annotations>...</Annotations>  
   </Kpi>  
   <!-- or -->  
   <Kpi xsi:type="PerspectiveKpi">...</Kpi> <!-- ancestor: Perspective -->  
   </Kpi>  
</Kpis>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[Cube](cube-element-assl.md)|なし|  
|[パースペクティブ](../data-type/perspectivekpi-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Kpi](../collections/kpis-element-assl.md)|  
  
## <a name="child-elements"></a>子要素  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[キューブ](../collections/annotations-element-assl.md)、 [AssociatedMeasureGroupID](../properties/id-element-assl.md)、 [CurrentTimeMember](member-element-assl.md)、[説明](../properties/description-element-assl.md)、 [DisplayFolder](../properties/displayfolder-element-assl.md)、 [目標](../properties/goal-element-assl.md)、 [ID](../properties/id-element-assl.md)、[名前](../properties/name-element-assl.md)、[状態](../properties/status-element-assl.md)、 [StatusGraphic](../properties/statusgraphic-element-assl.md)、[翻訳](../collections/translations-element-assl.md)、[傾向](../properties/trend-element-assl.md)、 [TrendGraphic](../properties/trendgraphic-element-assl.md)、[値](../properties/value-element-assl.md)|  
|[パースペクティブ](perspective-element-assl.md)|なし|  
  
## <a name="remarks"></a>Remarks  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.Kpi> と <xref:Microsoft.AnalysisServices.PerspectiveKpi> です。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
