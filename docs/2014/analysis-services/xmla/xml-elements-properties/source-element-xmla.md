---
title: Source 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Source Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Source
- http://schemas.microsoft.com/analysisservices/2003/engine#Source
- microsoft.xml.analysis.source
helpviewer_keywords:
- Source element
ms.assetid: 4d4665ae-e20f-4baf-ab0f-848660caf500
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 06c69de2879b2298b180b6dd487fe2dc28f09684
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095722"
---
# <a name="source-element-xmla"></a>Source 要素 (XMLA)
  中にマージする基になるパーティションを表す、 [MergePartitions](../xml-elements-commands/mergepartitions-element-xmla.md)コマンド。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Sources>  
   <Source>  
      <DatabaseID>...</DatabaseID>  
      <CubeID>...</CubeID>  
      <MeasureGroupID>...</MeasureGroupID>  
      <PartitionID>...</PartitionID>  
   </Source>  
</Sources>  
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
|親要素|[ソース](sources-element-xmla.md)|  
|子要素|[CubeID](id-element-xmla.md)、 [DatabaseID](databaseid-element-xmla.md)、 [MeasureGroupID](measuregroupid-element-xmla.md)、 [PartitionID](partitionid-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Source` 要素はオブジェクト参照で、親要素 `Target` の `MergePartitions` 要素によって指定されるマージ先パーティションにマージされる単一のパーティションを参照します。  
  
## <a name="example"></a>例  
 次の例は、 `Internet Sales` メジャー グループの 4 つのパーティションすべてを、マージ先パーティション `Internet_Sales_2004` に結合します。 例では、 **Adventure Works**のキューブ、[!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)]サンプル[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース。  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
     <Source>        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>        <CubeID>Adventure Works</CubeID>        <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>        <PartitionID>Internet_Sales_2001</PartitionID>     </Source>     <Source>        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>        <CubeID>Adventure Works</CubeID>      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>      <PartitionID>Internet_Sales_2002</PartitionID>    </Source>    <Source>      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>      <PartitionID>Internet_Sales_2003</PartitionID>    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>参照  
 [Target 要素&#40;XMLA&#41;](../xml-elements-properties/target-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  
