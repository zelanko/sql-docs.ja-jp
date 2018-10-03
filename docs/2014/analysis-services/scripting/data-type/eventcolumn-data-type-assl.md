---
title: EventColumn データ型 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EventColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EventColumn
helpviewer_keywords:
- EventColumn data type
ms.assetid: c0009f1d-d136-4155-9a1b-7baacda4b552
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 175504777bdba88ef434d275f136becc8241ada0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48118042"
---
# <a name="eventcolumn-data-type-assl"></a>EventColumn データ型 (ASSL)
  キャプチャされる情報の列を表すプリミティブ データ型を定義、[イベント](../objects/event-element-assl.md)要素の一部として、[トレース](../objects/trace-element-assl.md)要素。  
  
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
|子要素|[ColumnID](../properties/columnid-element-eventcolumn-assl.md)|  
|派生要素|[列](../objects/column-element-assl.md)([列](../collections/columns-element-assl.md)のコレクション[トレース](../objects/trace-element-assl.md))|  
  
## <a name="see-also"></a>参照  
 [Events 要素&#40;ASSL&#41;](../collections/events-element-assl.md)   
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
