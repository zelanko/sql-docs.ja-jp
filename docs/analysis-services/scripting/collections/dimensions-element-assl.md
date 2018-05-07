---
title: Dimensions 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 83470f746ff23338cf22040c0e6afa36353b7699
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dimensions-element-assl"></a>Dimensions 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|親要素|[集計](../../../analysis-services/scripting/objects/aggregation-element-assl.md)、 [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md)、 [AggregationInstance](../../../analysis-services/scripting/objects/aggregationinstance-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|子要素|[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DimensionCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
