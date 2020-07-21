---
title: server_event_session_events (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_session_events
- server_event_session_events_TSQL
- sys.server_event_session_events
- sys.server_event_session_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_events catalog view
- xe
ms.assetid: 75986e91-1fc7-4f14-98ac-4e90154a74db
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bcd8f24e3d594e7013900d31db2d459c9236d9d9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85896495"
---
# <a name="sysserver_event_session_events-transact-sql"></a>sys.server_event_session_events (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  イベント セッションのイベントごとに行を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベントセッションの ID。 NULL 値は許可されません。|  
|event_id|**int**|イベントの ID。 この ID は、イベントセッションオブジェクト内で一意です。 NULL 値は許可されません。|  
|name|**sysname**|イベントの名前です。 NULL 値は許可されません。|  
|package|**sysname**|イベントを含むイベント パッケージの名前。 NULL 値は許可されません。|  
|name|**sysname**|イベントが格納されているモジュールの名前。 NULL 値は許可されません。|  
|predicate|**nvarchar (3000)**|イベントに適用される述語式。 NULL 値が許可されます。|  
|predicate_xml|**nvarchar (3000)**|イベントに適用される XML 述語式。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>Remarks  
 このビューには、次のリレーションシップ基数があります。  
  
||||  
|-|-|-|  
|From|終了|リレーションシップ|  
|sys.server_event_session_events.event_session_id|server_event_sessions。 event_session_id|多対一|  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [拡張イベントのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
