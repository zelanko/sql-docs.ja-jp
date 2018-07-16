---
title: Hierarchies 要素 (ASSL) |Microsoft Docs
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
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe89bade8e70b6812dddca1a6e20d274acea3526
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308462"
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
  
  
