---
title: sp_help_jobcount (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_help_jobcount
- sp_help_jobcount_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobcount
ms.assetid: ae8ef851-646c-4889-bc11-c8ec78762572
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6165d86e2a086ef52e627451e613b021296082d9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobcount-transact-sql"></a>sp_help_jobcount (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スケジュールがアタッチされているジョブの数を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobcount   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>引数  
 [ **@schedule_id=** ] *schedule_id*  
 一覧表示するスケジュールの識別子を指定します。 *schedule_id*は**int**、既定値はありません。 いずれか*schedule_id*または*schedule_name*指定することがあります。  
  
 [ **@schedule_name=** ]  **'***schedule_name***'**  
 一覧表示するスケジュールの名前を指定します。 *schedule_name*は**sysname**、既定値はありません。 いずれか*schedule_id*または*schedule_name*指定することがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**JobCount**|**int**|指定されたスケジュールに対するジョブの数。|  
  
## <a name="remarks"></a>解説  
 このプロシージャでは、指定されたスケジュールにアタッチされたジョブの数が一覧表示されます。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバーだけ**sysadmin**は他のユーザーによって所有されているジョブのカウントを表示できます。  
  
## <a name="examples"></a>使用例  
 次の例では、`NightlyJobs` スケジュールにアタッチされたジョブの数を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobcount  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
