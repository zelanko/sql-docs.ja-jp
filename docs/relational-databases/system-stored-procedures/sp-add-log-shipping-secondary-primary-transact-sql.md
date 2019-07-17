---
title: sp_add_log_shipping_secondary_primary (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_log_shipping_secondary_primary_TSQL
- sp_add_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_primary
ms.assetid: bfbbbee2-c255-4a59-a963-47d6e980a8e2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: efbd753b40159afcca81b8922e8ef2842d22e5e4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68067726"
---
# <a name="spaddlogshippingsecondaryprimary-transact-sql"></a>sp_add_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したプライマリ データベースのセカンダリ サーバーに対して、プライマリ情報の設定、ローカルおよびリモート監視リンクの追加、コピー ジョブと復元ジョブの作成を行います。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_log_shipping_secondary_primary  
 [ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database',  
[ @backup_source_directory = ] 'backup_source_directory' ,   
[ @backup_destination_directory = ] 'backup_destination_directory'  
[ @copy_job_name = ] 'copy_job_name'  
[ @restore_job_name = ] 'restore_job_name'  
[, [ @file_retention_period = ] 'file_retention_period']  
[, [ @monitor_server = ] 'monitor_server']  
[, [ @monitor_server_security_mode = ] 'monitor_server_security_mode']  
[, [ @monitor_server_login = ] 'monitor_server_login']  
[, [ @monitor_server_password = ] 'monitor_server_password']  
[, [ @copy_job_id = ] 'copy_job_id' OUTPUT ]  
[, [ @restore_job_id = ] 'restore_job_id' OUTPUT ]  
[, [ @secondary_id = ] 'secondary_id' OUTPUT]  
```  
  
## <a name="arguments"></a>引数  
`[ @primary_server = ] 'primary_server'` プライマリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。 *primary_server*は**sysname** NULL にすることはできません。  
  
`[ @primary_database = ] 'primary_database'` プライマリ サーバー上のデータベースの名前です。 *primary_database*は**sysname**、既定値はありません。  
  
`[ @backup_source_directory = ] 'backup_source_directory'` プライマリ サーバーからのトランザクション ログ バックアップ ファイルの保存先ディレクトリ。 *backup_source_directory*は**nvarchar (500)** NULL にすることはできません。  
  
`[ @backup_destination_directory = ] 'backup_destination_directory'` バックアップ ファイルがコピー先のセカンダリ サーバー上のディレクトリ。 *backup_destination_directory*は**nvarchar (500)** NULL にすることはできません。  
  
`[ @copy_job_name = ] 'copy_job_name'` 使用する名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクション ログ バックアップをセカンダリ サーバーにコピーに作成されているエージェント ジョブ。 *copy_job_name*は**sysname** NULL にすることはできません。  
  
`[ @restore_job_name = ] 'restore_job_name'` 名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セカンダリ データベースにバックアップを復元するセカンダリ サーバー上のエージェント ジョブ。 *restore_job_name*は**sysname** NULL にすることはできません。  
  
`[ @file_retention_period = ] 'file_retention_period'` 指定されたパスのセカンダリ サーバーでバックアップ ファイルが保持される分単位の時間の長さ、@backup_destination_directoryパラメーターを削除する前にします。 *history_retention_period*は**int**、既定値は NULL です。 指定されていない場合、値 14420 が使用されます。  
  
`[ @monitor_server = ] 'monitor_server'` 監視サーバーの名前です。 *Monitor_server*は**sysname**、既定値はありません、NULL にすることはできません。  
  
`[ @monitor_server_security_mode = ] 'monitor_server_security_mode'` 監視サーバーへの接続に使用されるセキュリティ モード。  
  
 1 = Windows 認証。  
  
 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  
  
 *monitor_server_security_mode*は**ビット**NULL にすることはできません。  
  
`[ @monitor_server_login = ] 'monitor_server_login'` 監視サーバーへのアクセスに使用するアカウントの username です。  
  
`[ @monitor_server_password = ] 'monitor_server_password'` 監視サーバーへのアクセスに使用するアカウントのパスワードです。  
  
`[ @copy_job_id = ] 'copy_job_id' OUTPUT` セカンダリ サーバー上のコピー ジョブに関連付けられている ID です。 *copy_job_id*は**uniqueidentifier** NULL にすることはできません。  
  
`[ @restore_job_id = ] 'restore_job_id' OUTPUT` セカンダリ サーバー上の復元ジョブに関連付けられている ID です。 *restore_job_id*は**uniqueidentifier** NULL にすることはできません。  
  
`[ @secondary_id = ] 'secondary_id' OUTPUT` ログ配布構成におけるセカンダリ サーバーの ID。 *secondary_id*は**uniqueidentifier** NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_add_log_shipping_secondary_primary**から実行する必要があります、**マスター**セカンダリ サーバー上のデータベース。 このストアド プロシージャでは次の処理が行われます。  
  
1.  指定したプライマリ サーバーとプライマリ データベースのセカンダリ ID を生成する。  
  
2.  次を行います。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    1.  セカンダリ ID のエントリを追加します。 **log_shipping_secondary**指定された引数を使用します。  
  
    2.  無効になったセカンダリ ID のコピー ジョブを作成する。  
  
    3.  コピー ジョブ ID を設定、 **log_shipping_secondary**コピー ジョブのジョブ ID を入力します。  
  
    4.  無効になったセカンダリ ID の復元ジョブを作成します。  
  
    5.  復元ジョブ ID を設定、 **log_shipping_secondary**復元ジョブのジョブ ID を入力します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例を使用して、 **sp_add_log_shipping_secondary_primary**ストアド プロシージャをプライマリ データベースの情報を設定する[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]セカンダリ サーバーです。  
  
```  
EXEC master.dbo.sp_add_log_shipping_secondary_primary   
@primary_server = N'TRIBECA'   
,@primary_database = N'AdventureWorks'   
,@backup_source_directory = N'\\tribeca\LogShipping'   
,@backup_destination_directory = N''   
,@copy_job_name = N''   
,@restore_job_name = N''   
,@file_retention_period = 1440   
,@monitor_server = N'ROCKAWAY'   
,@monitor_server_security_mode = 1   
,@copy_job_id = @LS_Secondary__CopyJobId OUTPUT   
,@restore_job_id = @LS_Secondary__RestoreJobId OUTPUT   
,@secondary_id = @LS_Secondary__SecondaryId OUTPUT ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
