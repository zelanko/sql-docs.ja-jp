---
title: sysjobsteps (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobsteps
- dbo.sysjobsteps_TSQL
- sysjobsteps
- sysjobsteps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobsteps system table
ms.assetid: 978b8205-535b-461c-91f3-af9b08eca467
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d98b1ccc4dc8da3ba9d494a78bfea3727102da07
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827322"
---
# <a name="dbosysjobsteps-transact-sql"></a>dbo.sysjobsteps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって実行されるジョブ内の各ステップに関する情報を格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの ID。|  
|**step_id**|**int**|ジョブ ステップの ID。|  
|**step_name**|**sysname**|ジョブステップの名前。|  
|**サブ**|**nvarchar(40)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがジョブ ステップを実行するために使用するサブシステムの名前。|  
|**メニュー**|**nvarchar(max)**|**サブシステム**によって実行されるコマンドです。|  
|**flags**|**int**|予約済み。|  
|**additional_parameters**|**ntext**|予約済み。|  
|**cmdexec_success_code**|**int**|**CmdExec**サブシステムのステップによって返された、成功を示すエラーレベルの値。|  
|**on_success_action**|**tinyint**|ステップが正常に実行されたときに実行されるアクション。|  
|**on_success_step_id**|**int**|ステップが正常に実行されたときに実行する次のステップの ID。|  
|**on_fail_action**|**tinyint**|ステップが正常に実行されなかった場合に実行されるアクション。|  
|**on_fail_step_id**|**int**|ステップが正常に実行されないときに実行する次のステップの ID。|  
|**server**|**sysname**|予約済み。|  
|**database_name**|**sysname**|**サブシステム**が TSQL の場合に**コマンド**が実行されるデータベースの名前。|  
|**database_user_name**|**sysname**|ステップの実行時に使用されるアカウントを持つデータベースユーザーの名前。|  
|**retry_attempts**|**int**|ステップが失敗した場合の再試行回数。|  
|**retry_interval**|**int**|再試行の間に待機する時間。|  
|**os_run_priority**|**int**|予約済み。|  
|**output_file_name**|**nvarchar(200)**|**サブシステム**が TSQL、PowerShell、または**CmdExec**の場合に、ステップの出力が保存されるファイルの名前 _。_|  
|**last_run_outcome**|**int**|ジョブ ステップの前回の実行結果。<br /><br /> **0** = 失敗<br /><br /> **1** = 成功<br /><br /> **2** = 再試行<br /><br /> **3** = キャンセル<br /><br /> **5** = 不明|  
|**last_run_duration**|**int**|最後に実行されたときのステップの期間 (hhmmss)。|  
|**last_run_retries**|**int**|最後にジョブステップを実行したときの再試行回数。|  
|**last_run_date**|**int**|ステップの実行を最後に開始した日付 (yyyymmdd)。|  
|**last_run_time**|**int**|ステップの実行を最後に開始した時刻 (hhmmss)。|  
|**proxy_id**|**int**|ジョブステップのプロキシ。|  
|**step_uid**|**uniqueidentifier**|ジョブステップの識別子。|  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
