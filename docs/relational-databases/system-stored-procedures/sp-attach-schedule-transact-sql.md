---
title: sp_attach_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_attach_schedule_TSQL
- sp_attach_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_schedule
ms.assetid: 80c80eaf-cf23-4ed8-b8dd-65fe59830dd1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f04aefa642e21901a3070d71164f50f01cbc2ec7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732845"
---
# <a name="spattachschedule-transact-sql"></a>sp_attach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ジョブのスケジュールを設定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_attach_schedule  
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     { [ @schedule_id = ] schedule_id   
     | [ @schedule_name = ] 'schedule_name' }  
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id=** ] *job_id*  
 スケジュールを追加するジョブのジョブ識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name =** ] **'***job_name***'**  
 スケジュールを追加するジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@schedule_id =** ] *schedule_id*  
 ジョブに設定するスケジュールの識別番号を指定します。 *schedule_id*は**int**、既定値は NULL です。  
  
 [ **@schedule_name =** ] **'***schedule_name***'**  
 ジョブに設定するスケジュールの名前を指定します。 *schedule_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*schedule_id*または*schedule_name*指定する必要がありますが、両方を指定することはできません。  
  
## <a name="remarks"></a>コメント  
 スケジュールとジョブは同じ所有者であることが必要です。  
  
 スケジュールは複数のジョブに対して設定できます。 ジョブは複数のスケジュールで実行できます。  
  
 このストアド プロシージャを実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 ジョブ所有者は、同時にスケジュール所有者にならなくても、ジョブをスケジュールにアタッチしたり、スケジュールからデタッチしたりできます。 ただし、呼び出し元がスケジュール所有者ではない場合、デタッチによってスケジュールにジョブがなくなっても、スケジュールを削除することはできません。  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ユーザーがジョブとスケジュールの両方を所有しているかどうかを確認します。  
  
## <a name="examples"></a>使用例  
 次の例は、名前付きのスケジュールを作成`NightlyJobs`です。 このスケジュールを使用するジョブは、毎日、サーバーの時間が `01:00` になると実行されます。 例では、ジョブにスケジュールをアタッチする`BackupDatabase`とジョブ`RunReports`します。  
  
> [!NOTE]  
>  この例では、ジョブ`BackupDatabase`とジョブ`RunReports`既に存在します。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_add_schedule  
    @schedule_name = N'NightlyJobs' ,  
    @freq_type = 4,  
    @freq_interval = 1,  
    @active_start_time = 010000 ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'BackupDatabase',  
   @schedule_name = N'NightlyJobs' ;  
GO  
  
EXEC sp_attach_schedule  
   @job_name = N'RunReports',  
   @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
