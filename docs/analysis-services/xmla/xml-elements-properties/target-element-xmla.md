---
title: "ターゲット要素 (XMLA) |Microsoft ドキュメント"
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
- Target Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.target
- http://schemas.microsoft.com/analysisservices/2003/engine#Target
- urn:schemas-microsoft-com:xml-analysis#Target
helpviewer_keywords:
- Target element
ms.assetid: 9a69a777-5f34-4e94-b470-6bab2a98df8b
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6b9a30b4b16ee56479e594cf71c79e963e55ed77
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="target-element-xmla"></a>Target 要素 (XMLA)
  中にマージする先のパーティションを表す、 [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MergePartitions>  
   <Target>  
      <DatabaseID>...</DatabaseID>  
      <CubeID>...</CubeID>  
      <MeasureGroupID>...</MeasureGroupID>  
      <PartitionID>...</PartitionID>  
   </Target>  
</MergePartitions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)|  
|子要素|[CubeID](../../../analysis-services/xmla/xml-elements-properties/cubeid-element-xmla.md)、 [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md)、 [MeasureGroupID](../../../analysis-services/xmla/xml-elements-properties/measuregroupid-element-xmla.md)、 [PartitionID](../../../analysis-services/xmla/xml-elements-properties/partitionid-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **ターゲット**要素は、これには、ソース パーティションの内容がで指定された 1 つのパーティションへのオブジェクト参照、[ソース](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md)の親要素**MergePartitions**要素をマージします。  
  
## <a name="example"></a>例  
 次の例は、Internet Sales メジャー グループの 4 つのパーティションすべてを、マージ先パーティション `Internet_Sales_2004` に結合します。 この例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] のサンプル データベース [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] の、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] キューブを参照しています。  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
     <Source>  
        <DatabaseID>database</DatabaseID>  
        <CubeID>Adventure Works DW</CubeID>  
        <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
        <PartitionID>Internet_Sales_2001</PartitionID>  
     </Source>  
     <Source>  
      <DatabaseID>database</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>database</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>    <DatabaseID>database</DatabaseID>    <CubeID>Adventure Works DW</CubeID>    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>    <PartitionID>Internet_Sales_2004</PartitionID>  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>参照  
 [Source 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [プロパティ & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

