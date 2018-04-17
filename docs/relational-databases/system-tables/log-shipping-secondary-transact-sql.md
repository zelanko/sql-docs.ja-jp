---
title: log_shipping_secondary (TRANSACT-SQL) |Microsoft ドキュメント
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
- log_shipping_secondary
- log_shipping_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary system table
ms.assetid: 69723419-4544-49c6-a517-adb30ffa5741
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 71f859f5e1d840b161e3e4545b8c5338771341d1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="logshippingsecondary-transact-sql"></a>log_shipping_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セカンダリ ID ごとに 1 つのレコードを格納します。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**secondary_id**|**uniqueidentifier**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**primary_server**|**sysname**|ログ配布構成における SQL Server データベース エンジンのプライマリ インスタンスの名前。|  
|**primary_database**|**sysname**|ログ配布構成におけるプライマリ データベースの名前。|  
|**backup_source_directory**|**nvarchar(500)**|プライマリ サーバーのトランザクション ログ バックアップ ファイルが格納されているディレクトリ。|  
|**backup_destination_directory**|**nvarchar(500)**|バックアップ ファイルのコピー先となるセカンダリ サーバーのディレクトリ。|  
|**file_retention_period**|**int**|セカンダリ サーバーでバックアップ ファイルが保持される時間 (分単位)。この時間を過ぎるとファイルは削除されます。|  
|**copy_job_id**|**uniqueidentifier**|セカンダリ サーバーでのコピー ジョブに関連付けられた ID。|  
|**restore_job_id**|**uniqueidentifier**|セカンダリ サーバーでの復元ジョブに関連付けられた ID。|  
|**monitor_server**|**sysname**|インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成で監視サーバーとして使用されています。|  
|**monitor_server_security_mode**|**bit**|監視サーバーへの接続に使用されるセキュリティ モード。<br /><br /> 1 = Windows 認証です。<br /><br /> 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**last_copied_file**|**nvarchar(500)**|セカンダリ サーバーにコピーされた最後のバックアップ ファイルの名前。|  
|**last_copied_date**|**datetime**|セカンダリ サーバーに対して最後にコピー操作を行った日時。|  
  
## <a name="remarks"></a>解説  
 特定のプライマリ データベースと同じセカンダリ サーバー上の複数のセカンダリ データベースが一部の設定を共有、 **log_shipping_secondary**テーブル。 いずれかのデータベースに対して共有設定が変更された場合、変更はすべてのデータベースに適用されます。  
  
## <a name="see-also"></a>参照  
 [ログ配布 & #40; についてSQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
