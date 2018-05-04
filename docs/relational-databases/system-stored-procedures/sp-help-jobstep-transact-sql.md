---
title: sp_help_jobstep (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_help_jobstep_TSQL
- sp_help_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobstep
ms.assetid: 4a13b804-45f2-4f82-987f-42d9a57dd6db
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4b4ebc1e9ae647d770a5b77d3c0428837e8f8db9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpjobstep-transact-sql"></a>sp_help_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  によって使用されるジョブのステップに関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスを自動化された操作を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobstep { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]   
     [ , [ @step_name = ] 'step_name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id =**] **'***job_id***'**  
 ジョブ情報を返すジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name =**] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**NULL の既定値です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@step_id =**] *step_id*  
 ジョブ ステップの識別番号を指定します。 指定しない場合は、ジョブのすべてのステップが対象となります。 *step_id*は**int**、既定値は NULL です。  
  
 [ **@step_name =**] **'***step_name***'**  
 ジョブ ステップの名前を指定します。 *step_name*は**sysname**、既定値は NULL です。  
  
 [ **@suffix =**] *suffix*  
 テキストの説明を追加するかどうかを示すフラグ、**フラグ**出力内の列です。 *サフィックス*は**ビット**、既定値は**0**します。 場合*サフィックス*は**1**説明が追加されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**step_id**|**int**|ステップの一意識別子。|  
|**step_name**|**sysname**|ジョブ ステップの名前。|  
|**subsystem**|**nvarchar(40)**|ステップ コマンドを実行するサブシステム。|  
|**command**|**nvarchar(max)**|ステップで実行するコマンド。|  
|**flags**|**int**|ステップの動作を制御する値のビットマスク。|  
|**cmdexec_success_code**|**int**|**CmdExec**手順、これは、コマンドの成功のプロセス終了コード。|  
|**on_success_action**|**tinyint**|ステップが成功した場合に実行する動作。<br /><br /> **1** = 成功を報告するジョブを終了します。<br /><br /> **2** = 失敗を報告するジョブを終了します。<br /><br /> **3** = 次の手順に移動します。<br /><br /> **4** = 手順に進みます。|  
|**on_success_step_id**|**int**|場合**on_success_action** 4 を実行する次の手順を示します。|  
|**on_fail_action**|**tinyint**|ステップが失敗した場合に実行する操作。 値と同じ**on_success_action**です。|  
|**on_fail_step_id**|**int**|場合**on_fail_action** 4 を実行する次の手順を示します。|  
|**server**|**sysname**|予約されています。|  
|**database_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合は、コマンドを実行するデータベース。|  
|**database_user_name**|**sysname**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合は、コマンドを実行するデータベース ユーザー コンテキスト。|  
|**retry_attempts**|**int**|正常に実行できない場合にコマンドを再試行する最大回数。|  
|**retry_interval**|**int**|再試行する間隔 (分単位)。|  
|**os_run_priority**|**int**|予約されています。|  
|**output_file_name**|**nvarchar(200)**|コマンド出力を書き込むファイル ([!INCLUDE[tsql](../../includes/tsql-md.md)]、 **CmdExec**、および**PowerShell**ステップのみ)。|  
|**last_run_outcome**|**int**|最後に実行したときのステップの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **2** = 再試行<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**last_run_duration**|**int**|最後に実行したときのステップの経過時間 (秒単位)。|  
|**last_run_retries**|**int**|最後にステップを実行したときのコマンドの再試行回数。|  
|**last_run_date**|**int**|ステップの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ステップの実行を最後に開始した時刻。|  
|**proxy_id**|**int**|ジョブ ステップのプロキシ。|  
  
## <a name="remarks"></a>解説  
 **sp_help_jobstep**では、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**自分が所有しているジョブのジョブ ステップにのみ表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-return-information-for-all-steps-in-a-specific-job"></a>A. 特定のジョブのすべてのステップに関する情報を返す  
 次の例では、`Weekly Sales Data Backup` という名前のジョブに関する、すべてのジョブ ステップを返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-information-about-a-specific-job-step"></a>B. 特定のジョブ ステップに関する情報を返す  
 次の例は、最初のジョブ ステップという名前のジョブに関する情報を返します`Weekly Sales Data Backup`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_jobstep &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
