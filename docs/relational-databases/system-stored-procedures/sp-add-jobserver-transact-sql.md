---
title: sp_add_jobserver (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_add_jobserver
- sp_add_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobserver
ms.assetid: 485252cc-0081-490a-9bd1-cbbd68eea286
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e89ba03a88db9dd5977ace92cc498726da6b3e45
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spaddjobserver-transact-sql"></a>sp_add_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたジョブを、特定のサーバーにおける対象ジョブにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_jobserver [ @job_id = ] job_id | [ @job_name = ] 'job_name'  
     [ , [ @server_name = ] 'server' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@job_id =** ] *job_id*  
 ジョブの ID 番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@job_name =** ] **'***job_name***'**  
 ジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@server_name =** ] **'***server***'**  
 対象となるジョブを割り当てるサーバーの名前を指定します。 *サーバー*は**nvarchar (30)** N'(LOCAL) の既定値は ' です。 *サーバー*のいずれか **(ローカル)** ローカル サーバーまたは既存の対象サーバーの名前。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **@automatic_post** 内に存在する**sp_add_jobserver**は引数の下に記載されていません。 **@automatic_post** 内部使用のために予約されています。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、ジョブを簡単に管理できるグラフィカルなツールです。ジョブのインフラストラクチャを作成し、管理するには、このツールを使用することをお勧めします。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_jobserver**の複数のサーバーに関連するジョブです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-assigning-a-job-to-the-local-server"></a>A. ローカル サーバーにジョブを割り当てる  
 次の例には、ジョブが割り当てられます。 `NightlyBackups` 、ローカル サーバー上で実行します。  
  
> [!NOTE]  
>  この例では、`NightlyBackups`ジョブが既に存在します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-assigning-a-job-to-run-on-a-different-server"></a>B. 異なるサーバーで実行するようジョブを割り当てる  
 次の例には、マルチ サーバー ジョブが割り当てられます。`Weekly Sales Backups`サーバーに`SEATTLE2`です。  
  
> [!NOTE]  
>  この例では、`Weekly Sales Backups` ジョブが既に存在し、`SEATTLE2` が現在のインスタンスに対する対象サーバーとして登録されていることを前提としています。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',  
    @server_name = N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_apply_job_to_targets &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_jobserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
