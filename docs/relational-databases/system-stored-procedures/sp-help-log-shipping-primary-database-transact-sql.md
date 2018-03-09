---
title: "sp_help_log_shipping_primary_database (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_database_TSQL
- sp_help_log_shipping_primary_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_database
ms.assetid: e711b01c-ef29-4eb6-a016-0e647e337818
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 56de87e340bc9bd6006208754451c54c145fbdba
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sphelplogshippingprimarydatabase-transact-sql"></a>sp_help_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プライマリ データベース設定を取得します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_log_shipping_primary_database  
[ @database = ] 'database' OR  
[ @primary_id = ] 'primary_id'  
```  
  
## <a name="arguments"></a>引数  
 [  **@database =** ] '*データベース*'  
 ログ配布プライマリ データベースの名前を指定します。 *データベース*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 [ **@primary_id =** ] '*primary_id*'  
 ログ配布構成におけるプライマリ データベースの ID。 *primary_id*は**uniqueidentifier** NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|Description|  
|-----------------|-----------------|  
|**primary_id**|ログ配布構成におけるプライマリ データベースの ID。|  
|**primary_database**|ログ配布構成におけるプライマリ データベースの名前。|  
|**backup_directory**|プライマリ サーバーのトランザクション ログ バックアップ ファイルが格納されているディレクトリ。|  
|**backup_share**|バックアップ ディレクトリへのネットワーク パスまたは UNC パス。|  
|**backup_retention_period**|バックアップ ディレクトリでログ バックアップ ファイルが保持される時間 (分単位)。この時間を過ぎるとファイルは削除されます。|  
|**backup_compression**|ログ配布構成を使用するかどうかを示す[バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)です。<br /><br /> **0**無効になっています。 ログ バックアップは圧縮されません。<br /><br /> **1** = 有効にします。 ログ バックアップを常に圧縮します。<br /><br /> **2** = の設定を使用して、[表示または backup compression default サーバー構成オプションを構成する](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)です。 これが既定値です。<br /><br /> バックアップの圧縮がサポートされているのみ[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)](またはそれ以降のバージョン)。 その他のエディションでは、値は常に 2 です。|  
|**backup_job_id**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プライマリ サーバー上のバックアップ ジョブに関連付けられているエージェントのジョブ ID。|  
|**monitor_server**|インスタンスの名前、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成で監視サーバーとして使用されています。|  
|**monitor_server_security_mode**|監視サーバーへの接続に使用されるセキュリティ モード。<br /><br /> 1 = [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。<br /><br /> 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**backup_threshold**|バックアップ操作が始まってから警告が生成されるまでの許容経過時間 (分単位)。|  
|**threshold_alert**|バックアップのしきい値を超えたときに発生する警告。|  
|**threshold_alert_enabled**|バックアップのしきい値の警告が有効かどうか。<br /><br /> **1** = 有効にします。<br /><br /> **0**無効になっています。|  
|**last_backup_file**|最新のトランザクション ログ バックアップの絶対パス。|  
|**last_backup_date**|最後のログ バックアップ操作の日時。|  
|**last_backup_date_utc**|プライマリ データベースに対して最後にトランザクション ログのバックアップ操作を行った日時。協定世界時 (UTC) で表されます。|  
|**history_retention_period**|指定したプライマリ データベースでログ配布履歴レコードが保持される時間 (分単位)。この時間を過ぎるとレコードは削除されます。|  
  
## <a name="remarks"></a>解説  
 **sp_help_log_shipping_primary_database**から実行する必要があります、**マスター**プライマリ サーバー上のデータベースです。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例を使用して**sp_help_log_shipping_primary_database**データベースのプライマリ データベースの設定を取得する[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]です。  
  
```  
EXEC master.dbo.sp_help_log_shipping_primary_database @database=N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ログ配布 &#40; についてSQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
