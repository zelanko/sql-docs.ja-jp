---
title: "MeasureID 要素 (ASSL) |Microsoft ドキュメント"
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
- MeasureID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureID
helpviewer_keywords:
- MeasureID element
ms.assetid: 8457aebc-8fdd-4683-8640-baaf9d89b2a2
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0af1f1741ecfe2e50b4fae97c579e9259c0955e8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="measureid-element-assl"></a>MeasureID 要素 (ASSL)
  関連付けます、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)要素を親要素です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureBinding> <!-- or AggregationInstanceMeasure, PerspectiveMeasure -->  
   ...  
   <MeasureID>...</MeasureID>  
   ...  
</MeasureBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/aggregationinstancemeasure-data-type-assl.md)、 [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)、 [PerspectiveMeasure](../../../analysis-services/scripting/data-type/perspectivemeasure-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**MeasureID**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.AggregationInstanceMeasure>、 <xref:Microsoft.AnalysisServices.MeasureBinding>、および<xref:Microsoft.AnalysisServices.PerspectiveMeasure>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

