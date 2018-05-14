---
title: Perspective 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d84b369134c55a09317ae8812f2d511e147605bf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
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
  
  
