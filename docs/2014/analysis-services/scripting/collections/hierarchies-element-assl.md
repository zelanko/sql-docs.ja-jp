---
title: Hierarchies 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Hierarchies Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Hierarchies
helpviewer_keywords:
- Hierarchies element
ms.assetid: dc844eea-869c-4217-b9be-e543a76f5e92
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b9e8fa5c67d3b4b9b00be7c7517307f911327db
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129014"
---
# <a name="hierarchies-element-assl"></a>Hierarchies 要素 (ASSL)
  コレクションを格納[階層](../objects/hierarchy-element-assl.md)親要素に関連付けられた要素。  
  
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
|親要素|[CubeDimension](../data-type/dimension-data-type-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|  
  
|先祖または親|子要素|  
|------------------------|-------------------|  
|[CubeDimension](../data-type/dimension-data-type-assl.md)|[階層](../objects/hierarchy-element-assl.md)型の[CubeHierarchy](../data-type/hierarchy-data-type-assl.md)|  
|[Dimension](../objects/dimension-element-assl.md)|[Hierarchy](../objects/hierarchy-element-assl.md)|  
|[PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)|[階層](../objects/hierarchy-element-assl.md)型の[PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.HierarchyCollection>、<xref:Microsoft.AnalysisServices.CubeHierarchyCollection>、および <xref:Microsoft.AnalysisServices.PerspectiveHierarchyCollection> です。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
