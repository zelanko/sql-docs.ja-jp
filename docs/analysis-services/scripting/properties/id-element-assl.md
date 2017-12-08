---
title: "ID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ID Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ID
helpviewer_keywords: ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e0f489f02475053495704cdf82c30d5253abf949
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="id-element-assl"></a>ID 要素 (ASSL)
  親要素の一意の識別子 (ID) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
   <ID>...</ID>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (最大 100 文字)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)、[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)、[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、 [CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md)、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)、 [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md)、[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md)、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)、[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)、[ロール](../../../analysis-services/scripting/objects/role-element-assl.md)、[サーバー](../../../analysis-services/scripting/objects/server-element-assl.md)、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 すべての主要なオブジェクト[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]が、 **ID**プロパティとして要素。 値、 **ID**要素には、次の制限。  
  
-   値の先頭または末尾にスペースを含めることはできません。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]値から先頭または末尾のスペースを暗黙的に削除されます、 **ID**要素。  
  
-   値は、制御文字を含めることはできません。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]値から制御文字を暗黙的に削除されます、 **ID**要素。  
  
-   次の値は予約済みなので使用できません。  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 ～ COM9 (COM1、COM2、COM3 など)  
  
    -   CON  
  
    -   LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)  
  
    -   NUL (NUL)  
  
    -   PRN  
  
 次の表に、追加の文字の値の中で使用することはできませんが、 **ID**によっては、親要素の要素。  
  
|親要素|文字|  
|--------------------|----------------|  
|[[サーバー]](../../../analysis-services/scripting/objects/server-element-assl.md)|値は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows コンピューター名の規則に従う必要があります。 (IP アドレスが正しくありません。)|  
|[データ ソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)|:/\\*&#124;?"()[]{}<>|  
|[レベル](../../../analysis-services/scripting/objects/level-element-assl.md)、[要素の属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)|.,;'`:/\\*&#124;?"&%$!+=[]{}<>|  
|他のすべての親要素|.,;'`:/\\*&#124;?"&%$!+=()[]{}<>|  
  
## <a name="see-also"></a>参照  
 [Name 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/name-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
