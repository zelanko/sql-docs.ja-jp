---
title: Description 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7235f524cb4754470e15f250df7c61c7ffa20a26
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="description-element-assl"></a>Description 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素の説明を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Description>...</Description>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)、[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)、[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)、 [AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md)、 [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)、 [CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、 [CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)、[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)、 [パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)、[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)、 [トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)、[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、**説明**要素には、次の制限。  
  
-   値の先頭または末尾にスペースを含めることはできません。 値の先頭または末尾にスペースが含まれるかどうか、**説明**要素、そのスペースは暗黙的にによって削除されます[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
-   値は、制御文字を含めることはできません。 値に制御文字が含まれている場合、**説明**要素、これらの文字は暗黙的にによって削除されます[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [要素名を指定&#40;ASSL&#41;](../../../analysis-services/scripting/properties/name-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
