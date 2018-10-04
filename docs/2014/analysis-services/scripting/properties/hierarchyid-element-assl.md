---
title: HierarchyID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- HierarchyID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID element
ms.assetid: 6effe47d-e598-41f8-993a-b2bce49fd7dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5500eabc8465924d67accbf11fc685f9b57569b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48169102"
---
# <a name="hierarchyid-element-assl"></a>HierarchyID 要素 (ASSL)
  識別子 (ID) を含む、 [CubeHierarchy](../data-type/hierarchy-data-type-assl.md)、 [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md)、または[PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeHierarchy> <!-- or MeasureGroupHierarchy, PerspectiveHierarchy -->  
      ...  
   <HierarchyID>...</HierarchyID>  
      ...  
</CubeHierarchy>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeHierarchy](../data-type/hierarchy-data-type-assl.md)、 [MeasureGroupHierarchy](../data-type/measuregrouphierarchy-data-type-assl.md)、 [PerspectiveHierarchy](../data-type/perspectivehierarchy-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`HierarchyID`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CubeHierarchy>と<xref:Microsoft.AnalysisServices.PerspectiveHierarchy>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
