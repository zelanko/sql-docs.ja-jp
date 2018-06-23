---
title: MeasureGroupID 要素 (ASSL) |Microsoft ドキュメント
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
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7a6ab3a46de67deb375f74b30a0e802680a9d7ab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176975"
---
# <a name="measuregroupid-element-assl"></a>MeasureGroupID 要素 (ASSL)
  関連付けます、 [MeasureGroup](../objects/group-element-assl.md)親要素、バインド、または不一致のバインド。  
  
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
 親に対応する要素`MeasureGroupID`分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.ManyToManyMeasureGroupDimension>、 <xref:Microsoft.AnalysisServices.MeasureGroupBinding>、および<xref:Microsoft.AnalysisServices.PerspectiveMeasureGroup>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  