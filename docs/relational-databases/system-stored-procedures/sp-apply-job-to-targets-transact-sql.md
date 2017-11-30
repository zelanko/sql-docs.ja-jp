---
title: "sp_apply_job_to_targets (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_apply_job_to_targets
- sp_apply_job_to_targets_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_apply_job_to_targets
ms.assetid: 4a3e9173-7e3c-4100-a9ac-2f5d2c60a8b0
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f0b538c726a324709c35807c8e0f6bdc8bc3b607
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spapplyjobtotargets-transact-sql"></a>sp_apply_job_to_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上の対象サーバー、または 1 つ以上の対象サーバー グループに属する複数の対象サーバーにジョブを適用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_apply_job_to_targets { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }  
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]   
     [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@job_id =**] *job_id*  
 指定した対象サーバーまたは対象サーバー グループに適用するジョブの、ジョブ識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [  **@job_name =**] **'***job_name***'**  
 指定した対象サーバーまたは対象サーバー グループに適用するジョブの名前を指定します *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@target_server_groups =**] **'***target_server_groups***'**  
 指定したジョブを適用する対象サーバー グループを、コンマ区切りのリストで指定します。 *target_server_groups*は**nvarchar (2048)**、既定値は NULL です。  
  
 [  **@target_servers=** ] **'***target_servers***'**  
 指定したジョブを適用する対象サーバーを、コンマ区切りのリストで指定します *target_servers*は**nvarchar (2048)**、既定値は NULL です。  
  
 [  **@operation=** ] **'***操作***'**  
 指定したジョブを、指定した対象サーバーまたは対象サーバー グループに対して適用するか削除するかを指定します。 *操作*は**varchar (7)**、既定値は APPLY です。 有効な操作は**適用**と**削除**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_apply_job_to_targets**代わりを呼び出すことで、複数の対象サーバーからジョブを適用 (または削除) する簡単な方法を提供**sp_add_jobserver** (または**sp_delete_jobserver**) に必要なターゲット サーバーごとに 1 回です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**この手順を実行できるは、固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、以前に作成した適用`Backup Customer Information`ジョブ内のすべての対象サーバーを`Servers Maintaining Customer Information`グループ。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_apply_job_to_targets  
    @job_name = N'Backup Customer Information',  
    @target_server_groups = N'Servers Maintaining Customer Information',   
    @operation = N'APPLY' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_add_jobserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_delete_jobserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [sp_remove_job_from_targets &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-remove-job-from-targets-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
