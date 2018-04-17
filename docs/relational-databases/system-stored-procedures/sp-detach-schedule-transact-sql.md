---
title: sp_detach_schedule (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_detach_schedule
- sp_detach_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_detach_schedule
ms.assetid: 9a1fc335-1bef-4638-a33a-771c54a5dd19
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 01ea4f9566f3a50b37f782b5e601b0aae734df19
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spdetachschedule-transact-sql"></a>sp_detach_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スケジュールとジョブ間の関連付けを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_detach_schedule   
     { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
       { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @delete_unused_schedule = ] delete_unused_schedule   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id=** ] *job_id*  
 スケジュールを削除するジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name=** ] **'***job_name***'**  
 スケジュールを削除するジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@schedule_id=** ] *schedule_id*  
 ジョブから削除するスケジュールの識別番号を指定します。 *schedule_id*は**int**、既定値は NULL です。  
  
 [ **@schedule_name=** ] **'***schedule_name***'**  
 ジョブから削除するスケジュールの名前を指定します。 *schedule_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*schedule_id*または*schedule_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@delete_unused_schedule=** ] *@delete_unused_schedule*  
 使用のジョブ スケジュールを削除するかどうかを指定します。 *@delete_unused_schedule*は**ビット**、既定値は**0**、つまりすべてのスケジュールは保持されることでもジョブ参照されていない場合にします。 場合設定**1**、未使用のジョブ スケジュールがジョブ参照されていない場合に削除されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 ジョブ所有者は、同時にスケジュール所有者にならなくても、ジョブをスケジュールにアタッチしたり、スケジュールからデタッチしたりできます。 ただし、デタッチ後は、のままにジョブはありません、呼び出し元がスケジュールの所有者でない限り場合は、スケジュールを削除できません。  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ユーザーがスケジュールを所有しているかどうかが判断されます。 メンバーにのみ、 **sysadmin**固定サーバー ロールは、別のユーザーが所有するジョブからスケジュールをデタッチできます。  
  
## <a name="examples"></a>使用例  
 次の例は、間の関連付けを削除、`'NightlyJobs'`スケジュールと`'BackupDatabase'`ジョブです。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_detach_schedule  
    @job_name = 'BackupDatabase',  
    @schedule_name = 'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)  
  
  
