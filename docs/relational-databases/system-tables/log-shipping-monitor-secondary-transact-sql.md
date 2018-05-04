---
title: log_shipping_monitor_secondary (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- log_shipping_monitor_secondary_TSQL
- log_shipping_monitor_secondary
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_secondary system table
ms.assetid: afbe1bb7-89a7-4020-9408-0af64a043c2e
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3200a0616ffc3db7a328322a39d1767ecefe6614
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="logshippingmonitorsecondary-transact-sql"></a>log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各ログ配布構成内のセカンダリ データベースごとに、1 つの監視レコードを格納します。 次の表は、 **msdb**データベース。  
  
 履歴や監視に関するテーブルは、プライマリ サーバーとセカンダリ サーバーでも使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**secondary_server**|**sysname**|セカンダリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。|  
|**secondary_database**|**sysname**|ログ配布構成におけるセカンダリ データベースの名前。|  
|**secondary_id**|**uniqueidentifier**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**primary_server**|**sysname**|ログ配布構成における [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のプライマリ インスタンスの名前。|  
|**primary_database**|**sysname**|ログ配布構成におけるプライマリ データベースの名前。|  
|**restore_threshold**|**int**|復元操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。|  
|**threshold_alert**|**int**|復元のしきい値を超えたときに発生する警告。|  
|**threshold_alert_enabled**|**bit**|復元のしきい値の警告を有効にするかどうか。 1 = 有効にします。<br /><br /> 0 = 無効。|  
|**last_copied_file**|**nvarchar(500)**|セカンダリ サーバーにコピーされた最後のバックアップ ファイルの名前。|  
|**last_copied_date**|**datetime**|セカンダリ サーバーに対して最後にコピー操作を行った日時。|  
|**last_copied_date_utc**|**datetime**|セカンダリ サーバーに対して最後にコピー操作を行った日時。協定世界時 (UTC) で表されます。|  
|**last_restored_file**|**nvarchar(500)**|セカンダリ データベースに復元された最後のバックアップ ファイルの名前。|  
|**last_restored_date**|**datetime**|セカンダリ データベースに対して最後に復元操作を行った日時。|  
|**last_restored_date_utc**|**datetime**|セカンダリ データベースに対して最後に復元操作を行った日時。協定世界時 (UTC) で表されます。|  
|**last_restored_latency**|**int**|ログ バックアップがプライマリで作成されてからセカンダリで復元されるまでの経過時間 (分単位)。<br /><br /> 初期値は NULL です。|  
|**history_retention_period**|**int**|指定したセカンダリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>解説  
 リモート監視サーバーに格納されているだけでなくなるとセカンダリ サーバーでセカンダリ サーバーに関連する情報が格納されているもの**log_shipping_monitor_secondary**テーブル。  
  
## <a name="see-also"></a>参照  
 [ログ配布 & #40; についてSQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_refresh_log_shipping_monitor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_add_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_monitor_secondary &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
