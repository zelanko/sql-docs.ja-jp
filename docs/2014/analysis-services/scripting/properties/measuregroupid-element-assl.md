---
title: MeasureGroupID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroupID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupID
helpviewer_keywords:
- MeasureGroupID element
ms.assetid: 3b075f86-dbbc-4285-8d2d-61fa722181c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b4eb43414e0fd7da783f4a1ac588c4851e3c9bd9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083634"
---
# <a name="measuregroupid-element-assl"></a>MeasureGroupID 要素 (ASSL)
  関連付けます、 [MeasureGroup](../objects/group-element-assl.md)親要素、バインド、またはアウトオブ ライン バインドします。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ManyToManyMeasureGroupDimension> <!-- or MeasureGroupAttributeBinding, MeasureGroupBinding, PerspectiveMeasureGroup -->  
   ...  
   <MeasureGroupID>...</MeasureGroupID>  
   ...  
</ManyToManyMeasureGroupDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality||  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md)、 [MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)、 [MeasureGroupBinding](../data-type/binding-data-type-assl.md)、 [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
  
|子要素の先祖または親|Cardinality|  
|------------------------------------------|-----------------|  
|[ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
|[MeasureGroupAttributeBinding](../data-type/measuregroupattributebinding-data-type-out-of-line-assl.md)、 [MeasureGroupBinding](../data-type/binding-data-type-assl.md)と[PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`MeasureGroupID`分析管理オブジェクト (AMO) オブジェクト モデルは、 <xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>、 <xref:Microsoft.AnalysisServices.MeasureGroupBinding>、および<xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
