---
title: ColumnID 要素 (EventColumn) (ASSL) |Microsoft ドキュメント
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
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 71e51ec736b10a6d72621efb2a9b094882ed8057
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177610"
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
  
  