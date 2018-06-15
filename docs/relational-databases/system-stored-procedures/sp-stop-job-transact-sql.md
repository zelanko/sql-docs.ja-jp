---
title: sp_stop_job (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_stop_job_TSQL
- sp_stop_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_stop_job
ms.assetid: 64b4cc75-99a0-421e-b418-94e37595bbb0
caps.latest.revision: 38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 67e1476e8f0612796e3f31644aca192c2c25a90f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258697"
---
# <a name="spstopjob-transact-sql"></a>sp_stop_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント ジョブの実行を停止します。  

  
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
 [ **@job_name =**] **'***job_name***'**  
 停止するジョブの名前を指定します。 *job_name*は**sysname**、既定値は NULL です。  
  
 [ **@job_id =**] *job_id*  
 停止するジョブの識別番号を指定します。 *job_id*は**uniqueidentifier**、既定値は NULL です。  
  
 [ **@originating_server =**] **'***master_server***'**  
 マスター サーバーの名前を指定します。 指定した場合、すべてのマルチサーバー ジョブが停止します。 *master_server*は**nvarchar (128)**、既定値は NULL です。 呼び出すときにのみ、このパラメーターを指定**sp_stop_job**をターゲット サーバーにします。  
  
> [!NOTE]  
>  最初の 3 つのパラメーターは、いずれか 1 つだけを指定できます。  
  
 [ **@server_name =**] **'***target_server***'**  
 マルチサーバー ジョブを停止する特定の対象サーバーの名前を指定します。 *target_server*は**nvarchar (128)**、既定値は NULL です。 呼び出すときにのみ、このパラメーターを指定**sp_stop_job**マルチ サーバー ジョブのマスター サーバーでします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_stop_job**データベースに停止シグナルを送信します。 一部のプロセスをすぐに停止して、いくつかは、安定したポイント (または、コード パスのエントリ ポイント) に到達する必要があります未然に防ぐことができます。 いくつか実行時間の長い[!INCLUDE[tsql](../../includes/tsql-md.md)]バックアップ、復元、および一部の DBCC コマンドなどのステートメントは完了までに時間かかることができます。 これらが実行されている場合に、ジョブが取り消されるまでは、しばらくがかかる場合があります。 ジョブを停止すると、ジョブが取り消されたことを示すエントリがジョブ履歴に記録されます。  
  
 型のステップがジョブで実行されているかどうかは**CmdExec**または**PowerShell**、実行中のプロセス (MyProgram.exe など) は途中で強制終了します。 途中で終了した場合、そのプロセスによって使用されていたファイルが開いたままになるなど、予期しない結果が発生する可能性があります。 その結果、 **sp_stop_job**ジョブには、型のステップが含まれている場合に、極端な状況でのみ使用する必要があります**CmdExec**または**PowerShell**です。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**と**SQLAgentReaderRole**だけ、自分が所有するジョブを停止できます。 メンバー **SQLAgentOperatorRole**など他のユーザーによって所有されているすべてのローカル ジョブを停止することができます。 メンバー **sysadmin**すべてローカル ジョブおよびマルチ サーバー ジョブを停止することができます。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前のジョブを停止`Weekly Sales Data Backup`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_stop_job  
    N'Weekly Sales Data Backup' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_delete_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [sp_help_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_start_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md)   
 [sp_update_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
