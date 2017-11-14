---
title: "HierarchyID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- HierarchyID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- HierarchyID
helpviewer_keywords:
- HierarchyID element
ms.assetid: 6effe47d-e598-41f8-993a-b2bce49fd7dd
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e4aa9e9298a84d7befbdeea5011a0e712c8550b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchyid-element-assl"></a>HierarchyID 要素 (ASSL)
  識別子 (ID) が含まれています、 [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)、 [MeasureGroupHierarchy](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md)、または[PerspectiveHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)要素。  
  
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
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)、 [MeasureGroupHierarchy](../../../analysis-services/scripting/data-type/measuregrouphierarchy-data-type-assl.md)、 [PerspectiveHierarchy](../../../analysis-services/scripting/data-type/perspectivehierarchy-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**HierarchyID**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CubeHierarchy>と<xref:Microsoft.AnalysisServices.PerspectiveHierarchy>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

