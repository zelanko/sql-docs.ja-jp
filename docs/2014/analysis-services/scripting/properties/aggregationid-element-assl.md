---
title: AggregationID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- AggregationID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationID element
ms.assetid: 6056da1d-b6b4-4074-84db-45be719df49a
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fadf9884d769402e962c64ec00d86338a71328a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277818"
---
# <a name="aggregationid-element-assl"></a>AggregationID 要素 (ASSL)
  集計定義を識別、 [AggregationDesign](../objects/aggregationdesign-element-assl.md)集計インスタンスの作成に使用する要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationInstance>  
   ...  
   <AggregationID>...</AggregationID>  
   ...  
</AggregationInstance>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstance](../objects/aggregationinstance-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素がない場合や、空白文字列に設定されている場合、`AggregationInstance` はユーザー定義の集計を表します。  
  
 親に対応する要素`AggregationID`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.AggregationInstance>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
