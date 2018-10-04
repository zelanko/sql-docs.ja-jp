---
title: TableNotifications 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- TableNotifications Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- TableNotifications element
ms.assetid: 4cecdfea-0d4d-4bd6-bbb3-4d0d2284c665
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d4c48ef76db4a1dd2a96008c108d050ff832fd52
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188832"
---
# <a name="tablenotifications-element-assl"></a>TableNotifications 要素 (ASSL)
  コレクションを格納[TableNotification](../objects/tablenotification-element-assl.md)要素の情報を提供する、 [ProactiveCaching](../objects/proactivecaching-element-assl.md)テーブルや変更されたデータ ソース ビューの要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <TableNotifications>  
      <TableNotification>...</TableNotification>  
...</TableNotifications>  
</ProactiveCachingTablesBinding>  
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
|親要素|[ProactiveCachingTablesBinding](../data-type/binding-data-type-assl.md)|  
|子要素|[TableNotification](../objects/tablenotification-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.TableNotificationCollection>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingBinding データ型&#40;ASSL&#41;](../data-type/proactivecachingbinding-data-type-assl.md)   
 [ProactiveCachingObjectNotificationBinding データ型&#40;ASSL&#41;](../data-type/proactivecachingobjectnotificationbinding-data-type-assl.md)   
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
