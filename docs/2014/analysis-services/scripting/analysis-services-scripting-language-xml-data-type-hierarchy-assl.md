---
title: Analysis Services スクリプト言語の XML データ型階層 (ASSL) |Microsoft Docs
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
- Analysis Services Scripting Language XML Data Type Hierarchy
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
ms.assetid: f143c9f8-225d-495d-ac8e-ac2d2a7b4c07
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 259b843979c16d47c59bc0b3ab74843cc0015592
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243372"
---
# <a name="analysis-services-scripting-language-xml-data-type-hierarchy-assl"></a>Analysis Services スクリプト言語の XML データ型階層 (ASSL)
  次の表は、Analysis Services スクリプト言語 (ASSL) のデータ型の継承階層を示しています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
Action  
DrillThroughAction  
ReportAction  
StandardAction  
AggregationAttribute  
AggregationDesignAttribute  
AggregationDesignDimension  
AggregationDimension  
Assembly  
ClrAssembly  
ComAssembly  
AttributeTranslation  
Binding  
AttributeBinding  
ColumnBinding  
CubeAttributeBinding  
CubeDimensionBinding  
DataSourceViewBinding  
DimensionBinding  
InheritedBinding  
MeasureBinding  
MeasureGroupBinding  
MeasureGroupDimensionBinding  
PartitionBinding  
ProactiveCachingBinding  
ProactiveCachingIncrementalProcessingBinding  
ProactiveCachingObjectNotificationBinding  
ProactiveCachingInheritedBinding  
ProactiveCachingTablesBinding  
ProactiveCachingQueryBinding  
RowBinding  
TabularBinding  
DSVTableBinding  
QueryBinding  
TableBinding  
TimeAttributeBinding  
TimeBinding  
UserDefinedGroupBinding  
ClrAssemblyFile  
CubeAttribute  
CubeBinding (out-of-line)  
CubeDimension  
CubeDimensionPermission  
CubeHierarchy  
DataBlock  
DataItem  
DataMiningMeasureGroupDimension  
DegenerateMeasureGroupDimension  
DimensionAttribute  
EventColumn  
ManyToManyMeasureGroupDimension  
MeasureGroupAttribute  
MeasureGroupBinding (out-of-line)  
MeasureGroupDimension  
MeasureGroupHierarchy  
MiningModelColumn  
MiningModelingFlag  
MiningStructureColumn  
OlapDataSource  
Permission  
PerspectiveAction  
PerspectiveAttribute  
PerspectiveCalculation  
PerspectiveDimension  
PerspectiveHierarchy  
PerspectiveKpi  
PerspectiveMeasure  
PerspectiveMeasureGroup  
PushedDataSource  
ReferenceMeasureGroupDimension  
RegularMeasureGroupDimension  
RelationalDataSource  
ScalarMiningStructureColumn  
TableMiningStructureColumn  
  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](data-type/analysis-services-scripting-language-xml-data-types-assl.md)   
 [Analysis Services スクリプト言語の XML 要素階層&#40;ASSL&#41;](analysis-services-scripting-language-xml-element-hierarchy-assl.md)   
 [Analysis Services スクリプト言語&#40;ASSL&#41;リファレンス](analysis-services-scripting-language-assl-for-xmla.md)  
  
  
