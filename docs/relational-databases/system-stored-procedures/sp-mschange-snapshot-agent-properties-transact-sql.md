---
title: sp_MSchange_snapshot_agent_properties (Transact-SQL) |Microsoft Docs
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
ms.openlocfilehash: 9c4dcd79945644f0bc44d9ca3e948fa4f85d4e40
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905185"
---
# <a name="sp_mschange_snapshot_agent_properties-transact-sql"></a>sp_MSchange_snapshot_agent_properties (Transact-SQL)
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
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー* は **sysname** 、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'` パブリケーション データベースの名前です。 *publisher_db* は **sysname** 、既定値はありません。  
  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @frequency_type = ] frequency_type` スナップショット エージェントを実行する頻度です。 *frequency_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|[要求時]|  
|**4**|毎日。|  
|**8**|毎週。|  
|**10**|毎月。|  
|**20**|frequency_interval を基準とした月単位|  
|**40**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの起動時|  
  
`[ @frequency_interval = ] frequency_interval` 設定した頻度に適用する値は、 *frequency_type*します。 *frequency_interval*は**int**、既定値はありません。  
  
`[ @frequency_subday = ] frequency_subday` 単位*freq_subday_interval*します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値はありません。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` スナップショット エージェントを実行する日付です。 *frequency_relative_interval*は**int**、既定値はありません。  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値はありません。  
  
`[ @active_start_date = ] active_start_date` スナップショット エージェントの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値はありません。  
  
`[ @active_end_date = ] active_end_date` スナップショット エージェントが停止した日付、スケジュールに yyyymmdd です。 *active_end_date*は**int**、既定値はありません。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` スナップショット エージェントを最初のスケジュール設定する時刻、hhmmss 形式で指定として書式設定します。 *active_start_time_of_day*は**int**、既定値はありません。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` スナップショット エージェントが停止する時刻 hhmmss 形式で指定として書式設定、スケジュール設定します。 *active_end_time_of_day*は**int**、既定値はありません。  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` 既存のジョブが使用されている場合、既存のスナップショット エージェント ジョブ名の名前です。 *snapshot_agent_name*は**nvarchar (100)** 、既定値はありません。  
  
`[ @publisher_security_mode = ] publisher_security_mode` パブリッシャーに接続するときに、エージェントによって使用されるセキュリティ モード。 *publisher_security_mode*は**int**、既定値はありません。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、および**1** Windows 認証を指定します。 値**0**を指定する必要があります以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` パブリッシャーに接続するときに、ログインが使用されます。 *publisher_login*は**sysname**、既定値はありません。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login*が NULL で publisher *_ * * security_mode*は**1**で指定した Windows アカウント*job_login*になりますパブリッシャーに接続するときに使用されます。  
  
`[ @publisher_password = ] 'publisher_password'` パブリッシャーに接続するときに、パスワードが使用されます。 *publisher_password*は**nvarchar (524)** 、既定値はありません。  
  
> [!IMPORTANT]  
>  スクリプト ファイルでは、認証情報を格納しないでください。 セキュリティを向上させるには、実行時にログイン名とパスワードを指定することをお勧めします。  
  
`[ @job_login = ] 'job_login'` エージェントを実行する Windows アカウントのログインです。 *job_login*は**nvarchar (257)** 、既定値はありません。 この Windows アカウントは常に、ディストリビューターへのエージェント接続で使用します。 新しいスナップショット エージェント ジョブを作成するときに、このパラメーターを指定する必要があります。 *これ以外は変更できません*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *パブリッシャーです。*  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password* は **sysname** 、既定値はありません。 新しいスナップショット エージェント ジョブを作成するときに、このパラメーターを指定する必要があります。  
  
> [!IMPORTANT]  
>  スクリプト ファイルでは、認証情報を格納しないでください。 セキュリティを向上させるには、実行時にログイン名とパスワードを指定することをお勧めします。  
  
`[ @publisher_type = ] 'publisher_type'` パブリッシャーがのインスタンスで実行されていない場合、パブリッシャーの種類を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 *publisher_type*は**sysname**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**MSSQLSERVER**|指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。|  
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
  
  
