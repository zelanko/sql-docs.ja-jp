---
title: "sp_help_jobsteplog (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_jobsteplog_TSQL
- sp_help_jobsteplog
dev_langs: TSQL
helpviewer_keywords: sp_help_jobsteplog
ms.assetid: 1a0be7b1-8f31-4b4c-aadb-586c0e00ed04
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c6c6e778a416f6e8e5d615a435a2be6c1e6a097
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpjobsteplog-transact-sql"></a>sp_help_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のメタデータを返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブ ステップのログです。 **sp_help_jobsteplog**実際のログは返しません。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
     [ , [ @step_id = ] step_id ]  
     [ , [ @step_name = ] 'step_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@job_id =**] **'***job_id***'**  
 ジョブ ステップ ログ情報を返すジョブの識別番号を指定します。 *job_id*は**int**、既定値は NULL です。  
  
 [  **@job_name =**] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**NULL の既定値です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@step_id =**] *step_id*  
 ジョブ ステップの識別番号を指定します。 指定しない場合は、ジョブのすべてのステップが対象となります。 *step_id*は**int**、既定値は NULL です。  
  
 [  **@step_name =**] **'***step_name***'**  
 ジョブ ステップの名前を指定します。 *step_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの一意識別子。|  
|**job_name**|**sysname**|ジョブの名前。|  
|**step_id**|**int**|ジョブ ステップの識別子。 たとえば、ステップ、ジョブの最初の手順は、その*step_id*は 1 です。|  
|**step_name**|**sysname**|ジョブ ステップの名前。|  
|**step_uid**|**uniqueidentifier**|システムによって生成される、ジョブ ステップの一意識別子。|  
|**date_created**|**datetime**|ステップが作成された日付。|  
|**date_modified**|**datetime**|ステップが最後に変更された日付。|  
|**log_size**|**float**|ジョブ ステップ ログのサイズ (MB 単位)。|  
|**ログ**|**nvarchar(max)**|ジョブ ステップのログ出力。|  
  
## <a name="remarks"></a>解説  
 **sp_help_jobsteplog**では、 **msdb**データベース。  
  
## <a name="permissions"></a>Permissions  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**自分が所有するジョブ ステップのジョブ ステップ ログのメタデータのみを表示できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returns-job-step-log-information-for-all-steps-in-a-specific-job"></a>A. 特定のジョブ内にあるすべてのステップに関するジョブ ステップ ログ情報を返す  
 次の例では、`Weekly Sales Data Backup` という名前のジョブに関する、すべてのジョブ ステップ ログ情報を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup' ;  
GO  
```  
  
### <a name="b-return-job-step-log-information-about-a-specific-job-step"></a>B. 特定のジョブ ステップに関するジョブ ステップ ログ情報を返す  
 次の例では、`Weekly Sales Data Backup` という名前のジョブ内にある最初のジョブ ステップに関するジョブ ステップ ログ情報を返します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_jobstep &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [sp_delete_jobstep &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql.md)   
 [sp_delete_jobsteplog &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)   
 [SQL Server エージェント ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
