---
title: "要素 (ASSL) を測定 |Microsoft ドキュメント"
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
apiname: Measures Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Measures
helpviewer_keywords: Measures element
ms.assetid: d2107112-f620-4fd7-a05f-bb2606b4be18
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f00ad73b61bb0418c46380367313e63f412e16d9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="measures-element-assl"></a>Measures 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]コレクションを格納[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)親要素に関連付けられている要素です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup> <!-- or AggregationInstance, MeasureGroupBinding (out-of-line), PerspectiveMeasureGroup -->  
   ...  
   <Measures>  
      <Measure>...</Measure>  
   </Measures>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MeasureGroupBinding (不一致)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)、 [PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|  
|子要素|[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.MeasureCollection> と <xref:Microsoft.AnalysisServices.PerspectiveMeasureCollection> です。  
  
## <a name="see-also"></a>参照  
 [コレクション &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
