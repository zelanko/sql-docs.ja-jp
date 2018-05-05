---
title: log_shipping_monitor_error_detail (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_error_detail_TSQL
- log_shipping_monitor_error_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_error_detail system table
ms.assetid: 0c38a625-60d2-4ee2-bcf3-2ba367914220
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7a594771827da8a3af6b5158725e632f4488eed5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="logshippingmonitorerrordetail-transact-sql"></a>log_shipping_monitor_error_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ配布ジョブのエラーの詳細を格納します。 次の表は、 **msdb**データベース。  
  
 履歴や監視に関するテーブルは、プライマリ サーバーとセカンダリ サーバーでも使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|バックアップの場合はプライマリ ID、コピーまたは復元の場合はセカンダリ ID。|  
|**agent_type**|**tinyint**|ログ配布ジョブの種類を指定します。<br /><br /> 0 = バックアップ。<br /><br /> 1 = コピー。<br /><br /> 2 = 復元。|  
|**session_id**|**int**|バックアップ、コピー、または復元ジョブのセッション ID。|  
|**database_name**|**sysname**|このエラー レコードに関連付けられているデータベースの名前。 バックアップの場合はプライマリ データベースの名前、復元の場合はセカンダリ データベースの名前、コピーの場合は空白になります。|  
|**sequence_number**|**int**|複数のレコードに関連するエラーの情報を正しい順序で示すための増分番号。|  
|**log_time**|**datetime**|レコードが作成された日時。|  
|**log_time_utc**|**datetime**|レコードが作成された日時。協定世界時 (UTC) で表されます。|  
|**message**|**nvarchar**|メッセージ テキスト。|  
|**source**|**nvarchar**|エラー メッセージまたはイベントのソース。|  
|**help_url**|**nvarchar**|エラーの詳細を確認できる URL (使用可能な場合)。|  
  
## <a name="remarks"></a>解説  
 このテーブルには、ログ配布エージェントに関するエラーの詳細が格納されます。 各エラーは一連の例外として記録され、 各エージェント セッションでは複数のエラー (シーケンス) が記録される場合があります。  
  
 プライマリ サーバーでリモート監視サーバーに格納されるだけでなく、プライマリ サーバーに関連する情報が格納されているその**log_shipping_monitor_error_detail**テーブル、およびセカンダリ サーバーに関連する情報セカンダリ サーバーに格納されても、 **log_shipping_monitor_error_detail**テーブル。  
  
 エージェント セッションを識別するための列を使用して**agent_id**、 **agent_type**、および**session_id**です。 並べ替える**log_time**記録された順序でエラーを表示します。  
  
## <a name="see-also"></a>参照  
 [ログ配布 & #40; についてSQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [log_shipping_monitor_history_detail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
