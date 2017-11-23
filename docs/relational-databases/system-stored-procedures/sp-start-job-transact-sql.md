---
title: "sp_start_job (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_start_job
- sp_start_job_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_start_job
ms.assetid: 8a91df6a-eb84-4512-9a17-4a6e32a9538a
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 628484b1f5e2bf4282eb4f4b223beba5636d4ba5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spstartjob-transact-sql"></a>sp_start_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントをすぐにジョブを実行します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_start_job   
     {   [@job_name =] 'job_name'  
       | [@job_id =] job_id }  
     [ , [@error_flag =] error_flag]  
     [ , [@server_name =] 'server_name']  
     [ , [@step_name =] 'step_name']  
     [ , [@output_flag =] output_flag]  
```  
  
## <a name="arguments"></a>引数  
 [  **@job_name=** ] **'***job_name***'**  
 開始するジョブの名前を指定します。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。 *job_name*は**sysname**、既定値は NULL です。  
  
 [  **@job_id=** ] *job_id*  
 開始するジョブの識別番号を指定します。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [  **@error_flag=** ] *error_flag*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@server_name=** ] **'***server_name***'**  
 ジョブを開始する対象サーバーを指定します。 *server_name*は**nvarchar (128)**、既定値は NULL です。 *server_name*ジョブが現在対象となる対象サーバーのいずれかを指定する必要があります。  
  
 [  **@step_name=** ] **'***step_name***'**  
 ジョブの実行を開始するステップの名前を指定します。 ローカル ジョブにのみ適用されます。 *step_name*は**sysname**、既定値は NULL  
  
 [  **@output_flag=** ] *output_flag*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャは、 **msdb**データベース。  
  
## <a name="permissions"></a>Permissions  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**と**SQLAgentReaderRole**開始できるは、自分が所有するジョブのみです。 メンバー **SQLAgentOperatorRole**など他のユーザーによって所有されているすべてのローカル ジョブを開始できます。 メンバー **sysadmin**すべてローカル ジョブおよびマルチ サーバー ジョブを開始できます。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前のジョブを開始`Weekly Sales Data Backup`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_stop_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-stop-job-transact-sql.md)   
 [sp_update_job &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
