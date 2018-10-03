---
title: sp_delete_schedule (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd7f01df2c381ae4ee13b62e196efbc33809e23d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47803770"
---
# <a name="spdeleteschedule-transact-sql"></a>sp_delete_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スケジュールを削除します。  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_schedule { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @force_delete = ] force_delete  
```  
  
## <a name="arguments"></a>引数  
 [ **@schedule_id=** ] *schedule_id*  
 削除するスケジュールの識別番号を指定します。 *schedule_id*は**int**、既定値は NULL です。  
  
> **注:** か*schedule_id*または*schedule_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@schedule_name=** ] **'***schedule_name***'**  
 削除するスケジュールの名前を指定します。 *schedule_name*は**sysname**、既定値は NULL です。  
  
> **注:** か*schedule_id*または*schedule_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@force_delete** =] *force_delete*  
 スケジュールがジョブに関連付けられている場合にプロシージャを失敗させるかどうかを指定します。 *Force_delete*は bit で、既定値は、 **0**します。 ときに*force_delete*は**0**、ストアド プロシージャ、スケジュールがジョブに関連付けられている場合は失敗します。 ときに*force_delete*は**1**スケジュールをジョブにアタッチするかどうかに関係なく、スケジュールを削除します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 既定では、スケジュールがジョブに関連付けられている場合、スケジュールを削除することはできません。 ジョブに関連付けられているスケジュールを削除するには、値を指定**1**の*force_delete*します。 スケジュールを削除しても、現在実行中のジョブは停止しません。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 ジョブ所有者は、同時にスケジュール所有者にならなくても、ジョブをスケジュールにアタッチしたり、スケジュールからデタッチしたりできます。 ただし、呼び出し元がスケジュール所有者ではない場合、デタッチによってスケジュールにジョブがなくなっても、スケジュールを削除することはできません。  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 メンバーのみ、 **sysadmin**ロールは、別のユーザーによって所有されているジョブのスケジュールを削除できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-deleting-a-schedule"></a>A. スケジュールを削除する  
 次の例は、スケジュールを削除`NightlyJobs`します。 スケジュールがジョブに関連付けられている場合、この例ではスケジュールは削除されません。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="b-deleting-a-schedule-attached-to-a-job"></a>B. ジョブに関連付けられているスケジュールを削除する  
 次の例では、スケジュールがジョブに関連付けられているかどうかに関係なく、スケジュール `RunOnce` を削除します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = 'RunOnce',  
    @force_delete = 1;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ジョブの実装](../../ssms/agent/implement-jobs.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
  
