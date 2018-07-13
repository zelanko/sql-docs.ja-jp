---
title: 要素 (ASSL) を測定 |Microsoft Docs
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
- Measures Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Measures
helpviewer_keywords:
- Measures element
ms.assetid: d2107112-f620-4fd7-a05f-bb2606b4be18
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f781eb542d290635bb01b8582c8e51a7cb2b05f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37272298"
---
# <a name="measures-element-assl"></a>Measures 要素 (ASSL)
  コレクションを格納[メジャー](../objects/measure-element-assl.md)親要素に関連付けられた要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup> <!-- or AggregationInstance, MeasureGroupBinding (out-of-line), PerspectiveMeasureGroup -->  
   ...  
   <Measures>  
      <Measure>...</Measure>  
   </Measures>  
   ...  
</MeasureGroup>  
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
|親要素|[AggregationInstance](../objects/aggregationinstance-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、 [MeasureGroupBinding (不一致)](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)、 [PerspectiveMeasureGroup](../data-type/perspectivemeasuregroup-data-type-assl.md)|  
|子要素|[メジャー](../objects/measure-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は、<xref:Microsoft.AnalysisServices.MeasureCollection> と <xref:Microsoft.AnalysisServices.PerspectiveMeasureCollection> です。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
