---
title: CubeDimension データ型 (ASSL) |Microsoft Docs
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
- CubeDimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeDimension
helpviewer_keywords:
- CubeDimension data type
ms.assetid: 128ac790-65a1-4e35-b909-8dba2a61b24c
caps.latest.revision: 40
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a02ef89f5dac200450faf8151a71aeae703e8b35
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220325"
---
# <a name="cubedimension-data-type-assl"></a>CubeDimension データ型 (ASSL)
  ディメンションとキューブの関係を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension>  
      <ID>...</ID>  
   <Name>...</Name>  
   <Translations>...</Translations>  
   <DimensionID>...</DimensionID>  
   <Visible>...</Visible>  
   <AllMemberAggregationUsage>...</AllMemberAggregationUsage>  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
      <Attributes>...</Attributes>  
   <Hierarchies>...</Hierarchies>  
      <Annotations>...</Annotation>  
</CubeDimension>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[AllMemberAggregationUsage](../properties/aggregationusage-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、[属性](../collections/attributes-element-assl.md)、 [DimensionID](../properties/id-element-assl.md)、[階層](../collections/hierarchies-element-assl.md)、 [HierarchyUniqueNameStyle](../properties/hierarchyuniquenamestyle-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [MemberUniqueNameStyle](../properties/memberuniquenamestyle-element-assl.md)、[名前](../properties/name-element-assl.md)、[表示](../properties/visible-element-assl.md)、[翻訳](../collections/translations-element-assl.md)|  
|派生要素|[ディメンション](../objects/dimension-element-assl.md)([ディメンション](../collections/dimensions-element-assl.md)のコレクション[キューブ](../objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>コメント  
 `CubeDimension` のディメンション リレーションシップごとに 1 つの `Cube` があります。 `CubeDimension` では、キューブのすべての `MeasureGroups` が対象になります。  
  
 A`CubeDimension`含める必要があります、 [CubeHierarchy](hierarchy-data-type-assl.md)ディメンション、階層に関する特定の場合などの階層を無効にする (これにより、選択可能になりますがの階層は、特定に適用されます。ディメンションの使用法)、または階層を非表示にします。  
  
 同様に、`CubeDimension`含める必要があります、 [CubeAttribute](cubeattribute-data-type-assl.md)ディメンションに属性について固有のものがある場合にのみです。 属性は非表示にすることができますが、特定のディメンションの使用法に適用する属性を選択することはできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
