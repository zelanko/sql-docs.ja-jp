---
title: DataAggregation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataAggregation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- DataAggregation element
ms.assetid: baf6d2c9-54f6-4a6d-95f7-e1e758be458d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 01a86977cc6ebf85d004bf235b6d47a354e112a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134822"
---
# <a name="dataaggregation-element-assl"></a>DataAggregation 要素 (ASSL)
  インスタンスが永続化されたデータまたはキャッシュされたデータを集計できるかどうかを決定する、 [MeasureGroup](../objects/group-element-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup>  
   ...  
   <DataAggregation>...</DataAggregation>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*Dataandcacheaggregatable です。*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../objects/group-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*なし*|このメジャー グループに対して集計は実行されません。|  
|*DataAggregatable*|このメジャー グループに対して持続データが集計されます。|  
|*CacheAggregatable*|このメジャー グループに対してキャッシュされたデータが集計されます。|  
|*Dataandcacheaggregatable です。*|このメジャー グループに対して、持続データとキャッシュされたデータの両方が集計されます。|  
  
 親に対応する要素`DataAggregation`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MeasureGroup>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
