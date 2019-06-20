---
title: sp_changepublication_snapshot (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changepublication_snapshot_TSQL
- sp_changepublication_snapshot
helpviewer_keywords:
- sp_changepublication_snapshot
ms.assetid: 518a4618-3592-4edc-8425-cbc33cdff891
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a5b55d2ec6a8be0df305e2c1ce7121b638250c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62997839"
---
# <a name="spchangepublicationsnapshot-transact-sql"></a>sp_changepublication_snapshot (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたパブリケーションのスナップショット エージェントのプロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  リモート ディストリビューターを使用するパブリッシャーを構成する場合は、 *job_login* および *job_password*を含むすべてのパラメーターに指定された値がディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changepublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @frequency_type = ] frequency_type` エージェントをスケジュールする頻度です。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
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
  
`[ @frequency_interval = ] frequency_interval` エージェントを実行する曜日を指定します。 *frequency_interval*は**int**値は次のいずれかを指定できます。  
  
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
  
`[ @frequency_subday = ] frequency_subday` 単位*freq_subday_interval*します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (既定値)||  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` 間隔は、 *frequency_subday*します。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` スナップショット エージェントを実行する日付です。 *frequency_relative_interval*は**int**、既定値は NULL です。  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
`[ @active_start_date = ] active_start_date` スナップショット エージェントの最初の日付スケジュール設定を yyyymmdd 形式で指定として書式設定されます。 *active_start_date*は**int**、既定値は NULL です。  
  
`[ @active_end_date = ] active_end_date` スナップショット エージェントが停止した日付、スケジュールに yyyymmdd です。 *active_end_date*は**int**、既定値は NULL です。  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` スナップショット エージェントを最初のスケジュール設定する時刻、hhmmss 形式で指定として書式設定します。 *active_start_time_of_day* は **int** 、既定値は NULL です。  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` スナップショット エージェントが停止する時刻 hhmmss 形式で指定として書式設定、スケジュール設定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
`[ @snapshot_job_name = ] 'snapshot_agent_name'` 既存のジョブが使用されている場合、既存のスナップショット エージェント ジョブ名の名前です。 *snapshot_agent_name*は**nvarchar (100)** 既定値は NULL です。  
  
`[ @publisher_security_mode = ] publisher_security_mode` パブリッシャーに接続するときに、エージェントによって使用されるセキュリティ モード。 *publisher_security_mode*は**smallint**、既定値は NULL です。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証、および**1** Windows 認証を指定します。 値**0**を指定する必要があります以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
`[ @publisher_login = ] 'publisher_login'` パブリッシャーに接続するときに、ログインが使用されます。 *publisher_login* は **sysname** 、既定値は NULL です。 *publisher_login*場合に指定する必要があります*publisher_security_mode*は**0**します。 場合*publisher_login* null と*publisher_security_mode*は**1**で指定した Windows アカウント*job_login*ときに使用されますパブリッシャーに接続します。  
  
`[ @publisher_password = ] 'publisher_password'` パブリッシャーに接続するときに、パスワードが使用されます。 *publisher_password* は **sysname** 、既定値は NULL です。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @job_login = ] 'job_login'` エージェントを実行する Windows アカウントのログインです。 *job_login*は**nvarchar (257)** 、既定値は NULL です。 この Windows アカウントは常に、ディストリビューターへのエージェント接続で使用します。 新しいスナップショット エージェント ジョブを作成するときに、このパラメーターを指定する必要があります。 これ以外は変更できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
`[ @job_password = ] 'job_password'` エージェントを実行する Windows アカウントのパスワードです。 *job_password*は**sysname**、既定値は NULL です。 新しいスナップショット エージェント ジョブを作成するときに、このパラメーターを指定する必要があります。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @publisher = ] 'publisher'` 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*でスナップショット エージェントを作成するときに使用されません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changepublication_snapshot**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changepublication_snapshot**します。  
  
## <a name="see-also"></a>関連項目  
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addpublication_snapshot &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
