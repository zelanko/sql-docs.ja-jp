---
title: "BackColor 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: BackColor Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: BackColor
helpviewer_keywords: BackColor element
ms.assetid: 9024d131-74cc-4815-833a-f8cae57b7453
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e219fc5e38b1f420c80ad0044aa0c02eddb96673
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="backcolor-element-assl"></a>BackColor 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]親要素の色関連の表示特性を説明します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <BackColor>...</BackColor>  
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
 **BackColor**プロパティ多次元式 (MDX) 言語の式を含みに適用されます**CalculationProperty**要素を[CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)*メンバー*または*セル*です。  
  
 親に対応する要素**BackColor**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
