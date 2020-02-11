---
title: sp_stop_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_stop_job_TSQL
- sp_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stop_job
ms.assetid: 64b4cc75-99a0-421e-b418-94e37595bbb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9a0549d247078634feadced301570e00746d5ba7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032724"
---
# <a name="sp_stop_job-transact-sql"></a>sp_stop_job (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  エージェント[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にジョブの実行を停止するよう指示します。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_stop_job   
      [@job_name =] 'job_name'  
    | [@job_id =] job_id   
    | [@originating_server =] 'master_server'  
    | [@server_name =] 'target_server'  
```  
  
## <a name="arguments"></a>引数  
`[ @job_name = ] 'job_name'`停止するジョブの名前を指定します。 *job_name*は**sysname**,、既定値は NULL です。  
  
`[ @job_id = ] job_id`停止するジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**,、既定値は NULL です。  
  
`[ @originating_server = ] 'master_server'`マスターサーバーの名前。 指定した場合、すべてのマルチサーバージョブが停止します。 *master_server*は**nvarchar (128)**,、既定値は NULL です。 このパラメーターは、対象サーバーで**sp_stop_job**を呼び出すときにのみ指定します。  
  
> [!NOTE]  
>  最初の 3 つのパラメーターは、いずれか 1 つだけを指定できます。  
  
`[ @server_name = ] 'target_server'`マルチサーバージョブを停止する特定の対象サーバーの名前。 *target_server*は**nvarchar (128)**,、既定値は NULL です。 このパラメーターは、マルチサーバージョブのマスターサーバーで**sp_stop_job**を呼び出すときにのみ指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_stop_job**は、データベースに停止シグナルを送信します。 一部のプロセスはすぐに停止することができ、一部のプロセスは安定したポイント (またはコードパスへのエントリポイント) に到着しないと停止できません。 バックアップ、復元、 [!INCLUDE[tsql](../../includes/tsql-md.md)]一部の DBCC コマンドなど、長時間実行されるステートメントの完了には時間がかかることがあります。 これらが実行されている場合、ジョブが取り消されるまでにしばらく時間がかかることがあります。 ジョブを停止すると、ジョブが取り消されたことを示すエントリがジョブ履歴に記録されます。  
  
 ジョブが**CmdExec**または**PowerShell**タイプのステップを現在実行している場合は、実行中のプロセス (たとえば、myprogram .exe) が途中で強制的に終了します。 途中で終了した場合、そのプロセスによって使用されていたファイルが開いたままになるなど、予期しない結果が発生する可能性があります。 そのため、ジョブに**CmdExec**または**PowerShell**型のステップが含まれている場合は、極端な状況でのみ**sp_stop_job**を使用する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sysadmin**固定サーバーロールのメンバーは、このストアドプロシージャを実行できます。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
 **SQLAgentUserRole**と**SQLAgentReaderRole**のメンバーは、自分が所有するジョブのみを停止できます。 **Sqlagentoperatorrole**のメンバーは、他のユーザーによって所有されているものも含め、すべてのローカルジョブを停止できます。 **Sysadmin**のメンバーは、すべてのローカルジョブとマルチサーバージョブを停止できます。  
  
## <a name="examples"></a>例  
 次の例では、と`Weekly Sales Data Backup`いう名前のジョブを停止します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_stop_job  
    N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_start_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_update_job &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
