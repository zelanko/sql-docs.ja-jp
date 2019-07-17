---
title: sp_addpullsubscription_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addpullsubscription_agent
- sp_addpullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addpullsubscription_agent
ms.assetid: b9c2eaed-6d2d-4b78-ae9b-73633133180b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 220e21713935409d7d85ecd156524883dbbace08
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68022464"
---
# <a name="spaddpullsubscriptionagent-transact-sql"></a>sp_addpullsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
 
  トランザクション パブリケーションに対するプル サブスクリプションの同期で使用される、スケジュールされたエージェント ジョブを追加します。 このストアド プロシージャは、サブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addpullsubscription_agent [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]          , [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor = ] 'distributor' ]  
    [ , [ @distribution_db = ] 'distribution_db' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]  
    [ , [ @distributor_login = ] 'distributor_login' ]  
    [ , [ @distributor_password = ] 'distributor_password' ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @distribution_jobid = ] distribution_jobid OUTPUT ]  
    [ , [ @encrypted_distributor_password = ] encrypted_distributor_password ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port = ] ftp_port ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]  
    [ , [ @working_directory = ] 'working_directory' ]  
    [ , [ @use_ftp = ] 'use_ftp' ]  
    [ , [ @publication_type = ] publication_type ]  
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @offloadagent = ] 'remote_agent_activation' ]  
    [ , [ @offloadserver = ] 'remote_agent_server_name']  
    [ , [ @job_name = ] 'job_name' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'_` パブリッシャー データベースの名前です。 *publisher_db*は**sysname**既定値は NULL です。 *publisher_db* Oracle パブリッシャーでは無視されます。  
  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @subscriber = ] 'subscriber'` サブスクライバーの名前です。 *サブスクライバー* は **sysname** 、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。  
  
`[ @subscriber_db = ] 'subscriber_db'` サブスクリプション データベースの名前です。 *@subscriber_db* は **sysname** 、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` 同期するサブスクライバーに接続するときに使用するセキュリティ モードです。 *subscriber_security_mode*は**int、** 既定値は NULL です。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **1** Windows 認証を指定します。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。 ディストリビューション エージェントは、常に Windows 認証を使用してローカル サブスクライバーに接続します。 NULL 以外の値または**1**指定は、このパラメーターは、警告メッセージが返されます。  
  
`[ @subscriber_login = ] 'subscriber_login'` 同期するサブスクライバーに接続するときに使用するサブスクライバー ログインです。*subscriber_login*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。 このパラメーターの値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @subscriber_password = ] 'subscriber_password'` サブスクライバーのパスワードです。 *@subscriber_password* 場合は必須です *subscriber_security_mode* に設定されている **0** します。 *@subscriber_password* は **sysname** 、既定値は NULL です。 サブスクライバーのパスワードを使用する場合は自動的に暗号化します。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。 このパラメーターの値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @distributor = ] 'distributor'` ディストリビューターの名前です。 *ディストリビューター*は**sysname**、既定値で指定された値は*パブリッシャー*します。  
  
`[ @distribution_db = ] 'distribution_db'` ディストリビューション データベースの名前です。 *distribution_db*は**sysname**既定値は NULL です。  
  
`[ @distributor_security_mode = ] distributor_security_mode` 同期するときに、ディストリビューターに接続するときに使用するセキュリティ モードです。 *distributor_security_mode*は**int**、既定値は**1**します。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **1** Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` ディストリビューターに接続して同期するときに使用するディストリビューター ログインです。 *distributor_login* 場合は必須です *distributor_security_mode* に設定されている **0** します。 *distributor_login* は **sysname** 、既定値は NULL です。  
  
`[ @distributor_password = ] 'distributor_password'` ディストリビューターのパスワードです。 *distributor_password* 場合は必須です *distributor_security_mode* に設定されている **0** します。 *distributor_password* は **sysname** 、既定値は NULL です。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @optional_command_line = ] 'optional_command_line'` オプションのコマンド プロンプトは、ディストリビューション エージェントに提供されます。 たとえば、 **-definitionfile** C:\Distdef.txt または **- CommitBatchSize** 10。 *optional_command_line*は**nvarchar (4000)** 、既定値は空の文字列。  
  
`[ @frequency_type = ] frequency_type` ディストリビューション エージェントをスケジュールする頻度です。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2** (既定値)|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64**|自動開始|  
|**128**|定期的な|  
  
> [!NOTE]  
>  値を指定する**64**により、ディストリビューション エージェントが連続モードで実行します。 これは設定に対応、 **-継続的な**エージェントのパラメーター。 詳細については、「 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)」を参照してください。  
  
`[ @frequency_interval = ] frequency_interval` 設定した頻度に適用する値は、 *frequency_type*します。 *frequency_interval*は**int**、既定値は 1 です。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` ディストリビューション エージェントの日です。 このパラメーターが使用されるときに *frequency_type* に設定されている **32** (月単位)。 *frequency_relative_interval*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1** (既定値)|First|  
|**2**|第 2 週|  
|**4**|サードパーティ|  
|**8**|4 番目|  
|**16**|Last|  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は**1**します。  
  
`[ @frequency_subday = ] frequency_subday` 定義した期間中に再スケジュールするには、多くの場合、方法です。 *frequency_subday*は**int**値は次のいずれかを指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**1** (既定値)|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値は**1**します。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` ディストリビューション エージェントを最初のスケジュール設定する時刻、hhmmss 形式で指定として書式設定します。 *active_start_time_of_day*は**int**、既定値は**0**します。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` ディストリビューション エージェントが停止する時刻 hhmmss 形式で指定として書式設定、スケジュール設定します。 *active_end_time_of_day*は**int**、既定値は**0**します。  
  
`[ @active_start_date = ] active_start_date` ディストリビューション エージェントの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値は**0**します。  
  
`[ @active_end_date = ] active_end_date` ディストリビューション エージェントが停止した日付、スケジュールに yyyymmdd です。 *active_end_date*は**int**、既定値は**0**します。  
  
`[ @distribution_jobid = ] _distribution_jobidOUTPUT` このジョブのディストリビューション エージェントの ID です。 *distribution_jobid*は**binary (16)** 、既定値は null には、出力パラメーター。  
  
`[ @encrypted_distributor_password = ] encrypted_distributor_password` 設定*encrypted_distributor_password*現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` サブスクリプションを介した同期が可能かどうかは、[!INCLUDE[msCoName](../../includes/msconame-md.md)]同期マネージャーです。 *enabled_for_syncmgr*は**nvarchar (5)** 、既定値は FALSE。 場合**false**サブスクリプションが同期マネージャーに登録されません。 場合**true**、サブスクリプションは同期マネージャーに登録および起動しなくても同期できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。  
  
`[ @ftp_address = ] 'ftp_address'` 旧バージョンと互換性を保つのためです。  
  
`[ @ftp_port = ] ftp_port` 旧バージョンと互換性を保つのためです。  
  
`[ @ftp_login = ] 'ftp_login'` 旧バージョンと互換性を保つのためです。  
  
`[ @ftp_password = ] 'ftp_password'` 旧バージョンと互換性を保つのためです。  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'_` スナップショットの代替フォルダーの場所を指定します。 *alternate_snapshot_folder*は**nvarchar (255)** 、既定値は NULL です。  
  
`[ @working_directory = ] 'working_director'` パブリケーションのデータとスキーマ ファイルを格納するために使用する作業ディレクトリの名前です。 *working_directory*は**nvarchar (255)** 、既定値は NULL です。 名前は UNC 形式で指定する必要があります。  
  
`[ @use_ftp = ] 'use_ftp'` スナップショットを取得する標準のプロトコルの代わりに FTP の使用を指定します。 *@use_ftp* は **nvarchar (5)** 、既定値は FALSE。  
  
`[ @publication_type = ] publication_type` パブリケーションのレプリケーションの種類を指定します。 *publication_type*は、 **tinyint** 、既定値は**0**します。 場合**0**パブリケーションがトランザクションの種類。 場合**1**パブリケーションがスナップショットの種類。 場合**2**パブリケーションはマージの種類。  
  
`[ @dts_package_name = ] 'dts_package_name'` DTS パッケージの名前を指定します。 *dts_package_name*は、 **sysname**既定値は NULL です。 たとえば、`DTSPub_Package` というパッケージを指定するには、パラメーターを `@dts_package_name = N'DTSPub_Package'` と設定します。  
  
`[ @dts_package_password = ] 'dts_package_password'` 1 つを使用する必要がある場合、パッケージのパスワードを指定します。 *dts_package_password*は**sysname**既定値は NULL には、つまり、パッケージにパスワードがないです。  
  
> [!NOTE]  
>  場合は、パスワードを指定する必要があります*dts_package_name*を指定します。  
  
`[ @dts_package_location = ] 'dts_package_location'` パッケージの場所を指定します。 *dts_package_location*は、 **nvarchar (12)** 、既定値は**サブスクライバー**します。 パッケージの場所を指定できます**ディストリビューター**または**サブスクライバー**します。  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  リモート エージェントのアクティブ化は非推奨し、現在サポートされていません。 このパラメーターは、スクリプトの旧バージョンとの互換性を維持するためにのみサポートされます。 設定*remote_agent_activation*以外の値を**false**エラーが生成されます。  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  リモート エージェントのアクティブ化は非推奨し、現在サポートされていません。 このパラメーターは、スクリプトの旧バージョンとの互換性を維持するためにのみサポートされます。 設定*remote_agent_server_name* NULL 以外の値にエラーが生成されます。  
  
`[ @job_name = ] 'job_name'` 既存のエージェント ジョブの名前です。 *job_name* は **sysname** 既定値は NULL です。 新しく作成されたジョブ (既定値) の代わりに、既存のジョブを使用して、サブスクリプションを同期するときにのみこのパラメーターを指定します。 メンバーになっていない場合、 **sysadmin**するを指定する必要があります固定サーバー ロール、 *job_login*と*job_password*を指定すると*job_name*.  
  
`[ @job_login = ] 'job_login'` エージェントを実行する Windows アカウントのログインです。 *job_login*は**nvarchar (257)** 、既定値はありません。 この Windows アカウントはサブスクライバーへのエージェント接続で常に使用されます。  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password* は **sysname** 、既定値はありません。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addpullsubscription_agent**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-a_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addpullsubscription_agent**します。  
  
## <a name="see-also"></a>関連項目  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
