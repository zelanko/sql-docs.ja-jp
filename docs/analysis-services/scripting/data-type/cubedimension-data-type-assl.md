---
title: CubeDimension データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0910e7bbad6797a2e34c9684589a47203bde0b30
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cubedimension-data-type-assl"></a>CubeDimension データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|子要素|[AllMemberAggregationUsage](../../../analysis-services/scripting/properties/allmemberaggregationusage-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)、 [DimensionID](../../../analysis-services/scripting/properties/dimensionid-element-assl.md)、[階層](../../../analysis-services/scripting/collections/hierarchies-element-assl.md)、 [HierarchyUniqueNameStyle](../../../analysis-services/scripting/properties/hierarchyuniquenamestyle-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [MemberUniqueNameStyle](../../../analysis-services/scripting/properties/memberuniquenamestyle-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[表示](../../../analysis-services/scripting/properties/visible-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|派生要素|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)([ディメンション](../../../analysis-services/scripting/collections/dimensions-element-assl.md)のコレクション[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 1 つを使用する必要がある**CubeDimension**のディメンション リレーションシップごとに、**キューブ**です。 **CubeDimension**すべて、 **MeasureGroups**キューブのです。  
  
 A **CubeDimension**含める必要があります、 [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)がディメンションにある特定の階層に関する記述でも含める場合は、階層を無効にする (これにより、選択可能になりますが階層を適用する特定のディメンションの使用)、または階層を非表示にします。  
  
 同様に、 **CubeDimension**含める必要があります、 [CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)ディメンションに属性に対するに固有のものがある場合にのみです。 属性は非表示にすることができますが、特定のディメンションの使用法に適用する属性を選択することはできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
