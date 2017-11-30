---
title: "sp_help_jobserver (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_help_jobserver
- sp_help_jobserver_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_jobserver
ms.assetid: 57971787-f9f5-4199-9f64-c2b61a308906
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 83de0b76e66e08571a53e3ea62c665ba595a6572
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpjobserver-transact-sql"></a>sp_help_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたジョブのサーバーに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobserver  
     { [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name' }  
     [ , [ @show_last_run_details = ] show_last_run_details ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@job_id=** ] *job_id*  
 情報を返すジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [  **@job_name=** ] **'***job_name***'**  
 情報を返すジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@show_last_run_details=** ] *show_last_run_details*  
 前回の実行情報を結果セットに含めるかどうかを指定します。 *show_last_run_details*は**tinyint**、既定値は**0**します。 **0**前回の実行情報は含まれませんと**1**はします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|対象サーバーの識別番号|  
|**サーバー名**|**nvarchar (30)**|対象サーバーのコンピューター名。|  
|**enlist_date**|**datetime**|対象サーバーがマスター サーバーに参加した日付。|  
|**last_poll_date**|**datetime**|対象サーバーが最後にマスター サーバーを呼び出した日付。|  
  
 場合**sp_help_jobserver**を実行すると*show_last_run_details* 'éý' **1**、結果セットがこれらの列を追加します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**last_run_date**|**int**|対象サーバーでジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|対象サーバーでジョブの実行を最後に開始した時刻|  
|**last_run_duration**|**int**|対象サーバーで最後に実行したときのジョブの経過時間 (秒単位)|  
|**last_outcome_message**|**nvarchar (1024)**|ジョブの最後の結果に関する説明|  
|**last_run_outcome**|**int**|対象サーバーで最後に実行したときのジョブの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
  
## <a name="permissions"></a>Permissions  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**のみ、自分が所有するジョブに関する情報を表示できます。  
  
## <a name="examples"></a>使用例  
 次の例は、に関する前回の実行情報などの情報を返します、`NightlyBackups`ジョブです。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_jobserver  
    @job_name = N'NightlyBackups',  
    @show_last_run_details = 1 ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_jobserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
