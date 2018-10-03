---
title: sys.dm_xe_session_event_actions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xe_session_event_actions_TSQL
- sys.dm_xe_session_event_actions_TSQL
- dm_xe_session_event_actions
- sys.dm_xe_session_event_actions
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_xe_session_event_actions dynamic management view
ms.assetid: 0c22a546-683e-4c84-ab97-1e9e95304b03
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8b430e6f8c5d9d1febefadf615ca24cfff02fa87
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835046"
---
# <a name="sysdmxesessioneventactions-transact-sql"></a>sys.dm_xe_session_event_actions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  イベント セッション アクションに関する情報を返します。 アクションは、イベントが発生したときに実行されます。 この管理ビューでは、アクションの実行回数およびアクションの合計実行時間に関する統計が集計されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|イベント セッションのメモリ アドレス。 NULL 値は許可されません。|  
|action_name|**nvarchar(60)**|アクションの名前。 NULL 値は許可されません。|  
|action_package_guid|**uniqueidentifier**|アクションを含むパッケージの GUID。 NULL 値は許可されません。|  
|event_name|**nvarchar(60)**|アクションがバインドされているイベントの名前。 NULL 値は許可されません。|  
|event_package_guid|**uniqueidentifier**|イベントを含むパッケージの GUID。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_session_event_actions.event_session_address|sys.dm_xe_sessions.address|多対一|  
|sys.dm_xe_session_event_actions.action_name<br /><br /> sys.dm_xe_session_event_actions.action_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_session_events.event_package_guid|多対一|  
|sys.dm_xe_session_event_actions.event_name<br /><br /> sys.dm_xe_session_event_actions.event_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|多対一|  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|「リレーションシップの基数」の表の動的管理ビューの名前と列の名前を修正しました。|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

