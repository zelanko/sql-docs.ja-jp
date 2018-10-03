---
title: ProactiveCaching 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ProactiveCaching Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ProactiveCaching
helpviewer_keywords:
- ProactiveCaching element
ms.assetid: 85f9ed44-2ede-406f-b0ca-237ab2f49722
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c873cc6885d4f3a40f0de9e2f34048aff193c72
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183244"
---
# <a name="proactivecaching-element-assl"></a>ProactiveCaching 要素 (ASSL)
  親要素のプロアクティブ キャッシュの設定を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <ProactiveCaching>  
      <OnlineMode>...</OnlineMode>  
      <AggregationStorage>...</AggregationStorage>  
      <Source>...</Source>  
      <SilenceInterval>...</SilenceInterval>  
      <Latency>...</Latency>  
      <SilenceOverrideInterval>...</SilenceOverrideInterval>  
      <ForceRebuildInterval>...</ForceRebuildInterval>  
      <Enabled >...</Enabled>  
   </ProactiveCaching>  
   ...  
</Cube>  
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
|親要素|[キューブ](cube-element-assl.md)、[ディメンション](dimension-element-assl.md)、 [MeasureGroup](group-element-assl.md)、[パーティション](partition-element-assl.md)|  
|子要素|[AggregationStorage](../properties/aggregationstorage-element-assl.md)、[有効になっている](../properties/enabled-element-assl.md)、 [ForceRebuildInterval](../properties/forcerebuildinterval-element-assl.md)、[待機時間](../properties/latency-element-assl.md)、 [OnlineMode](../properties/onlinemode-element-assl.md)、 [SilenceInterval](../properties/silenceinterval-element-assl.md)、 [SilenceOverrideInterval](../properties/silenceoverrideinterval-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ProactiveCaching>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
