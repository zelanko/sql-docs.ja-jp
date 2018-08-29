---
title: sp_addmergepullsubscription_agent (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addmergepullsubscription_agent
- sp_addmergepullsubscription_agent_TSQL
helpviewer_keywords:
- sp_addmergepullsubscription_agent
ms.assetid: a2f4b086-078d-49b5-8971-8a1e3f6a6feb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 86af98d30aa9c892472b4226f30dafd63531cc21
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43019607"
---
# <a name="spaddmergepullsubscriptionagent-transact-sql"></a>sp_addmergepullsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションに対するプル サブスクリプションの同期化をスケジュールするための、新しいエージェント ジョブを追加します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
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
 [ **@name =** ] **'***name***'**  
 エージェントの名前を指定します。 *名前*は**sysname**、既定値は NULL です。  
  
 [  **@publisher =** ] **'***パブリッシャー***'**  
 パブリッシャー サーバーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db =** ] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@publication =** ] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@publisher_security_mode =** ] *publisher_security_mode*  
 パブリッシャーへ接続して同期するときに使用するセキュリティ モードを指定します。 *publisher_security_mode*は**int**、既定値は 1 です。 場合**0**を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 場合**1**、Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@publisher_login =** ] **'***publisher_login***'**  
 パブリッシャーへ接続して同期するときに使用するログインを指定します。 *publisher_login*は**sysname**、既定値は NULL です。  
  
 [  **@publisher_password =** ] **'***publisher_password***'**  
 パブリッシャーへの接続時に使用するパスワードを指定します。 *publisher_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [  **@publisher_encrypted_password =** ]*publisher_encrypted_password*  
 設定*publisher_encrypted_password*現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
 [  **@subscriber =** ] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_db =** ] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_security_mode =** ] *subscriber_security_mode*  
 サブスクライバーへ接続して同期するときに使用するセキュリティ モードを指定します。 *subscriber_security_mode*は**int**、既定値は 1 です。 場合**0**を指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 場合**1**、Windows 認証を指定します。  
  
> [!NOTE]  
>  このパラメーターは、スクリプトの下位互換性を確保するために用意されているものであり、非推奨とされます。 マージ エージェントは常に Windows 認証を使用してローカル サブスクライバーに接続します。 このパラメーターに値を指定した場合は、警告メッセージが返されますが、値は無視されます。  
  
 [  **@subscriber_login =** ] **'***subscriber_login***'**  
 サブスクライバーへ接続して同期するときに使用するサブスクライバー ログインを指定します。 *subscriber_login*場合は必須です*subscriber_security_mode*に設定されている**0**します。 *subscriber_login*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは、スクリプトの下位互換性を確保するために用意されているものであり、非推奨とされます。 このパラメーターに値を指定した場合は、警告メッセージが返されますが、値は無視されます。  
  
 [  **@subscriber_password =** ] **'***@subscriber_password***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証で使用するサブスクライバーのパスワードを指定します。 *@subscriber_password*場合は必須です*subscriber_security_mode*に設定されている**0**します。 *@subscriber_password*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  このパラメーターは、スクリプトの下位互換性を確保するために用意されているものであり、非推奨とされます。 このパラメーターに値を指定した場合は、警告メッセージが返されますが、値は無視されます。  
  
 [  **@distributor =** ] **'***ディストリビューター***'**  
 ディストリビューターの名前です。 *ディストリビューター*は**sysname**、既定値は*パブリッシャー*; は、パブリッシャーがディストリビューターでも。  
  
 [  **@distributor_security_mode =** ] *distributor_security_mode*  
 ディストリビューターへ接続して同期するときに使用するセキュリティ モードを指定します。 *distributor_security_mode*は**int**、既定値は 0。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **1** Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@distributor_login =** ] **'***distributor_login***'**  
 ディストリビューターへ接続して同期するときに使用するディストリビューター ログインを指定します。 *distributor_login*場合は必須です*distributor_security_mode*に設定されている**0**します。 *distributor_login*は**sysname**、既定値は NULL です。  
  
 [  **@distributor_password =** ] **'***distributor_password***'**  
 ディストリビューターのパスワードです。 *distributor_password*場合は必須です*distributor_security_mode*に設定されている**0**します。 *distributor_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [  **@encrypted_password =** ] *encrypted_password*  
 設定*encrypted_password*現在サポートされていません。 これを設定しようとしています。**ビット**パラメーターを**1** 、エラーが発生します。  
  
 [  **@frequency_type =** ] *frequency_type*  
 マージ エージェントをスケジュールに組み込む頻度を指定します。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64**|自動的に起動|  
|**128**|定期的|  
|NULL (既定値)||  
  
> [!NOTE]  
>  値を指定する**64**により、マージ エージェントを連続モードで実行します。 これは設定に対応、 **-継続的な**エージェントのパラメーター。 詳細については、「 [Replication Merge Agent](../../relational-databases/replication/agents/replication-merge-agent.md)」を参照してください。  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 マージ エージェントを実行する日を指定します。 *frequency_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|日曜日|  
|**2**|月曜日|  
|**3**|火曜日|  
|**4**|水曜日|  
|**5**|木曜日|  
|**6**|金曜日|  
|**7**|土曜日|  
|**8**|日|  
|**9**|平日|  
|"**10**"|週末の曜日|  
|NULL (既定値)||  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 マージ エージェントを実行する日付です。 このパラメーターが使用されるときに*frequency_type*に設定されている**32** (月単位)。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
|NULL (既定値)||  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を指定します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (既定値)||  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 マージ エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 マージ エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
 [ **@active_start_date =** ] *active_start_date*  
 マージ エージェントを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は NULL です。  
  
 [ **@active_end_date =** ] *active_end_date*  
 マージ エージェントのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は NULL です。  
  
 [  **@optional_command_line =** ] **'***optional_command_line***'**  
 マージ エージェントに提供されるコマンド プロンプトを指定します (省略可能)。 *optional_command_line*は**nvarchar (255)**、既定値は '' です。 追加のパラメーターをマージ エージェントに提供する場合に使用できます。たとえば、次の例では、既定のクエリ タイムアウトを `600` 秒に増やします。  
  
```  
@optional_command_line = N'-QueryTimeOut 600'  
```  
  
 [  **@merge_jobid =** ] *merge_jobid*  
 ジョブ ID の出力パラメーターを指定します。 *merge_jobid*は**binary (16)**、既定値は NULL です。  
  
 [  **@enabled_for_syncmgr =** ] **'***enabled_for_syncmgr***'**  
 Windows 同期マネージャーを介したサブスクリプションの同期が可能かどうかを指定します。 *enabled_for_syncmgr*は**nvarchar (5)**、既定値は FALSE。 場合**false**サブスクリプションが同期マネージャーに登録されません。 場合**true**、サブスクリプションは同期マネージャーに登録および起動しなくても同期できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。  
  
 [  **@ftp_address =** ] **'***ftp_address***'**  
 これは旧バージョンとの互換性のためにだけ用意されています。  
  
 [  **@ftp_port =** ] *ftp_port*  
 これは旧バージョンとの互換性のためにだけ用意されています。  
  
 [  **@ftp_login =** ] **'***ftp_login***'**  
 これは旧バージョンとの互換性のためにだけ用意されています。  
  
 [  **@ftp_password =** ] **'***ftp_password***'**  
 これは旧バージョンとの互換性のためにだけ用意されています。  
  
 [  **@alt_snapshot_folder =** ] **'***alternate_snapshot_folder***'**  
 スナップショット ファイルを取得する場所を指定します。 *alternate_snapshot_folder*は**nvarchar (255)**、既定値は NULL です。 NULL の場合、スナップショット ファイルは、パブリッシャーによって指定される既定の場所から取得されます。  
  
 [  **@working_directory =** ] **'***working_directory***'**  
 FTP を使用してスナップショット ファイルを転送するときに、パブリケーションのデータ ファイルとスキーマ ファイルを一時的に格納するために使用する作業ディレクトリの名前を指定します。 *working_directory*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@use_ftp =** ] **'***@use_ftp***'**  
 スナップショットを取得するときに、一般的なプロトコルの代わりに FTP を使用するかどうかを指定します。 *@use_ftp*は**nvarchar (5)**、既定値は FALSE。  
  
 [  **@reserved =** ] **'***予約***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@use_interactive_resolver =** ] **'***use_interactive_resolver***'** ]  
 対話的な競合解決が可能なすべてのアーティクルについて、インタラクティブ競合回避モジュールを使用して競合を解決します。 *use_interactive_resolver*は**nvarchar (5)**、既定値は FALSE。  
  
 [  **@offloadagent =** ] **'***remote_agent_activation***'**  
 > [!NOTE]  
>  リモート エージェント アクティブ化は現在サポートされておらず、非推奨とされます。 このパラメーターは、スクリプトの下位互換性を確保するためだけに用意されています。 設定*remote_agent_activation*以外の値を**false**エラーが生成されます。  
  
 [  **@offloadserver =** ] **'***remote_agent_server_name***'**  
 > [!NOTE]  
>  リモート エージェント アクティブ化は現在サポートされておらず、非推奨とされます。 このパラメーターは、スクリプトの下位互換性を確保するためだけに用意されています。 設定*remote_agent_server_name* NULL 以外の値にエラーが生成されます。  
  
 [  **@job_name =** ] **'***job_name***'** ]  
 既存のエージェント ジョブの名前を指定します。 *job_name*は**sysname**既定値は NULL です。 このパラメーターは、新しく作成したジョブ (既定値) の代わりに既存のジョブを使ってサブスクリプションを同期するときにだけ指定します。 メンバーになっていない場合、 **sysadmin**するを指定する必要があります固定サーバー ロール、 *job_login*と*job_password*を指定すると*job_name*.  
  
 [  **@dynamic_snapshot_location =** ] **'***dynamic_snapshot_location***'** ]  
 フィルター選択されたデータのスナップショットを使用する場合に、読み込むスナップショット ファイルが格納されているフォルダーのパスを指定します。 *dynamic_snapshot_location*は**nvarchar (260)**、既定値は NULL です。 詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
 [  **@use_web_sync =** ] *@use_web_sync*  
 Web 同期が有効であることを示します。 *@use_web_sync*は**ビット**、既定値は 0。 **1** HTTP を使用してインターネット経由でプル サブスクリプションを同期できることを指定します。  
  
 [  **@internet_url =** ] **'***internet_url***'**  
 Web 同期用のレプリケーション リスナー (REPLISAPI.DLL) の場所を指定します。 *internet_url*は**nvarchar (260)**、既定値は NULL です。 *internet_url*形式での完全修飾 URL は、`http://server.domain.com/directory/replisapi.dll`します。 サーバーの構成で、リッスンするポートがポート 80 以外の場合は、`http://server.domain.com:portnumber/directory/replisapi.dll` の形式のポート番号も指定する必要があります。ここで `portnumber` はポートを表します。  
  
 [  **@internet_login =** ] **'***internet_login***'**  
 HTTP 基本認証を使って Web 同期をホストしている Web サーバーに接続するときに、マージ エージェントが使用するログインを指定します。 *internet_login*は**sysname**、既定値は NULL です。  
  
 [  **@internet_password =** ] **'***internet_password***'**  
 HTTP 基本認証を使って Web 同期をホストしている Web サーバーに接続するときに、マージ エージェントが使用するパスワードを指定します。 *internet_password*は**nvarchar (524)** 既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 [  **@internet_security_mode =** ] *internet_security_mode*  
 HTTPS を使った Web 同期で Web サーバーに接続するときに、マージ エージェントが使用する認証方式を指定します。 *internet_security_mode*は**int**これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|基本認証を使用|  
|**1** (既定値)|Windows 統合認証を使用|  
  
> [!NOTE]  
>  基本認証を Web 認証と共に使用することをお勧めします。 Web 認証を使用するには、Web サーバーに SSL で接続する必要があります。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
 [  **@internet_timeout =** ] *internet_timeout*  
 Web 同期要求が期限切れとなるまでの時間を秒単位で指定します。 *internet_timeout*は**int**、既定値は**300**秒。  
  
 [  **@hostname =** ] **'***hostname***'**  
 HOST_NAME() がパラメーター化フィルターの WHERE 句で使用される場合に、この関数の値はオーバーライドされます。 *ホスト名*は**sysname**、既定値は NULL です。  
  
 [  **@job_login =** ] **'***job_login***'**  
 エージェントを実行する Windows アカウント用のログインを指定します。 *job_login*は**nvarchar (257)**、既定値はありません。 Windows 統合認証を使用する場合、この Windows アカウントは、サブスクライバーへのエージェント接続、およびディストリビューターやパブリッシャーへの接続に常に使用されます。  
  
 [  **@job_password =** ] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 最大限のセキュリティを得るには、ログイン名とパスワードを実行時に指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addmergepullsubscription_agent**はマージ レプリケーションで使用してと同様の機能を使用して[sp_addpullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。  
  
 正しく実行するときにセキュリティ設定を指定する方法の例については**sp_addmergepullsubscription_agent**を参照してください[Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_1_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergepullsubscription_agent**します。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_changemergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
