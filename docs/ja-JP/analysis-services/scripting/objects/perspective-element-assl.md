---
title: Perspective 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
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
- Perspective Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bf23f3a033a4600d3c3022c5e074c693e531d890
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="perspective-element-assl"></a>Perspective 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  詳細のパースペクティブを定義、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
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
|親要素|[パースペクティブ](../../../analysis-services/scripting/collections/perspectives-element-assl.md)|  
|子要素|[アクション](../../../analysis-services/scripting/collections/actions-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[計算](../../../analysis-services/scripting/collections/calculations-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [DefaultMeasure](../../../analysis-services/scripting/properties/defaultmeasure-element-assl.md)、 [説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [Kpi](../../../analysis-services/scripting/collections/kpis-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [MeasureGroups](../../../analysis-services/scripting/collections/measuregroups-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 パースペクティブでは、含まれるディメンション、階層、属性、その他の詳細を選択し、含まれるデータのスライスを定義することによって、キューブのサブセットが提供されます。 パースペクティブは 1 つのキューブにより所有されます。 パースペクティブ内のオブジェクトをオーバーライドしたり追加したりすることはできません。すべてのディメンション、階層、その他の詳細は、基になるキューブに存在する必要があります。 オブジェクトを含めたり、非表示としてマークすることもできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Perspective>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
