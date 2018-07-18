---
title: CalculationProperty 要素 (ASSL) |Microsoft Docs
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
- CalculationProperty Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalculationProperty
helpviewer_keywords:
- CalculationProperty element
ms.assetid: 5f0b4cfc-7d25-4c01-a517-cc2e89859be3
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 251cd4bd439fad70fd64e1c5ebf4be2965cf983d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308402"
---
# <a name="calculationproperty-element-assl"></a>CalculationProperty 要素 (ASSL)
  使用される計算のユーザー インターフェイスのプロパティのコレクションを格納する[MdxScript](mdxscript-element-assl.md)要素。  
  
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
|親要素|[CalculationProperties](../collections/calculationproperties-element-assl.md)|  
|子要素|[AssociatedMeasureGroupID](../properties/id-element-assl.md)、 [BackColor](../properties/backcolor-element-assl.md)、 [CalculationReference](../properties/calculationreference-element-assl.md)、 [CalculationType](../properties/calculationtype-element-assl.md)、[説明](../properties/description-element-assl.md)、[DisplayFolder](../properties/displayfolder-element-assl.md)、 [FontFlags](../properties/fontflags-element-assl.md)、 [FontName](../properties/name-element-assl.md)、 [FontSize](../properties/fontsize-element-assl.md)、 [ForeColor](../properties/forecolor-element-assl.md)、[FormatString](../properties/formatstring-element-assl.md)、 [NonEmptyBehavior](../properties/nonemptybehavior-element-assl.md)、 [SolveOrder](../properties/solveorder-element-assl.md)、[翻訳](../collections/translations-element-assl.md)、[表示](../properties/visible-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
