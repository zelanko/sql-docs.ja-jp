---
title: Description 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Description Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Description
helpviewer_keywords:
- Description element
ms.assetid: 34d67e7c-e79a-429b-8cc3-6ca13b9cf9c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 19a041d81646361d1f6eefb96604829ec1928032
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126132"
---
# <a name="description-element-assl"></a>Description 要素 (ASSL)
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../objects/action-element-assl.md)、[集計](../objects/aggregation-element-assl.md)、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)、[アセンブリ](../objects/assembly-element-assl.md)、 [AttributePermission](../objects/attributepermission-element-assl.md)、 [CalculationProperty](../objects/calculationproperty-element-assl.md)、 [CellPermission](../objects/cellpermission-element-assl.md)、[キューブ](../objects/cube-element-assl.md)、 [CubeDimensionPermission](../data-type/permission-data-type-assl.md)、[データベース](../objects/database-element-assl.md)、 [DataSource](../objects/datasource-element-assl.md)、 [DataSourceView](../objects/datasourceview-element-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、[階層](../objects/hierarchy-element-assl.md)、 [Kpi](../objects/kpi-element-assl.md)、[レベル](../objects/level-element-assl.md)、 [MdxScript](../objects/mdxscript-element-assl.md)、[メジャー](../objects/measure-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、[MiningModel](../objects/miningmodel-element-assl.md)、 [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)、 [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)、 [パーティション](../objects/partition-element-assl.md)、[権限](../data-type/permission-data-type-assl.md)、[パースペクティブ](../objects/perspective-element-assl.md)、[ロール](../objects/role-element-assl.md)、 [Server](../objects/server-element-assl.md)、 [トレース](../objects/trace-element-assl.md)、[翻訳](../objects/translation-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Description` 要素の値には次の制限があります。  
  
-   値の先頭または末尾にスペースを含めることはできません。 値で、先頭または末尾のスペースが含まれているかどうか、`Description`要素、そのスペースは暗黙的に削除されますが[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
-   値は、制御文字を含めることはできません。 `Description` 要素の値に制御文字が含まれている場合、その文字は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって暗黙的に削除されます。  
  
## <a name="see-also"></a>参照  
 [要素名を指定&#40;ASSL&#41;](name-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
