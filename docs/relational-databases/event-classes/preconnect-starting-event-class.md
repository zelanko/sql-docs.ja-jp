---
title: "PreConnect:Starting イベント クラス | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6f7c13428afb6680445a0ad4a16c6700b6075dbe
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] PreConnect:Starting イベント クラスは、LOGON トリガーまたはリソース ガバナーの分類関数が実行を開始したことを示します。  
  
## <a name="preconnectstarting-event-class-data-columns"></a>PreConnect:Starting イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|215|27|いいえ|  
|SPID|**int**|このイベントを発生させるサーバー プロセスの ID。|12|はい|  
|EventSubClass|**int**|ユーザー定義の分類子関数の場合は 1。|21|はい|  
|StartTime|**datetime**|ユーザー定義の分類子関数が開始された時刻。|14|はい|  
|ObjectID|**int**|ユーザー定義の分類オブジェクトの ID。|22|はい|  
|ObjectName|**nvarchar (256)**|ユーザー定義の分類子関数の 2 部構成の名前 (dbo.classifier など)。|34|はい|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Completed イベント クラス](../../relational-databases/event-classes/preconnect-completed-event-class.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  
