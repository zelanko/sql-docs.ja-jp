---
title: MeasureID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureID
helpviewer_keywords:
- MeasureID element
ms.assetid: 8457aebc-8fdd-4683-8640-baaf9d89b2a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 87f79713090454e2426212eeecf56630eac7fe2c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48197551"
---
# <a name="measureid-element-assl"></a>MeasureID 要素 (ASSL)
  関連付けます、[メジャー](../objects/measure-element-assl.md)親要素を持つ要素。  
  
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstanceMeasure](../data-type/aggregationinstancemeasure-data-type-assl.md)、 [MeasureBinding](../data-type/binding-data-type-assl.md)、 [PerspectiveMeasure](../data-type/perspectivemeasure-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`MeasureID`分析管理オブジェクト (AMO) オブジェクト モデルは、 <xref:Microsoft.AnalysisServices.AggregationInstanceMeasure>、 <xref:Microsoft.AnalysisServices.MeasureBinding>、および<xref:Microsoft.AnalysisServices.PerspectiveMeasure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
