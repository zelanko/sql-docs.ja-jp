---
title: server_event_session_actions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.server_event_session_actions
- server_event_session_actions_TSQL
- server_event_session_actions
- sys.server_event_session_actions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_actions catalog view
- xe
ms.assetid: 1d8c604e-4361-4846-8661-14cfd1c44f63
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 50766acbfa3f626061f71cf312d904dc350bc61b
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918445"
---
# <a name="sysserver_event_session_actions-transact-sql"></a>sys.server_event_session_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  イベント セッションの各イベントのアクションごとに 1 行のデータを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベントセッションの ID。 NULL 値は許可されません。|  
|event_id|**int**|イベントの ID。 この ID は、イベントセッションオブジェクト内で一意です。 NULL 値は許可されません。|  
|name|**sysname**|アクションの名前。 NULL 値が許可されます。|  
|package|**sysname**|イベントを含むイベント パッケージの名前。 NULL 値が許可されます。|  
|name|**sysname**|イベントが格納されているモジュールの名前。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>注釈  
 このビューには、次のリレーションシップ基数があります。  
  
| ソース | ターゲット | リレーションシップ |
| ---- | -- | ------------ |
|sys.server_event_session_actions.event_session_id|sys.sys.server_event_sessions.event_session_id|多対一|  
|sys.server_event_session_actions.event_id<br /><br /> sys.server_event_session_actions.event_session_id|sys.server_event_session_events.event_session_id<br /><br /> sys.server_event_session_events.event_id|多対一|  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [拡張イベントのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
