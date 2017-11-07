---
title: "Columns 要素 (ASSL) |Microsoft ドキュメント"
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
- Columns Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- COLUMNS
helpviewer_keywords:
- Columns element
ms.assetid: 14011eed-6f10-4120-b256-d599d59bde80
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 85e58f48f9b014e6dcb2f79982ad96b19afdae95
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="columns-element-assl"></a>Columns 要素 (ASSL)
  親要素に関連付けられた列のコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action xsi:type="DrillThroughAction"> <!-- or one of the elements listed below in the Element Relationships table -->  
   <Columns>  
      <Column xsi:type="MeasureBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent: DrillThroughAction -->  
      <!-- or -->  
      <Column xsi:type="EventColumn">...</Column> <!-- parent: Event -->  
      <!-- or -->  
      <Column xsi:type="MiningModelColumn">...</Column> <!-- parent: MiningModel or MiningModelColumn -->  
      <!-- or -->  
      <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent: MiningStructure or TableMiningStructureColumn -->  
   </Columns>  
</DrillThroughAction>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|次の表を参照してください。|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[イベント](../../../analysis-services/scripting/objects/event-element-assl.md)|1-1 : 必須要素で、1 回だけ出現します|  
|他のすべて|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)型の[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)、[イベント](../../../analysis-services/scripting/objects/event-element-assl.md)、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、 [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|--------------------|  
|[DrillThroughAction](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)|[CubeAttributeBinding](../../../analysis-services/scripting/data-type/cubeattributebinding-data-type-assl.md)または[MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)|  
|[イベント](../../../analysis-services/scripting/objects/event-element-assl.md)|[EventColumn](../../../analysis-services/scripting/data-type/eventcolumn-data-type-assl.md)|  
|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|[MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md)|  
|[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、 [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 **DrillThroughAction** 要素の場合、 **Columns** コレクションでは、アクションの実行時に返されるデータが含まれた列が識別されます。  
  
 **TableMiningStructureColumn** 要素の場合、 **Columns** コレクションでは、1 つのレベルの再帰だけが許可されます。 つまり、このコレクションに含まれている **TableMiningStructureColumn** 要素には、 **TableMiningStructureColumn** コレクションの **Columns** 要素を含めることができません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する一部の要素は、<xref:Microsoft.AnalysisServices.TraceColumnCollection>、<xref:Microsoft.AnalysisServices.MiningModelColumnCollection>、および <xref:Microsoft.AnalysisServices.MiningStructureColumnCollection> です。  
  
## <a name="see-also"></a>参照  
 [コレクション & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  

