---
title: 要素 (ASSL) を測定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Measure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measure
helpviewer_keywords:
- Measure element
ms.assetid: 4c2c2ed1-7f78-4564-982a-132f13bea36f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1079cd11970fad7299064fbbfefe1d476b0daed7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059392"
---
# <a name="measure-element-assl"></a>Measure 要素 (ASSL)
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
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[AggregationInstance](../data-type/binding-data-type-assl.md)|  
|[メジャー グループ](group-element-assl.md)|なし|  
|[MeasureGroupBinding (不一致)](../data-type/measurebinding-data-type-assl.md)|  
|[PerspectiveMeasureGroup](../data-type/perspectivemeasure-data-type-assl.md)|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー](../collections/measures-element-assl.md)|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[MeasureGroup](../properties/aggregatefunction-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、 [BackColor](../properties/backcolor-element-assl.md)、 [DataType](../properties/datatype-element-assl.md)、[説明](../properties/description-element-assl.md)、 [DisplayFolder](../properties/displayfolder-element-assl.md)、 [FontFlags](../properties/fontflags-element-assl.md)、 [FontName](../properties/name-element-assl.md)、 [FontSize](../properties/fontsize-element-assl.md)、 [ForeColor](../properties/forecolor-element-assl.md)、 [FormatString](../properties/formatstring-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [MeasureExpression](../properties/expression-element-assl.md)、[名前](../properties/name-element-assl.md)、[ソース](../properties/source-element-measure-assl.md)、 [の翻訳](../collections/translations-element-assl.md)、[表示](../properties/visible-element-assl.md)|  
|他のすべて|なし|  
  
## <a name="remarks"></a>コメント  
 メジャーに対して、バインドの詳細を指定できます。 これらの詳細は、各パーティションの既定として使用されます。  
  
 比較的大きなキューブには、何百ものメジャーと階層が含まれている場合があります。 `DisplayFolder` プロパティは、クライアントにおけるユーザーの外観を定義します。 `DisplayFolder` プロパティの値には、次のいずれかのオプションが含まれている場合があります。  
  
-   空にする - メジャーがフォルダーに所属しないことを示します。  
  
-   単一のフォルダー名を含んでいる - 同じ名前のフォルダーに所属するものとしてメジャーを表示する必要があることを示します。  
  
-   円記号で区切られた複数のフォルダー名が含まれます (\\)、フォルダー階層が埋め込まを示します。  
  
 `DisplayFolder` プロパティは、計算されるメジャーおよび階層にも適用されます。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.Measure> と <xref:Microsoft.AnalysisServices.PerspectiveMeasure> です。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
