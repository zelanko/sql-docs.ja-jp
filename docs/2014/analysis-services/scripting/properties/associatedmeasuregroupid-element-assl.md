---
title: AssociatedMeasureGroupID 要素 (ASSL) |Microsoft Docs
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
- AssociatedMeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AssociatedMeasureGroupID
helpviewer_keywords:
- AssociatedMeasureGroupID element
ms.assetid: a18ff25b-00a2-4ddf-abcc-ef4d52c8a462
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad28fbc5023c06bdc260e301732bfb1567ce27f8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155333"
---
# <a name="associatedmeasuregroupid-element-assl"></a>AssociatedMeasureGroupID 要素 (ASSL)
  ID を含む、 [MeasureGroup](../objects/group-element-assl.md)要素に関連付けられている、 [CalculationProperty](../objects/calculationproperty-element-assl.md)要素または[Kpi](../objects/kpi-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Kpi -->  
   ...  
   <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../objects/calculationproperty-element-assl.md)、 [Kpi](../objects/kpi-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 適用すると`CalculationProperty`、要素、`AssociatedMeasureGroupID`プロパティを持つ要素に適用される、 [CalculationType](calculationtype-element-assl.md)の*メンバー*します。  
  
 親に対応する要素`AssociatedMeasureGroupID`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CalculationProperty>と<xref:Microsoft.AnalysisServices.Kpi>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
