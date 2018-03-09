---
title: "sp_help_jobschedule (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- sp_help_jobschedule
- sp_help_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobschedule
ms.assetid: 2cded902-9272-4667-ac4b-a4f95a9f008e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 87131f3a5347f24593798bbb81e9f81494897593
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sphelpjobschedule-transact-sql"></a>sp_help_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  によって使用されるジョブのスケジュールに関する情報を返します[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]自動化された操作を実行します。  
 
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobschedule { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @schedule_name = ] 'schedule_name' ]  
     [ , [ @schedule_id = ] schedule_id ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id=** ] *job_id*  
 ジョブの識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name=** ] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> **注:**か*job_id*または*job_name*指定する必要がありますが両方指定することはできません。  
  
 [ **@schedule_name=** ] **'***schedule_name***'**  
 ジョブのスケジュール アイテムの名前を指定します。 *schedule_name*は**sysname**、既定値は NULL です。  
  
 [ **@schedule_id=** ] *schedule_id*  
 ジョブのスケジュール アイテムの識別番号を指定します。 *schedule_id*は**int**、既定値は NULL です。  
  
 [ **@include_description=** ] *include_description*  
 結果セットにスケジュールの説明を含めるかどうかを指定します。 *include_description*は**ビット**、既定値は**0**します。 ときに*include_description*は**0**スケジュールの説明が結果セットに含まれません。 ときに*include_description*は**1**スケジュールの説明は、結果セットに含まれます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|スケジュール識別番号。|  
|**schedule_name**|**sysname**|スケジュールの名前。|  
|**enabled**|**int**|スケジュールが有効かどうか (**1**) または有効でない (**0**)。|  
|**freq_type**|**int**|ジョブが実行されるときを示す値。<br /><br /> **1** = 1 回<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32** = 毎月、相対的な**freq_interval**<br /><br /> **64** = 時に実行**SQLServerAgent**サービスの開始。|  
|**freq_interval**|**int**|日数は、ジョブが実行されるとします。 値は、の値によって異なります。 **freq_type**です。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)。|  
|**freq_subday_type**|**int**|単位**freq_subday_interval**です。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)。|  
|**freq_subday_interval**|**int**|数**freq_subday_type**ジョブの各実行間に発生する期間。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)。|  
|**freq_relative_interval**|**int**|スケジュールされたジョブの発生、 **freq_interval**各月にします。 詳細については、次を参照してください。 [sp_add_schedule (& a) #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)。|  
|**freq_recurrence_factor**|**int**|定期ジョブの実行間隔 (月単位)。|  
|**active_start_date**|**int**|スケジュールをアクティブにした日付。|  
|**active_end_date**|**int**|スケジュールの終了日。|  
|**active_start_time**|**int**|スケジュールを開始する時刻。|  
|**active_end_time**|**int**|スケジュールを終了する時刻。|  
|**date_created**|**datetime**|スケジュールを作成した日付。|  
|**schedule_description**|**nvarchar (4000)**|値から派生したスケジュールの英語版の説明**msdb.dbo.sysschedules**です。 ときに*include_description*は**0**、この列には示すテキストが、説明が要求されていないことが含まれています。|  
|**next_run_date**|**int**|スケジュールで次にジョブを実行する日付。|  
|**next_run_time**|**int**|スケジュールで次にジョブを実行する時刻。|  
|**schedule_uid**|**uniqueidentifier**|スケジュールの識別子。|  
|**job_count**|**int**|返されたジョブの数。|  
  
> **注:****sp_help_jobschedule**から値を返します、**では**と**dbo.sysschedules**システム テーブルに**msdb**. **sysjobschedules** 20 分ごとに更新します。 そのため、このストアド プロシージャから返される値に影響が生じることがあります。  
  
## <a name="remarks"></a>解説  
 パラメーターの**sp_help_jobschedule**特定の組み合わせでのみ使用できます。 場合*schedule_id*指定すると、どちらも*job_id*も*job_name*を指定できます。 それ以外の場合、 *job_id*または*job_name*でパラメーターを使用できます*schedule_name*です。  
  
## <a name="permissions"></a>権限  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**自分が所有するジョブ スケジュールのプロパティだけを表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-job-schedule-for-a-specific-job"></a>A. 特定のジョブのジョブ スケジュールを返す  
 次の例は、という名前のジョブのスケジュール情報を返します`BackupDatabase`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule  
    @job_name = N'BackupDatabase' ;  
GO  
```  
  
### <a name="b-returning-the-job-schedule-for-a-specific-schedule"></a>B. 特定のスケジュールのジョブ スケジュールを返す  
 次の例では、`NightlyJobs` という名前のスケジュールと、`RunReports` という名前のジョブの情報を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule   
    @job_name = N'RunReports',  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="c-returning-the-job-schedule-and-schedule-description-for-a-specific-schedule"></a>C. 特定スケジュールのジョブ スケジュールとスケジュール説明を返す  
 次の例では、`NightlyJobs` という名前のスケジュールと、`RunReports` という名前のジョブの情報を返します。 返される結果セットには、スケジュールの説明が含まれます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobschedule  
    @job_name = N'RunReports',  
    @schedule_name = N'NightlyJobs',  
    @include_description = 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_schedule &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_update_schedule &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
