---
title: sp_delete_jobsteplog (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
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
- sp_delete_jobsteplog
- sp_delete_jobsteplog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobsteplog
ms.assetid: e9ef4c99-abde-4038-b6a3-a25dcbaf0958
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 83299ab01c2ec8c82b979bb2193cce1a9ca87803
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spdeletejobsteplog-transact-sql"></a>sp_delete_jobsteplog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  引数で指定したすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップ ログを削除します。 維持するためにこのストアド プロシージャを使用して、 **sysjobstepslogs**テーブルに、 **msdb**データベース。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_jobsteplog { [ @job_id = ] 'job_id' | [ @job_name = ] 'job_name' }  
       [ , [ @step_id = ] step_id | [ @step_name = ] 'step_name' ]  
       [ , [ @older_than = ] 'date' ]  
       [ , [ @larger_than = ] 'size_in_bytes' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id =**] **'***job_id***'**  
 削除するジョブ ステップ ログを含むジョブのジョブ識別番号を指定します。 *job_id*は**int**、既定値は NULL です。  
  
 [ **@job_name =**] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> **注:**か*job_id*または*job_name*指定する必要がありますが両方指定することはできません。  
  
 [ **@step_id =**] *step_id*  
 ジョブ ステップ ログを削除するジョブ ステップの識別番号を指定します。 含まれていなければ、その場合は、ジョブ内のすべてのジョブ ステップ ログは削除されます**@older_than**または**@larger_than**が指定されています。 *step_id*は**int**、既定値は NULL です。  
  
 [ **@step_name =**] **'***step_name***'**  
 ジョブ ステップ ログを削除するジョブ ステップの名前を指定します。 *step_name*は**sysname**、既定値は NULL です。  
  
> **注:**か*step_id*または*step_name*を指定できますが両方指定することはできません。  
  
 [  **@older_than =**] **'***日付***'**  
 保持しておく一番古いジョブ ステップ ログの日時を指定します。 この日時より前のジョブ ステップ ログはすべて削除されます。 *日付*は**datetime**、既定値は NULL です。 両方**@older_than**と**@larger_than**を指定できます。  
  
 [ **@larger_than =**] **'***size_in_bytes***'**  
 保持するジョブ ステップ ログの最大サイズをバイト単位で指定します。 このサイズより大きいすべてのジョブ ステップ ログは、削除されます。 両方**@larger_than**と**@older_than**を指定できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_delete_jobsteplog**では、 **msdb**データベース。  
  
 場合を除く引数なし**@job_id**または**@job_name**指定すると、指定されたジョブのすべてのジョブ ステップのログが削除されます。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバーだけ**sysadmin**別のユーザーによって所有されているジョブ ステップ ログを削除することができます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-removing-all-job-step-logs-from-a-job"></a>A. ジョブからすべてのジョブ ステップ ログを削除する  
 次の例では、削除、ジョブのジョブ ステップ ログをすべて`Weekly Sales Data Backup`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup';  
GO  
```  
  
### <a name="b-removing-the-job-step-log-for-a-particular-job-step"></a>B. 特定のジョブ ステップに対するジョブ ステップ ログを削除する  
 次の例では、ジョブ `Weekly Sales Data Backup` のステップ 2 に対するジョブ ステップ ログを削除します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 2;  
GO  
```  
  
### <a name="c-removing-all-job-step-logs-based-on-age-and-size"></a>C. 有効期間とサイズに基づいてすべてのジョブ ステップ ログを削除する  
 次の例では、すべてのジョブ ステップ ログは、2005 年 10 月 25 日の正午よりも古いジョブから 100 メガバイト (MB) よりも大きいを`Weekly Sales Data Backup`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobsteplog  
    @job_name = N'Weekly Sales Data Backup',  
    @older_than = '10/25/2005 12:00:00',  
    @larger_than = 104857600;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_help_jobsteplog &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)  
  
  
