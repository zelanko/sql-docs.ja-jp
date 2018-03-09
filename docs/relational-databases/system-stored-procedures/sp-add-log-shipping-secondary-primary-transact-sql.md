---
title: "sp_add_log_shipping_secondary_primary (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_add_log_shipping_secondary_primary_TSQL
- sp_add_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_log_shipping_secondary_primary
ms.assetid: bfbbbee2-c255-4a59-a963-47d6e980a8e2
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c83d0a0062f7f7affc19e91b929bb16831a8946d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
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
 [  **@primary_server**  =] '*primary_server*'  
 プライマリ インスタンスの名前、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ログ配布構成にします。 *primary_server*は**sysname** NULL にすることはできません。  
  
 [  **@primary_database**  =] '*primary_database*'  
 プライマリ サーバー上のデータベースの名前を指定します。 *primary_database*は**sysname**、既定値はありません。  
  
 [  **@backup_source_directory**  =] '*backup_source_directory*'  
 プライマリ サーバーのトランザクション ログ バックアップ ファイルが格納されているディレクトリ。 *backup_source_directory* is **nvarchar(500)** and cannot be NULL.  
  
 [  **@backup_destination_directory**  =] '*backup_destination_directory*'  
 バックアップ ファイルのコピー先となるセカンダリ サーバーのディレクトリ。 *backup_destination_directory*は**nvarchar (500)** NULL にすることはできません。  
  
 [ **@copy_job_name** = ] '*copy_job_name*'  
 使用する名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクション ログ バックアップをセカンダリ サーバーにコピーするために作成されているエージェント ジョブ。 *copy_job_name*は**sysname** NULL にすることはできません。  
  
 [ **@restore_job_name** = ] '*restore_job_name*'  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セカンダリ データベースにバックアップを復元するセカンダリ サーバー上のエージェント ジョブ。 *restore_job_name*は**sysname** NULL にすることはできません。  
  
 [  **@file_retention_period**  =] '*file_retention_period*'  
 分単位で指定されたパスのセカンダリ サーバーでバックアップ ファイルが保持される時間の長さ、@backup_destination_directoryパラメーターを削除する前にします。 *ヒストリは削除*は**int**、既定値は NULL です。 値 14420 は、指定されていない場合に使用されます。  
  
 [  **@monitor_server**  =] '*monitor_server*'  
 監視サーバーの名前を指定します。 *Monitor_server*は**sysname**、既定値はありません、NULL にすることはできません。  
  
 [  **@monitor_server_security_mode**  =] '*monitor_server_security_mode*'  
 監視サーバーへの接続に使用されるセキュリティ モード。  
  
 1 = Windows 認証です。  
  
 0 =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  
  
 *monitor_server_security_mode*は**ビット**NULL にすることはできません。  
  
 [  **@monitor_server_login**  =] '*monitor_server_login*'  
 監視サーバーへのアクセスに使用するアカウントのユーザー名を指定します。  
  
 [  **@monitor_server_password**  =] '*monitor_server_password*'  
 監視サーバーへのアクセスに使用するアカウントのパスワードを指定します。  
  
 [ **@copy_job_id** = ] '*copy_job_id*' OUTPUT  
 セカンダリ サーバーでのコピー ジョブに関連付けられた ID。 *copy_job_id*は**uniqueidentifier** NULL にすることはできません。  
  
 [ **@restore_job_id** = ] '*restore_job_id*' OUTPUT  
 セカンダリ サーバーでの復元ジョブに関連付けられた ID。 *restore_job_id*は**uniqueidentifier** NULL にすることはできません。  
  
 [  **@secondary_id**  =] '*secondary_id*' 出力  
 ログ配布構成におけるセカンダリ サーバーの ID。 *secondary_id*は**uniqueidentifier** NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_add_log_shipping_secondary_primary** must be run from the **master** database on the secondary server. このストアド プロシージャでは次の処理が行われます。  
  
1.  指定したプライマリ サーバーとプライマリ データベースのセカンダリ ID を生成する。  
  
2.  また、次の処理が行われます。  
  
    1.  セカンダリ ID のエントリを追加**log_shipping_secondary**指定された引数を使用します。  
  
    2.  無効になったセカンダリ ID のコピー ジョブを作成する。  
  
    3.  コピー ジョブ ID を設定、 **log_shipping_secondary**コピー ジョブのジョブ ID を入力します。  
  
    4.  無効になったセカンダリ ID の復元ジョブを作成する。  
  
    5.  復元ジョブの ID を設定、 **log_shipping_secondary**復元ジョブのジョブ ID を入力します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 この例を使用して、 **sp_add_log_shipping_secondary_primary**ストアド プロシージャをプライマリ データベースの情報を設定する[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]セカンダリ サーバーでします。  
  
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
  
## <a name="see-also"></a>参照  
 [ログ配布 &#40; についてSQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
