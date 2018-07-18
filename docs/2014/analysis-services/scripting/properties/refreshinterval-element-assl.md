---
title: RefreshInterval 要素 (ASSL) |Microsoft Docs
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
- RefreshInterval Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RefreshInterval
helpviewer_keywords:
- RefreshInterval element
ms.assetid: 2761d26a-5fb0-452c-9a89-12f8dc658c33
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f3fecbe3eef6eb68af256dfcc0a94ddef1ba3aee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37315052"
---
# <a name="refreshinterval-element-assl"></a>RefreshInterval 要素 (ASSL)
  親要素に関連付けられたバインド データの更新間隔を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionBinding> <!-- or MeasureGroupBinding, ProactiveCachingIncrementalProcessingBinding, ProactiveCachingQueryBinding -->  
   ...  
   <RefreshInterval>...</RefreshInterval>  
   ...  
</DimensionBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|XML Duration|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
|既定値|[ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md)または[ProactiveCachingQueryBinding](../data-type/querybinding-data-type-assl.md) PT 1 を =|  
|既定値|他のすべて PT1m を =|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionBinding](../data-type/dimensionbinding-data-type-assl.md)、 [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)、 [ProactiveCachingIncrementalProcessingBinding](../data-type/binding-data-type-assl.md)、 [ProactiveCachingQueryBinding](../data-type/querybinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで `RefreshInterval` の親に対応する要素は、<xref:Microsoft.AnalysisServices.DimensionBinding>、<xref:Microsoft.AnalysisServices.MeasureGroupBinding>、<xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding>、および <xref:Microsoft.AnalysisServices.ProactiveCachingQueryBinding> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
