---
title: log_shipping_secondary (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_secondary
- log_shipping_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_secondary system table
ms.assetid: 69723419-4544-49c6-a517-adb30ffa5741
author: stevestein
ms.author: sstein
ms.openlocfilehash: 687f9f7441b7d77ea191047ef22491728ba81047
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68095824"
---
# <a name="log_shipping_secondary-transact-sql"></a>log_shipping_secondary (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セカンダリ ID ごとに1つのレコードを格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**secondary_id**|**UNIQUEIDENTIFIER**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**primary_server**|**sysname**|ログ配布構成にデータベースエンジン SQL Server のプライマリインスタンスの名前。|  
|**primary_database**|**sysname**|ログ配布構成のプライマリデータベースの名前。|  
|**backup_source_directory**|**nvarchar (500)**|プライマリサーバーからのトランザクションログバックアップファイルが格納されているディレクトリ。|  
|**backup_destination_directory**|**nvarchar (500)**|バックアップファイルのコピー先となるセカンダリサーバー上のディレクトリ。|  
|**file_retention_period**|**int**|バックアップファイルが削除される前にセカンダリサーバーで保持される時間 (分単位)。|  
|**copy_job_id**|**UNIQUEIDENTIFIER**|セカンダリ サーバーでのコピー ジョブに関連付けられた ID。|  
|**restore_job_id**|**UNIQUEIDENTIFIER**|セカンダリサーバー上の復元ジョブに関連付けられている ID。|  
|**monitor_server**|**sysname**|ログ配布構成で監視サーバーと[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]して使用されているのインスタンスの名前。|  
|**monitor_server_security_mode**|**bit**|監視サーバーへの接続に使用されるセキュリティモード。<br /><br /> 1 = Windows 認証。<br /><br /> 0 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証。|  
|**last_copied_file**|**nvarchar (500)**|セカンダリ サーバーにコピーされた最後のバックアップ ファイルの名前。|  
|**last_copied_date**|**DATETIME**|セカンダリサーバーに最後にコピー操作を行った日時です。|  
  
## <a name="remarks"></a>解説  
 特定のプライマリデータベースに対する同じセカンダリサーバー上の複数のセカンダリデータベースは、 **log_shipping_secondary**テーブルの一部の設定を共有します。 いずれかのデータベースに対して共有設定が変更された場合、変更はすべてのデータベースに適用されます。  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_secondary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql.md)   
 [sp_change_log_shipping_secondary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_help_log_shipping_secondary_database &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql.md)   
 [システムテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
