---
title: sp_help_schedule (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_help_schedule
- sp_help_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_schedule
ms.assetid: b2fc4ce1-0a8e-44d2-b206-7dc7b258d8c9
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1803a5a2842d40700cc4b0f82c800cfbb6cc2e05
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpschedule-transact-sql"></a>sp_help_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スケジュールについての情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_schedule   
     [ @schedule_id = ] id ,  
     [ @schedule_name = ] 'schedule_name'   
     [ , [ @attached_schedules_only = ] attached_schedules_only ]  
     [ , [ @include_description = ] include_description ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@schedule_id =** ] *id*  
 一覧表示するスケジュールの識別子を指定します。 *schedule_name*は**int**、既定値はありません。 いずれか*schedule_id*または*schedule_name*指定することがあります。  
  
 [ **@schedule_name =** ] **'***schedule_name***'**  
 一覧表示するスケジュールの名前を指定します。 *schedule_name*は**sysname**、既定値はありません。 いずれか*schedule_id*または*schedule_name*指定することがあります。  
  
 [ **@attached_schedules_only** =] *attached_schedules_only* ]  
 ジョブがアタッチされているスケジュールのみを表示するかどうかを指定します。 *attached_schedules_only*は**ビット**、既定値は**0**します。 ときに*attached_schedules_only*は**0**、すべてのスケジュールが表示されます。 ときに*attached_schedules_only*は**1**、結果セットには、ジョブに関連付けられているスケジュールのみが含まれています。  
  
 [ **@include_description** =] *include_description*  
 結果セットに説明を含めるかどうかを指定します。 *include_description*は**ビット**、既定値は**0**します。 ときに*include_description*は**0**、 *schedule_description*結果セットの列には、プレース ホルダーが含まれています。 ときに*include_description*は**1**スケジュールの説明は、結果セットに含まれます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 このプロシージャは次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|スケジュール識別番号。|  
|**schedule_uid**|**uniqueidentifier**|スケジュールの識別子。|  
|**schedule_name**|**sysname**|スケジュールの名前。|  
|**enabled**|**int**|スケジュールが有効かどうか (**1**) または有効でない (**0**)。|  
|**freq_type**|**int**|ジョブが実行されるときを示す値。<br /><br /> **1** = 1 回<br /><br /> **4** = 毎日<br /><br /> **8** = 毎週<br /><br /> **16**毎月を =<br /><br /> **32** = 毎月、相対的な**freq_interval**<br /><br /> **64** SQLServerAgent サービスの起動時に実行を = です。|  
|**freq_interval**|**int**|日数は、ジョブが実行されるとします。 値は、の値によって異なります。 **freq_type**です。 詳細については、次を参照してください。 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)です。|  
|**freq_subday_type**|**int**|単位**freq_subday_interval**です。 詳細については、次を参照してください。 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)です。|  
|**freq_subday_interval**|**int**|数**freq_subday_type**ジョブの各実行間に発生する期間。 詳細については、次を参照してください。 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)です。|  
|**freq_relative_interval**|**int**|スケジュールされたジョブの発生、 **freq_interval**各月にします。 詳細については、次を参照してください。 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)です。|  
|**freq_recurrence_factor**|**int**|定期ジョブの実行間隔 (月単位)。|  
|**active_start_date**|**int**|スケジュールをアクティブにした日付。|  
|**active_end_date**|**int**|スケジュールの終了日。|  
|**active_start_time**|**int**|スケジュールを開始する時刻。|  
|**active_end_time**|**int**|スケジュールを終了する時刻。|  
|**date_created**|**datetime**|スケジュールを作成した日付。|  
|**schedule_description**|**nvarchar (4000)**|英語によるスケジュールの説明 (必要な場合)。|  
|**job_count**|**int**|このスケジュールを参照するジョブの数を返します。|  
  
## <a name="remarks"></a>解説  
 パラメーターが指定されていないときに**sp_help_schedule**インスタンス内のすべてのスケジュールに関する情報を一覧表示します。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**所有しているスケジュールのみを表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-information-for-all-schedules-in-the-instance"></a>A. インスタンスのすべてのスケジュールに関する情報を一覧表示する  
 次の例では、インスタンスのすべてのスケジュールに関する情報を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-schedule"></a>B. 特定のスケジュールに関する情報を一覧表示する  
 次の例では、`NightlyJobs` というスケジュールに関する情報を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
