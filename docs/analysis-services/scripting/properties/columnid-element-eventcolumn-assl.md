---
title: "ColumnID 要素 (EventColumn) (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ColumnID Element (EventColumn)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ColumnID
helpviewer_keywords: ColumnID element
ms.assetid: c4f4fbad-9d70-4de2-8cf7-caee80a4a1e4
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 39c497caeffb5439169c20199cdde01c27331a08
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="columnid-element-eventcolumn-assl"></a>ColumnID 要素 (EventColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]イベントの一部としてキャプチャされる情報の列の識別子 (ID) を含む、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素。  
  
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
 [Columns 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/columns-element-assl.md)   
 [Event 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/event-element-assl.md)   
 [Events 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/events-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
