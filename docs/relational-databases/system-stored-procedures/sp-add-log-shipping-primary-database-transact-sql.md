---
title: sp_add_log_shipping_primary_database (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_primary_database
- sp_add_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_primary_database
ms.assetid: 69531611-113f-46b5-81a6-7bf496d0353c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b73ec62b6b0abc8ab8334efdc5f26c5bd2748605
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034740"
---
# <a name="spaddlogshippingprimarydatabase-transact-sql"></a>sp_add_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バックアップ ジョブ、ローカル監視レコード、リモート監視レコードを含め、ログ配布構成のプライマリ データベースを設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_log_shipping_primary_database [ @database = ] 'database',   
[ @backup_directory = ] 'backup_directory',   
[ @backup_share = ] 'backup_share',   
[ @backup_job_name = ] 'backup_job_name',   
[, [ @backup_retention_period = ] backup_retention_period]  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] monitor_server_security_mode]  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] backup_threshold ]   
[, [ @threshold_alert = ] threshold_alert ]   
[, [ @threshold_alert_enabled = ] threshold_alert_enabled ]   
[, [ @history_retention_period = ] history_retention_period ]  
[, [ @backup_job_id = ] backup_job_id OUTPUT ]  
[, [ @primary_id = ] primary_id OUTPUT]  
[, [ @backup_compression = ] backup_compression_option ]  
  
```  
  
## <a name="arguments"></a>引数  
 [  **@database=** ] '*データベース*'  
 ログ配布プライマリ データベースの名前を指定します。 *データベース*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 [  **@backup_directory=** ] '*backup_directory*'  
 プライマリ サーバー上のバックアップ フォルダーのパスを指定します。 *backup_directory*は**nvarchar (500)**、既定値はありません、NULL にすることはできません。  
  
 [ **@backup_share=** ] '*backup_share*'  
 プライマリ サーバー上のバックアップ ディレクトリのパスを指定します。 *backup_share*は**nvarchar (500)**、既定値はありません、NULL にすることはできません。  
  
 [ **@backup_job_name=** ] '*backup_job_name*'  
 プライマリ サーバー上で動作し、バックアップをバックアップ フォルダーにコピーする SQL Server エージェント ジョブの名前を指定します。 *backup_job_name*は**sysname** NULL にすることはできません。  
  
 [ **@backup_retention_period=** ] *backup_retention_period*  
 プライマリ サーバー上のバックアップ ディレクトリでログ バックアップ ファイルを保持する期間を、分単位で指定します。 *backup_retention_period*は**int**、既定値はありません、NULL にすることはできません。  
  
 [  **@monitor_server=** ] '*monitor_server*'  
 監視サーバーの名前を指定します。 *Monitor_server*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 [  **@monitor_server_security_mode=** ] *monitor_server_security_mode*  
 監視サーバーへの接続に使用されるセキュリティ モード。  
  
 1 = Windows 認証。  
  
 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 *monitor_server_security_mode*は**ビット**NULL にすることはできません。  
  
 [  **@monitor_server_login=** ] '*monitor_server_login*'  
 監視サーバーへのアクセスに使用するアカウントのユーザー名を指定します。  
  
 [  **@monitor_server_password=** ] '*monitor_server_password*'  
 監視サーバーへのアクセスに使用するアカウントのパスワードを指定します。  
  
 [ **@backup_threshold=** ] *backup_threshold*  
 前に前回のバックアップ後の分の時間の長さ、 *threshold_alert*エラーが発生します。 *backup_threshold*は**int**、既定値は 60 分です。  
  
 [ **@threshold_alert=** ] *threshold_alert*  
 バックアップのしきい値を超過したときに生成する警告を指定します。 *threshold_alert*は**int**、既定値は 14,420 です。  
  
 [ **@threshold_alert_enabled=** ] *threshold_alert_enabled*  
 アラートがあるかどうかを指定する場合に発生します*backup_threshold*を超過します。 値 0 (既定値) を指定すると、警告が無効になり、生成されなくなります。 *threshold_alert_enabled*は**ビット**します。  
  
 [ **@history_retention_period=** ] *history_retention_period*  
 履歴を保持する期間を分単位で指定します。 *history_retention_period*は**int**、既定値は NULL です。 指定されていない場合、値 14420 が使用されます。  
  
 [ **@backup_job_id=** ] *backup_job_id* OUTPUT  
 プライマリ サーバー上のバックアップ ジョブに関連付けられている、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ID。 *backup_job_id*は**uniqueidentifier** NULL にすることはできません。  
  
 [ **@primary_id=** ] *primary_id* OUTPUT  
 ログ配布構成におけるプライマリ データベースの ID。 *primary_id*は**uniqueidentifier** NULL にすることはできません。  
  
 [ **@backup_compression**=] *backup_compression_option*  
 ログ配布構成を使用するかどうかを指定[バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)します。 このパラメーターは [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) でのみサポートされます。  
  
 0 = 無効。 ログ バックアップは圧縮されません。  
  
 1 = 有効にします。 ログ バックアップを常に圧縮します。  
  
 2 = の設定を使用して、 [backup compression default サーバー構成オプションの構成を表示または](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)します。 これが既定値です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_add_log_shipping_primary_database**から実行する必要があります、**マスター**プライマリ サーバー上のデータベース。 このストアド プロシージャは、次の関数を実行します。  
  
1.  プライマリ ID を生成し、テーブル内のプライマリ データベースのエントリを追加**log_shipping_primary_databases**指定された引数を使用します。  
  
2.  無効になったプライマリ データベースのバックアップ ジョブを作成する。  
  
3.  バックアップ ジョブの ID を設定、 **log_shipping_primary_databases**バックアップ ジョブのジョブ ID を入力します。  
  
4.  ローカル監視レコードをテーブルの追加**log_shipping_monitor_primary**プライマリ サーバーを使用して引数を指定します。  
  
5.  監視サーバーがプライマリ サーバーと異なる場合は、監視レコードを追加します。 **log_shipping_monitor_primary**モニターでサーバーを使用して引数を指定します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 次の例では、ログ配布構成のプライマリ データベースとして、データベース [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] を追加します。  
  
```  
DECLARE @LS_BackupJobId AS uniqueidentifier ;  
DECLARE @LS_PrimaryId AS uniqueidentifier ;  
  
EXEC master.dbo.sp_add_log_shipping_primary_database   
@database = N'AdventureWorks'   
,@backup_directory = N'c:\lsbackup'   
,@backup_share = N'\\tribeca\lsbackup'   
,@backup_job_name = N'LSBackup_AdventureWorks'   
,@backup_retention_period = 1440  
,@monitor_server = N'rockaway'   
,@monitor_server_security_mode = 1   
,@backup_threshold = 60   
,@threshold_alert = 0   
,@threshold_alert_enabled = 0   
,@history_retention_period = 1440   
,@backup_job_id = @LS_BackupJobId OUTPUT   
,@primary_id = @LS_PrimaryId OUTPUT   
,@overwrite = 1   
,@backup_compression = 0;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
