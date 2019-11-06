---
title: sp_help_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_job_TSQL
- sp_help_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_job
ms.assetid: 8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa
author: stevestein
ms.author: sstein
ms.openlocfilehash: a6c2929062451d139cc3452b6bd272dd85bac951
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054993"
---
# <a name="sphelpjob-transact-sql"></a>sp_help_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  自動化された操作を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用されるジョブに関する情報を返します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_job { [ @job_id = ] job_id  
[ @job_name = ] 'job_name' }   
     [ , [ @job_aspect = ] 'job_aspect' ]   
     [ , [ @job_type = ] 'job_type' ]   
     [ , [ @owner_login_name = ] 'login_name' ]   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @enabled = ] enabled ]   
     [ , [ @execution_status = ] status ]   
     [ , [ @date_comparator = ] 'date_comparison' ]   
     [ , [ @date_created = ] date_created ]   
     [ , [ @date_last_modified = ] date_modified ]   
     [ , [ @description = ] 'description_pattern' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @job_id = ] job_id` ジョブの識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
`[ @job_name = ] 'job_name'` ジョブの名前。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  か、特定のジョブを表示する*job_id*または*job_name*指定する必要があります。  どちらも省略*job_id*と*job_name*すべてのジョブに関する情報を返します。
  
`[ @job_aspect = ] 'job_aspect'` 表示するジョブ属性。 *job_aspect*は**varchar (9)** 、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**ALL**|ジョブのすべての属性情報|  
|**JOB**|ジョブ情報|  
|**SCHEDULES**|スケジュール情報|  
|**手順**|ジョブ ステップ情報|  
|**ターゲット**|表示対象情報|  
  
`[ @job_type = ] 'job_type'` レポートに含めるジョブの種類。 *job_type*は**varchar (12)** 、既定値は NULL です。 *job_type*できる**ローカル**または**MULTI-SERVER**します。  
  
`[ @owner_login_name = ] 'login_name'` ジョブの所有者のログイン名。 *login_name*は**sysname**、既定値は NULL です。  
  
`[ @subsystem = ] 'subsystem'` サブシステムの名前。 *サブシステム*は**nvarchar (40)** 、既定値は NULL です。  
  
`[ @category_name = ] 'category'` カテゴリの名前。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
`[ @enabled = ] enabled` 情報を表示するかどうかを示す数には、ジョブと無効なジョブが有効になります。 *有効になっている*は**tinyint**、既定値は NULL です。 **1**有効なジョブ、および**0**ジョブを無効になっていることを示します。  
  
`[ @execution_status = ] status` ジョブの実行状態です。 *ステータス*は**int**、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|アクティブなジョブだけを返す。|  
|**1**|実行中。|  
|**2**|スレッド待機中。|  
|**3**|再試行待ち。|  
|**4**|アイドル。|  
|**5**|一時中断。|  
|**7**|完了操作の実行中。|  
  
`[ @date_comparator = ] 'date_comparison'` 比較に使用する比較演算子*date_created*と*date_modified*します。 *date_comparison*は**char (1)** 、できますが、=、 \<、または >。  
  
`[ @date_created = ] date_created` ジョブが作成された日付。 *date_created*は**datetime**、既定値は NULL です。  
  
`[ @date_last_modified = ] date_modified` ジョブの最終変更日。 *date_modified*は**datetime**、既定値は NULL です。  
  
`[ @description = ] 'description_pattern'` ジョブの説明。 *description_pattern*は**nvarchar (512)** 、既定値は NULL です。 *description_pattern*パターン マッチングの SQL Server のワイルドカード文字を含めることができます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 引数が指定されていない場合**sp_help_job**この結果セットを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの一意な ID。|  
|**originating_server**|**nvarchar(30)**|ジョブを実行したサーバーの名前。|  
|**name**|**sysname**|ジョブの名前。|  
|**enabled**|**tinyint**|ジョブが実行可能かどうか。|  
|**description**|**nvarchar(512)**|ジョブの説明。|  
|**start_step_id**|**int**|実行を開始するジョブ ステップの ID。|  
|**category**|**sysname**|ジョブ カテゴリ。|  
|**所有者**|**sysname**|ジョブ所有者。|  
|**notify_level_eventlog**|**int**|**ビットマスク**示すどのような場合は、Microsoft Windows アプリケーション ログに、通知イベントが記録する必要があります。 これらの値のいずれかを指定できます。<br /><br /> **0** = なし<br /><br /> **1** = ジョブが成功した場合<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_level_email**|**int**|**ビットマスク**ジョブの完了時にどのような状況通知の電子メールを送信する必要があります。 指定できる値は同じである**notify_level_eventlog**します。|  
|**notify_level_netsend**|**int**|**ビットマスク**ジョブの完了時にどのようなネットワーク メッセージを送信する必要があります。 指定できる値は同じである**notify_level_eventlog**します。|  
|**notify_level_page**|**int**|**ビットマスク**ジョブの完了時にどのような場合、ページを送信する必要があります。 指定できる値は同じである**notify_level_eventlog**します。|  
|**notify_email_operator**|**sysname**|通知先のオペレーターの電子メール名。|  
|**notify_netsend_operator**|**sysname**|ネットワーク メッセージを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**notify_page_operator**|**sysname**|ページを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**delete_level**|**int**|**ビットマスク**示すジョブの完了時にどのような場合、ジョブを削除する必要があります。 指定できる値は同じである**notify_level_eventlog**します。|  
|**date_created**|**datetime**|ジョブを作成した日付。|  
|**date_modified**|**datetime**|ジョブを最後に変更した日付。|  
|**version_number**|**int**|ジョブのバージョン。ジョブを変更するたびに自動的に更新されます。|  
|**last_run_date**|**int**|ジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ジョブの実行を最後に開始した時刻。|  
|**last_run_outcome**|**int**|最後に実行したときのジョブの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**next_run_date**|**int**|ジョブの次回実行予定日。|  
|**next_run_time**|**int**|ジョブの次回実行予定時刻。|  
|**next_run_schedule_id**|**int**|次回の実行スケジュールの識別番号。|  
|**current_execution_status**|**int**|現在の実行ステータス。|  
|**current_execution_step**|**sysname**|ジョブの現在の実行ステップ。|  
|**current_retry_attempt**|**int**|ジョブの実行中にステップを再試行した場合、現在の再試行を示します。|  
|**has_step**|**int**|ジョブのジョブ ステップ数。|  
|**has_schedule**|**int**|ジョブのジョブ スケジュール数。|  
|**has_target**|**int**|ジョブのターゲット サーバー数。|  
|**type**|**int**|ジョブの種類。<br /><br /> 1 = ローカル ジョブ<br /><br /> **2** = マルチ サーバー ジョブです。<br /><br /> **0** = ジョブには、対象サーバーがありません。|  
  
 場合*job_id*または*job_name*が指定されている**sp_help_job**ジョブ ステップ、ジョブのスケジュール、およびジョブ対象サーバーの場合は、これらの結果セットを返します。  
  
 次に、ジョブ ステップに関する結果セットを示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|このジョブでのみ一意なステップの識別子。|  
|**step_name**|**sysname**|ステップの名前。|  
|**subsystem**|**nvarchar(40)**|ステップ コマンドを実行するサブシステム。|  
|**command**|**nvarchar(3200)**|実行するコマンド。|  
|**flags**|**nvarchar (4000)**|**ビットマスク**のステップの動作を制御する値。|  
|**cmdexec_success_code**|**int**|**CmdExec**手順では、これは、コマンドの成功のプロセス終了コード。|  
|**on_success_action**|**nvarchar (4000)**|ステップが成功した場合に実行する操作。<br /><br /> **1** = 成功状態で終了します。<br /><br /> **2** = エラーで終了します。<br /><br /> **3** = 次の手順に移動します。<br /><br /> **4** = 手順に進みます。|  
|**on_success_step_id**|**int**|場合**on_success_action**は**4**を実行する次の手順を示します。|  
|**on_fail_action**|**nvarchar (4000)**|ステップが失敗した場合に実行する動作。 値は同じである**on_success_action**します。|  
|**on_fail_step_id**|**int**|場合**on_fail_action**は**4**を実行する次の手順を示します。|  
|**server**|**sysname**|予約済み。|  
|**database_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)]手順、これは、データベース コマンドを実行します。|  
|**database_user_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合は、コマンドを実行するデータベース ユーザー コンテキスト。|  
|**retry_attempts**|**int**|ステップを正常に実行できない場合、コマンドを再試行する最大回数。この回数に達すると、ステップが失敗したと判断されます。|  
|**retry_interval**|**int**|再試行の間隔 (分単位) をいずれかです。|  
|**os_run_priority**|**varchar(4000)**|予約済み。|  
|**output_file_name**|**varchar(200)**|コマンド出力を書き込むファイル ([!INCLUDE[tsql](../../includes/tsql-md.md)]と**CmdExec**ステップのみ)。|  
|**last_run_outcome**|**int**|最後に実行したときのステップの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**last_run_duration**|**int**|最後に実行したときのステップの経過時間 (秒単位)。|  
|**last_run_retries**|**int**|最後にステップを実行したときのコマンドの再試行回数。|  
|**last_run_date**|**int**|ステップの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ステップの実行を最後に開始した時刻。|  
|**proxy_id**|**int**|ジョブ ステップのプロキシ。|  
  
 次に、ジョブ スケジュールに関する結果セットを示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|すべてのジョブで一意なスケジュール識別子。|  
|**schedule_name**|**sysname**|このジョブでのみ一意なスケジュールの名前。|  
|**enabled**|**int**|スケジュールがアクティブかどうか (**1**) かどうか (**0**)。|  
|**freq_type**|**int**|ジョブを実行する頻度を示す値。<br /><br /> **1** = 1 回<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32**を基準とする、毎月を =、 **freq_interval**<br /><br /> **64** = の場合に実行**SQLServerAgent**サービスの開始。|  
|**freq_interval**|**int**|日のジョブを実行するとします。 値の値に依存**freq_type**します。 詳細については、次を参照してください[sp_add_schedule &#40;TRANSACT-SQL。&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|単位**freq_subday_interval**します。 詳細については、次を参照してください[sp_add_schedule &#40;TRANSACT-SQL。&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|数**freq_subday_type**にジョブの各実行間に発生する期間。 詳細については、次を参照してください[sp_add_schedule &#40;TRANSACT-SQL。&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|定期ジョブの**freq_interval**各月にします。 詳細については、次を参照してください[sp_add_schedule &#40;TRANSACT-SQL。&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|定期ジョブの実行間隔 (月単位)。|  
|**active_start_date**|**int**|ジョブの実行を開始する日付。|  
|**active_end_date**|**int**|ジョブの実行を終了する日付。|  
|**active_start_time**|**int**|ジョブの実行を開始する時刻**active_start_date します。**|  
|**active_end_time**|**int**|上のジョブの実行を終了する時間**active_end_date**します。|  
|**date_created**|**datetime**|スケジュールを作成した日付。|  
|**schedule_description**|**nvarchar (4000)**|英語によるスケジュールの説明 (必要な場合)。|  
|**next_run_date**|**int**|スケジュールで次にジョブを実行する日付。|  
|**next_run_time**|**int**|スケジュールで次にジョブを実行する時刻。|  
|**schedule_uid**|**uniqueidentifier**|スケジュールの識別子。|  
|**job_count**|**int**|このスケジュールを参照するジョブの数。|  
  
 次に、ジョブターゲット サーバーに関する結果セットを示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ターゲット サーバーの識別子。|  
|**server_name**|**nvarchar(30)**|ターゲット サーバーのコンピューター名。|  
|**enlist_date**|**datetime**|ターゲット サーバーがマスター サーバーに参加した日付。|  
|**last_poll_date**|**datetime**|ターゲット サーバーが最後にマスター サーバーを呼び出した日付。|  
|**last_run_date**|**int**|ターゲット サーバーでジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ターゲット サーバーでジョブの実行を最後に開始した時刻。|  
|**last_run_duration**|**int**|ターゲット サーバーで最後に実行したときのジョブの経過時間。|  
|**last_run_outcome**|**tinyint**|対象サーバーで最後に実行したときのジョブの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**last_outcome_message**|**nvarchar(1024)**|ターゲット サーバーで最後に実行したときのジョブからの結果メッセージ。|  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 メンバーの**SQLAgentUserRole**自分が所有するジョブのみを表示できます。 メンバーの**sysadmin**、 **SQLAgentReaderRole**、および**SQLAgentOperatorRole**すべてローカル ジョブおよびマルチ サーバー ジョブを表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-list-information-for-all-jobs"></a>A. すべてのジョブに関する情報を表示  
 次の例では、実行、`sp_help_job`で現在定義されているジョブのすべての情報を返すパラメーターなしでプロシージャ、`msdb`データベース。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-matching-a-specific-criteria"></a>B. 指定した条件に一致するジョブについての情報を一覧表示する  
 次の例では、`françoisa` が所有するマルチサーバー ジョブのジョブ情報を一覧表示します。ここでは、有効でかつ、実行中のジョブが対象になります。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job   
   @job_type = N'MULTI-SERVER',  
   @owner_login_name = N'françoisa',  
   @enabled = 1,  
   @execution_status = 1 ;  
GO  
```  
  
### <a name="c-listing-all-aspects-of-information-for-a-job"></a>C. ジョブに関するすべての属性情報を一覧表示する  
 次の例では、`NightlyBackups` ジョブに関するすべての属性情報を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job  
    @job_name = N'NightlyBackups',  
    @job_aspect = N'ALL' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
