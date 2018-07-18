---
title: EstimatedRows 要素 (ASSL) |Microsoft Docs
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
- EstimatedRows Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EstimatedRows
helpviewer_keywords:
- EstimatedRows element
ms.assetid: 08a66481-6479-4a93-aa7e-15e8b1f854f2
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e35ff79a747ad2106ac976ae2a4bdfeb408f6359
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37213872"
---
# <a name="estimatedrows-element-assl"></a>EstimatedRows 要素 (ASSL)
  親要素によって表される行の推定数を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationDesign> <!-- or Cube, MeasureGroup, MeasureGroupBinding, Partition -->  
   ...  
   <EstimatedRows>...</EstimatedRows>  
   ...  
</AggregationDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Long|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationDesign](../objects/aggregationdesign-element-assl.md)、[キューブ](../objects/cube-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、 [MeasureGroupBinding](../data-type/binding-data-type-assl.md)、[パーティション](../objects/partition-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで `EstimatedRows` の親に対応する要素は、<xref:Microsoft.AnalysisServices.AggregationDesign>、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.MeasureGroup>、<xref:Microsoft.AnalysisServices.MeasureGroupBinding>、および <xref:Microsoft.AnalysisServices.Partition> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
