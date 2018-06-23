---
title: MeasureGroupDimension データ型 (ASSL) |Microsoft ドキュメント
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
- MeasureGroupDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupDimension
helpviewer_keywords:
- MeasureGroupDimension data type
ms.assetid: 9d1c1c19-31ce-4c42-b2e6-4c1b08875a83
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 369e20e1eaf3c5716e81a580b587c69efa64455f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176267"
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
|派生データ型|[DataMiningMeasureGroupDimension](dimension-data-type-assl.md)、 [DegenerateMeasureGroupDimension](measuregroupdimension-data-type-assl.md)、 [ManyToManyMeasureGroupDimension](manytomanymeasuregroupdimension-data-type-assl.md)、 [ReferenceMeasureGroupDimension](referencemeasuregroupdimension-data-type-assl.md)、 [RegularMeasureGroupDimension](regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CubeDimensionID](../properties/id-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)|  
|派生要素|[ディメンション](../objects/dimension-element-assl.md)([ディメンション](../collections/dimensions-element-assl.md)のコレクション[MeasureGroup](../objects/group-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 各 `MeasureGroupDimension` は、キューブにあるいずれかのディメンションへの参照です。 これにより、メジャー グループに適用されるキューブ ディメンションを定義します。  
  
 提供されている属性セットによって、メジャー グループ上でメジャーが認識される粒度 (スコープ) が指定されます。 たとえば、製品売上を表すメジャーは、Sales メジャー グループに含まれています。 これらのメジャーに関する情報は、週単位または日単位ではなく、月単位の粒度で、基になるデータ ソースに格納されています。 この場合、時間ディメンションと Sale メジャー グループ間のリレーションシップを示す `MeasureGroupDimension` の一覧には Month 属性のみが含まれます。 まれに、属性のセットに関して粒度が定義されている場合もあります。 たとえば、属性セット {Day,Week, Month, Year} で Day は Week と Month を暗黙に指定するが Week は Month を暗黙に指定しない場合、Forecasts メジャー グループに含まれるメジャーは Month および Week によって認識されるが Day によって認識されない場合があります。  
  
 属性が指定されていない場合、そのディメンションのキー属性のみが一覧に含まれ、最低の粒度レベルを定義しているかのようになります。 メジャー グループの各パーティションの粒度は同一である必要があります。 一覧表示される属性のセットは、属性間のリレーションシップが重複することはありません。 たとえば、Month が Year を暗黙に指定する場合、粒度は Month として定義され、Month と Year としては定義されません。  
  
 `MeasureGroupDimension` は、自身について示すなんらかの情報がある場合にのみ、階層を含む必要があります  (特定のメジャー グループにどの階層を適用するかを選択することはできません)。 同様を含める必要があります、 [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md)について示す固有のものがある場合のみです。  
  
 各階層に含まれている階層のサブセットである必要があります、 [CubeDimension](cubedimension-data-type-assl.md)です。 メジャー グループの粒度によっては自動的に無効になるレベルがある場合もありますが、レベルを選択することはできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MeasureGroupDimension>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  