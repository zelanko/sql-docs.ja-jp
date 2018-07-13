---
title: AggregationInstances 要素 (ASSL) |Microsoft Docs
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
- AggregationInstances Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstances element
ms.assetid: e8321aa8-361b-4d8a-bd89-a596eeb814b1
caps.latest.revision: 10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4580f50935a9819bba3a10531376389033c3ae04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237592"
---
# <a name="aggregationinstances-element-assl"></a>AggregationInstances 要素 (ASSL)
  定義されている集計インスタンスのコレクションを格納する[パーティション](../objects/partition-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Partition>  
   ...  
   <AggregationInstances>  
      <AggregationInstance>...</AggregationInstance>  
   </AggregationInstances>  
   ...  
</Partition>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし (コレクション型)|  
|既定値|なし (コレクション型)|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パーティション](../objects/partition-element-assl.md)|  
|子要素|[AggregationInstance](../objects/aggregationinstance-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationInstanceCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
