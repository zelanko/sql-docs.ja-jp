---
title: "sp_help_job (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_job_TSQL
- sp_help_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_job
ms.assetid: 8a8b6104-e0e4-4d07-a2c3-f4243ee0d6fa
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9d91594f032409dbe2597dd859a549c17b795e04
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
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
 [ **@job_id =**] *job_id*  
 ジョブの識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name =**] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@job_aspect =**] **'***job_aspect***'**  
 表示するジョブ属性を指定します。 *job_aspect*は**varchar (9)**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|[値]|Description|  
|-----------|-----------------|  
|**ALL**|ジョブのすべての属性情報|  
|**JOB**|ジョブ情報|  
|**SCHEDULES**|スケジュール情報|  
|**手順**|ジョブ ステップ情報|  
|**ターゲット**|表示対象情報|  
  
 [ **@job_type =**] **'***job_type***'**  
 レポートに含めるジョブの種類を指定します。 *job_type*は**varchar (12)**、既定値は NULL です。 *job_type*できます**ローカル**または**MULTI-SERVER**です。  
  
 [ **@owner_login_name =**] **'***login_name***'**  
 ジョブの所有者のログイン名を指定します。 *login_name*は**sysname**、既定値は NULL です。  
  
 [  **@subsystem =**] **'***サブシステム***'**  
 サブシステムの名前です。 *サブシステム*は**nvarchar (40)**、既定値は NULL です。  
  
 [ **@category_name =**] **'***category***'**  
 カテゴリの名前を指定します。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
 [ **@enabled =**] *enabled*  
 有効なジョブと無効なジョブのどちらの情報を表示するかを示す数値を指定します。 *有効になっている*は**tinyint**、既定値は NULL です。 **1**有効なジョブ、および**0**ジョブを無効になっていることを示します。  
  
 [ **@execution_status =**] *status*  
 ジョブの実行状態を指定します。 *ステータス*は**int**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**0**|アクティブなジョブだけを返す。|  
|**1**|実行中。|  
|**2**|スレッド待機中。|  
|**3**|再試行待ち。|  
|**4**|アイドル。|  
|**5**|一時中断。|  
|**7**|完了操作の実行中。|  
  
 [ **@date_comparator =**] **'***date_comparison***'**  
 比較に使用する比較演算子*date_created*と*date_modified*です。 *date_comparison*は**char (1)**、ことができます = する\<、または >。  
  
 [ **@date_created =**] *date_created*  
 ジョブが作成された日付を指定します。 *date_created*は**datetime**、既定値は NULL です。  
  
 [ **@date_last_modified =**] *date_modified*  
 ジョブが最後に変更された日付を指定します。 *date_modified*は**datetime**、既定値は NULL です。  
  
 [  **@description =**] **'***description_pattern***'**  
 ジョブの説明を指定します。 *description_pattern*は**nvarchar (512)**、既定値は NULL です。 *description_pattern*パターン一致の SQL Server のワイルドカード文字を含めることができます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 引数が指定されていない場合**sp_help_job**この結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの一意な ID。|  
|**originating_server**|**nvarchar(30)**|ジョブを実行したサーバーの名前。|  
|**name**|**sysname**|ジョブの名前。|  
|**enabled**|**tinyint**|ジョブが実行可能かどうか。|  
|**説明**|**nvarchar(512)**|ジョブの説明。|  
|**start_step_id**|**int**|実行を開始するジョブ ステップの ID。|  
|**category**|**sysname**|ジョブ カテゴリ。|  
|**所有者**|**sysname**|ジョブ所有者。|  
|**notify_level_eventlog**|**int**|**ビットマスク**示すどのような場合は、Microsoft Windows アプリケーション ログに、通知イベントが記録する必要があります。 これらの値のいずれかを指定できます。<br /><br /> **0** = なし<br /><br /> **1** = ジョブが成功した場合<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_level_email**|**int**|**ビットマスク**を示す、ジョブの完了時にどのような場合、通知電子メールを送信する必要があります。 指定できる値は同じである**notify_level_eventlog**です。|  
|**notify_level_netsend**|**int**|**ビットマスク**ジョブの完了時にどのような状況ネットワーク メッセージを送信する必要があります。 指定できる値は同じである**notify_level_eventlog**です。|  
|**notify_level_page**|**int**|**ビットマスク**ジョブの完了時にどのような状況ページを送信する必要があります。 指定できる値は同じである**notify_level_eventlog**です。|  
|**notify_email_operator**|**sysname**|通知先のオペレーターの電子メール名。|  
|**notify_netsend_operator**|**sysname**|ネットワーク メッセージを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**notify_page_operator**|**sysname**|ページを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**delete_level**|**int**|**ビットマスク**ジョブの完了時にどのような状況下でジョブを削除するかを示すです。 指定できる値は同じである**notify_level_eventlog**です。|  
|**date_created**|**datetime**|ジョブを作成した日付。|  
|**date_modified**|**datetime**|ジョブを最後に変更した日付。|  
|**version_number**|**int**|ジョブのバージョン。ジョブを変更するたびに自動的に更新されます。|  
|**last_run_date**|**int**|ジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ジョブの実行を最後に開始した時刻。|  
|**last_run_outcome**|**int**|最後に実行したときのジョブの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**next_run_date**|**int**|ジョブが次回実行予定日。|  
|**next_run_time**|**int**|ジョブの次回実行予定時刻。|  
|**next_run_schedule_id**|**int**|次回の実行スケジュールの識別番号。|  
|**current_execution_status**|**int**|現在の実行ステータス。|  
|**current_execution_step**|**sysname**|ジョブの現在の実行ステップ。|  
|**current_retry_attempt**|**int**|ジョブの実行中にステップを再試行した場合、現在の再試行を示します。|  
|**has_step**|**int**|ジョブのジョブ ステップ数。|  
|**has_schedule**|**int**|ジョブのジョブ スケジュール数。|  
|**has_target**|**int**|ジョブの対象サーバー数。|  
|**type**|**int**|ジョブの種類。<br /><br /> 1 = ローカル ジョブ<br /><br /> **2**マルチ サーバー ジョブを = です。<br /><br /> **0** = ジョブに対象サーバーがありません。|  
  
 場合*job_id*または*job_name*が指定されている**sp_help_job**ジョブ ステップ、ジョブのスケジュール、およびジョブ対象サーバーの場合は、これらの結果セットを返します。  
  
 次に、ジョブ ステップに関する結果セットを示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|このジョブでのみ一意なステップの識別子。|  
|**step_name**|**sysname**|ステップの名前。|  
|**subsystem**|**nvarchar(40)**|ステップ コマンドを実行するサブシステム。|  
|**command**|**nvarchar(3200)**|実行するコマンド。|  
|**flags**|**nvarchar (4000)**|**ビットマスク**のステップの動作を制御する値。|  
|**cmdexec_success_code**|**int**|**CmdExec**手順、これは、コマンドの成功のプロセス終了コード。|  
|**on_success_action**|**nvarchar (4000)**|ステップが成功した場合に実行する操作。<br /><br /> **1** = success で終了します。<br /><br /> **2** = エラーで終了します。<br /><br /> **3** = 次の手順に移動します。<br /><br /> **4** = 手順に進みます。|  
|**on_success_step_id**|**int**|場合**on_success_action**は**4**を実行する次の手順を示します。|  
|**on_fail_action**|**nvarchar (4000)**|ステップが失敗した場合に実行する動作。 値が同じである**on_success_action**です。|  
|**on_fail_step_id**|**int**|場合**on_fail_action**は**4**を実行する次の手順を示します。|  
|**server**|**sysname**|予約されています。|  
|**database_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)]手順、これは、コマンドを実行するデータベース。|  
|**database_user_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合は、コマンドを実行するデータベース ユーザー コンテキスト。|  
|**retry_attempts**|**int**|ステップを正常に実行できない場合、コマンドを再試行する最大回数。この回数に達すると、ステップが失敗したと判断されます。|  
|**retry_interval**|**int**|再試行の間隔 (分単位) をいずれかです。|  
|**os_run_priority**|**varchar(4000)**|予約されています。|  
|**output_file_name**|**varchar(200)**|コマンド出力を書き込むファイル ([!INCLUDE[tsql](../../includes/tsql-md.md)]と**CmdExec**ステップのみ)。|  
|**last_run_outcome**|**int**|最後に実行したときのステップの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**last_run_duration**|**int**|最後に実行したときのステップの経過時間 (秒単位)。|  
|**last_run_retries**|**int**|最後にステップを実行したときのコマンドの再試行回数。|  
|**last_run_date**|**int**|ステップの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ステップの実行を最後に開始した時刻。|  
|**proxy_id**|**int**|ジョブ ステップのプロキシ。|  
  
 次に、ジョブ スケジュールに関する結果セットを示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|すべてのジョブで一意なスケジュール識別子。|  
|**schedule_name**|**sysname**|このジョブでのみ一意なスケジュールの名前。|  
|**enabled**|**int**|スケジュールがアクティブかどうか (**1**) か (**0**)。|  
|**freq_type**|**int**|ジョブを実行する頻度を示す値。<br /><br /> **1** = 1 回<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32** = 毎月、相対的な**freq_interval**<br /><br /> **64** = 時に実行**SQLServerAgent**サービスの開始。|  
|**freq_interval**|**int**|日数は、ジョブが実行されるとします。 値は、の値によって異なります。 **freq_type**です。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|単位**freq_subday_interval**です。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|数**freq_subday_type**ジョブの各実行間に発生する期間。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|スケジュールされたジョブの発生、 **freq_interval**各月にします。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|定期ジョブの実行間隔 (月単位)。|  
|**active_start_date**|**int**|ジョブの実行を開始する日付。|  
|**active_end_date**|**int**|ジョブの実行を終了する日付。|  
|**active_start_time**|**int**|ジョブの実行を開始する時刻**active_start_date です。**|  
|**active_end_time**|**int**|上のジョブの実行を終了する時刻**active_end_date**です。|  
|**date_created**|**datetime**|スケジュールを作成した日付。|  
|**schedule_description**|**nvarchar (4000)**|英語によるスケジュールの説明 (必要な場合)。|  
|**next_run_date**|**int**|スケジュールで次にジョブを実行する日付。|  
|**next_run_time**|**int**|スケジュールで次にジョブを実行する時刻。|  
|**schedule_uid**|**uniqueidentifier**|スケジュールの識別子。|  
|**job_count**|**int**|このスケジュールを参照するジョブの数。|  
  
 次に、ジョブ対象サーバーに関する結果セットを示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|対象サーバーの識別子。|  
|**server_name**|**nvarchar(30)**|対象サーバーのコンピューター名。|  
|**enlist_date**|**datetime**|対象サーバーがマスター サーバーに参加した日付。|  
|**last_poll_date**|**datetime**|対象サーバーが最後にマスター サーバーを呼び出した日付。|  
|**last_run_date**|**int**|対象サーバーでジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|対象サーバーでジョブの実行を最後に開始した時刻。|  
|**last_run_duration**|**int**|対象サーバーで最後に実行したときのジョブの経過時間。|  
|**last_run_outcome**|**tinyint**|対象サーバーで最後に実行したときのジョブの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**last_outcome_message**|**nvarchar(1024)**|対象サーバーで最後に実行したときのジョブからの結果メッセージ。|  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**所有しているジョブのみを表示します。 メンバー **sysadmin**、 **SQLAgentReaderRole**、および**SQLAgentOperatorRole**すべてローカル ジョブおよびマルチ サーバー ジョブを表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-list-information-for-all-jobs"></a>A. すべてのジョブの情報を一覧表示  
 次の例を実行、`sp_help_job`で現在定義されているジョブのすべての情報を返すパラメーターなしでプロシージャ、`msdb`データベース。  
  
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
 [sp_delete_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
