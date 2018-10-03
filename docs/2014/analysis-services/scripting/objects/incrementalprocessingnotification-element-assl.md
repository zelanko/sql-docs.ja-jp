---
title: IncrementalProcessingNotification 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IncrementalProcessingNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- IncrementalProcessingNotification element
ms.assetid: bfc9b0a4-4043-4aaf-82d9-67e7f1d1eb81
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 639d58928b27e965a707602c0ea124c9078e5b47
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120742"
---
# <a name="incrementalprocessingnotification-element-assl"></a>IncrementalProcessingNotification 要素 (ASSL)
  情報が含まれています、 [ProactiveCaching](proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリについての要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[IncrementalProcessingNotification](../data-type/incrementalprocessingnotification-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[IncrementalProcessingNotifications](../collections/incrementalprocessingnotifications-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingQueryBinding データ型&#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [ProactiveCaching 要素&#40;ASSL&#41;](proactivecaching-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
