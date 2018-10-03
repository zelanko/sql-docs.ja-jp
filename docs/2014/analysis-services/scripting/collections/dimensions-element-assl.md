---
title: Dimensions 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Dimensions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Dimensions
helpviewer_keywords:
- Dimensions element
ms.assetid: 104e3154-92e9-4c6b-9cf3-e3f3fc712b28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f7c25008bd3f47a8efc9ebb0b57d2507667f9116
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163282"
---
# <a name="dimensions-element-assl"></a>Dimensions 要素 (ASSL)
  親要素に関連付けられたディメンションのコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database> <!-- or Aggregation, AggregationDesign, AggregationInstance, Cube, MeasureGroup, Perspective -->  
   ...  
   <Dimensions>  
      <Dimension>...</Dimension>  
   </Dimensions>  
   ...  
</Database>  
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
|親要素|[集計](../objects/aggregation-element-assl.md)、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)、 [AggregationInstance](../objects/aggregationinstance-element-assl.md)、[キューブ](../objects/cube-element-assl.md)、[データベース](../objects/database-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、[パースペクティブ](../objects/perspective-element-assl.md)|  
|子要素|[Dimension](../objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
