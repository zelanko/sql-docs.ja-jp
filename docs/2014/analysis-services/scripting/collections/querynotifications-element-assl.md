---
title: QueryNotifications 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- QueryNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- QueryNotifications element
ms.assetid: 0e7e951f-c8b9-4492-bb01-e4b5d16edde6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7da194e4d4aaa51d5b54553a3eacf162d4040eaa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124192"
---
# <a name="querynotifications-element-assl"></a>QueryNotifications 要素 (ASSL)
  コレクションを格納[QueryNotification](../objects/querynotification-element-assl.md)要素に情報を提供する、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)データ ソースが変更されているかどうかを判断するために実行するクエリについての要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingQueryBinding>  
   ...  
   <QueryNotifications>  
      <QueryNotification>...</QueryNotification>  
...</QueryNotifications>  
   ...  
</ProactiveCachingQueryBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ProactiveCachingQueryBinding](../data-type/binding-data-type-assl.md)|  
|子要素|[QueryNotification](../objects/querynotification-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.QueryNotificationCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
