---
title: sp_help_log_shipping_secondary_database (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_secondary_database
- sp_help_log_shipping_secondary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_secondary_database
ms.assetid: 11ce42ca-d3f1-44c8-9cac-214ca8896b9a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19bac76afeb56bf196b7f717596777435d813f04
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846430"
---
# <a name="sphelplogshippingsecondarydatabase-transact-sql"></a>sp_help_log_shipping_secondary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上のセカンダリ データベースの設定を取得します。  
  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_log_shipping_secondary_database  
[ @secondary_database = ] 'secondary_database' OR  
[ @secondary_id = ] 'secondary_id'  
```  
  
## <a name="arguments"></a>引数  
 [  **@secondary_database =** ] '*secondary_database*'  
 セカンダリ データベースの名前を指定します。 *secondary_database*は**sysname**、既定値はありません。  
  
 [  **@secondary_id =** ] '*secondary_id*'  
 ログ配布構成におけるセカンダリ サーバーの ID。 *secondary_id*は**uniqueidentifier** NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|説明|  
|-----------------|-----------------|  
|**secondary_id**|ログ配布構成におけるセカンダリ サーバーの ID。|  
|**primary_server**|プライマリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。|  
|**primary_database**|ログ配布構成におけるプライマリ データベースの名前。|  
|**backup_source_directory**|プライマリ サーバーのトランザクション ログ バックアップ ファイルが格納されているディレクトリ。|  
|**backup_destination_directory**|バックアップ ファイルのコピー先となるセカンダリ サーバーのディレクトリ。|  
|**file_retention_period**|セカンダリ サーバーでバックアップ ファイルが保持される時間 (分単位)。この時間を過ぎるとファイルは削除されます。|  
|**copy_job_id**|セカンダリ サーバーでのコピー ジョブに関連付けられた ID。|  
|**restore_job_id**|セカンダリ サーバーでの復元ジョブに関連付けられた ID。|  
|**monitor_server**|インスタンスの名前、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成で監視サーバーとして使用されています。|  
|**monitor_server_security_mode**|監視サーバーへの接続に使用されるセキュリティ モード。<br /><br /> 1 = [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。<br /><br /> 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**secondary_database**|ログ配布構成におけるセカンダリ データベースの名前。|  
|**restore_delay**|セカンダリ サーバーが指定されたバックアップ ファイルを復元する前に待機する分単位の時間数。 既定値は、0 分です。|  
|**restore_all**|1 に設定すると、セカンダリ サーバーでは復元ジョブの実行時にすべてのトランザクション ログ バックアップが復元されます。 1 以外に設定すると、セカンダリ サーバーは 1 つのファイルが復元された後で停止します。|  
|**restore_mode**|セカンダリ データベースの復元モードを指定します。<br /><br /> 0 = NORECOVERY でログを復元します。<br /><br /> 1 = STANDBY でログを復元します。|  
|**disconnect_users**|1 に設定すると、復元操作の実行時、ユーザーはセカンダリ データベースから切断されます。 既定 = 0。|  
|**block_size**|バックアップ デバイスのブロック サイズに使用されるサイズ (バイト単位)。|  
|**buffer_count**|バックアップまたは復元操作で使用されるバッファーの総数。|  
|**max_transfer_size**|サイズをバイト単位の最大入力または出力要求によって発行された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ デバイスにします。|  
|**restore_threshold**|復元操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。|  
|**threshold_alert**|復元のしきい値を超えたときに発生する警告。|  
|**threshold_alert_enabled**|復元のしきい値の警告を有効にするかどうか。<br /><br /> 1 = 有効にします。<br /><br /> 0 = 無効。|  
|**last_copied_file**|セカンダリ サーバーにコピーされた最後のバックアップ ファイルの名前。|  
|**last_copied_date**|セカンダリ サーバーに対して最後にコピー操作を行った日時。|  
|**last_copied_date_utc**|セカンダリ サーバーに対して最後にコピー操作を行った日時。協定世界時 (UTC) で表されます。|  
|**last_restored_file**|セカンダリ データベースに復元された最後のバックアップ ファイルの名前。|  
|**last_restored_date**|セカンダリ データベースに対して最後に復元操作を行った日時。|  
|**last_restored_date_utc**|セカンダリ データベースに対して最後に復元操作を行った日時。協定世界時 (UTC) で表されます。|  
|**history_retention_period**|指定したセカンダリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
|**last_restored_latency**|ログ バックアップがプライマリで作成されてからセカンダリで復元されるまでの経過時間 (分単位)。<br /><br /> 初期値は NULL です。|  
  
## <a name="remarks"></a>コメント  
 含める場合は、 *secondary_database*パラメーター、結果セットが含まれますセカンダリ データベースに関する情報を含める場合、 *secondary_id*パラメーター、結果セットが含まれますそのセカンダリ ID に関連付けられているすべてのセカンダリ データベースに関する情報  
  
 **sp_help_log_shipping_secondary_database**から実行する必要があります、**マスター**セカンダリ サーバー上のデータベース。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="see-also"></a>参照  
 [sp_help_log_shipping_secondary_primary &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql.md)   
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
