---
title: "ForeColor 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ForeColor Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ForeColor
helpviewer_keywords: ForeColor element
ms.assetid: 5125520c-3bce-40e6-a722-8d4d47306fed
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e9db6570825c23e85ca936e8733c96d7ed1a97b0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="forecolor-element-assl"></a>ForeColor 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]色関連の表示特性を記述、 [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)または[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)親要素です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <ForeColor>...</ForeColor>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **ForeColor**プロパティは多次元式 (MDX) 式を含みに適用されます**CalculationProperty**を持つ要素を[CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)の*メンバー*または*セル*です。  
  
 親に対応する要素**ForeColor**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CalculationProperty>と<xref:Microsoft.AnalysisServices.Measure>です。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
