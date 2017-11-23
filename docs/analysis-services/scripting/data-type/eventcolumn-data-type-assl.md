---
title: "EventColumn データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: EventColumn Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: EventColumn
helpviewer_keywords: EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 71c0a41a5f08eea077d9fa1e92e9e879add972a2
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="eventcolumn-data-type-assl"></a>EventColumn データ型 (ASSL)
  キャプチャされる情報の列を表すプリミティブ データ型を定義、[イベント](../../../analysis-services/scripting/objects/event-element-assl.md)要素の一部として、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<EventColumn>  
   <ColumnID>...</ColumnID>  
</EventColumn>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ColumnID](../../../analysis-services/scripting/properties/columnid-element-eventcolumn-assl.md)|  
|派生要素|[列](../../../analysis-services/scripting/objects/column-element-assl.md)([列](../../../analysis-services/scripting/collections/columns-element-assl.md)のコレクション[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>参照  
 [Events 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/events-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
