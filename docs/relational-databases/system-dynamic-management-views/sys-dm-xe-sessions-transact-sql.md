---
title: "sys.dm_xe_sessions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_xe_sessions_TSQL
- dm_xe_sessions
- sys.dm_xe_sessions_TSQL
- sys.dm_xe_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_sessions dynamic management view
- extended events [SQL Server], views
ms.assetid: defd6efb-9507-4247-a91f-dc6ff5841e17
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c871158b5085d14eda8974530e392b5ed24baf5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxesessions-transact-sql"></a>sys.dm_xe_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アクティブな拡張イベント セッションに関する情報を返します。 このセッションは、イベント、アクション、およびターゲットのコレクションです。  
    
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|address|**varbinary(8)**|セッションのメモリ アドレス。 アドレスは、ローカル システム全体で一意です。 NULL 値は許可されません。|  
|name|**nvarchar (256)**|セッションの名前。 名前は、ローカル システム全体で一意です。 NULL 値は許可されません。|  
|pending_buffers|**int**|いっぱいになって処理が保留されているバッファーの数。 NULL 値は許可されません。|  
|total_regular_buffers|**int**|セッションに関連付けられている標準バッファーの総数。 NULL 値は許可されません。<br /><br /> 注: 標準バッファーはほとんどの場合に使用されます。 標準バッファーには、多数のイベントを保持できるだけの十分なサイズがあります。 通常は、各セッションに 3 つ以上のバッファーがあります。 標準バッファーの数は、MEMORY_PARTITION_MODE オプションによって設定されるメモリのパーティション分割に基づいて、サーバーで自動的に決定されます。 標準バッファーのサイズは、MAX_MEMORY オプションの値 (既定では 4 MB) をバッファーの数で割った値になります。 MEMORY_PARTITION_MODE オプションと MAX_MEMORY オプションの詳細については、次を参照してください。 [CREATE EVENT SESSION &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-event-session-transact-sql.md)。|  
|regular_buffer_size|**bigint**|標準バッファーのサイズ (バイト単位)。 NULL 値は許可されません。|  
|total_large_buffers|**int**|ラージ バッファーの総数。 NULL 値は許可されません。<br /><br /> 注: ラージ バッファーは、イベントが標準バッファーより大きい場合に使用されます。 この目的のために明示的に確保されています。 ラージ バッファーは、イベント セッションが開始されるときに割り当てられ、サイズは MAX_EVENT_SIZE オプションによって決まります。 MAX_EVENT_SIZE オプションの詳細については、次を参照してください。 [CREATE EVENT SESSION &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/create-event-session-transact-sql.md)。|  
|large_buffer_size|**bigint**|ラージ バッファーのサイズ (バイト単位)。 NULL 値は許可されません。|  
|total_buffer_size|**bigint**|セッションのイベントを格納するためのメモリ バッファーの合計サイズ (バイト単位)。 NULL 値は許可されません。|  
|buffer_policy_flags|**int**|すべてのバッファーがいっぱいになっているときに新しいイベントが発生した場合のセッション イベント バッファーの動作を示すビットマップ。 NULL 値は許可されません。|  
|buffer_policy_desc|**nvarchar (256)**|すべてのバッファーがいっぱいになっているときに新しいイベントが発生した場合のセッション イベント バッファーの動作を示す説明。  NULL 値は許可されません。 buffer_policy_desc は、次のいずれかになります。<br /><br /> Drop event<br /><br /> Do not drop events<br /><br /> Drop full buffer<br /><br /> Allocate new buffer|  
|flags|**int**|セッションに設定されているフラグを示すビットマップ。 NULL 値は許可されません。|  
|flag_desc|**nvarchar (256)**|セッションに設定されているフラグの説明。  NULL 値は許可されません。 flag_desc は、次の任意の組み合わせを指定できます。<br /><br /> Flush buffers on close<br /><br /> Dedicated dispatcher<br /><br /> Allow recursive events|  
|dropped_event_count|**int**|バッファーがいっぱいのときに削除されたイベントの数。 この値は**0**かどうか、バッファー ポリシーが Drop full buffer"または"Do not drop events"です。 NULL 値は許可されません。|  
|dropped_buffer_count|**int**|バッファーがいっぱいのときに削除されたバッファーの数。 この値は**0**バッファー ポリシーが Drop event"または"Do not drop events"に設定されているかどうか。 NULL 値は許可されません。|  
|blocked_event_fire_time|**int**|バッファーがいっぱいのときにイベントの発生がブロックされていた時間。 この値は**0**バッファー ポリシーが [Drop full buffer] または [Drop event] かどうか。 NULL 値は許可されません。|  
|create_time|**datetime**|セッションが作成された時刻。 NULL 値は許可されません。|  
|largest_event_dropped_size|**int**|セッション バッファーに収まらなかった最大のイベントのサイズ。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|name 列と blocked_event_fire_time 列のデータ型を修正しました。|  
|buffer_size 列と total_buffers 列を削除しました。|  
|Total_regular_buffers、regular_buffer_size、total_large_buffers、追加しましたおよび total_buffer_size の各列を追加します。|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

