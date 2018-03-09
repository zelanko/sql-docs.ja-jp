---
title: "sp_addpushsubscription_agent (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addpushsubscription_agent_TSQL
- sp_addpushsubscription_agent
helpviewer_keywords:
- sp_addpushsubscription_agent
ms.assetid: 1fdd2052-50d8-4318-8aa7-fc635d5cad18
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ea57cd5bbcb264b38efc4fecf63153f56ba7e92
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spaddpushsubscriptionagent-transact-sql"></a>sp_addpushsubscription_agent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  トランザクション パブリケーションに対してプッシュ サブスクリプションを同期するために使用する、新たにスケジュールされたエージェント ジョブを追加します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addpushsubscription_agent [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @subscriber_security_mode = ] subscriber_security_mode ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @job_name = ] 'job_name' ]   
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
    [ , [ @dts_package_name = ] 'dts_package_name' ]  
    [ , [ @dts_package_password = ] 'dts_package_password' ]  
    [ , [ @dts_package_location = ] 'dts_package_location' ]  
    [ , [ @enabled_for_syncmgr = ] 'enabled_for_syncmgr' ]  
    [ , [ @distribution_job_name = ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @subscriber_provider = ] 'subscriber_provider' ]   
    [ , [ @subscriber_datasrc = ] 'subscriber_datasrc' ]   
    [ , [ @subscriber_location = ] 'subscriber_location' ]  
    [ , [ @subscriber_provider_string = ] 'subscriber_provider_string' ]   
    [ , [ @subscriber_catalog = ] 'subscriber_catalog' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@subscriber =**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_db =**] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値は NULL です。 値を指定するため、SQL Server 以外のサブスクライバー、 **(既定の出力先)**の*@subscriber_db*です。  
  
 [  **@subscriber_security_mode =**] *subscriber_security_mode*  
 サブスクライバーへ接続して同期するときに使用するセキュリティ モードを指定します。 *subscriber_security_mode*は**int**、既定値は 1 です。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 **1** Windows 認証を指定します。  
  
> [!IMPORTANT]  
>  キュー更新サブスクリプションの場合、サブスクライバーへの接続には [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用し、各サブスクライバーへの接続にはそれぞれ異なるアカウントを指定してください。 他のすべてのサブスクリプションについては、Windows 認証を使用してください。  
  
 [  **@subscriber_login =**] **'***subscriber_login***'**  
 サブスクライバーへ接続して同期するときに使用するサブスクライバー ログインを指定します。 *subscriber_login*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_password =**] **'***subscriber_password***'**  
 サブスクライバーのパスワードです。 *subscriber_password*場合は必須*subscriber_security_mode*に設定されている**0**します。 *subscriber_password*は**sysname**、既定値は NULL です。 サブスクライバー パスワードを使用する場合、サブスクライバー パスワードは自動的に暗号化されます。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [  **@job_login =** ] **'***job_login***'**  
 エージェントを実行する Windows アカウント用のログインを指定します。 *job_login*は**nvarchar (257)**既定値は NULL です。 この Windows アカウントは、エージェントがディストリビューターに接続するとき、および Windows 統合認証を使用してサブスクライバーに接続するときに必ず使用されます。  
  
 [  **@job_password =** ] **'***job_password***'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [  **@job_name =** ] **'***job_name***'**  
 既存のエージェント ジョブの名前を指定します。 *job_name*は**sysname**既定値は NULL です。 このパラメーターは、新しく作成したジョブ (既定値) の代わりに既存のジョブを使ってサブスクリプションを同期するときにだけ指定します。 メンバーではない場合、 **sysadmin**固定サーバー ロールを指定してください*job_login*と*job_password*を指定すると*job_name*.  
  
 [  **@frequency_type =** ] *frequency_type*  
 ディストリビューション エージェントをスケジュールに組み込む頻度を指定します。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|指定日時|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**16**|毎月。|  
|**32**|月単位|  
|**64** (既定値)|自動的に起動|  
|**128**|定期的|  
  
> [!NOTE]  
>  値を指定する**64**によりディストリビューション エージェントを連続モードで実行します。 これは、設定に対応しています、 **-連続**エージェントのパラメーターです。 詳細については、「 [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)」を参照してください。  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 設定した頻度に適用する値は、 *frequency_type*です。 *frequency_interval*は**int**、既定値は 1 です。  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 ディストリビューション エージェントを実行する日付です。 このパラメーターが使用されるときに*frequency_type*に設定されている**32** (月単位)。 *frequency_relative_interval*は**int**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**1** (既定値)|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 によって使用される定期実行係数*frequency_type*です。 *frequency_recurrence_factor*は**int**、既定値は 0 です。  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を指定します。 *frequency_subday*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4** (既定値)|Minute|  
|**8**|Hour|  
  
 [  **@frequency_subday_interval =** ] *frequency_subday_interval*  
 間隔は、 *frequency_subday*です。 *frequency_subday_interval*は**int**、既定値は 5 です。  
  
 [  **@active_start_time_of_day =** ] *active_start_time_of_day*  
 ディストリビューション エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は 0 です。  
  
 [  **@active_end_time_of_day =** ] *active_end_time_of_day*  
 ディストリビューション エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は 235959 です。  
  
 [  **@active_start_date =** ] *active_start_date*  
 ディストリビューション エージェントを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は 0 です。  
  
 [  **@active_end_date =** ] *active_end_date*  
 ディストリビューション エージェントのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は 99991231 です。  
  
 [  **@dts_package_name =** ] **'***dts_package_name***'**  
 データ変換サービス (DTS) パッケージの名前。 *dts_package_name*は、 **sysname**既定値は NULL です。 たとえば、パッケージ名を指定する`DTSPub_Package`、パラメーターであるが`@dts_package_name = N'DTSPub_Package'`です。  
  
 [  **@dts_package_password =** ] **'***dts_package_password***'**  
 パッケージの実行に必要なパスワードを指定します。 *dts_package_password*は**sysname**既定値は NULL です。  
  
> [!NOTE]  
>  場合は、パスワードを指定する必要があります*dts_package_name*を指定します。  
  
 [  **@dts_package_location =** ] **'***dts_package_location***'**  
 パッケージの場所を指定します。 *dts_package_location*は、 **nvarchar (12)**、既定値は DISTRIBUTOR です。 パッケージの場所を指定できます**ディストリビューター**または**サブスクライバー**です。  
  
 [  **@enabled_for_syncmgr =** ] **'***enabled_for_syncmgr***'**  
 使用、サブスクリプションを同期させるかどうかが[!INCLUDE[msCoName](../../includes/msconame-md.md)]同期マネージャーです。 *enabled_for_syncmgr*は**nvarchar (5)**、既定値は FALSE。 場合**false**サブスクリプションは同期マネージャーに登録されていません。 場合**true**、サブスクリプションは同期マネージャーに登録および起動しなくても同期できます[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
 [  **@distribution_job_name =** ] **'***distribution_job_name***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@publisher =** ] **'***パブリッシャー***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**既定値は NULL です。  
  
 [  **@subscriber_provider=** ] **'***subscriber_provider***'**  
 使用する一意なプログラム識別子 (PROGID) には、OLE DB provider for 以外の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソースを登録します。 *subscriber_provider*は**sysname**既定値は NULL です。 *subscriber_provider*ディストリビューターにインストールされている OLE DB プロバイダーに対して一意である必要があります。 *subscriber_provider*のみがサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
 [  **@subscriber_datasrc=** ] **'***subscriber_datasrc***'**  
 OLE DB プロバイダーで認識されるデータ ソースの名前を指定します。 *subscriber_datasrc*は**nvarchar (4000)**既定値は NULL です。 *subscriber_datasrc* OLE DB プロバイダーを初期化する DBPROP_INIT_DATASOURCE プロパティとして渡されます。 *subscriber_datasrc*のみがサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
 [  **@subscriber_location=** ] **'***subscriber_location***'**  
 OLE DB プロバイダーで認識される、データベースの場所です。 *subscriber_location*は**nvarchar (4000)**既定値は NULL です。 *subscriber_location* OLE DB プロバイダーを初期化する DBPROP_INIT_LOCATION プロパティとして渡されます。 *subscriber_location*のみがサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
 [  **@subscriber_provider_string=** ] **'***subscriber_provider_string***'**  
 データ ソースを識別する OLE DB プロバイダー固有の接続文字列を指定します。 *subscriber_provider_string*は**nvarchar (4000)**既定値は NULL です。 *subscriber_provider_string* IDataInitialize に渡したり、OLE DB プロバイダーを初期化する DBPROP_INIT_PROVIDERSTRING プロパティとして設定します。 *subscriber_provider_string*のみがサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
 [  **@subscriber_catalog=** ] **'***対応する、***'**  
 OLE DB プロバイダーに接続するときに使用するカタログを指定します。 *対応する、*は**sysname**既定値は NULL です。 *対応する、* OLE DB プロバイダーを初期化する DBPROP_INIT_CATALOG プロパティとして渡されます。 *対応する、*のみがサポートされていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addpushsubscription_agent**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addpushsubscription-a_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addpushsubscription_agent**です。  
  
## <a name="see-also"></a>参照  
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [SQL Server 以外のサブスクライバーのサブスクリプションの作成](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_addsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_changesubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)   
 [sp_dropsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
