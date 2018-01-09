---
title: "RefreshInterval 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: RefreshInterval Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: RefreshInterval
helpviewer_keywords: RefreshInterval element
ms.assetid: 2761d26a-5fb0-452c-9a89-12f8dc658c33
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1cc3ba13afdae0f85272564985cd7e002a78a24b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="refreshinterval-element-assl"></a>RefreshInterval 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素に関連付けられているバインドされたデータの更新間隔を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding, ProactiveCachingIncrementalProcessingBinding, ProactiveCachingQueryBinding -->  
   ...  
   <RefreshInterval>...</RefreshInterval>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|XML Duration|  
|既定値|先祖または親があるとき[ProactiveCachingIncrementalProcessingBinding](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md)または[ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)既定値は 1 PT です。 その他のすべてのケースは PT1m です。|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、 [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)、 [ProactiveCachingIncrementalProcessingBinding](../../../analysis-services/scripting/data-type/proactivecachingincrementalprocessingbinding-data-type-assl.md)、 [ProactiveCachingQueryBinding](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**RefreshInterval**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.DimensionBinding>、 <xref:Microsoft.AnalysisServices.MeasureGroupBinding>、 <xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding>、および<xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
