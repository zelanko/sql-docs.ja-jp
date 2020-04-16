---
title: sp_help_job (トランザクション-SQL) |マイクロソフトドキュメント
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
ms.openlocfilehash: 29870a0ffb3d2c3b1872acbb40266aef0d16b62c
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "75546565"
---
# <a name="sp_help_job-transact-sql"></a>sp_help_job (トランザクション-SQL)
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
`[ @job_id = ] job_id`ジョブ ID 番号。 *job_id*は**一意識別子**で、既定値は NULL です。  
  
`[ @job_name = ] 'job_name'`ジョブの名前。 *job_name*は**sysname**で、既定値は NULL です。  
  
> [!NOTE]  
>  特定のジョブを表示するには *、job_id*または*job_name*を指定する必要があります。  すべてのジョブに関する情報を返す場合は *、job_id*と*job_name*の両方を省略します。
  
`[ @job_aspect = ] 'job_aspect'`表示するジョブ属性。 *job_aspect*は**varchar(9) で**、デフォルトは NULL で、これらの値の 1 つを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**ALL**|ジョブのすべての属性情報|  
|**ジョブ**|求人情報|  
|**スケジュール**|スケジュール情報|  
|**手順**|ジョブ ステップ情報|  
|**ターゲット**|ターゲット情報|  
  
`[ @job_type = ] 'job_type'`レポートに含めるジョブの種類。 *job_type*は**varchar(12) で**、デフォルトは NULL です。 *job_type*は **、ローカル**または**マルチサーバー**にすることができます。  
  
`[ @owner_login_name = ] 'login_name'`ジョブの所有者のログイン名。 *login_name*は**sysname**で、デフォルトは NULL です。  
  
`[ @subsystem = ] 'subsystem'`サブシステムの名前。 *サブシステム*は**nvarchar(40) で**、デフォルトは NULL です。  
  
`[ @category_name = ] 'category'`カテゴリの名前。 *カテゴリ*は**sysname**で、デフォルトは NULL です。  
  
`[ @enabled = ] enabled`有効なジョブまたは使用不可のジョブの情報を表示するかどうかを示す番号。 *有効*は**tinyint**で、デフォルトは NULL です。 **1**は有効なジョブを示し **、0 は**無効なジョブを示します。  
  
`[ @execution_status = ] status`ジョブの実行ステータス。 *status*は**int**で、デフォルトは NULL で、これらの値の 1 つを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|アイドルまたは中断されていないジョブのみを返します。|  
|**1**|実行。|  
|**2**|スレッド待機中。|  
|**3**|再試行の間。|  
|**4**|[アイドル]。|  
|**5**|中断。|  
|**7**|完了操作の実行中。|  
  
`[ @date_comparator = ] 'date_comparison'`*date_created*と*date_modified*の比較で使用する比較演算子。 *date_comparison*は**char(1)** で、= \<、、、または > することができます。  
  
`[ @date_created = ] date_created`ジョブが作成された日付。 *date_created*は**datetime**で、既定値は NULL です。  
  
`[ @date_last_modified = ] date_modified`ジョブが最後に修正された日付。 *date_modified*は**datetime**で、既定値は NULL です。  
  
`[ @description = ] 'description_pattern'`ジョブの説明。 *description_pattern*は**nvarchar(512) で**、デフォルトは NULL です。 *description_pattern*には、パターン マッチング用の SQL Server ワイルドカード文字を含めることができます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 引数を指定しない場合 **、sp_help_job**はこの結果セットを返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの一意の ID。|  
|**originating_server**|**nvarchar(30)**|ジョブの取得元のサーバーの名前。|  
|**name**|**sysname**|ジョブの名前。|  
|**有効**|**tinyint**|ジョブの実行が有効になっているかどうかを示します。|  
|**説明**|**nvarchar(512)**|ジョブの説明。|  
|**start_step_id**|**int**|実行を開始するジョブのステップの ID。|  
|**カテゴリ**|**sysname**|ジョブ カテゴリ。|  
|**所有者**|**sysname**|ジョブ所有者。|  
|**notify_level_eventlog**|**int**|どのような状況で通知イベントを Microsoft Windows アプリケーション ログに記録するかを示す**ビットマスク**。 次のいずれかの値を指定します。<br /><br /> **0** = なし<br /><br /> **1** = ジョブが成功したとき<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = ジョブが完了するたびに (ジョブ結果に関係なく)|  
|**notify_level_email**|**int**|どのような状況で、ジョブの完了時に通知電子メールを送信するかを示す**ビットマスク**。 指定できる値は **、notify_level_eventlog**の場合と同じです。|  
|**notify_level_netsend**|**int**|ジョブの完了時にネットワーク メッセージを送信する必要がある状況を示す**ビットマスク**。 指定できる値は **、notify_level_eventlog**の場合と同じです。|  
|**notify_level_page**|**int**|ジョブの完了時にページを送信する必要がある状況を示す**ビットマスク**。 指定できる値は **、notify_level_eventlog**の場合と同じです。|  
|**notify_email_operator**|**sysname**|通知するオペレータの電子メール名。|  
|**notify_netsend_operator**|**sysname**|ネットワーク メッセージの送信時に使用するコンピュータまたはユーザーの名前。|  
|**notify_page_operator**|**sysname**|ページを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**delete_level**|**int**|ジョブの完了時にジョブを削除する必要がある状況を示す**ビットマスク**。 指定できる値は **、notify_level_eventlog**の場合と同じです。|  
|**date_created**|**datetime**|ジョブが作成された日付。|  
|**date_modified**|**datetime**|ジョブが最後に修正された日付。|  
|**version_number**|**int**|ジョブのバージョン (ジョブを変更するたびに自動的に更新されます)。|  
|**last_run_date**|**int**|ジョブが最後に実行を開始した日付。|  
|**last_run_time**|**int**|ジョブが最後に実行を開始した時刻。|  
|**last_run_outcome**|**int**|最後に実行したジョブの結果:<br /><br /> **0** = 失敗<br /><br /> **1** = 成功しました<br /><br /> **3** = 取り消し済み<br /><br /> **5** = 不明|  
|**next_run_date**|**int**|ジョブが次に実行される予定日。|  
|**next_run_time**|**int**|ジョブの次回実行予定時刻。|  
|**next_run_schedule_id**|**int**|次回の実行スケジュールの識別番号。|  
|**current_execution_status**|**int**|現在の実行ステータス:<br /><br /> **1** = 実行<br /><br /> **2** = スレッド待機中<br /><br /> **3** = 再試行の間<br /><br /> **4** = アイドル<br /><br /> **5** = 中断<br /><br /> **6** = 廃止<br /><br /> **7** = 完了アクションの実行|  
|**current_execution_step**|**sysname**|ジョブの現在の実行ステップ。|  
|**current_retry_attempt**|**int**|ジョブが実行中で、ステップが再試行された場合、これは現在の再試行です。|  
|**has_step**|**int**|ジョブのジョブ ステップ数。|  
|**has_schedule**|**int**|ジョブのジョブ スケジュール数。|  
|**has_target**|**int**|ジョブのターゲット サーバー数。|  
|**type**|**int**|ジョブの種類。<br /><br /> 1 = ローカル ジョブ。<br /><br /> **2** = マルチサーバー ジョブ。<br /><br /> **0** = ジョブには対象サーバーがありません。|  
  
 *job_id*または*job_name*を指定すると **、sp_help_job**は、ジョブ・ステップ、ジョブ・スケジュール、およびジョブ・ターゲット・サーバーに対して、これらの追加結果セットを戻します。  
  
 次に、ジョブ ステップに関する結果セットを示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|ステップの (このジョブで) 一意の ID。|  
|**step_name**|**sysname**|ステップの名前。|  
|**サブシステム**|**nvarchar(40)**|ステップ コマンドを実行するサブシステム。|  
|**コマンド**|**nvarchar(3200)**|実行するコマンド。|  
|**フラグ**|**nvarchar (4000)**|ステップの動作を制御する値の**ビットマスク**。|  
|**cmdexec_success_code**|**int**|**CmdExec**ステップの場合、これは正常なコマンドのプロセス終了コードです。|  
|**on_success_action**|**nvarchar (4000)**|ステップが成功した場合の処理方法:<br /><br /> **1** = 成功して終了します。<br /><br /> **2** = 失敗して終了します。<br /><br /> **3** = 次のステップに進みます。<br /><br /> **4** = ステップに移動します。|  
|**on_success_step_id**|**int**|**on_success_action**が**4**の場合、次に実行するステップを示します。|  
|**on_fail_action**|**nvarchar (4000)**|ステップが失敗した場合に実行する動作。 値は **、on_success_action**の場合と同じです。|  
|**on_fail_step_id**|**int**|**on_fail_action**が**4**の場合、次に実行するステップを示します。|  
|**サーバー**|**sysname**|予約済み。|  
|**database_name**|**sysname**|ステップの[!INCLUDE[tsql](../../includes/tsql-md.md)]場合、これはコマンドが実行されるデータベースです。|  
|**database_user_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合は、コマンドを実行するデータベース ユーザー コンテキスト。|  
|**retry_attempts**|**int**|ステップを正常に実行できない場合、コマンドを再試行する最大回数。この回数に達すると、ステップが失敗したと判断されます。|  
|**retry_interval**|**int**|再試行の間隔 (分単位)。|  
|**os_run_priority**|**ヴァルチャル(4000)**|予約済み。|  
|**output_file_name**|**ヴァルチャル(200)**|コマンド出力を書き込むファイル[!INCLUDE[tsql](../../includes/tsql-md.md)](および**CmdExec**ステップのみ)。|  
|**last_run_outcome**|**int**|最後に実行したときのステップの結果。<br /><br /> **0** = 失敗<br /><br /> **1** = 成功しました<br /><br /> **3** = 取り消し済み<br /><br /> **5** = 不明|  
|**last_run_duration**|**int**|最後に実行したときのステップの経過時間 (秒単位)。|  
|**last_run_retries**|**int**|最後にステップを実行した時点でコマンドが再試行された回数。|  
|**last_run_date**|**int**|ステップの実行が最後に開始された日付。|  
|**last_run_time**|**int**|ステップが最後に実行を開始した時刻。|  
|**proxy_id**|**int**|ジョブ ステップのプロキシ。|  
  
 これはジョブ・スケジュールの結果セットです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|すべてのジョブで一意なスケジュール識別子。|  
|**schedule_name**|**sysname**|スケジュールの名前 (このジョブのみで一意)。|  
|**有効**|**int**|スケジュールがアクティブかどうか (**1**) か非アクティブか (**0**) 。|  
|**freq_type**|**int**|ジョブを実行するタイミングを示す値:<br /><br /> **1** = 1 回<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16** = 月<br /><br /> **32** = 月単位 **、freq_interval**に対する相対値<br /><br /> **64** = **SQLServerAgent**サービスの開始時に実行します。|  
|**freq_interval**|**int**|ジョブが実行される日数。 値は **、freq_type**の値によって異なります。 詳細については[、「sp_add_schedule &#40;の SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_type**|**Int**|**freq_subday_interval**の単位。 詳細については[、「sp_add_schedule &#40;の SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_subday_interval**|**int**|ジョブの実行ごとに発生する**freq_subday_type**期間の数。 詳細については[、「sp_add_schedule &#40;の SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_relative_interval**|**int**|毎月の**freq_interval**のスケジュール済みジョブの発生。 詳細については[、「sp_add_schedule &#40;の SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)|  
|**freq_recurrence_factor**|**int**|ジョブのスケジュールされた実行までの月数。|  
|**active_start_date**|**int**|ジョブの実行を開始する日付。|  
|**active_end_date**|**int**|ジョブの実行を終了する日付。|  
|**active_start_time**|**int**|active_start_dateでジョブの実行を開始する時間 **。**|  
|**active_end_time**|**int**|**active_end_date**でジョブの実行を終了する時間。|  
|**date_created**|**datetime**|スケジュールが作成された日付。|  
|**schedule_description**|**nvarchar (4000)**|スケジュールの英語の説明 (要求された場合)。|  
|**next_run_date**|**int**|スケジュールが次にジョブを実行する日付。|  
|**next_run_time**|**int**|スケジュールが次にジョブを実行する時刻。|  
|**schedule_uid**|**uniqueidentifier**|スケジュールの識別子。|  
|**job_count**|**int**|このスケジュールを参照するジョブの数。|  
  
 次に、ジョブターゲット サーバーに関する結果セットを示します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ターゲット サーバーの識別子。|  
|**server_name**|**nvarchar(30)**|対象サーバーのコンピューター名。|  
|**enlist_date**|**datetime**|ターゲット サーバーがマスタ サーバーに登録された日付。|  
|**last_poll_date**|**datetime**|ターゲット サーバーが最後にマスタ サーバーをポーリングした日付。|  
|**last_run_date**|**int**|ターゲット サーバーでジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ターゲット サーバーでジョブの実行を最後に開始した時刻。|  
|**last_run_duration**|**int**|このターゲット サーバーで最後に実行されたジョブの期間。|  
|**last_run_outcome**|**tinyint**|このサーバーで最後に実行されたジョブの結果:<br /><br /> **0** = 失敗<br /><br /> **1** = 成功しました<br /><br /> **3** = 取り消し済み<br /><br /> **5** = 不明|  
|**last_outcome_message**|**nvarchar(1024)**|このターゲット サーバーで最後に実行されたジョブからの結果メッセージ。|  
  
## <a name="permissions"></a>アクセス許可  
 既定では **、sysadmin**固定サーバー ロールのメンバは、このストアド プロシージャを実行できます。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 **SQLAgentUserRole**のメンバーは、自分が所有するジョブのみを表示できます。 **sysadmin** **、SQLAgentReaderRole**、および**SQLAgentOperatorRole**のメンバーは、すべてのローカル およびマルチサーバー ジョブを表示できます。  
  
## <a name="examples"></a>例  
  
### <a name="a-list-information-for-all-jobs"></a>A. すべてのジョブの情報を一覧表示する  
 次の例では、`sp_help_job`パラメータを指定しないプロシージャを実行して、データベースで現在定義されているすべてのジョブの情報`msdb`を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_job ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-matching-a-specific-criteria"></a>B. 特定の条件に一致するジョブの情報の一覧表示  
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
 [&#41;&#40;&#40;sp_add_job](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_delete_job &#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_update_job&#40;のトランザクション SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
