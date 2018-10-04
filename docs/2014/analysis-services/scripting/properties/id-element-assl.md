---
title: ID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ID
helpviewer_keywords:
- ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71de55c773ce75ec75b38b774ad0a5e8ec35ed9b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170262"
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
|親要素|[アクション](../objects/action-element-assl.md)、[集計](../objects/aggregation-element-assl.md)、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)、[アセンブリ](../objects/assembly-element-assl.md)、[キューブ](../objects/cube-element-assl.md)、 [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)、 [CubeDimension](../data-type/dimension-data-type-assl.md)、[データベース](../objects/database-element-assl.md)、 [DataSource](../objects/datasource-element-assl.md)、 [DataSourceView](../objects/datasourceview-element-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、[階層](../objects/hierarchy-element-assl.md)、 [Kpi](../objects/kpi-element-assl.md)、[レベル](../objects/level-element-assl.md)、 [MdxScript](../objects/mdxscript-element-assl.md)、[メジャー](../objects/measure-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、 [MeasureGroupBinding](../data-type/binding-data-type-assl.md)、 [MiningModel](../objects/miningmodel-element-assl.md)、 [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)、 [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)、[パーティション](../objects/partition-element-assl.md)、[権限](../data-type/permission-data-type-assl.md)、[パースペクティブ](../objects/perspective-element-assl.md)、[ロール](../objects/role-element-assl.md)、 [Server](../objects/server-element-assl.md)、[トレース](../objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 すべての主要なオブジェクトで[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]が、`ID`プロパティとして要素。 値、`ID`要素には、次の制限。  
  
-   値の先頭または末尾にスペースを含めることはできません。 そのようなスペースは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって暗黙的に `ID` 要素の値から削除されます。  
  
-   値は、制御文字を含めることはできません。 制御文字は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって暗黙的に `ID` 要素の値から削除されます。  
  
-   次の値は予約済みなので使用できません。  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 ～ COM9 (COM1、COM2、COM3 など)  
  
    -   CON  
  
    -   LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)  
  
    -   NUL (NUL)  
  
    -   PRN  
  
 次の表に、追加の文字の値内で使用することはできません、`ID`親要素に応じての要素。  
  
|親要素|文字|  
|--------------------|----------------|  
|[[サーバー]](../objects/server-element-assl.md)|値は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows コンピューター名の規則に従う必要があります。 (IP アドレスが無効です。)|  
|[DataSource](../objects/datasource-element-assl.md)|:/\\*&#124;?"(){}<>|  
|[レベル](../objects/level-element-assl.md)、[要素の属性](../objects/attribute-element-assl.md)|.,;'`:/\\*&#124;?"& % $! + ={}<>|  
|他のすべての親要素|.,;'`:/\\*&#124;?"& % $! + = (){}<>|  
  
## <a name="see-also"></a>参照  
 [要素名を指定&#40;ASSL&#41;](name-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
