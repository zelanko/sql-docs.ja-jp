---
title: sp_add_job (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a71f128947a3e8acc08760ed19c31af949210384
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spaddjob-transact-sql"></a>sp_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL Server エージェント サービスによって実行される新しいジョブを追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_job [ @job_name = ] 'job_name'  
     [ , [ @enabled = ] enabled ]   
     [ , [ @description = ] 'description' ]   
     [ , [ @start_step_id = ] step_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @category_id = ] category_id ]   
     [ , [ @owner_login_name = ] 'login' ]   
     [ , [ @notify_level_eventlog = ] eventlog_level ]   
     [ , [ @notify_level_email = ] email_level ]   
     [ , [ @notify_level_netsend = ] netsend_level ]   
     [ , [ @notify_level_page = ] page_level ]   
     [ , [ @notify_email_operator_name = ] 'email_name' ]   
          [ , [ @notify_netsend_operator_name = ] 'netsend_name' ]   
     [ , [ @notify_page_operator_name = ] 'page_name' ]   
     [ , [ @delete_level = ] delete_level ]   
     [ , [ @job_id = ] job_id OUTPUT ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_name =** ] **'***job_name***'**  
 ジョブの名前を指定します。 名前が一意であり、割合を含めることはできません (**%**) 文字です。 *job_name*は**nvarchar (128)**、既定値はありません。  
  
 [ **@enabled =** ] *enabled*  
 追加されるジョブの状態を指定します。 *有効になっている*は**tinyint**の既定値は 1 (有効) です。 場合**0**ジョブが有効でないと、そのスケジュールに従って実行されません。 ただし、これを手動で実行します。  
  
 [ **@description =** ] **'***description***'**  
 ジョブの説明を指定します。 *説明*は**nvarchar (512)**、既定値は NULL です。 場合*説明*は省略すると、「使用可能な説明はありません」が使用されます。  
  
 [ **@start_step_id =** ] *step_id*  
 ジョブで実行する最初のステップの ID 番号を指定します。 *step_id*は**int**、既定値は 1 です。  
  
 [  **@category_name =** ] **'***カテゴリ***'**  
 ジョブのカテゴリを指定します。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
 [ **@category_id =** ] *category_id*  
 ジョブ カテゴリを指定するための、言語に依存しないメカニズムを指定します。 *category_id*は**int**、既定値は NULL です。  
  
 [ **@owner_login_name =** ] **'***login***'**  
 ジョブを所有するログインの名前です。 *ログイン*は**sysname**の既定値は NULL には、現在のログイン名として解釈されます。 メンバーにのみ、 **sysadmin**固定サーバー ロールの設定またはの値を変更できます **@owner_login_name**です。 場合のメンバーでもないユーザーの**sysadmin**ロールを設定またはの値を変更**@owner_login_name**、このストアド プロシージャの実行は失敗し、エラーが返されます。  
  
 [ **@notify_level_eventlog =** ] *eventlog_level*  
 対象となるジョブのエントリをいつ Microsoft Windows アプリケーション ログに記録するかを示す値を指定します。 *eventlog_level*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|Never|  
|**1**|成功時|  
|**2** (既定値)|失敗時|  
|**3**|毎回|  
  
 [ **@notify_level_email =** ] *email_level*  
 対象となるジョブの完了後、いつ電子メールを送信するかを示す値を指定します。 *email_level*は**int**、既定値は**0**、しないことを示します。 *email_level*と同じ値を使用して*eventlog_level*です。  
  
 [ **@notify_level_netsend =** ] *netsend_level*  
 対象となるジョブの完了後、いつネットワーク メッセージを送信するかを示す値を指定します。 *netsend_level*は**int**、既定値は**0**、しないことを示します。 *netsend_level*と同じ値を使用して*eventlog_level*です。  
  
 [ **@notify_level_page =** ] *page_level*  
 対象となるジョブの完了後、いつポケットベルのメッセージを送信するかを示す値を指定します。 *page_level*は**int**、既定値は**0**、しないことを示します。 *page_level*と同じ値を使用して*eventlog_level*です。  
  
 [ **@notify_email_operator_name =** ] **'***email_name***'**  
 ときに電子メールの送信先となる相手の電子メール名*email_level*に到達します。 *email_name*は**sysname**、既定値は NULL です。  
  
 [ **@notify_netsend_operator_name =** ] **'***netsend_name***'**  
 対象となるジョブの完了時にネットワーク メッセージの送信先となるオペレーターの名前を指定します。 *netsend_name*は**sysname**、既定値は NULL です。  
  
 [ **@notify_page_operator_name =** ] **'***page_name***'**  
 対象となるジョブの完了時にポケットベルのメッセージの送信先となる相手の名前を指定します。 *page_name*は**sysname**、既定値は NULL です。  
  
 [ **@delete_level =** ] *delete_level*  
 いつジョブを削除するかを示す値を指定します。 *delete_value*は**int**、既定値は 0、つまりことはありません。 *delete_level*と同じ値を使用して*eventlog_level*です。  
  
> [!NOTE]  
>  ときに*delete_level*は**3**ジョブを 1 回だけ実行、ジョブのスケジュールに関係を定義します。 また、ジョブが自分自身を削除した場合、そのジョブのすべての履歴も削除されます。  
  
 [ **@job_id =** ] *job_id***OUTPUT**  
 ジョブの作成が成功したときにジョブに割り当てられるジョブ ID 番号を指定します。 *job_id*型の output 変数は、 **uniqueidentifier**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **@originating_server** 内に存在する**sp_add_job**は引数の下に記載されていません。 **@originating_server** 内部使用のために予約されています。  
  
 後に**sp_add_job** 、ジョブを追加するのには実行されて**sp_add_jobstep**ジョブの処理を実行するステップを追加するために使用できます。 **sp_add_jobschedule**に使用できるスケジュールを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスが、ジョブの実行に使用します。 使用して**sp_add_jobserver**を設定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス ジョブを実行、および**sp_delete_jobserver**からジョブを削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 ジョブがマルチ サーバー環境に 1 つまたは複数の対象サーバーで実行される場合を使用して**sp_apply_job_to_targets**を対象サーバーを設定またはジョブのサーバー グループを対象とします。 対象サーバーまたは対象サーバー グループからジョブを削除するには、使用**sp_remove_job_from_targets**です。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
## <a name="permissions"></a>権限  
 このストアド プロシージャを実行するには、ユーザーがのメンバーをする必要があります、 **sysadmin**固定サーバー ロール、または、次のいずれかに付与する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント固定データベース ロールに存在する、 **msdb**データベース。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらの各固定に関連付けられている特定の権限については、データベース ロールを参照してください[SQL Server エージェント固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)です。  
  
 メンバーにのみ、 **sysadmin**固定サーバー ロールの設定またはの値を変更できます **@owner_login_name**です。 場合のメンバーでもないユーザーの**sysadmin**ロールを設定またはの値を変更**@owner_login_name**、このストアド プロシージャの実行は失敗し、エラーが返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-adding-a-job"></a>A. ジョブを追加する  
 この例は、という名前の新しいジョブを追加`NightlyBackups`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-adding-a-job-with-pager-e-mail-and-net-send-information"></a>B. ポケットベル、電子メール、Net Send で情報を送るジョブを追加する  
 この例は、という名前のジョブを作成`Ad hoc Sales Data Backup`ことを通知`François Ajenstat`(ポケットベル、電子メール、またはネットワーク ポップアップ メッセージ) をジョブが失敗した場合、正常完了時にジョブを削除するとします。  
  
> [!NOTE]  
>  この例では、オペレーターがという名前の`François Ajenstat`という名前のログインと`françoisa`既に存在します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'Ad hoc Sales Data Backup',   
    @enabled = 1,  
    @description = N'Ad hoc backup of sales data',  
    @owner_login_name = N'françoisa',  
    @notify_level_eventlog = 2,  
    @notify_level_email = 2,  
    @notify_level_netsend = 2,  
    @notify_level_page = 2,  
    @notify_email_operator_name = N'François Ajenstat',  
    @notify_netsend_operator_name = N'François Ajenstat',   
    @notify_page_operator_name = N'François Ajenstat',  
    @delete_level = 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_add_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_add_jobserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_apply_job_to_targets &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_delete_jobserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_update_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
