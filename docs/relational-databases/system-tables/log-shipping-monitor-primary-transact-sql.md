---
title: "log_shipping_monitor_primary (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_primary
- log_shipping_monitor_primary_TSQL
dev_langs: TSQL
helpviewer_keywords: log_shipping_monitor_primary system table
ms.assetid: 5f629a29-1a62-40e6-ae33-6f6b7dd09a36
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4386b5cade983a01c33dae27393dccad667c0842
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="logshippingmonitorprimary-transact-sql"></a>log_shipping_monitor_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各ログ配布構成内のプライマリ データベースごとに、1 つの監視レコードを格納します。 次の表は、 **msdb**データベース。  
  
 履歴や監視に関するテーブルは、プライマリ サーバーとセカンダリ サーバーでも使用されます。   
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**primary_id**|**uniqueidentifier**|ログ配布構成におけるプライマリ データベースの ID。|  
|**primary_server**|**sysname**|プライマリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。|  
|**primary_database**|**sysname**|ログ配布構成におけるプライマリ データベースの名前。|  
|**backup_threshold**|**int**|バックアップ操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。|  
|**threshold_alert**|**int**|バックアップのしきい値を超えたときに発生する警告。|  
|**threshold_alert_enabled**|**bit**|バックアップのしきい値の警告が有効かどうか。 1 = 有効にします。<br /><br /> 0 = 無効。|  
|**last_backup_file**|**nvarchar (500)**|最新のトランザクション ログ バックアップの絶対パス。|  
|**last_backup_date**|**datetime**|プライマリ データベースに対して最後にトランザクション ログのバックアップ操作を行った日時。|  
|**last_backup_date_utc**|**datetime**|プライマリ データベースに対して最後にトランザクション ログのバックアップ操作を行った日時。協定世界時 (UTC) で表されます。|  
|**ヒストリは削除**|**int**|指定したプライマリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>解説  
 プライマリ サーバーでリモート監視サーバーに格納されるだけでなく、プライマリ サーバーに関連する情報が格納されているその**log_shipping_monitor_primary**テーブル。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)   
 [sp_change_log_shipping_primary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_help_log_shipping_primary_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [sp_help_log_shipping_monitor_primary &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql.md)   
 [sp_delete_log_shipping_alert_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql.md)   
 [システム テーブルと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
