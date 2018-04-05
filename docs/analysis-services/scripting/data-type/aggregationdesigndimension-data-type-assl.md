---
title: AggregationDesignDimension データ型 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AggregationDesignDimension Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationDesignDimension
helpviewer_keywords:
- AggregationDesignDimension data type
ms.assetid: 06a0d418-014c-4f40-a63a-5cfeee3f6a41
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3ddfc11592478d55a1ca8b253fa33c3b7af4b449
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="aggregationdesigndimension-data-type-assl"></a>AggregationDesignDimension データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]キューブ ディメンションの間のリレーションシップを表すプリミティブ データ型を定義し、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationDesignDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
   <Attributes>...</Attributes>  
      <Annotations>...</Annotations>  
</AggregationDesignDimension>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)、 [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)|  
|派生要素|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)([ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)のコレクション[AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationDesignDimension>します。  
  
## <a name="see-also"></a>参照  
 [AggregationDesign 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
