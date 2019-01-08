---
title: sp_MSchange_snapshot_agent_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_snapshot_agent_properties_TSQL
- sp_MSchange_snapshot_agent_properties
helpviewer_keywords:
- sp_MSchange_snapshot_agent_properties
ms.assetid: 7947a788-3fd7-469f-84db-b03ba89a153c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a4c8eb45ad7864466ccedc3de5b034325279322
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589756"
---
# <a name="spmschangesnapshotagentproperties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行されるスナップショット エージェント ジョブのプロパティを変更、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]またはそれ以降のバージョンのディストリビューター。 このストアド プロシージャがパブリッシャーのインスタンス上の実行時にプロパティを変更する使用[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_MSchange_snapshot_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @frequency_type= ] frequency_type  
        , [ @frequency_interval= ] frequency_interval  
        , [ @frequency_subday= ] frequency_subday  
        , [ @frequency_subday_interval= ] frequency_subday_interval  
        , [ @frequency_relative_interval= ] frequency_relative_interval  
        , [ @frequency_recurrence_factor= ] frequency_recurrence_factor  
        , [ @active_start_date= ] active_start_date  
        , [ @active_end_date= ] active_end_date  
        , [ @active_start_time_of_day= ] active_start_time_of_day  
        , [ @active_end_time_of_day= ] active_end_time_of_day  
        , [ @snapshot_job_name = ] 'snapshot_agent_name'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publisher** =] **'**_パブリッシャー_**'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=** ] **'**_publisher_db_**'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publication =** ] **'**_パブリケーション_**'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@frequency_type =** ] *frequency_type*  
 スナップショット エージェントの実行頻度を指定します。 *frequency_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|"**10**"|毎月。|  
|**20**|frequency_interval を基準とした月単位|  
|**40**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの起動時|  
  
 [  **@frequency_interval =** ] *frequency_interval*  
 設定した頻度に適用する値は、 *frequency_type*します。 *frequency_interval*は**int**、既定値はありません。  
  
 [  **@frequency_subday =** ] *frequency_subday*  
 単位*freq_subday_interval*します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値はありません。  
  
 [  **@frequency_relative_interval =** ] *frequency_relative_interval*  
 スナップショット エージェントを実行する日付を指定します。 *frequency_relative_interval*は**int**、既定値はありません。  
  
 [  **@frequency_recurrence_factor =** ] *frequency_recurrence_factor*  
 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値はありません。  
  
 [ **@active_start_date =** ] *active_start_date*  
 スナップショット エージェントを最初にスケジュール設定する日付を、YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値はありません。  
  
 [ **@active_end_date =** ] *active_end_date*  
 スナップショット エージェントのスケジュール設定を停止する日付を、YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値はありません。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 スナップショット エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値はありません。  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 スナップショット エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値はありません。  
  
 [  **@snapshot_job_name =** ] **'**_snapshot_agent_name_**'**  
 既存のジョブが使用されている場合、既存のスナップショット エージェントのジョブ名を指定します。 *snapshot_agent_name*は**nvarchar (100)**、既定値はありません。  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 パブリッシャーへの接続時にエージェントが使用するセキュリティ モードを指定します。 *publisher_security_mode*は**int**、既定値はありません。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、および**1** Windows 認証を指定します。 値**0**を指定する必要があります以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [ **@publisher_login**=] **'**_publisher_login_**'**  
 パブリッシャーへの接続時に使用するログインを指定します。 *publisher_login*は**sysname**、既定値はありません。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login*が NULL で publisher *_ * * security_mode*は**1**で指定した Windows アカウント*job_login*になりますパブリッシャーに接続するときに使用されます。  
  
 [ **@publisher_password**=] **'**_publisher_password_**'**  
 パブリッシャーへの接続時に使用するパスワードを指定します。 *publisher_password*は**nvarchar (524)**、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 セキュリティを強化するため、実行時にログイン名とパスワードを指定することをお勧めします。  
  
 [ **@job_login**=] **'**_job_login_**'**  
 エージェントを実行する Windows アカウント用のログインを指定します。 *job_login*は**nvarchar (257)**、既定値はありません。 この Windows アカウントはディストリビューターへのエージェント接続で常に使用されます。 新しいスナップショット エージェント ジョブを作成するときにはこのパラメーターを指定する必要があります。 *これ以外は変更できません*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*  
  
 [ **@job_password**=] **'**_job_password_**'**  
 エージェントを実行する Windows アカウント用のパスワードを指定します。 *job_password*は**sysname**、既定値はありません。 新しいスナップショット エージェント ジョブを作成するときにはこのパラメーターを指定する必要があります。  
  
> [!IMPORTANT]  
>  スクリプト ファイルに認証情報を格納しないでください。 セキュリティを強化するため、実行時にログイン名とパスワードを指定することをお勧めします。  
  
 [ **@publisher_type**=] **'**_publisher_type_**'**  
 パブリッシャーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで実行されていないときのパブリッシャーの種類を指定します。 *publisher_type*は**sysname**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**MSSQLSERVER**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーを指定します。|  
|**ORACLE**|標準の Oracle パブリッシャーを指定します。|  
|**ORACLE GATEWAY**|Oracle ゲートウェイ パブリッシャーを指定します。|  
  
 Oracle パブリッシャーと Oracle ゲートウェイ パブリッシャーとの違いの詳細については、次を参照してください。 [Oracle 公開の概要](../../relational-databases/replication/non-sql/oracle-publishing-overview.md)します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_MSchange_snapshot_agent_properties**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
 実行するときに、すべてのパラメーターを指定する必要があります**sp_MSchange_snapshot_agent_properties**します。 実行[sp_helppublication_snapshot](../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md)をスナップショット エージェント ジョブの現在のプロパティを返します。  
  
 インスタンスで、パブリッシャーを実行するときに[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンを使用する必要がありますまたは[sp_changepublication_snapshot](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)スナップショット エージェント ジョブのプロパティを変更します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin** 、ディストリビューター側の固定サーバー ロールが実行できる**sp_MSchange_snapshot_agent_properties**します。  
  
## <a name="see-also"></a>参照  
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)  
  
  
