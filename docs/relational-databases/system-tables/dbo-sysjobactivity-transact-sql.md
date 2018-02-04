---
title: dbo.sysjobactivity (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/05/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysjobactivity_TSQL
- dbo.sysjobactivity
- sysjobactivity
- sysjobactivity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobactivity system table
ms.assetid: fd17cac9-5d1f-4b44-b2dc-ee9346d8bf1e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d0edab9e591470a0100bde529f53cee44a016dab
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysjobactivity-transact-sql"></a>dbo.sysjobactivity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの利用状況と状態を記録します。  次の表は、 **msdb**データベース。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|格納されているセッションの ID、 **syssessions**テーブルに、 **msdb**データベース。|  
|**job_id**|**uniqueidentifier**|ジョブの ID です。|  
|**run_requested_date**|**datetime**|ジョブの実行が要求された日時。|  
|**run_requested_source**|**sysname(nvarchar(128))**|ジョブの実行要求の発生元。<br /><br /> **1** = SOURCE_SCHEDULER<br /><br /> **2** = SOURCE_ALERTER<br /><br /> **3** = SOURCE_BOOT<br /><br /> **4** = SOURCE_USER<br /><br /> **6** = SOURCE_ON_IDLE_SCHEDULE|  
|**queued_date**|**datetime**|ジョブがキューに格納された日時。 ジョブが直接実行される場合、この列は NULL になります。|  
|**start_execution_date**|**datetime**|ジョブの実行が予定されている日時。|  
|**last_executed_step_id**|**int**|実行された最後のジョブ ステップの ID。|  
|**last_executed_step_**<br /><br /> **date**|**datetime**|最後のジョブ ステップの実行が開始された日時。|  
|**stop_execution_date**|**datetime**|ジョブの実行が終了した日時。|  
|**job_history_id**|**int**|内の行を識別するため、 **sysjobhistory**テーブル。|  
|**next_scheduled_run_date**|**datetime**|ジョブの次回実行予定日時。|  

## <a name="example"></a>例
この例では、すべての SQL Server エージェント ジョブの実行時の状態を返します。  [!INCLUDE[tsql](../../includes/tsql-md.md)] で次の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を実行します。
```sql
SELECT sj.Name, 
    CASE
        WHEN sja.start_execution_date IS NULL THEN 'Not running'
        WHEN sja.start_execution_date IS NOT NULL AND sja.stop_execution_date IS NULL THEN 'Running'
        WHEN sja.start_execution_date IS NOT NULL AND sja.stop_execution_date IS NOT NULL THEN 'Not running'
    END AS 'RunStatus'
FROM msdb.dbo.sysjobs sj
JOIN msdb.dbo.sysjobactivity sja
ON sj.job_id = sja.job_id
WHERE session_id = (
    SELECT MAX(session_id) FROM msdb.dbo.sysjobactivity); 
```
  
## <a name="see-also"></a>参照  
 [dbo.sysjobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobhistory-transact-sql.md)  
  
  
