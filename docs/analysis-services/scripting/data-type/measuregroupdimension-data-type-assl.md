---
title: "MeasureGroupDimension データ型 (ASSL) |Microsoft ドキュメント"
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
- MeasureGroupDimension Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MeasureGroupDimension
helpviewer_keywords:
- MeasureGroupDimension data type
ms.assetid: 9d1c1c19-31ce-4c42-b2e6-4c1b08875a83
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6f2d7763bd8d4d5ee42714ac102cc5ebdf37ba71
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="measuregroupdimension-data-type-assl"></a>MeasureGroupDimension データ型 (ASSL)
  ディメンションとメジャー グループとの間のリレーションシップを表す抽象プリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroupDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
      <Annotations>...</Annotations>  
   <Source>...</Source>  
</MeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|[DataMiningMeasureGroupDimension](../../../analysis-services/scripting/data-type/dataminingmeasuregroupdimension-data-type-assl.md)、 [DegenerateMeasureGroupDimension](../../../analysis-services/scripting/data-type/degeneratemeasuregroupdimension-data-type-assl.md)、 [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md)、 [ReferenceMeasureGroupDimension](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md)、 [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|派生要素|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)([ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)のコレクション[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 各**MeasureGroupDimension**キューブにディメンションの 1 つへの参照です。 これにより、メジャー グループに適用されるキューブ ディメンションを定義します。  
  
 提供されている属性セットによって、メジャー グループ上でメジャーが認識される粒度 (スコープ) が指定されます。 たとえば、製品売上を表すメジャーは、Sales メジャー グループに含まれています。 これらのメジャーに関する情報は、週単位または日単位ではなく、月単位の粒度で、基になるデータ ソースに格納されています。 Month 属性のみが表示されます。 ここで、 **MeasureGroupDimension**時間ディメンションと Sales メジャー グループ間のリレーションシップを示すです。 まれに、属性のセットに関して粒度が定義されている場合もあります。 たとえば、属性セット {Day,Week, Month, Year} で Day は Week と Month を暗黙に指定するが Week は Month を暗黙に指定しない場合、Forecasts メジャー グループに含まれるメジャーは Month および Week によって認識されるが Day によって認識されない場合があります。  
  
 属性が指定されていない場合、そのディメンションのキー属性のみが一覧に含まれ、最低の粒度レベルを定義しているかのようになります。 メジャー グループの各パーティションの粒度は同一である必要があります。 一覧表示される属性のセットは、属性間のリレーションシップが重複することはありません。 たとえば、Month が Year を暗黙に指定する場合、粒度は Month として定義され、Month と Year としては定義されません。  
  
 A **MeasureGroupDimension**について示す固有のものがある場合にのみ、階層を含める必要があります。 (特定のメジャー グループにどの階層を適用するかを選択することはできません)。 同様を含める必要があります、 [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)について示す固有のものがある場合のみです。  
  
 各階層に含まれている階層のサブセットである必要があります、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)です。 メジャー グループの粒度によっては自動的に無効になるレベルがある場合もありますが、レベルを選択することはできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MeasureGroupDimension>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

