---
title: ColumnID 要素 (EventColumn) (ASSL) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dcbc88925b788c90f965e0b3b526979047f96b38
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="columnid-element-eventcolumn-assl"></a>ColumnID 要素 (EventColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  イベントの一部としてキャプチャされる情報の列の識別子 (ID) を含む、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[EventColumn](../../../analysis-services/scripting/data-type/eventcolumn-data-type-assl.md)|  
|子要素|[なし] :|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**ColumnID**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.TraceColumn>します。  
  
## <a name="see-also"></a>参照  
 [Columns 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/columns-element-assl.md)   
 [Event 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/event-element-assl.md)   
 [Events 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/events-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
