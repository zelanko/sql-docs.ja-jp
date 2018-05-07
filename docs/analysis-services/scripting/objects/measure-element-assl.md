---
title: メジャー要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d39885ddba7f1a1a012a278bc3a93dff8ec4c47a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="measure-element-assl"></a>Measure 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メジャーを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Measures>  
   <Measure> <!-- ancestor: MeasureGroup -->  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <AggregateFunction>...</AggregateFunction>  
            <DataType>...</DataType>  
            <Source>...</Source>  
      <Visible>...</Visible>  
      <MeasureExpression>...</MeasureExpression>  
      <DisplayFolder>...</DisplayFolder>  
      <FormatString>...</FormatString>  
      <BackColor>...</BackColor>  
      <ForeColor>...</ForeColor>  
            <FontName>...</FontName>  
            <FontSize>...</FontSize>  
            <FontFlags>...</FontFlags>  
            <Translations>...</Translations>  
      <Annotations>...</Annotations>  
   </Measure>  
   <!-- or  -->  
   <Measure xsi:type="AggregationInstanceMeasure">...</Measure> <!-- parent: AggregationInstance -->  
      <!-- or  -->  
   <Measure xsi:type="MeasureBinding">...</Measure> <!-- ancestor: MeasureGroupBinding (out-of-line) -->  
   <!-- or  -->  
   <Measure xsi:type="PerspectiveMeasure">...</Measure> <!-- ancestor: PerspectiveMeasureGroup -->  
</Measures>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|次の表を参照してください。|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)|[AggregationInstanceMeasure](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|なし|  
|[MeasureGroupBinding (不一致)](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../../../analysis-services/scripting/data-type/perspectivemeasuregroup-data-type-assl.md)|[PerspectiveMeasure](../../../analysis-services/scripting/data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー](../../../analysis-services/scripting/collections/measures-element-assl.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[AggregateFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [BackColor](../../../analysis-services/scripting/properties/backcolor-element-assl.md)、 [DataType](../../../analysis-services/scripting/properties/datatype-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [DisplayFolder](../../../analysis-services/scripting/properties/displayfolder-element-assl.md)、 [FontFlags](../../../analysis-services/scripting/properties/fontflags-element-assl.md)、 [FontName](../../../analysis-services/scripting/properties/fontname-element-assl.md)、 [FontSize](../../../analysis-services/scripting/properties/fontsize-element-assl.md)、 [ForeColor](../../../analysis-services/scripting/properties/forecolor-element-assl.md)、 [FormatString](../../../analysis-services/scripting/properties/formatstring-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [MeasureExpression](../../../analysis-services/scripting/properties/measureexpression-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-measure-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)|  
|他のすべて|なし|  
  
## <a name="remarks"></a>解説  
 メジャーに対して、バインドの詳細を指定できます。 これらの詳細は、各パーティションの既定として使用されます。  
  
 比較的大きなキューブには、何百ものメジャーと階層が含まれている場合があります。 **DisplayFolder**プロパティは、クライアントのユーザーの外観を定義します。 値、 **DisplayFolder**プロパティは、次のオプションのいずれかを含めることができます。  
  
-   空にする - メジャーがフォルダーに所属しないことを示します。  
  
-   単一のフォルダー名を含んでいる - 同じ名前のフォルダーに所属するものとしてメジャーを表示する必要があることを示します。  
  
-   円記号で区切られた複数のフォルダー名が含まれます (\\)、埋め込みのフォルダー階層を示すです。  
  
 **DisplayFolder**プロパティは、計算されるメジャーと階層にも適用されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.Measure> と <xref:Microsoft.AnalysisServices.PerspectiveMeasure> です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
