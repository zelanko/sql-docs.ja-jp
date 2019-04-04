---
title: sp_purge_jobhistory (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ab2f2fcb07fb181fd32d5a60f9fd2d8f25725f96
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535684"
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ジョブの履歴レコードを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>引数  
`[ @job_name = ] 'job_name'` 履歴レコードを削除するジョブの名前。 *job_name*は**sysname**、既定値は NULL です。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。  
  
> [!NOTE]  
>  メンバー、 **sysadmin**固定サーバー ロールのメンバーや、 **SQLAgentOperatorRole**固定データベース ロールが実行できる**sp_purge_jobhistory** を指定せず*job_name*または*job_id*します。 ときに**sysadmin**ユーザーは、これらの引数を指定しない、によって指定された時間内のすべてのローカルおよびマルチ サーバー ジョブのジョブ履歴が削除された*oldest_date*します。 ときに**SQLAgentOperatorRole**ユーザーは、これらの引数を指定しない、によって指定された時間内のすべてのローカル ジョブのジョブ履歴が削除された*oldest_date*します。  
  
`[ @job_id = ] job_id` 削除するレコードのジョブのジョブ識別番号。 *job_id*は**uniqueidentifier**、既定値は NULL です。 いずれか*job_id*または*job_name*指定する必要がありますが、両方を指定することはできません。 注の説明を参照してください**@job_name**について**sysadmin**または**SQLAgentOperatorRole**ユーザーは、この引数を使用できます。  
  
`[ @oldest_date = ] oldest_date` 履歴に保持する最も古いレコード。 *oldest_date*は**datetime**、既定値は NULL です。 ときに*oldest_date*が指定されている**sp_purge_jobhistory**のみに指定された値よりも古いレコードを削除します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 ときに**sp_purge_jobhistory**が正常に完了すると、メッセージが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 既定のメンバーだけで、 **sysadmin**固定サーバー ロールまたは**SQLAgentOperatorRole**固定データベース ロールは、このストアド プロシージャを実行できます。 メンバーの**sysadmin**すべてローカル ジョブおよびマルチ サーバー ジョブのジョブ履歴を削除できます。 メンバーの**SQLAgentOperatorRole**のすべてのローカル ジョブだけのジョブ履歴を削除できます。  
  
 メンバーを含む、他のユーザー **SQLAgentUserRole**とメンバーの**SQLAgentReaderRole**、する必要があります明示的に EXECUTE アクセス許可で許可**sp_purge_jobhistory**. このストアド プロシージャに対する EXECUTE 権限が許可されていると、これらのユーザーは自分が所有しているジョブの履歴だけを削除できます。  
  
 **SQLAgentUserRole**、 **SQLAgentReaderRole**、および**SQLAgentOperatorRole**に固定データベース ロールがある、 **msdb**データベース。 詳細については、そのアクセス許可は、[SQL Server エージェント固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-remove-history-for-a-specific-job"></a>A. 特定のジョブの履歴を削除します。  
 次の例は、という名前のジョブの履歴を削除します。`NightlyBackups`します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-remove-history-for-all-jobs"></a>B. すべてのジョブの履歴を削除する  
  
> [!NOTE]  
>  メンバーのみ、 **sysadmin**固定サーバー ロールのメンバーと、 **SQLAgentOperatorRole**すべてのジョブの履歴を削除することができます。 ときに**sysadmin**パラメーターなしでこのストアド プロシージャを実行するユーザー、すべてローカル ジョブおよびマルチ サーバー ジョブのジョブ履歴を削除します。 ときに**SQLAgentOperatorRole**ユーザー パラメーターなしでこのストアド プロシージャを実行するとのすべてのローカル ジョブのジョブ履歴のみを削除します。  
  
 次の例では、すべての履歴レコードを削除するパラメーターなしでプロシージャを実行します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  
