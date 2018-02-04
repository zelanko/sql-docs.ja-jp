---
title: "log_shipping_monitor_history_detail (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_history_detail_TSQL
- log_shipping_monitor_history_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_history_detail system table
ms.assetid: 7080c888-323b-4206-a1ab-e6c51f9e2579
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b44a87a77f22a9815e7dc645e85478315fe8959a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="logshippingmonitorhistorydetail-transact-sql"></a>log_shipping_monitor_history_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ配布ジョブの履歴の詳細を格納します。 次の表は、 **msdb**データベース。  
  
 履歴や監視に関するテーブルは、プライマリ サーバーとセカンダリ サーバーでも使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|バックアップの場合はプライマリ ID、コピーまたは復元の場合はセカンダリ ID。|  
|**agent_type**|**tinyint**|ログ配布ジョブの種類を指定します。<br /><br /> 0 = バックアップ。<br /><br /> 1 = コピー。<br /><br /> 2 = 復元。|  
|**session_id**|**int**|バックアップ、コピー、または復元ジョブのセッション ID。|  
|**database_name**|**sysname**|このレコードに関連付けられているデータベースの名前。 バックアップの場合はプライマリ データベースの名前、復元の場合はセカンダリ データベースの名前、コピーの場合は空白になります。|  
|**session_status**|**tinyint**|セッションの状態。<br /><br /> 0 = 開始<br /><br /> 1 = 実行中です。<br /><br /> 2 = 成功します。<br /><br /> 3 = エラーです。<br /><br /> 4 = 警告|  
|**log_time**|**datetime**|レコードが作成された日時。|  
|**log_time_utc**|**datetime**|レコードが作成された日時。協定世界時 (UTC) で表されます。|  
|**message**|**nvarchar(max)**|メッセージ テキスト。|  
  
## <a name="remarks"></a>解説  
 このテーブルには、ログ配布エージェントの履歴の詳細が格納されます。 エージェント セッションを識別するための列を使用して**agent_id**、 **agent_type**、および**session_id**です。 エージェント セッションの履歴の詳細情報を表示、並べ替える**log_time**です。  
  
 プライマリ サーバーでリモート監視サーバーに格納されるだけでなく、プライマリ サーバーに関連する情報が格納されているその**log_shipping_monitor_history_detail**テーブル、およびセカンダリに関連する情報サーバーがセカンダリ サーバーでも格納されているその**log_shipping_monitor_history_detail**テーブル。  
  
## <a name="see-also"></a>参照  
 [ログ配布 &#40; についてSQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_delete_log_shipping_primary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [log_shipping_monitor_error_detail &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql.md)  
  
  
