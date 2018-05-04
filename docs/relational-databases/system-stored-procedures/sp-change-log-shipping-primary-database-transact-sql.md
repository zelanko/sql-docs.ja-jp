---
title: sp_change_log_shipping_primary_database (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_change_log_shipping_primary_database
- sp_change_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_change_log_shipping_primary_database
ms.assetid: 8c9dce6b-d2a3-4ca7-a832-8f59a5adb214
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5d4a266a220a1be4597a82248618413348e4d62b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spchangelogshippingprimarydatabase-transact-sql"></a>sp_change_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プライマリ データベースの設定を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_change_log_shipping_primary_database [ @database = ] 'database'  
[, [ @backup_directory = ] 'backup_directory']   
[, [ @backup_share = ] 'backup_share']   
[, [ @backup_retention_period = ] 'backup_retention_period']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @backup_threshold = ] 'backup_threshold']   
[, [ @threshold_alert = ] 'threshold_alert']   
[, [ @threshold_alert_enabled = ] 'threshold_alert_enabled']   
[, [ @history_retention_period = ] 'history_retention_period']  
[, [ @backup_compression = ] backup_compression_option ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@database =** ] '*データベース*'  
 プライマリ サーバー上のデータベースの名前を指定します。 *primary_database*は**sysname**、既定値はありません。  
  
 [  **@backup_directory =** ] '*backup_directory*'  
 プライマリ サーバー上のバックアップ フォルダーのパスを指定します。 *backup_directory*は**nvarchar (500)**、既定値はありません、NULL にすることはできません。  
  
 [ **@backup_share =** ] '*backup_share*'  
 プライマリ サーバー上のバックアップ ディレクトリのパスを指定します。 *backup_share*は**nvarchar (500)**、既定値はありません、NULL にすることはできません。  
  
 [  **@backup_retention_period =** ] '*backup_retention_period*'  
 プライマリ サーバー上のバックアップ ディレクトリでログ バックアップ ファイルを保持する期間を、分単位で指定します。 *backup_retention_period*は**int**、既定値はありません、NULL にすることはできません。  
  
 [  **@monitor_server_security_mode =** ] '*monitor_server_security_mode*'  
 監視サーバーへの接続に使用されるセキュリティ モード。  
  
 1 = Windows 認証です。  
  
 0 = SQL Server 認証。  
  
 *monitor_server_security_mode*は**ビット**NULL にすることはできません。  
  
 [  **@monitor_server_login =** ] '*monitor_server_login*'  
 監視サーバーへのアクセスに使用するアカウントのユーザー名を指定します。  
  
 [  **@monitor_server_password =** ] '*monitor_server_password*'  
 監視サーバーへのアクセスに使用するアカウントのパスワードを指定します。  
  
 [  **@backup_threshold =** ] '*backup_threshold*'  
 前に最後のバックアップ後の分単位の時間の長さ、 *threshold_alert*エラーが発生します。 *backup_threshold*は**int**で、既定値は 60 分です。  
  
 [  **@threshold_alert =** ] '*threshold_alert*'  
 バックアップのしきい値を超えたときに発生する警告。 *threshold_alert*は**int** NULL にすることはできません。  
  
 [  **@threshold_alert_enabled =** ] '*threshold_alert_enabled*'  
 アラートが発生するかどうかを指定と*backup_threshold*を超過します。  
  
 1 = 有効。  
  
 0 = 無効になっています。  
  
 *threshold_alert_enabled*は**ビット**NULL にすることはできません。  
  
 [  **@history_retention_period =** ] '*ヒストリは削除*'  
 分の履歴を保持する時間の長さです。 *ヒストリは削除*は**int**です。何も指定しない場合は、値 14420 が使用されます。  
  
 [ **@backup_compression**=] *backup_compression_option*  
 ログ配布構成を使用するかどうかを示す[バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)です。 このパラメーターは [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) でのみサポートされます。  
  
 0 = 無効。 ログ バックアップは圧縮されません。  
  
 1 = 有効にします。 ログ バックアップを常に圧縮します。  
  
 2 = の設定を使用して、[表示または backup compression default サーバー構成オプションを構成する](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)です。 これが既定値です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_change_log_shipping_primary_database**から実行する必要があります、**マスター**プライマリ サーバー上のデータベースです。 このストアド プロシージャでは次の処理が行われます。  
  
1.  設定を変更、 **log_shipping_primary_database**必要な場合は、記録します。  
  
2.  ローカルのレコードを変更**log_shipping_monitor_primary**プライマリ サーバーを使用して、指定された引数に必要な場合です。  
  
3.  監視サーバーがプライマリ サーバーから異なる場合に変更を記録**log_shipping_monitor_primary**モニターでサーバーを使用して、指定された引数に必要な場合です。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例で使用する**sp_change_log_shipping_primary_database** 、プライマリ データベースに関連付けられている設定を更新する[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]です。  
  
```  
EXEC master.dbo.sp_change_log_shipping_primary_database   
 @database = N'AdventureWorks'   
, @backup_directory = N'c:\LogShipping'   
, @backup_share = N'\\tribeca\LogShipping'   
, @backup_retention_period = 1440   
, @backup_threshold = 60   
, @threshold_alert = 0   
, @threshold_alert_enabled = 1   
, @history_retention_period = 1440   
,@monitor_server_security_mode = 1  
,@backup_compression = 1;  
```  
  
## <a name="see-also"></a>参照  
 [ログ配布 & #40; についてSQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [log_shipping_primary_databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/log-shipping-primary-databases-transact-sql.md)  
  
  
