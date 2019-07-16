---
title: sp_addmergepullsubscription_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_agent
- sp_addmergepullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addmergepullsubscription_agent
ms.assetid: a2f4b086-078d-49b5-8971-8a1e3f6a6feb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8bfa9ff0683f67a1d38aeb17bccd0cfc1443d6d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117959"
---
# <a name="spaddmergepullsubscriptionagent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションに対するプル サブスクリプションの同期化をスケジュールするための、新しいエージェント ジョブを追加します。 このストアド プロシージャは、サブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergepullsubscription_agent [ [ @name = ] 'name' ]   
        , [ @publisher = ] 'publisher'   
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication =] 'publication'   
    [ , [ @publisher_security_mod e= ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @publisher_encrypted_password = ] publisher_encrypted_password ]   
    [ , [ @subscriber = ] 'subscriber' ]   
    [ , [ @subscriber_db = ] 'subscriber_db' ]   
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]   
    [ , [ @subscriber_login = ] 'subscriber_login' ]   
    [ , [ @subscriber_password= ] 'subscriber_password' ]   
    [ , [ @distributor = ] 'distributor' ]   
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @encrypted_password = ] encrypted_password ]   
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
    [ , [ @optional_command_line = ] 'optional_command_line' ]   
    [ , [ @merge_jobid = ] merge_jobid ]   
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]    
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @working_directory = ] 'working_directory' ]   
    [ , [ @use_ftp = ] 'use_ftp' ]   
    [ , [ @reserved = ] 'reserved' ]   
    [ , [ @use_interactive_resolver = ] 'use_interactive_resolver' ]   
    [ , [ @offloadagent = ] 'remote_agent_activation' ]   
    [ , [ @offloadserver = ] 'remote_agent_server_name']   
    [ , [ @job_name = ] 'job_name' ]   
    [ , [ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]  
    [ , [ @use_web_sync = ] use_web_sync ]  
        [ , [ @internet_url = ] 'internet_url' ]  
    [ , [ @internet_login = ] 'internet_login' ]  
        [ , [ @internet_password = ] 'internet_password' ]  
    [ , [ @internet_security_mode = ] internet_security_mode ]  
        [ , [ @internet_timeout = ] internet_timeout ]  
    [ , [ @hostname = ] 'hostname' ]  
        [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @name = ] 'name'` エージェントの名前です。 *名前* は **sysname** 、既定値は NULL です。  
  
`[ @publisher = ] 'publisher'` パブリッシャー サーバーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'` パブリッシャー データベースの名前です。 *publisher_db* は **sysname** 、既定値はありません。  
  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @publisher_security_mode = ] publisher_security_mode` 同期するときに、パブリッシャーに接続するときに使用するセキュリティ モードです。 *publisher_security_mode*は**int**、既定値は 1 です。 場合**0**を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 場合**1**、Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` パブリッシャーに接続して同期するときに使用するログインです。 *publisher_login* は **sysname** 、既定値は NULL です。  
  
`[ @publisher_password = ] 'publisher_password'` パブリッシャーに接続するときに、パスワードが使用されます。 *publisher_password* は **sysname** 、既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password` 設定*publisher_encrypted_password*現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
`[ @subscriber = ] 'subscriber'` サブスクライバーの名前です。 *サブスクライバー* は **sysname** 、既定値は NULL です。  
  
`[ @subscriber_db = ] 'subscriber_db'` サブスクリプション データベースの名前です。 *@subscriber_db* は **sysname** 、既定値は NULL です。  
  
`[ @subscriber_security_mode = ] subscriber_security_mode` 同期するサブスクライバーに接続するときに使用するセキュリティ モードです。 *subscriber_security_mode*は**int**、既定値は 1 です。 場合**0**を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 場合**1**、Windows 認証を指定します。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。 マージ エージェントは、常に Windows 認証を使用してローカル サブスクライバーに接続します。 このパラメーターの値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @subscriber_login = ] 'subscriber_login'` 同期するサブスクライバーに接続するときに使用するサブスクライバー ログインです。 *subscriber_login* 場合は必須です *subscriber_security_mode* に設定されている **0** します。 *subscriber_login* は **sysname** 、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。 このパラメーターの値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @subscriber_password = ] 'subscriber_password'` サブスクライバーのパスワードの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 *@subscriber_password* 場合は必須です *subscriber_security_mode* に設定されている **0** します。 *@subscriber_password* は **sysname** 、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。 このパラメーターの値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @distributor = ] 'distributor'` ディストリビューターの名前です。 *ディストリビューター* は **sysname** 、既定値は *パブリッシャー*; は、パブリッシャーがディストリビューターでも。  
  
`[ @distributor_security_mode = ] distributor_security_mode` 同期するときに、ディストリビューターに接続するときに使用するセキュリティ モードです。 *distributor_security_mode*は**int**、既定値は 0。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **1** Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'` ディストリビューターに接続して同期するときに使用するディストリビューター ログインです。 *distributor_login* 場合は必須です *distributor_security_mode* に設定されている **0** します。 *distributor_login* は **sysname** 、既定値は NULL です。  
  
`[ @distributor_password = ] 'distributor_password'` ディストリビューターのパスワードです。 *distributor_password* 場合は必須です *distributor_security_mode* に設定されている **0** します。 *distributor_password* は **sysname** 、既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @encrypted_password = ] encrypted_password` 設定*encrypted_password*現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
`[ @frequency_type = ] frequency_type` マージ エージェントをスケジュールする頻度です。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64**|自動開始|  
|**128**|定期的な|  
|NULL (既定値)||  
  
> [!NOTE]  
>  値を指定する**64**により、マージ エージェントを連続モードで実行します。 これは設定に対応、 **-継続的な**エージェントのパラメーター。 詳細については、「 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)」を参照してください。  
  
`[ @frequency_interval = ] frequency_interval` マージ エージェントを実行する曜日または日付。 *frequency_interval*は**int**、これらの値のいずれかを指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**1**|日曜日|  
|**2**|月曜日|  
|**3**|火曜日|  
|**4**|水曜日|  
|**5**|木曜日|  
|**6**|金曜日|  
|**7**|土曜日|  
|**8**|Day|  
|**9**|平日|  
|"**10**"|週末の曜日|  
|NULL (既定値)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` マージ エージェントの日です。 このパラメーターが使用されるときに *frequency_type* に設定されている **32** (月単位)。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|サードパーティ|  
|**8**|4 番目|  
|**16**|Last|  
|NULL (既定値)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
`[ @frequency_subday = ] frequency_subday` 定義した期間中に再スケジュールするには、多くの場合、方法です。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (既定値)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` マージ エージェントを最初のスケジュール設定する時刻、hhmmss 形式で指定として書式設定します。 *active_start_time_of_day* は **int** 、既定値は NULL です。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` マージ エージェントが停止する時刻 hhmmss 形式で指定として書式設定、スケジュール設定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
`[ @active_start_date = ] active_start_date` マージ エージェントの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値は NULL です。  
  
`[ @active_end_date = ] active_end_date` マージ エージェントが停止した日付、スケジュールに yyyymmdd です。 *active_end_date*は**int**、既定値は NULL です。  
  
`[ @optional_command_line = ] 'optional_command_line'` マージ エージェントに用意されているオプションのコマンド プロンプトです。 *optional_command_line*は**nvarchar (255)** 、既定値は '' です。 追加のパラメーターをマージ エージェントに提供する場合に使用できます。たとえば、次の例では、既定のクエリ タイムアウトを `600` 秒に増やします。  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid` ジョブ ID の出力パラメーターです。 *merge_jobid*は**binary (16)** 、既定値は NULL です。  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'` Windows 同期マネージャーを使用できる、サブスクリプションに同期するかどうかを指定します。 *enabled_for_syncmgr*は**nvarchar (5)** 、既定値は FALSE。 場合**false**サブスクリプションが同期マネージャーに登録されません。 場合**true**、サブスクリプションは同期マネージャーに登録および起動しなくても同期できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。  
  
`[ @ftp_address = ] 'ftp_address'` 旧バージョンと互換性を保つのためです。  
  
`[ @ftp_port = ] ftp_port` 旧バージョンと互換性を保つのためです。  
  
`[ @ftp_login = ] 'ftp_login'` 旧バージョンと互換性を保つのためです。  
  
`[ @ftp_password = ] 'ftp_password'` 旧バージョンと互換性を保つのためです。  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'` スナップショット ファイルを取得する元の場所を指定します。 *alternate_snapshot_folder*は**nvarchar (255)** 、既定値は NULL です。 NULL の場合、スナップショット ファイルは、発行元によって指定された既定の場所から取得します。  
  
`[ @working_directory = ] 'working_directory'` FTP を使用してスナップショット ファイルを転送する場合、パブリケーションのデータとスキーマ ファイルを一時的に格納するために使用する作業ディレクトリの名前です。 *working_directory*は**nvarchar (255)** 、既定値は NULL です。  
  
`[ @use_ftp = ] 'use_ftp'` スナップショットを取得する一般的なプロトコルの代わりに FTP を使用して指定します。 *@use_ftp* は **nvarchar (5)** 、既定値は FALSE。  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]` 対話型の解決を許可するすべてのアーティクルの競合を解決するのにには、インタラクティブ競合回避モジュールを使用します。 *use_interactive_resolver* は **nvarchar (5)** 、既定値は FALSE。  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  リモート エージェントのアクティブ化は非推奨し、現在サポートされていません。 このパラメーターは、スクリプトの旧バージョンとの互換性を維持するためにのみサポートされます。 設定*remote_agent_activation*以外の値を**false**エラーが生成されます。  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  リモート エージェントのアクティブ化は非推奨し、現在サポートされていません。 このパラメーターは、スクリプトの旧バージョンとの互換性を維持するためにのみサポートされます。 設定*remote_agent_server_name* NULL 以外の値にエラーが生成されます。  
  
`[ @job_name = ] 'job_name' ]` 既存のエージェント ジョブの名前です。 *job_name* は **sysname** 既定値は NULL です。 新しく作成されたジョブ (既定値) の代わりに、既存のジョブを使用して、サブスクリプションを同期するときにのみこのパラメーターを指定します。 メンバーになっていない場合、 **sysadmin**するを指定する必要があります固定サーバー ロール、 *job_login*と*job_password*を指定すると*job_name*.  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]` 場所、スナップショット ファイルが読み取られる場合からフィルター選択されたデータ スナップショット フォルダーへのパスでは、使用します。 *dynamic_snapshot_location*は**nvarchar (260)** 、既定値は NULL です。 詳しくは、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。  
  
`[ @use_web_sync = ] use_web_sync` Web 同期が有効になっていることを示します。 *@use_web_sync*は**ビット**、既定値は 0。 **1** HTTP を使用してインターネット経由でプル サブスクリプションを同期できることを指定します。  
  
`[ @internet_url = ] 'internet_url'` レプリケーション リスナー (REPLISAPI の場所はします。DLL) Web 同期します。 *internet_url*は**nvarchar (260)** 、既定値は NULL です。 *internet_url*形式での完全修飾 URL は、`http://server.domain.com/directory/replisapi.dll`します。 サーバーの構成で、リッスンするポートがポート 80 以外の場合は、`http://server.domain.com:portnumber/directory/replisapi.dll` の形式のポート番号も指定する必要があります。ここで `portnumber` はポートを表します。  
  
`[ @internet_login = ] 'internet_login'` HTTP 基本認証を使用して Web 同期をホストしている Web サーバーに接続するときに、マージ エージェントが使用するログインをします。 *internet_login* は **sysname** 、既定値は NULL です。  
  
`[ @internet_password = ] 'internet_password'` HTTP 基本認証を使用して Web 同期をホストしている Web サーバーに接続するときに、マージ エージェントが使用するパスワード。 *internet_password*は**nvarchar (524)** 既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode` HTTPS を使用して Web 同期中に、Web サーバーに接続するときに、マージ エージェントで使用する認証方法。 *internet_security_mode*は**int**これらの値のいずれかを指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**0**|基本認証を使用します。|  
|**1** (既定値)|Windows 統合認証を使用|  
  
> [!NOTE]  
>  Web 同期で基本認証を使用することをお勧めします。 Web 認証を使用するには、Web サーバーに SSL で接続する必要があります。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
`[ @internet_timeout = ] internet_timeout` Web 同期要求の有効期限が切れる前に、秒の時間の長さです。 *internet_timeout*は**int**、既定値は**300**秒。  
  
`[ @hostname = ] 'hostname'` この関数はパラメーター化されたフィルターの WHERE 句で使用すると、HOST_NAME() の値をオーバーライドします。 *ホスト名* は **sysname** 、既定値は NULL です。  
  
`[ @job_login = ] 'job_login'` エージェントを実行する Windows アカウントのログインです。 *job_login*は**nvarchar (257)** 、既定値はありません。 Windows 統合認証を使用する場合は、この Windows アカウントが、サブスクライバーへのエージェント接続と、ディストリビューターとパブリッシャーへの接続を常に使用します。  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password* は **sysname** 、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルでは、認証情報を格納しないでください。 安全性を高めるためには、ログイン名とパスワードを実行時に指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addmergepullsubscription_agent**はマージ レプリケーションで使用してと同様の機能を使用して[sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。  
  
 正しく実行するときにセキュリティ設定を指定する方法の例については**sp_addmergepullsubscription_agent**を参照してください[プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergepullsubscription_agent**します。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
