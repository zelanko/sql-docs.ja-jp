---
title: sp_addmergesubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addmergesubscription_TSQL
- sp_addmergesubscription
helpviewer_keywords:
- sp_addmergesubscription
ms.assetid: a191d817-0132-49ff-93ca-76f13e609b38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5b319f6065c31a33f30469a73286491c1d641dc3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601120"
---
# <a name="spaddmergesubscription-transact-sql"></a>sp_addmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プッシュ マージ サブスクリプションまたはプル マージ サブスクリプションを作成します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergesubscription [ @publication= ] 'publication'  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db= ] 'subscriber_db' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @subscriber_type= ] 'subscriber_type' ]  
    [ , [ @subscription_priority= ] subscription_priority ]  
    [ , [ @sync_type= ] 'sync_type' ]  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @optional_command_line= ] 'optional_command_line' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @use_interactive_resolver= ] 'use_interactive_resolver' ]  
    [ , [ @merge_job_name= ] 'merge_job_name' ]  
    [ , [ @hostname = ] 'hostname'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。 パブリケーションは既に存在している必要があります。  
  
 [  **@subscriber =**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_db=**] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *@subscriber_db*は**sysname**、既定値は NULL です。  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 サブスクリプションの種類を指定します。 *subscription_type*は**nvarchar (15)**、既定値は PUSH です。 場合**プッシュ**、プッシュ サブスクリプションが追加され、ディストリビューターでマージ エージェントを追加します。 場合**プル**ディストリビューターでマージ エージェントを追加せずにプル サブスクリプションが追加されます。  
  
> [!NOTE]  
>  匿名サブスクリプションの場合、このストアド プロシージャを使用する必要はありません。  
  
 [  **@subscriber_type=**] **'***subscriber_type***'**  
 サブスクライバーの種類を指定します。 *subscriber_type*は**nvarchar (15)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**ローカル**(既定値)|パブリッシャーだけが認識しているサブスクライバー。|  
|**グローバル**|すべてのサーバーが認識しているサブスクライバー。|  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のバージョンでは、ローカル サブスクリプションは、クライアント サブスクリプションとして参照し、グローバル サブスクリプションはサーバー サブスクリプションとして参照と  
  
 [  **@subscription_priority=**] *subscription_priority*  
 サブスクリプションの優先度を示す数値を指定します。 *subscription_priority*は**実際**、既定値は NULL です。 ローカル サブスクリプションと匿名サブスクリプションの場合、優先度は 0.0 です。 グローバル サブスクリプションの場合は、優先度を 100.0 未満にする必要があります。  
  
 [  **@sync_type=**] **'***sync_type***'**  
 サブスクリプションの同期の種類を指定します。 *sync_type*は**nvarchar (15)**、既定値は**自動**します。 **自動**または**none**します。 場合**自動**スキーマと初期データのパブリッシュされたテーブルの最初に転送されます、サブスクライバー。 場合**none**サブスクライバーが既にスキーマと初期データのパブリッシュされたテーブルのことが前提とします。 システム テーブルとデータは常に転送されます。  
  
> [!NOTE]  
>  値を指定しないことをお勧めします**none**します。  
  
 [  **@frequency_type=**] *frequency_type*  
 いつマージ エージェントを実行するかを示す値を指定します。 *frequency_type*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**4**|毎日。|  
|**8**|毎週。|  
|"**10**"|毎月。|  
|**20**|frequency_interval を基準とした月単位|  
|**40**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの起動時|  
|NULL (既定値)||  
  
 [  **@frequency_interval=**] *frequency_interval*  
 マージ エージェントを実行する日を指定します。 *frequency_interval*は**int**値は次のいずれかを指定できます。  
  
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
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 スケジュールに組み込まれているマージを毎月第何週に実行するかを指定します。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|First|  
|**2**|第 2 週|  
|**4**|第 3 週|  
|**8**|第 4 週|  
|**16**|Last|  
|NULL (既定値)||  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 使用される定期実行係数*frequency_type*します。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
 [  **@frequency_subday=**] *frequency_subday*  
 単位を*frequency_subday_interval*します。 *frequency_subday*は**int**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|1 回。|  
|**2**|第 2 週|  
|**4**|Minute|  
|**8**|Hour|  
|NULL (既定値)||  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 頻度*frequency_subday*をそれぞれのマージの間に発生します。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 マージ エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 マージ エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
 [  **@active_start_date=**] *active_start_date*  
 マージ エージェントを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は NULL です。  
  
 [  **@active_end_date=**] *active_end_date*  
 マージ エージェントのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は NULL です。  
  
 [  **@optional_command_line=**] **'***optional_command_line***'**  
 省略可能な実行用のコマンド プロンプトを指定します。 *optional_command_line*は**nvarchar (4000)**、既定値は NULL です。 このパラメーターを使用して、出力をキャプチャしてファイルに保存するコマンドを追加したり、構成ファイルや属性を指定できます。  
  
 [  **@description=**] **'***説明***'**  
 対象となるマージ サブスクリプションの短い説明を指定します。 *説明*は**nvarchar (255)**、既定値は NULL です。 レプリケーション モニターでこの値が表示されます、**フレンドリ名**列は、監視されるパブリケーションのサブスクリプションの並べ替えに使用できます。  
  
 [  **@enabled_for_syncmgr=**] **'***enabled_for_syncmgr***'**  
 を介してサブスクリプションを同期することができるかどうかを指定します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーです。 *enabled_for_syncmgr*は**nvarchar (5)**、既定値は FALSE。 場合**false**サブスクリプションが同期マネージャーに登録されません。 場合**true**、サブスクリプションは同期マネージャーに登録および起動しなくても同期できます[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。  
  
 [  **@offloadagent=** ] *remote_agent_activation*  
 エージェントをリモートから起動できることを指定します。 *remote_agent_activation*は**ビット**、既定値は**0**します。  
  
> [!NOTE]  
>  このパラメーターは非推奨とされました、スクリプトの旧バージョンとの互換性だけ保持されます。  
  
 [  **@offloadserver=** ] **'***remote_agent_server_name***'**  
 エージェントをリモートから起動するときに使用するサーバーのネットワーク名を指定します。 *remote_agent_server_name*は**sysname**、既定値は NULL です。  
  
 [  **@use_interactive_resolver=** ] **'***use_interactive_resolver***'**  
 対話的に競合を回避できるすべてのアーティクルについて、対話的に競合を解決できるようにします。 *use_interactive_resolver*は**nvarchar (5)**、既定値は FALSE。  
  
 [  **@merge_job_name=** ] **'***merge_job_name***'**  
 *@merge_job_name*パラメーターは非推奨し、設定することはできません。 *merge_job_name*は**sysname**、既定値は NULL です。  
  
 [ **@hostname**=] **'***hostname***'**  
 によって返される値よりも優先[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)パラメーター化されたフィルターの WHERE 句でこの関数を使用する場合。 *ホスト名*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  パラメーター化された行フィルター句では列名に関数を適用しないことをお勧めします。これは、 `LEFT([MyColumn]) = SUSER_SNAME()`のように指定すると、パフォーマンスに問題が生じるためです。 使用する場合[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)フィルター句と HOST_NAME 値を使用してデータ型に変換するために必要な場合があります[変換](../../t-sql/functions/cast-and-convert-transact-sql.md)します。 このようなケースの推奨事項の詳細については、「[Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)」の「HOST_NAME() 値のオーバーライド」をご覧ください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addmergesubscription**はマージ レプリケーションで使用します。  
  
 ときに**sp_addmergesubscription**のメンバーによって実行される、 **sysadmin**プッシュ サブスクリプションを作成するサーバーの役割を修正するには、マージ エージェント ジョブが暗黙的に作成し、実行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントサービス アカウント。 実行することをお勧めします[sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)に対して異なるエージェントに固有の Windows アカウントの資格情報を指定**@job_login**と **。@job_password**. 詳細については、「 [レプリケーション エージェント セキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergesubscription-_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergesubscription**します。  
  
## <a name="see-also"></a>参照  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [インタラクティブな競合解決](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_changemergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
