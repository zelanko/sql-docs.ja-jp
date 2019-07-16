---
title: log_shipping_primary_databases (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_primary_databases
- log_shipping_primary_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_primary_databases system table
ms.assetid: 56888756-a798-42be-9b5e-0f9aa05a2cc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 893f016fba45d18947af376425012d21964709b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004717"
---
# <a name="logshippingprimarydatabases-transact-sql"></a>log_shipping_primary_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログ配布構成で、プライマリ データベースの 1 つのレコードを格納します。 このテーブルに格納されます、 **msdb**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**primary_id**|**uniqueidentifier**|ログ配布構成におけるプライマリ データベースの ID。|  
|**primary_database**|**sysname**|ログ配布構成におけるプライマリ データベースの名前。|  
|**backup_directory**|**nvarchar(500)**|プライマリ サーバーからのトランザクション ログ バックアップ ファイルの保存先ディレクトリ。|  
|**backup_share**|**nvarchar(500)**|ネットワークまたはバックアップ ディレクトリへの UNC パス。|  
|**backup_retention_period**|**int**|バックアップ ディレクトリでログ バックアップ ファイルが保持される時間 (分単位)。この時間を過ぎるとファイルは削除されます。|  
|**backup_job_id**|**uniqueidentifier**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プライマリ サーバー上のバックアップ ジョブに関連付けられているエージェント ジョブの ID。|  
|**monitor_server**|**sysname**|インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成で監視サーバーとして使用されています。|  
|**monitor_server_security_mode**|**bit**|監視サーバーへの接続に使用されるセキュリティ モード。<br /><br /> 1 = Windows 認証。<br /><br /> 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**last_backup_file**|**nvarchar(500)**|最新のトランザクション ログ バックアップの絶対パス。|  
|**last_backup_date**|**datetime**|最後のログ バックアップ操作の日時。|  
|**user_specified_monitor**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **sp_help_log_shipping_primary_database**と**sp_help_log_shipping_secondary_primary**この列を使用して、モニターの設定の表示を制御する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。<br /><br /> 0 = ユーザーが明示的な値を指定しなかったこれら 2 つのストアド プロシージャのいずれかを呼び出すときに、 **@monitor_server** パラメーター。<br /><br /> 1 = ユーザーが明示的な値を指定しました。|  
|**backup_compression**|**tinyint**|ログ配布構成のサーバー レベルのバックアップ圧縮動作を上書きするかどうかを示します。<br /><br /> 0 = 無効になっています。 ログ バックアップは圧縮されません、バックアップの圧縮をサーバーで構成された設定に関係なく。<br /><br /> 1 = 有効にします。 ログ バックアップは常に圧縮、バックアップの圧縮をサーバーで構成された設定に関係なく。<br /><br /> 2 = のサーバーの構成を使用して、 [backup compression default サーバー構成オプションの構成を表示または](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)サーバー構成オプション。 これは既定値です。<br /><br /> バックアップの圧縮は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Enterprise エディションでのみサポートされています。|  
  
## <a name="see-also"></a>関連項目  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_help_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql.md)   
 [システム テーブル &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
