---
title: "CalculationProperty 要素 (ASSL) |Microsoft ドキュメント"
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
- CalculationProperty Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CalculationProperty
helpviewer_keywords:
- CalculationProperty element
ms.assetid: 5f0b4cfc-7d25-4c01-a517-cc2e89859be3
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 499f002694022d737b7711c0d69891a5b08059eb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="calculationproperty-element-assl"></a>CalculationProperty 要素 (ASSL)
  使用する計算のユーザー インターフェイスのプロパティのコレクションを格納、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperties>  
   <CalculationProperty>  
      <CalculationReference>...</CalculationReference>  
      <CalculationType>...</CalculationType>  
      <Translations>...</Translations>  
      <Description>...</Description>  
      <Visible>...</Visible>  
      <SolveOrder>...</SolveOrder>  
      <FormatString>...</FormatString>  
      <ForeColor>...</ForeColor>  
      <BackColor>...</BackColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <NonEmptyBehavior>...</NonEmptyBehavior>  
      <AssociatedMeasureGroupID>...</AssociatedMeasureGroupID>  
      <DisplayFolder>...</DisplayFolder>  
   </CalculationProperty>  
</CalculationProperties>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperties](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)|  
|子要素|[AssociatedMeasureGroupID](../../../analysis-services/scripting/properties/associatedmeasuregroupid-element-assl.md)、 [BackColor](../../../analysis-services/scripting/properties/backcolor-element-assl.md)、 [CalculationReference](../../../analysis-services/scripting/properties/calculationreference-element-assl.md)、 [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md)、 [FontFlags](../../../analysis-services/scripting/properties/fontflags-element-assl.md)、 [FontName](../../../analysis-services/scripting/properties/fontname-element-assl.md)、 [FontSize](../../../analysis-services/scripting/properties/fontsize-element-assl.md)、 [ForeColor](../../../analysis-services/scripting/properties/forecolor-element-assl.md)、[FormatString](../../../analysis-services/scripting/properties/formatstring-element-assl.md)、 [NonEmptyBehavior](../../../analysis-services/scripting/properties/nonemptybehavior-element-assl.md)、 [SolveOrder](../../../analysis-services/scripting/properties/solveorder-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

