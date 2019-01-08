---
title: sp_update_jobstep (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobstep
- sp_update_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobstep
ms.assetid: e158802c-c347-4a5d-bf75-c03e5ae56e6b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 102e9122b93938b8e16d2e8714eed8d1372d21ad
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591526"
---
# <a name="spupdatejobstep-transact-sql"></a>sp_update_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  自動化された処理の実行に使用するジョブのステップに関する設定を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_jobstep   
     {   [@job_id =] job_id   
       | [@job_name =] 'job_name' } ,  
     [@step_id =] step_id  
     [ , [@step_name =] 'step_name' ]  
     [ , [@subsystem =] 'subsystem' ]   
     [ , [@command =] 'command' ]  
     [ , [@additional_parameters =] 'parameters' ]  
     [ , [@cmdexec_success_code =] success_code ]  
     [ , [@on_success_action =] success_action ]   
     [ , [@on_success_step_id =] success_step_id ]  
     [ , [@on_fail_action =] fail_action ]   
     [ , [@on_fail_step_id =] fail_step_id ]  
     [ , [@server =] 'server' ]   
     [ , [@database_name =] 'database' ]  
     [ , [@database_user_name =] 'user' ]   
     [ , [@retry_attempts =] retry_attempts ]  
     [ , [@retry_interval =] retry_interval ]   
     [ , [@os_run_priority =] run_priority ]  
     [ , [@output_file_name =] 'file_name' ]   
     [ , [@flags =] flags ]  
     [ ,  {   [ @proxy_id = ] proxy_id   
            | [ @proxy_name = ] 'proxy_name' }   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id =**] *job_id*  
 ステップが属するジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@job_name =**] **'**_job_name_**'**  
 ステップが属するジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@step_id =**] *step_id*  
 変更するジョブ ステップの識別番号を指定します。 この番号は変更できません。 *step_id*は**int**、既定値はありません。  
  
 [  **@step_name =**] **'**_step_name_**'**  
 ステップの新しい名前を指定します。 *step_name*は**sysname**、既定値は NULL です。  
  
 [  **@subsystem =**] **'**_サブシステム_**'**  
 実行する Microsoft SQL Server エージェントによって使用されるサブシステム*コマンド*します。 *サブシステム*は**nvarchar (40)**、既定値は NULL です。  
  
 [  **@command =**] **'**_コマンド_**'**  
 使用して実行するコマンド*サブシステム*します。 *コマンド*は**nvarchar (max)**、既定値は NULL です。  
  
 [  **@additional_parameters =**] **'**_パラメーター_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@cmdexec_success_code =**] *success_code*  
 によって返される値、 **CmdExec**を示すサブシステム コマンド*コマンド*が正常に実行します。 *success_code*は**int**、既定値は NULL です。  
  
 [ **@on_success_action =**] *success_action*  
 ステップが成功した場合に実行するアクション。*success_action*は**tinyint**、既定値は null の場合、これらの値のいずれかを指定できます。  
  
|値|説明 (動作)|  
|-----------|----------------------------|  
|**1**|正常に終了します。|  
|**2**|失敗した状態で終了|  
|**3**|次のステップに進む|  
|**4**|手順に進みます*success_step_id します。*|  
  
 [ **@on_success_step_id =**] *success_step_id*  
 ステップが成功した場合に実行するには、このジョブ ステップの識別番号と*success_action*は**4**します。 *success_step_id*は**int**、既定値は NULL です。  
  
 [ **@on_fail_action =**] *fail_action*  
 ステップが失敗した場合に実行する動作を指定します。 *fail_action*は**tinyint**、既定値は NULL でこれらの値のいずれかを指定できます。  
  
|値|説明 (動作)|  
|-----------|----------------------------|  
|**1**|正常に終了します。|  
|**2**|失敗した状態で終了|  
|**3**|次のステップに進む|  
|**4**|手順に進みます*fail_step_id * *。*|  
  
 [ **@on_fail_step_id =**] *fail_step_id*  
 ステップが失敗した場合に実行するには、このジョブ ステップの識別番号と*fail_action*は**4**します。 *fail_step_id*は**int**、既定値は NULL です。  
  
 [  **@server =**] **'**_server_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *server*は**nvarchar (128)**、既定値は NULL です。  
  
 [  **@database_name =**] **'**_データベース_**'**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステップを実行するデータベースの名前を指定します。 *データベース*は**sysname**します。 角かっこ ([ ]) で囲まれた名前は使用できません。 既定値は NULL になります。  
  
 [  **@database_user_name =**] **'**_ユーザー_**'**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステップを実行するときに使用するユーザー アカウントの名前を指定します。 *ユーザー*は**sysname**、既定値は NULL です。  
  
 [ **@retry_attempts =**] *retry_attempts*  
 ステップが失敗したときに行う再試行の回数を指定します。 *retry_attempts*は**int**、既定値は NULL です。  
  
 [ **@retry_interval =**] *retry_interval*  
 再試行の間隔を分単位で指定します。 *retry_interval*は**int**、既定値は NULL です。  
  
 [  **@os_run_priority =**] *run_priority*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@output_file_name =**] **'**_file_name_**'**  
 ステップの出力を保存するファイルの名前を指定します。 *file_name*は**nvarchar (200)**、既定値は NULL です。 このパラメーターは、[!INCLUDE[tsql](../../includes/tsql-md.md)] サブシステムまたは CmdExec サブシステム上で実行されるコマンドに対してのみ有効です。  
  
 Output_file_name を NULL に設定するに設定する必要があります*output_file_name*に空の文字列 (' ') や、空白文字の文字列を使用できない、 **char (32)** 関数。 この引数に空文字列を設定する例を次に示します。  
  
 **@output_file_name = ' '**  
  
 [ **@flags =**] *flags*  
 動作を制御するオプションを指定します。 *フラグ*は**int**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0** (既定値)|出力ファイルを上書き|  
|**2**|出力ファイルに追加|  
|**4**|Transact-SQL ジョブ ステップの出力をステップ履歴に書き込む|  
|**8**|ログをテーブルに書き込む (既存の履歴を上書き)|  
|**16**|ログをテーブルに書き込む (既存の履歴に追加)|  
  
 [ **@proxy_id**= ] *proxy_id*  
 ジョブ ステップを実行するプロキシの ID 番号を指定します。 *proxy_id*型は、 **int**、既定値は NULL です。 いない場合*proxy_id*が指定されていない*proxy_name*が指定されているおよび no *user_name*を指定すると、ジョブ ステップをサービス アカウントとして実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。  
  
 [ **@proxy_name**=] **'**_proxy_name_**'**  
 ジョブ ステップを実行するプロキシの名前を指定します。 *proxy_name*型は、 **sysname**、既定値は NULL です。 いない場合*proxy_id*が指定されていない*proxy_name*が指定されているおよび no *user_name*を指定すると、ジョブ ステップをサービス アカウントとして実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_update_jobstep**から実行する必要があります、 **msdb**データベース。  
  
 ジョブ ステップを更新すると、ジョブのバージョン番号が増えます。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 メンバーだけ**sysadmin**別のユーザーが所有するジョブ ステップを更新することができます。  
  
 ジョブ ステップでプロキシにアクセスする必要がある場合、ジョブ ステップの作成者は、ジョブ ステップのプロキシへのアクセス権を保持している必要があります。 Transact-SQL を除くすべてのサブシステムでは、プロキシ アカウントが必要です。 メンバーの**sysadmin**と使用できるすべてのプロキシにアクセスできる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロキシ エージェント サービス アカウント。  
  
## <a name="examples"></a>使用例  
 次の例では、`Weekly Sales Data Backup` ジョブの最初のステップに対して、再試行の回数を変更します。 この例を実行すると、再試行回数は `10` 回になります。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1,  
    @retry_attempts = 10 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [表示またはジョブの変更](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_delete_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
