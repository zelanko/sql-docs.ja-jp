---
title: Hierarchies 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dd31f29dc3dac32fbb3acf9e9cd1a206ac092533
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="hierarchies-element-assl"></a>Hierarchies 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素に関連付けられた [Hierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) 要素のコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension> <!-- or CubeDimension, PerspectiveDimension -->  
   ...  
   <Hierarchies>  
            <Hierarchy>...</Hierarchy> <!-- parent: Dimension -->  
      <!-- or -->  
      <Hierarchy xsi:type="CubeHierarchy">...</Hierarchy> <!-- parent: CubeDimension -->  
     <!-- or -->  
      <Hierarchy xsi:type="PerspectiveHierarchy">...</Hierarchy> <!-- parent: PerspectiveDimension -->  
   <Hierarchies>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)、 [Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|  
|子要素|次の表を参照してください。|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)型の[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)|  
|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)|  
|[PerspectiveDimension](../../../analysis-services/scripting/data-type/perspectivedimension-data-type-assl.md)|[PerspectiveHierarchy](../../../analysis-services/scripting/objects/hierarchy-element-assl.md) 型の [Hierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.HierarchyCollection>、<xref:Microsoft.AnalysisServices.CubeHierarchyCollection>、および <xref:Microsoft.AnalysisServices.PerspectiveHierarchyCollection> です。  
  
## <a name="see-also"></a>参照  
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
