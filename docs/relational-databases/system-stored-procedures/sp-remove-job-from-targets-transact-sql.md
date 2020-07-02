---
title: sp_remove_job_from_targets (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_job_from_targets_TSQL
- sp_remove_job_from_targets
dev_langs:
- TSQL
helpviewer_keywords:
- sp_remove_job_from_targets
ms.assetid: b8171fb1-c11d-4244-8618-a12e28a150ce
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 033a2c950ec695a64aced30a383d25206e7f6d10
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751682"
---
# <a name="sp_remove_job_from_targets-transact-sql"></a>sp_remove_job_from_targets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  指定した対象サーバーまたは対象サーバーグループから、指定したジョブを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_remove_job_from_targets [ @job_id = ] job_id   
     | [ @job_name = ] 'job_name'   
     [ , [ @target_server_groups = ] 'target_server_groups' ]   
     [ , [ @target_servers = ] 'target_servers' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @job_id = ] job_id`指定した対象サーバーまたは対象サーバーグループを削除するジョブのジョブ識別番号を指定します。 *Job_id*または*job_name*のいずれかを指定する必要がありますが、両方を指定することはできません。 *job_id*は**uniqueidentifier**,、既定値は NULL です。  
  
`[ @job_name = ] 'job_name'`指定した対象サーバーまたは対象サーバーグループを削除するジョブの名前を指定します。 *Job_id*または*job_name*のいずれかを指定する必要がありますが、両方を指定することはできません。 *job_name*は**sysname**,、既定値は NULL です。  
  
`[ @target_server_groups = ] 'target_server_groups'`指定したジョブから削除する対象サーバーグループのコンマ区切りのリスト。 *target_server_groups*は**nvarchar (1024)**,、既定値は NULL です。  
  
`[ @target_servers = ] 'target_servers'`指定したジョブから削除する対象サーバーのコンマ区切りのリスト。 *target_servers*は**nvarchar (1024)**,、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では **sysadmin** 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
 次の例では、以前に作成した `Weekly Sales Backups` ジョブを `Servers Processing Customer Orders` 対象サーバーグループ、 `SEATTLE1` およびサーバーから削除し `SEATTLE2` ます。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_remove_job_from_targets  
    @job_name = N'Weekly Sales Backups',  
    @target_server_groups = N'Servers Processing Customer Orders',   
    @target_servers = N'SEATTLE2,SEATTLE1' ;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sp_apply_job_to_targets &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
