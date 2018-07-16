---
title: AggregationDesigns 要素 (ASSL) |Microsoft Docs
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
- AggregationDesigns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AggregationDesigns
helpviewer_keywords:
- AggregationDesigns element
ms.assetid: 7291956a-9c53-41fe-af2e-2418e26956c5
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 89140d57aafd7a74b5d1ad8082e8feba075c33bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37279598"
---
# <a name="aggregationdesigns-element-assl"></a>AggregationDesigns 要素 (ASSL)
  データベースの複数のパーティションで共有できる集計デザインのコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup>  
   ...  
   <AggregationDesigns>  
      <AggregationDesign>...</AggregationDesign>  
   </AggregationDesigns>  
   ...  
</MeasureGroup>  
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
|親要素|[メジャー グループ](../objects/group-element-assl.md)|  
|子要素|[AggregationDesign](../objects/aggregationdesign-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationDesignCollection>します。  
  
## <a name="see-also"></a>参照  
 [要素をパーティション分割&#40;ASSL&#41;](../objects/partition-element-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
