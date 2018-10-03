---
title: log_shipping_monitor_history_detail (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_history_detail_TSQL
- log_shipping_monitor_history_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_history_detail system table
ms.assetid: 7080c888-323b-4206-a1ab-e6c51f9e2579
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f8968661442adabe4c04608ca5a5bb5362341c4b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804110"
---
# <a name="logshippingmonitorhistorydetail-transact-sql"></a>log_shipping_monitor_history_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ配布ジョブの履歴の詳細を格納します。 このテーブルに格納されます、 **msdb**データベース。  
  
 履歴や監視に関するテーブルは、プライマリ サーバーとセカンダリ サーバーでも使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|バックアップの場合はプライマリ ID、コピーまたは復元の場合はセカンダリ ID。|  
|**agent_type**|**tinyint**|ログ配布ジョブの種類を指定します。<br /><br /> 0 = バックアップ。<br /><br /> 1 = コピー。<br /><br /> 2 = 復元。|  
|**session_id**|**int**|バックアップ、コピー、または復元ジョブのセッション ID。|  
|**database_name**|**sysname**|このレコードに関連付けられているデータベースの名前。 バックアップの場合はプライマリ データベースの名前、復元の場合はセカンダリ データベースの名前、コピーの場合は空白になります。|  
|**session_status**|**tinyint**|セッションの状態。<br /><br /> 0 = 開始<br /><br /> 1 = 実行中です。<br /><br /> 2 = 成功。<br /><br /> 3 = エラー。<br /><br /> 4 = 警告|  
|**log_time**|**datetime**|レコードが作成された日時。|  
|**log_time_utc**|**datetime**|レコードが作成された日時。協定世界時 (UTC) で表されます。|  
|**message**|**nvarchar(max)**|メッセージ テキスト。|  
  
## <a name="remarks"></a>コメント  
 このテーブルには、ログ配布エージェントの履歴の詳細が格納されます。 エージェント セッションを識別するために列を使用して、 **agent_id**、 **agent_type**、および**session_id**します。 エージェント セッションの履歴詳細を表示、並べ替え**log_time**します。  
  
 内のプライマリ サーバーでリモート監視サーバーに格納されるだけでなく、プライマリ サーバーに関連する情報が格納されているその**log_shipping_monitor_history_detail**テーブル、およびセカンダリに関連する情報サーバーがセカンダリ サーバーでも格納されているその**log_shipping_monitor_history_detail**テーブル。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_delete_log_shipping_primary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [システム テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [log_shipping_monitor_error_detail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql.md)  
  
  
