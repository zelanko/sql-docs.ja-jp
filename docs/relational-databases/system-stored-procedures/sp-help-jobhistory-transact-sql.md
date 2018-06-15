---
title: sp_help_jobhistory (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobhistory_TSQL
- sp_help_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobhistory
ms.assetid: a944d44e-411b-4735-8ce4-73888d4262d7
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e001e9e0ea0dd7dfdbe64a788db465125b04e414
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261821"
---
# <a name="sphelpjobhistory-transact-sql"></a>sp_help_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マルチサーバー管理ドメインに所属するサーバーのジョブに関する情報を提供します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobhistory [ [ @job_id = ] job_id ]   
     [ , [ @job_name = ] 'job_name' ]   
     [ , [ @step_id = ] step_id ]   
     [ , [ @sql_message_id = ] sql_message_id ]   
     [ , [ @sql_severity = ] sql_severity ]   
     [ , [ @start_run_date = ] start_run_date ]   
     [ , [ @end_run_date = ] end_run_date ]   
     [ , [ @start_run_time = ] start_run_time ]   
     [ , [ @end_run_time = ] end_run_time ]   
     [ , [ @minimum_run_duration = ] minimum_run_duration ]   
     [ , [ @run_status = ] run_status ]   
     [ , [ @minimum_retries = ] minimum_retries ]   
     [ , [ @oldest_first = ] oldest_first ]   
     [ , [ @server = ] 'server' ]   
     [ , [ @mode = ] 'mode' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id=** ] *job_id*  
 ジョブの識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name=** ] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
 [ **@step_id=** ] *step_id*  
 ステップの識別番号を指定します。 *step_id*は**int**、既定値は NULL です。  
  
 [ **@sql_message_id=** ] *sql_message_id*  
 ジョブの実行時に Microsoft SQL Server で返されるエラー メッセージの識別番号を指定します。 *sql_message_id*は**int**、既定値は NULL です。  
  
 [ **@sql_severity=** ] *sql_severity*  
 ジョブの実行時に SQL Server で返されるエラー メッセージの重大度を指定します。 *sql_severity*は**int**、既定値は NULL です。  
  
 [ **@start_run_date=** ] *start_run_date*  
 ジョブを開始した日付を指定します。 *start_run_date*は**int**、既定値は NULL です。 *start_run_date*する必要があります形式で入力 yyyymmdd 形式で指定、YYYY は 4 桁の年、MM は 2 桁の月、DD は 2 桁の日です。  
  
 [ **@end_run_date=** ] *end_run_date*  
 ジョブが完了した日付を指定します。 *end_run_date*は**int**、既定値は NULL です。 *end_run_date*する必要があります形式で入力 yyyymmdd 形式で指定、YYYY は 4 桁の年、MM は 2 桁の月、DD は 2 桁の日です。  
  
 [ **@start_run_time=** ] *start_run_time*  
 ジョブを開始した時刻を指定します。 *start_run_time*は**int**、既定値は NULL です。 *start_run_time*必要があります形式で入力 hhmmss で、HH は、1 日の 2 桁の時、MM は、2 桁の分、SS は、1 日の 2 桁の秒。  
  
 [ **@end_run_time=** ] *end_run_time*  
 ジョブが完了した時刻を指定します。 *end_run_time*は**int**、既定値は NULL です。 *end_run_time*必要があります形式で入力 hhmmss で、HH は、1 日の 2 桁の時、MM は、2 桁の分、SS は、1 日の 2 桁の秒。  
  
 [  **@minimum_run_duration=** ] *minimum_run_duration*  
 ジョブを完了するのに必要な最小時間を指定します。 *minimum_run_duration*は**int**、既定値は NULL です。 *minimum_run_duration*必要があります形式で入力 hhmmss で、HH は、1 日の 2 桁の時、MM は、2 桁の分、SS は、1 日の 2 桁の秒。  
  
 [ **@run_status=** ] *run_status*  
 ジョブの実行ステータス。 *run_status*は**int**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|失敗|  
|**1**|成功しました|  
|**2**|再試行 (ステップのみ)|  
|**3**|Canceled|  
|**4**|実行中メッセージ|  
|**5**|Unknown|  
  
 [ **@minimum_retries=** ] *minimum_retries*  
 ジョブの実行を再試行する最小回数を指定します。 *minimum_retries*は**int**、既定値は NULL です。  
  
 [ **@oldest_first=** ] *oldest_first*  
 ジョブを古い順に出力するかどうかを指定します。 *oldest_first*は**int**、既定値は**0**、最初にすること、最新のジョブを示します。 **1**最初、最も古いジョブを表示します。  
  
 [ **@server=** ] **'***server***'**  
 ジョブを実行したサーバーの名前を示します。 *サーバー*は**nvarchar (30)**、既定値は NULL です。  
  
 [  **@mode=** ] **'***モード***'**  
 SQL Server が結果セット内のすべての列を出力するか (**完全**) または列の概要です。 *モード*は**varchar (7)**、既定値は**概要**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 実際の列リストの値に応じて異なります*モード*です。 列の最も包括的なセットが次に示すし、ときに返される*モード*いっぱいです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|履歴エントリの識別番号。|  
|**job_id**|**uniqueidentifier**|ジョブ識別番号。|  
|**job_name**|**sysname**|ジョブ名。|  
|**step_id**|**int**|ステップ識別番号 (なります**0**ジョブ履歴の場合)。|  
|**step_name**|**sysname**|ステップ名。ジョブ履歴の場合は NULL です。|  
|**sql_message_id**|**int**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合、コマンドの実行中に最も新しく発生した [!INCLUDE[tsql](../../includes/tsql-md.md)] エラーの番号。|  
|**sql_severity**|**int**|[!INCLUDE[tsql](../../includes/tsql-md.md)] ステップの場合、コマンドの実行中に発生した最も重大な [!INCLUDE[tsql](../../includes/tsql-md.md)] エラーの重大度。|  
|**message**|**nvarchar(1024)**|ジョブまたはステップの履歴メッセージ。|  
|**run_status**|**int**|ジョブまたはステップの結果。|  
|**run_date**|**int**|ジョブまたはステップの実行を開始した日付。|  
|**run_time**|**int**|ジョブまたはステップの実行を開始した時刻。|  
|**run_duration**|**int**|ジョブまたはステップを実行してからの経過時間 (HHMMSS 形式)。|  
|**operator_emailed**|**nvarchar(20)**|このジョブに関する電子メールを送信したオペレーター。ステップ履歴の場合は NULL です。|  
|**operator_netsent**|**nvarchar(20)**|このジョブに関するネットワーク メッセージを送信したオペレーター。ステップ履歴の場合は NULL です。|  
|**operator_paged**|**nvarchar(20)**|このジョブに関するページを送信したオペレーター。ステップ履歴の場合は NULL です。|  
|**retries_attempted**|**int**|ステップの再試行回数。ジョブ履歴の場合は常に 0 です。|  
|**server**|**nvarchar(30)**|ステップまたはジョブを実行するサーバー。 常に (**ローカル**)。|  
  
## <a name="remarks"></a>解説  
 **sp_help_jobhistory**の指定されたスケジュールされたジョブの履歴レポートを返します。 どのパラメーターも指定しない場合は、レポートにはすべての定期ジョブの履歴が含まれます。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー、 **SQLAgentUserRole**データベース ロールは、自分が所有しているジョブの履歴のみを表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-job-information-for-a-job"></a>A. すべてのジョブに関する情報を一覧表示する  
 次の例は、すべてのジョブ情報を一覧表示、`NightlyBackups`ジョブです。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobhistory   
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-listing-information-for-jobs-that-match-certain-conditions"></a>B. 一定の条件に一致するジョブに関する情報を一覧表示する  
 次の例は、すべての列を出力し、ジョブ情報をすべてが失敗したジョブおよびジョブ ステップのエラー メッセージで失敗しました`50100`(ユーザー定義エラー メッセージ) と重大度`20`です。  
  
```  
USE msdb  
GO  
  
EXEC dbo.sp_help_jobhistory  
    @sql_message_id = 50100,  
    @sql_severity = 20,  
    @run_status = 0,  
    @mode = N'FULL' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
