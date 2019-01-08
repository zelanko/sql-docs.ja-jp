---
title: sp_add_job (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_job_TSQL
- sp_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_job
ms.assetid: 6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c6ac15a78e8689e76fc9687a6cd8784eb1fc4dd2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52537871"
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
 [  **@job_name =** ] **'**_job_name_**'**  
 ジョブの名前を指定します。 名前が一意であり、割合を含めることはできません (**%**) 文字。 *job_name*は**nvarchar (128)**、既定値はありません。  
  
 [ **@enabled =** ] *enabled*  
 追加されるジョブの状態を指定します。 *有効になっている*は**tinyint**、既定値は 1 (有効)。 場合**0**、ただし、これは手動で実行するには、ジョブが有効でないと、スケジュールに従って実行されません。  
  
 [  **@description =** ] **'**_説明_**'**  
 ジョブの説明を指定します。 *説明*は**nvarchar (512)**、既定値は NULL です。 場合*説明*は省略すると、「使用可能な説明はありません」が使用されます。  
  
 [ **@start_step_id =** ] *step_id*  
 ジョブで実行する最初のステップの ID 番号を指定します。 *step_id*は**int**、既定値は 1 です。  
  
 [  **@category_name =** ] **'**_カテゴリ_**'**  
 ジョブのカテゴリを指定します。 *カテゴリ*は**sysname**、既定値は NULL です。  
  
 [ **@category_id =** ] *category_id*  
 ジョブ カテゴリを指定するための、言語に依存しないメカニズムを指定します。 *category_id*は**int**、既定値は NULL です。  
  
 [  **@owner_login_name =** ] **'**_ログイン_**'**  
 ジョブを所有するログインの名前です。 *ログイン*は**sysname**の既定値は NULL には、現在のログイン名として解釈されます。 メンバーのみ、 **sysadmin**固定サーバー ロールの設定またはの値を変更できる **@owner_login_name**します。 場合以外のユーザーがメンバーの**sysadmin**ロールを設定またはの値を変更**@owner_login_name**、このストアド プロシージャの実行が失敗し、エラーが返されます。  
  
 [ **@notify_level_eventlog =** ] *eventlog_level*  
 対象となるジョブのエントリをいつ Microsoft Windows アプリケーション ログに記録するかを示す値を指定します。 *eventlog_level*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|Never|  
|**1**|成功時|  
|**2** (既定値)|失敗時|  
|**3**|毎回|  
  
 [ **@notify_level_email =** ] *email_level*  
 対象となるジョブの完了後、いつ電子メールを送信するかを示す値を指定します。 *email_level*は**int**、既定値は**0**、しないことを示します。 *email_level*として同じ値を使用して*eventlog_level*します。  
  
 [ **@notify_level_netsend =** ] *netsend_level*  
 対象となるジョブの完了後、いつネットワーク メッセージを送信するかを示す値を指定します。 *netsend_level*は**int**、既定値は**0**、しないことを示します。 *netsend_level*として同じ値を使用して*eventlog_level*します。  
  
 [ **@notify_level_page =** ] *page_level*  
 対象となるジョブの完了後、いつポケットベルのメッセージを送信するかを示す値を指定します。 *page_level*は**int**、既定値は**0**、しないことを示します。 *page_level*として同じ値を使用して*eventlog_level*します。  
  
 [  **@notify_email_operator_name =** ] **'**_email_name_**'**  
 ときに電子メールの送信先となる相手の電子メール名*email_level*に到達します。 *email_name*は**sysname**、既定値は NULL です。  
  
 [  **@notify_netsend_operator_name =** ] **'**_netsend_name_**'**  
 対象となるジョブの完了時にネットワーク メッセージの送信先となるオペレーターの名前を指定します。 *netsend_name*は**sysname**、既定値は NULL です。  
  
 [  **@notify_page_operator_name =** ] **'**_page_name_**'**  
 対象となるジョブの完了時にポケットベルのメッセージの送信先となる相手の名前を指定します。 *page_name*は**sysname**、既定値は NULL です。  
  
 [ **@delete_level =** ] *delete_level*  
 いつジョブを削除するかを示す値を指定します。 *delete_value*は**int**、既定値は 0、つまりことはありません。 *delete_level*として同じ値を使用して*eventlog_level*します。  
  
> [!NOTE]  
>  ときに*delete_level*は**3**ジョブを 1 回だけ実行、ジョブのスケジュールに関係を定義します。 また、ジョブが自分自身を削除した場合、そのジョブのすべての履歴も削除されます。  
  
 [  **@job_id =** ] _job_id_**出力**  
 ジョブの作成が成功したときにジョブに割り当てられるジョブ ID 番号を指定します。 *job_id*型の output 変数は、 **uniqueidentifier**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **@originating_server** 内に存在する**sp_add_job**は引数の下に記載されていません。 **@originating_server** 内部使用のため予約されています。  
  
 後**sp_add_job** 、ジョブを追加が実行された**sp_add_jobstep**ジョブの処理を実行するステップを追加するために使用できます。 **sp_add_jobschedule**に使用できるスケジュールを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスを使用して、ジョブを実行します。 使用**sp_add_jobserver**を設定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ジョブが実行されるインスタンスと**sp_delete_jobserver**からジョブを削除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。  
  
 場合は、マルチ サーバー環境で 1 つまたは複数の対象サーバーでジョブを実行するを使用して、 **sp_apply_job_to_targets**ターゲット サーバーを設定またはジョブのサーバー グループを対象にします。 対象サーバーまたは対象サーバー グループからジョブを削除するには使用**sp_remove_job_from_targets**します。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーをこのストアド プロシージャを実行するのメンバーである必要があります、 **sysadmin**固定サーバー ロール、または、次のいずれかに付与する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント固定データベース ロール内にある、 **msdb**データベース。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらの各固定に関連付けられている特定のアクセス許可については、データベース ロールを参照してください[SQL Server エージェント固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)します。  
  
 メンバーのみ、 **sysadmin**固定サーバー ロールの設定またはの値を変更できる **@owner_login_name**します。 場合以外のユーザーがメンバーの**sysadmin**ロールを設定またはの値を変更**@owner_login_name**、このストアド プロシージャの実行が失敗し、エラーが返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-adding-a-job"></a>A. ジョブを追加する  
 次の例では、`NightlyBackups` という新しいジョブを追加します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-adding-a-job-with-pager-e-mail-and-net-send-information"></a>B. ポケットベル、電子メール、Net Send で情報を送るジョブを追加する  
 次の例では、`Ad hoc Sales Data Backup` というジョブを作成します。このジョブが失敗したときにはポケットベル、電子メール、またはネットワーク ポップアップ メッセージを使って `François Ajenstat` に通知し、ジョブが正常に完了したときにはジョブを削除します。  
  
> [!NOTE]  
>  この例では、`François Ajenstat` というオペレーターと、`françoisa` というログインが存在することを前提としています。  
  
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
  
  
