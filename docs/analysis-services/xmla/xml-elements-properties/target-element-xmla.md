---
title: Target 要素 (XMLA) |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 53cf0589cff69dab21c07979ba89e84e35f30d11
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38064139"
---
# <a name="target-element-xmla"></a>Target 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  中にマージする対象のパーティションを表す、 [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)コマンド。  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)|  
|子要素|[CubeID](../../../analysis-services/xmla/xml-elements-properties/cubeid-element-xmla.md)、 [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md)、 [MeasureGroupID](../../../analysis-services/xmla/xml-elements-properties/measuregroupid-element-xmla.md)、 [PartitionID](../../../analysis-services/xmla/xml-elements-properties/partitionid-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **ターゲット**要素は、先になるパーティションの内容がで指定された 1 つのパーティションへのオブジェクト参照、[ソース](../../../analysis-services/xmla/xml-elements-properties/sources-element-xmla.md)要素の親の**MergePartitions**要素をマージします。  
  
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
 [Source 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)   
 [プロパティ&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
