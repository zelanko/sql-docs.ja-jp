---
title: dm_broker_activated_tasks (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_activated_tasks
- sys.dm_broker_activated_tasks_TSQL
- dm_broker_activated_tasks
- dm_broker_activated_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_activated_tasks dynamic management view
ms.assetid: 17e6f87f-8f56-489d-9aed-216afc8ef310
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9a8d8c7d8c78af63afbd3c0343c855289d40e97b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85677802"
---
# <a name="sysdm_broker_activated_tasks-transact-sql"></a>sys.dm_broker_activated_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Service Broker によってアクティブ化されるストアドプロシージャごとに1行の値を返します。  
 

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**調べる**|**int**|アクティブ化されたストアドプロシージャのセッションの ID。 NULLABLE.|  
|**database_id**|**smallint**|キューが定義されているデータベースの ID。 NULLABLE.|  
|**queue_id**|**int**|ストアドプロシージャがアクティブ化されたキューのオブジェクトの ID。 NULLABLE.|  
|**procedure_name**|**nvarchar (650)**|アクティブ化されたストアドプロシージャの名前。 NULLABLE.|  
|**execute_as**|**int**|ストアドプロシージャを実行するユーザーの ID。 NULLABLE.|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![sys.dm_broker_activated_tasks の結合](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-activated-tasks-1.gif "sys.dm_broker_activated_tasks の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|From|終了|リレーションシップ|  
|----------|--------|------------------|  
|dm_broker_activated_tasks。|dm_exec_sessions。 session_id|一対一|  
  
## <a name="see-also"></a>関連項目  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Service Broker 関連の動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

