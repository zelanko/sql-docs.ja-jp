---
title: QueryNotification 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- QueryNotification Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- QueryNotification element
ms.assetid: 0ee06730-81ff-4913-96e6-f39b6f181650
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4eddd5a96c5c5ab541ba9349d7b664b110589a74
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177737"
---
# <a name="querynotification-element-assl"></a>QueryNotification 要素 (ASSL)
  データ ソースが変更されているかどうかを調べるために実行するクエリについての [ProactiveCaching](proactivecaching-element-assl.md) 要素の情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<QueryNotifications>  
   <QueryNotification>  
      <Query>...</Query>  
...</QueryNotification>  
</QueryNotifications>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[QueryNotifications](../collections/querynotifications-element-assl.md)|  
|子要素|[クエリ](../properties/query-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.QueryNotification>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingQueryBinding データ型&#40;ASSL&#41;](../data-type/binding-data-type-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
