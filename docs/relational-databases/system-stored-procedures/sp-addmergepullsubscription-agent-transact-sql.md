---
title: sp_addmergepullsubscription_agent (トランザクション-SQL) |マイクロソフトドキュメント
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
ms.openlocfilehash: 07cc514d615c86a90dcf37fbd4748c3ab1776f06
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528976"
---
# <a name="sp_addmergepullsubscription_agent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  マージ パブリケーションに対するプル サブスクリプションの同期化をスケジュールするための、新しいエージェント ジョブを追加します。 このストアド プロシージャは、サブスクリプション データベースのサブスクライバで実行されます。  
  
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
`[ @name = ] 'name'`エージェントの名前です。 *名前*は**sysname**で、デフォルトは NULL です。  
  
`[ @publisher = ] 'publisher'`パブリッシャ サーバーの名前です。 *発行元*は**sysname**で、デフォルトはありません。  
  
`[ @publisher_db = ] 'publisher_db'`パブリッシャー データベースの名前です。 *publisher_db*は**sysname**で、デフォルトはありません。  
  
`[ @publication = ] 'publication'`パブリケーションの名前です。 *パブリケーション*は**sysname**で、デフォルトはありません。  
  
`[ @publisher_security_mode = ] publisher_security_mode`同期時にパブリッシャに接続するときに使用するセキュリティ モードです。 *publisher_security_mode*は**int**で、デフォルトは 1 です。 **0**の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、認証を指定します。 **1**の場合は、Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'`同期するときにパブリッシャに接続するときに使用するログインです。 *publisher_login*は**sysname**で、デフォルトは NULL です。  
  
`[ @publisher_password = ] 'publisher_password'`パブリッシャーに接続するときに使用するパスワードです。 *publisher_password*は**sysname**で、デフォルトは NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @publisher_encrypted_password = ]publisher_encrypted_password`*publisher_encrypted_password*の設定はサポートされなくなりました。 この**ビット**パラメータを**1**に設定しようとすると、エラーが発生します。  
  
`[ @subscriber = ] 'subscriber'`サブスクライバーの名前です。 *サブスクライバ*は**sysname**で、デフォルトは NULL です。  
  
`[ @subscriber_db = ] 'subscriber_db'`サブスクリプション データベースの名前です。 *subscriber_db*は**sysname**で、デフォルトは NULL です。  
  
`[ @subscriber_security_mode = ] subscriber_security_mode`同期時にサブスクライバーに接続するときに使用するセキュリティ モードです。 *subscriber_security_mode*は**int**で、デフォルトは 1 です。 **0**の場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、認証を指定します。 **1**の場合は、Windows 認証を指定します。  
  
> [!NOTE]  
>  このパラメーターは非推奨となっており、スクリプトの下位互換性のために維持されています。 マージ エージェントは、常に Windows 認証を使用してローカル サブスクライバに接続します。 このパラメーターに値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @subscriber_login = ] 'subscriber_login'`同期時にサブスクライバーに接続するときに使用するサブスクライバー ログインです。 *subscriber_security_mode*が**0**に設定されている場合は *、subscriber_login*が必要です。 *subscriber_login*は**sysname**で、デフォルトは NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨となっており、スクリプトの下位互換性のために維持されています。 このパラメーターに値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @subscriber_password = ] 'subscriber_password'`認証用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のサブスクライバー パスワードです。 *subscriber_security_mode*が**0**に設定されている場合は *、subscriber_password*が必要です。 *subscriber_password*は**sysname**で、デフォルトは NULL です。  
  
> [!NOTE]  
>  このパラメーターは非推奨となっており、スクリプトの下位互換性のために維持されています。 このパラメーターに値を指定すると、警告メッセージが返されますが、値は無視されます。  
  
`[ @distributor = ] 'distributor'`ディストリビュータの名前です。 *ディストリビュータ*は**sysname**で、デフォルトでは*パブリッシャ*が使用されます。つまり、パブリッシャーはディストリビューターでもあります。  
  
`[ @distributor_security_mode = ] distributor_security_mode`同期時にディストリビュータに接続するときに使用するセキュリティ モードです。 *distributor_security_mode*は**int**で、デフォルトは 0 です。 **0** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は認証を指定します。 **1 は**Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @distributor_login = ] 'distributor_login'`同期時にディストリビュータに接続するときに使用するディストリビュータ ログインです。 *distributor_security_mode*が**0**に設定されている場合は *、distributor_login*が必要です。 *distributor_login*は**sysname**で、既定値は NULL です。  
  
`[ @distributor_password = ] 'distributor_password'`ディストリビュータのパスワードです。 *distributor_security_mode*が**0**に設定されている場合は *、distributor_password*が必要です。 *distributor_password*は**sysname**で、デフォルトは NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @encrypted_password = ] encrypted_password`*encrypted_password*設定はサポートされなくなりました。 この**ビット**パラメータを**1**に設定しようとすると、エラーが発生します。  
  
`[ @frequency_type = ] frequency_type`マージ エージェントのスケジュールを設定する頻度です。 *frequency_type*は**int**であり、次のいずれかの値を指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回|  
|**2**|オン デマンド|  
|**4**|毎日|  
|**8**|週単位|  
|**16**|月単位|  
|**32**|月単位の相対値|  
|**64**|Autostart|  
|**128**|繰り返し|  
|NULL (デフォルト)||  
  
> [!NOTE]  
>  **値 64**を指定すると、マージ エージェントは連続モードで実行されます。 これはエージェントの **-連続**パラメータの設定に対応します。 詳細については、「 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)」を参照してください。  
  
`[ @frequency_interval = ] frequency_interval`マージ エージェントが実行される日または曜日。 *frequency_interval*は**int**であり、これらの値のいずれかになります。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|土曜日|  
|**2**|月曜日|  
|**3**|Tuesday|  
|**4**|水曜日|  
|**5**|Thursday|  
|**6**|金曜日|  
|**7**|土曜日|  
|**8**|日|  
|**9**|平日|  
|"**10**"|週末|  
|NULL (デフォルト)||  
  
`[ @frequency_relative_interval = ] frequency_relative_interval`マージ エージェントの日付です。 このパラメーターは *、frequency_type*が**32** (月単位の相対) に設定されている場合に使用されます。 *frequency_relative_interval*は**int**であり、これらの値のいずれかになります。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First (先頭へ)|  
|**2**|秒|  
|**4**|第 3 週|  
|**8**|4 番目|  
|**16**|Last (最後へ)|  
|NULL (デフォルト)||  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor`frequency_typeで使用される定期的な要素*です*。 *frequency_recurrence_factor*は**int**で、既定値は NULL です。  
  
`[ @frequency_subday = ] frequency_subday`定義された期間にスケジュールを変更する頻度です。 *frequency_subday*は**int**であり、これらの値のいずれかになります。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 度|  
|**2**|秒|  
|**4**|分|  
|**8**|時|  
|NULL (デフォルト)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval`*frequency_subday*の間隔です。 *frequency_subday_interval*は**int**で、デフォルトは NULL です。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day`マージ エージェントが最初にスケジュールされる時刻で、HHMMSS 形式です。 *active_start_time_of_day*は**int**で、デフォルトは NULL です。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day`マージ エージェントがスケジュールを停止する時刻で、HHMMSS 形式です。 *active_end_time_of_day*は**int**で、デフォルトは NULL です。  
  
`[ @active_start_date = ] active_start_date`マージ エージェントが最初にスケジュールされる日付で、YYYYMMDD 形式です。 *active_start_date*は**int**で、既定値は NULL です。  
  
`[ @active_end_date = ] active_end_date`マージ エージェントがスケジュールを停止する日付で、YYYYMMDD 形式です。 *active_end_date*は**int**で、既定値は NULL です。  
  
`[ @optional_command_line = ] 'optional_command_line'`マージ エージェントに提供される省略可能なコマンド プロンプトです。 *optional_command_line*は**nvarchar(255) で**、デフォルトは ' ' です。 追加のパラメーターをマージ エージェントに提供する場合に使用できます。たとえば、次の例では、既定のクエリ タイムアウトを `600` 秒に増やします。  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
`[ @merge_jobid = ] merge_jobid`ジョブ ID の出力パラメーターです。 *merge_jobid*は**バイナリ(16)で**、デフォルトは NULL です。  
  
`[ @enabled_for_syncmgr = ] 'enabled_for_syncmgr'`Windows 同期マネージャを使用してサブスクリプションを同期できるかどうかを指定します。 *enabled_for_syncmgr*は**nvarchar(5) で**、デフォルトは FALSE です。 **false の**場合、サブスクリプションは同期マネージャに登録されません。 **true**の場合、サブスクリプションは同期マネージャに登録され、を起動[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]せずに同期できます。  
  
`[ @ftp_address = ] 'ftp_address'`下位互換性のためだけに。  
  
`[ @ftp_port = ] ftp_port`下位互換性のためだけに。  
  
`[ @ftp_login = ] 'ftp_login'`下位互換性のためだけに。  
  
`[ @ftp_password = ] 'ftp_password'`下位互換性のためだけに。  
  
`[ @alt_snapshot_folder = ] 'alternate_snapshot_folder'`スナップショット ファイルの取得元の場所を指定します。 *alternate_snapshot_folder*は**nvarchar(255) で**、デフォルトは NULL です。 NULL の場合、スナップショット ファイルは、パブリッシャーによって指定された既定の場所から取得されます。  
  
`[ @working_directory = ] 'working_directory'`スナップショット ファイルの転送に FTP を使用する場合に、パブリケーションのデータ ファイルとスキーマ ファイルを一時的に格納するために使用される作業ディレクトリの名前です。 *working_directory*は**nvarchar(255) で**、デフォルトは NULL です。  
  
`[ @use_ftp = ] 'use_ftp'`スナップショットを取得するための一般的なプロトコルの代わりに FTP を使用することを指定します。 *use_ftp*は**nvarchar(5) で**、デフォルトは FALSE です。  
  
`[ @reserved = ] 'reserved'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @use_interactive_resolver = ] 'use_interactive_resolver' ]`対話的な解決を可能にするすべてのアーティクルの競合を解決するために、対話的なリゾルバを使用します。 *use_interactive_resolver*は**nvarchar(5) で**、デフォルトは FALSE です。  
  
`[ @offloadagent = ] 'remote_agent_activation'`
 > [!NOTE]  
>  リモート エージェントのアクティブ化は非推奨になりました。 このパラメーターは、スクリプトの下位互換性を維持するためだけにサポートされます。 *remote_agent_activation*を**false**以外の値に設定すると、エラーが発生します。  
  
`[ @offloadserver = ] 'remote_agent_server_name'`
 > [!NOTE]  
>  リモート エージェントのアクティブ化は非推奨になりました。 このパラメーターは、スクリプトの下位互換性を維持するためだけにサポートされます。 *remote_agent_server_nameを*NULL 以外の値に設定すると、エラーが発生します。  
  
`[ @job_name = ] 'job_name' ]`既存のエージェント ジョブの名前です。 *job_name*は**sysname**で、既定値は NULL です。 このパラメーターは、新しく作成されたジョブ (デフォルト) ではなく、既存のジョブを使用してサブスクリプションを同期する場合にのみ指定されます。 **sysadmin**固定サーバー ロールのメンバでない場合は、job_name*を指定*するときに*job_login*と*job_password*を指定する必要があります。  
  
`[ @dynamic_snapshot_location = ] 'dynamic_snapshot_location' ]`フィルター処理されたデータ スナップショットを使用する場合に、スナップショット ファイルの読み取り元となるフォルダーへのパス。 *dynamic_snapshot_location*は**nvarchar(260) で**、デフォルトは NULL です。 詳しくは、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。  
  
`[ @use_web_sync = ] use_web_sync`Web 同期が有効であることを示します。 *use_web_sync*は**ビット**で、デフォルトは 0 です。 **1**は、HTTP を使用してインターネット経由でプル サブスクリプションを同期できることを指定します。  
  
`[ @internet_url = ] 'internet_url'`レプリケーション・リスナーの場所です (REPLISAPI。DLL) を使用して Web 同期を実行します。 *internet_url*は**nvarchar(260) で**、デフォルトは NULL です。 *internet_url*は、完全修飾 URL です`http://server.domain.com/directory/replisapi.dll`。 サーバーの構成で、リッスンするポートがポート 80 以外の場合は、`http://server.domain.com:portnumber/directory/replisapi.dll` の形式のポート番号も指定する必要があります。ここで `portnumber` はポートを表します。  
  
`[ @internet_login = ] 'internet_login'`HTTP 基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するログインです。 *internet_login*は**sysname**で、デフォルトは NULL です。  
  
`[ @internet_password = ] 'internet_password'`HTTP 基本認証を使用して Web 同期をホストしている Web サーバーに接続するときにマージ エージェントが使用するパスワードです。 *internet_password*は**nvarchar(524) で**、デフォルト値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
`[ @internet_security_mode = ] internet_security_mode`HTTPS を使用した Web 同期中に Web サーバーに接続するときにマージ エージェントが使用する認証方法です。 *internet_security_mode*は**int**で、これらの値のいずれかになります。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|基本認証が使用されます。|  
|**1** (既定値)|Windows 統合認証を使用|  
  
> [!NOTE]  
>  Web 同期では基本認証を使用することをお勧めします。 Web 同期を使用するには、Web サーバーへの TLS 接続を確立する必要があります。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
`[ @internet_timeout = ] internet_timeout`Web 同期要求の有効期限が切れるまでの時間 (秒単位) です。 *internet_timeout*は**int**で、デフォルトは**300**秒です。  
  
`[ @hostname = ] 'hostname'`パラメーター化されたフィルターの WHERE 句でこの関数を使用する場合は、HOST_NAME() の値をオーバーライドします。 *ホスト名*は**sysname**で、デフォルトは NULL です。  
  
`[ @job_login = ] 'job_login'`エージェントが実行される Windows アカウントのログインです。 *job_login*は**nvarchar(257) で**、デフォルトはありません。 この Windows アカウントは、サブスクライバーへのエージェント接続、および Windows 統合認証を使用する場合のディストリビューターとパブリッシャーへの接続に常に使用されます。  
  
`[ @job_password = ] 'job_password'`エージェントが実行される Windows アカウントのパスワードです。 *job_password*は**sysname**で、デフォルトはありません。  
  
> [!IMPORTANT]  
>  認証情報をスクリプト ファイルに格納しないでください。 セキュリティを最も高めるには、実行時にログイン名とパスワードを指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addmergepullsubscription_agent**はマージ レプリケーションで使用され[、sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)と同様の機能を使用します。  
  
 **sp_addmergepullsubscription_agent**の実行時にセキュリティ設定を正しく指定する方法の例については、「[プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 sp_addmergepullsubscription_agent実行できるのは、固定サーバー ロール**sysadmin**または固定データベース ロール**db_owner**メンバー**のみです。**  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [&#40;の&#41;を&#40;sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
