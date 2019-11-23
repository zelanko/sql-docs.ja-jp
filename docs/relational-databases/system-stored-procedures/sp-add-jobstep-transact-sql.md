---
title: sp_add_jobstep (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_jobstep_TSQL
- sp_add_jobstep
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobstep
ms.assetid: 97900032-523d-49d6-9865-2734fba1c755
author: stevestein
ms.author: sstein
ms.openlocfilehash: b679f34e16b0f22018357f3c6fd6a531d283b2bc
ms.sourcegitcommit: df1f71231f8edbdfe76e8851acf653c25449075e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2019
ms.locfileid: "70810543"
---
# <a name="sp_add_jobstep-transact-sql"></a>sp_add_jobstep (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  SQL エージェントジョブにステップ (操作) を追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
  > [!IMPORTANT]  
  > [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では、ほとんどの SQL Server エージェントジョブの種類はサポートされていません。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。
  
## <a name="syntax"></a>構文  
  
```
sp_add_jobstep [ @job_id = ] job_id | [ @job_name = ] 'job_name'   
     [ , [ @step_id = ] step_id ]   
     { , [ @step_name = ] 'step_name' }   
     [ , [ @subsystem = ] 'subsystem' ]   
     [ , [ @command = ] 'command' ]   
     [ , [ @additional_parameters = ] 'parameters' ]   
          [ , [ @cmdexec_success_code = ] code ]   
     [ , [ @on_success_action = ] success_action ]   
          [ , [ @on_success_step_id = ] success_step_id ]   
          [ , [ @on_fail_action = ] fail_action ]   
          [ , [ @on_fail_step_id = ] fail_step_id ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @database_user_name = ] 'user' ]   
     [ , [ @retry_attempts = ] retry_attempts ]   
     [ , [ @retry_interval = ] retry_interval ]   
     [ , [ @os_run_priority = ] run_priority ]   
     [ , [ @output_file_name = ] 'file_name' ]   
     [ , [ @flags = ] flags ]   
     [ , { [ @proxy_id = ] proxy_id   
         | [ @proxy_name = ] 'proxy_name' } ]  
```  
  
## <a name="arguments"></a>引数  
ステップを追加するジョブの識別番号を `[ @job_id = ] job_id` します。 *job_id*は**uniqueidentifier**,、既定値は NULL です。  
  
ステップを追加するジョブの名前 `[ @job_name = ] 'job_name'` ます。 *job_name*は**sysname**,、既定値は NULL です。  
  
> [!NOTE]  
>  *Job_id*または*job_name*のいずれかを指定する必要がありますが、両方を指定することはできません。  
  
ジョブステップのシーケンス id 番号を `[ @step_id = ] step_id` します。 ステップの識別番号は**1**から始まり、ギャップなしで増分されます。 既存のシーケンスにステップを挿入すると、シーケンス番号が自動的に調整されます。 *Step_id*が指定されていない場合は、値が指定されます。 *step_id*は**int**,、既定値は NULL です。  
  
ステップの名前 `[ @step_name = ] 'step_name'` ます。 *step_name*は**sysname**であり、既定値はありません。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントサービスが*コマンド*を実行するために使用するサブシステムを `[ @subsystem = ] 'subsystem'` します。 *サブシステム*は**nvarchar (40)** ,、これらの値のいずれかを指定することができます。  
  
|ReplTest1|[説明]|  
|-----------|-----------------|  
|'**ACTIVESCRIPTING**'|アクティブスクリプト<br /><br /> **\*\* 重要 \*\*** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|'**CMDEXEC**'|オペレーティング システム コマンドまたは実行可能なプログラム|  
|'**DISTRIBUTION**'|レプリケーションディストリビューションエージェントジョブ|  
|'**SNAPSHOT**'|レプリケーションスナップショットエージェントジョブ|  
|"**ログリーダー**"|レプリケーションログリーダーエージェントジョブ|  
|'**MERGE**'|レプリケーション マージ エージェント ジョブ|  
|'**QueueReader**'|レプリケーションキューリーダーエージェントジョブ|  
|'**ANALYSISQUERY**'|Analysis Services クエリ (MDX、DMX)。|  
|'**ANALYSISCOMMAND**'|Analysis Services コマンド (XMLA)|  
|'**Dts**'|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ実行|  
|'**PowerShell**'|PowerShell スクリプト|  
|'**TSQL**' (既定値)|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント|  
  
*サブシステム*を介して**SQLServerAgent**サービスによって実行されるコマンドを `[ @command = ] 'command'` します。 *コマンド*は**nvarchar (max)** ,、既定値は NULL です。 SQL Server エージェントでは、ソフトウェア プログラムを記述するときの変数と同じような柔軟性を持つトークン置換を使用できます。  
  
> [!IMPORTANT]  
>  エスケープマクロには、ジョブステップで使用されるすべてのトークンが含まれている必要があります。そうでない場合、これらのジョブステップは失敗します。 さらに、トークン名をかっこで囲み、トークン構文の先頭にドル記号 (`$`) を付ける必要があります。 例 :  
>   
>  *マクロ名*の `$(ESCAPE_` `(DATE))`  
  
 これらのトークンの詳細と、新しいトークン構文を使用するジョブステップの更新については、「[ジョブステップでのトークンの使用](../../ssms/agent/use-tokens-in-job-steps.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Windows イベント ログに対して書き込みのアクセス許可を持っている Windows ユーザーであればだれでも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告または WMI 警告によってアクティブ化されるジョブ ステップにアクセスできます。 このセキュリティ上のリスクを避けるために、警告によってアクティブになるジョブで使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント トークンは、既定で無効になっています。 このようなトークンには、 **A-DBN**、 **A-SVR**、 **A-ERR**、 **A-SEV**、 **A-MSG**、および **WMI(** _プロパティ_ **)** があります。 このリリースでは、トークンの使用はすべての警告に拡張されていることに注意してください。  
>   
>  これらのトークンを使用する必要がある場合は、まず、Administrators グループなどの信頼されている Windows セキュリティ グループのメンバーのみが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するコンピューターのイベント ログに対して書き込みのアクセス許可を持っていることを確認してください。 確認したら、[オブジェクト エクスプローラー] で **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** をクリックします。次に、 **[警告システム]** ページで、 **[警告に応答するすべてのジョブのトークンを置き換える]** チェック ボックスをオンにして、これらのトークンを有効にします。  
  
`[ @additional_parameters = ] 'parameters'` の [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]*パラメーター*は**ntext**,、既定値は NULL です。  
  
**CmdExec**サブシステムコマンドによって返された値を `[ @cmdexec_success_code = ] code` して、*コマンド*が正常に実行されたことを示します。 *コード*は**int**,、既定値は**0**です。  
  
ステップが成功した場合に実行するアクションを `[ @on_success_action = ] success_action` します。 *success_action*は**tinyint**で、次のいずれかの値を指定できます。  
  
|ReplTest1|説明 (アクション)|  
|-----------|----------------------------|  
|**1** (既定値)|成功時に終了|  
|**2**|失敗した状態で終了します。|  
|**3**|次のステップに進みます。|  
|**4**|手順に進む*on_success_step_id*|  
  
ステップが成功し、 *success_action*が**4**の場合に実行する、このジョブのステップの ID を `[ @on_success_step_id = ] success_step_id` します。 *success_step_id*は**int**,、既定値は**0**です。  
  
ステップが失敗した場合に実行するアクションを `[ @on_fail_action = ] fail_action` します。 *fail_action*は**tinyint**で、次のいずれかの値を指定できます。  
  
|ReplTest1|説明 (アクション)|  
|-----------|----------------------------|  
|**1**|成功時に終了|  
|**2** (既定値)|失敗した状態で終了します。|  
|**3**|次のステップに進みます。|  
|**4**|手順に進む*on_fail_step_id*|  
  
ステップが失敗し、 *fail_action*が**4**の場合に実行する、このジョブのステップの ID を `[ @on_fail_step_id = ] fail_step_id` します。 *fail_step_id*は**int**,、既定値は**0**です。  
  
`[ @server = ] 'server'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *サーバー*は**nvarchar (30)** ,、既定値は NULL です。  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] の手順を実行するデータベースの名前を `[ @database_name = ] 'database'` します。 *データベースのデータ*型は**sysname**で、既定値は NULL です。この場合、 **master**データベースが使用されます。 角かっこ ([]) で囲まれた名前は使用できません。 ActiveX ジョブステップの場合、*データベース*は、ステップで使用するスクリプト言語の名前です。  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] の手順を実行するときに使用するユーザーアカウントの名前を `[ @database_user_name = ] 'user'` します。 *user*の部分は**sysname**で、既定値は NULL です。 *ユーザー*が NULL の場合、ステップは*データベース*のジョブ所有者のユーザーコンテキストで実行されます。  このパラメーターは、ジョブの所有者が SQL Server sysadmin である場合にのみ SQL Server エージェントに含まれます。 その場合、指定された Transact-sql ステップは、指定された SQL Server ユーザー名のコンテキストで実行されます。 ジョブの所有者が SQL Server sysadmin でない場合、Transact-sql ステップは常にこのジョブを所有するログインのコンテキストで実行され、@database_user_name パラメーターは無視されます。  
  
このステップが失敗した場合に使用する再試行回数を `[ @retry_attempts = ] retry_attempts` します。 *retry_attempts*は**int**,、既定値は**0**,、これは再試行がないことを示します。  
  
再試行の間隔を分単位で `[ @retry_interval = ] retry_interval` します。 *retry_interval*は**int**,、既定値は**0,、** **0**分間隔を示します。  
  
`[ @os_run_priority = ] run_priority` 予約済みです。  
  
この手順の出力を保存するファイルの名前 `[ @output_file_name = ] 'file_name'` ます。 *file_name*は**nvarchar (200)** ,、既定値は NULL です。 *file_name*には、[*コマンド*] に一覧表示されているトークンを1つ以上含めることができます。 このパラメーターは、[!INCLUDE[tsql](../../includes/tsql-md.md)]、 **CmdExec**、 **PowerShell**、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サブシステムで実行されているコマンドでのみ有効です。  
  
`[ @flags = ] flags` は、動作を制御するオプションです。 *フラグ*は**int**,、これらの値のいずれかを指定できます。  
  
|ReplTest1|[説明]|  
|-----------|-----------------|  
|**0** (既定値)|出力ファイルを上書きする|  
|**2**|出力ファイルに追加|  
|**4**|ステップの履歴にジョブステップの出力を書き込む [!INCLUDE[tsql](../../includes/tsql-md.md)]|  
|**8**|テーブルにログを書き込む (既存の履歴を上書きする)|  
|**16**|ログをテーブルに書き込む (既存の履歴に追加する)|  
|**32**|すべての出力をジョブ履歴に書き込みます。|  
|**64**|Windows イベントを作成して、Cmd jobstep が中止するシグナルとして使用する|  
  
ジョブステップを実行するプロキシの id 番号を `[ @proxy_id = ] proxy_id` します。 *proxy_id*の型は**int**で、既定値は NULL です。 *Proxy_id*が指定されておらず、 *proxy_name*が指定されておらず、 *user_name*が指定されていない場合、ジョブステップは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービスアカウントとして実行されます。  
  
`[ @proxy_name = ] 'proxy_name'`、ジョブステップを実行するプロキシの名前を指定します。 *proxy_name*の型は**sysname**で、既定値は NULL です。 *Proxy_id*が指定されておらず、 *proxy_name*が指定されておらず、 *user_name*が指定されていない場合、ジョブステップは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのサービスアカウントとして実行されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 [InclusionThresholdSetting]  
  
## <a name="remarks"></a>Remarks  
 **sp_add_jobstep**は、 **msdb**データベースから実行する必要があります。  
  
 SQL Server Management Studio は、簡単かつ直観的な方法でジョブを管理するためのツールで、ジョブ体系の作成および管理に最適です。  
  
 ジョブステップの作成者が**sysadmin**固定セキュリティロールのメンバーである場合を除き、ジョブステップでプロキシを指定する必要があります。  
  
 プロキシは*proxy_name*または*proxy_id*によって識別できます。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「[SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 ジョブステップの作成者は、ジョブステップのプロキシへのアクセス権を持っている必要があります。 **Sysadmin**固定サーバーロールのメンバーは、すべてのプロキシにアクセスできます。 他のユーザーには、明示的にプロキシへのアクセスを許可する必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、Sales データベースのデータベースアクセスを読み取り専用に変更するジョブステップを作成します。 さらに、この例では、5分間待機した後に再試行が5回発生する5回の再試行が指定されています。  
  
> [!NOTE]  
>  この例では、`Weekly Sales Data Backup` ジョブが既に存在していることを前提としています。  
  
```sql
USE msdb;  
GO  
EXEC sp_add_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_name = N'Set database to read only',  
    @subsystem = N'TSQL',  
    @command = N'ALTER DATABASE SALES SET READ_ONLY',
    @retry_attempts = 5,  
    @retry_interval = 5 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ジョブの表示または変更](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [transact-sql &#40;  の&#41; sp_add_schedule](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
 [transact-sql &#40;  の&#41; sp_delete_jobstep](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)  
 [transact-sql &#40;  の&#41; sp_help_job](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)  
 [transact-sql &#40;  の&#41; sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)  
 [transact-sql &#40;  の&#41; sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
