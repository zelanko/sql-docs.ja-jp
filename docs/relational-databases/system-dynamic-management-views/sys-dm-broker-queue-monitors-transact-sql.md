---
title: "sys.dm_broker_queue_monitors (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_broker_queue_monitors
- sys.dm_broker_queue_monitors_TSQL
- dm_broker_queue_monitors_TSQL
- sys.dm_broker_queue_monitors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_queue_monitors dynamic management view
ms.assetid: 401207dc-ef4a-4a3f-879c-76dcbb52d6bc
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9bc93ac489094fcf9dfba593acd670bc4babbaa6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmbrokerqueuemonitors-transact-sql"></a>sys.dm_broker_queue_monitors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンス内のキュー モニターごとに 1 行のデータを返します。 キュー モニターは、キューのアクティブ化を管理します。  
  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|モニターで監視するキューが含まれるデータベースのオブジェクト識別子。 NULL 値は許可されます。|  
|**queue_id**|**int**|モニターで監視するキューのオブジェクト識別子。 NULL 値は許可されます。|  
|**状態**|**nvarchar(32)**|モニターの状態です。 NULL 値は許可されます。 これは、次のいずれかです。<br /><br /> **INACTIVE**<br /><br /> **NOTIFIED**<br /><br /> **RECEIVES_OCCURRING**|  
|**last_empty_rowset_time**|**datetime**|キューからの RECEIVE で、空の結果が返された前回の時刻。 NULL 値は許可されます。|  
|**last_activated_time**|**datetime**|キュー モニターによってストアド プロシージャがアクティブ化された前回の時刻。 NULL 値は許可されます。|  
|**tasks_waiting**|**int**|キューの RECEIVE ステートメント内で現在待機中のセッション数。 NULL 値は許可されます。<br /><br /> 注: この数には、キュー モニターが、セッションを開始するかどうかに関係なく、receive ステートメントを実行するセッションが含まれます。 これは、RECEIVE と共に WAITFOR を使用する場合に該当します。 基本的に、これらのタスクはキューでメッセージが受信されるのを待機しています。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-current-status-queue-monitor"></a>A. キュー モニターで現在の状態を監視する  
 次の例では、すべてのメッセージ キューの現在の状態が提供されます。  
  
```  
SELECT t1.name AS [Service_Name],  t3.name AS [Schema_Name],  t2.name AS [Queue_Name],    
CASE WHEN t4.state IS NULL THEN 'Not available'   
ELSE t4.state   
END AS [Queue_State],    
CASE WHEN t4.tasks_waiting IS NULL THEN '--'   
ELSE CONVERT(VARCHAR, t4.tasks_waiting)   
END AS tasks_waiting,   
CASE WHEN t4.last_activated_time IS NULL THEN '--'   
ELSE CONVERT(varchar, t4.last_activated_time)   
END AS last_activated_time ,    
CASE WHEN t4.last_empty_rowset_time IS NULL THEN '--'   
ELSE CONVERT(varchar,t4.last_empty_rowset_time)   
END AS last_empty_rowset_time,   
(   
SELECT COUNT(*)   
FROM sys.transmission_queue t6   
WHERE (t6.from_service_name = t1.name) ) AS [Tran_Message_Count]   
FROM sys.services t1    INNER JOIN sys.service_queues t2   
ON ( t1.service_queue_id = t2.object_id )     
INNER JOIN sys.schemas t3 ON ( t2.schema_id = t3.schema_id )    
LEFT OUTER JOIN sys.dm_broker_queue_monitors t4   
ON ( t2.object_id = t4.queue_id  AND t4.database_id = DB_ID() )    
INNER JOIN sys.databases t5 ON ( t5.database_id = DB_ID() );  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

