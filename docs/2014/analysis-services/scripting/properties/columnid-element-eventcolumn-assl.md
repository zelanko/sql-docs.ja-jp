---
title: ColumnID 要素 (EventColumn) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ColumnID Element (EventColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ColumnID
helpviewer_keywords:
- ColumnID element
ms.assetid: c4f4fbad-9d70-4de2-8cf7-caee80a4a1e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4eeb9954f3318a9286865454b6eb61a15f4d4236
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216392"
---
# <a name="columnid-element-eventcolumn-assl"></a>ColumnID 要素 (EventColumn) (ASSL)
  イベントの一部としてキャプチャされる情報の列の識別子 (ID) を含む、[トレース](../objects/trace-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[EventColumn](../data-type/eventcolumn-data-type-assl.md)|  
|子要素|[なし] :|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`ColumnID`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.TraceColumn>します。  
  
## <a name="see-also"></a>参照  
 [Columns 要素&#40;ASSL&#41;](../collections/columns-element-assl.md)   
 [Event 要素&#40;ASSL&#41;](../objects/event-element-assl.md)   
 [Events 要素&#40;ASSL&#41;](../collections/events-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
