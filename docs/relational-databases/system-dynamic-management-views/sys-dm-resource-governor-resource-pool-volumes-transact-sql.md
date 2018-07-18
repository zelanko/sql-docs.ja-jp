---
title: sys.dm_resource_governor_resource_pool_volumes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes_TSQL
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_volumes
- sys.dm_resource_governor_resource_pool_volumes
ms.assetid: fa692e56-c561-4533-97c5-bc12c600553f
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 49c3cc7312978f313ed55147530c371bdde69675
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969224"
---
# <a name="sysdmresourcegovernorresourcepoolvolumes-transact-sql"></a>sys.dm_resource_governor_resource_pool_volumes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  現在のリソース プールの IO の統計に関する情報をディスク ボリュームごとに返します。 リソース プール レベルではこの情報は使用可能なも[sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)します。  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|volume_name|**sysname**|ディスク ボリュームの名前。 NULL 値は許可されません。|  
|read_io_queued_total|**int**|リソース ガバナーがリセットされた後、読み取り IOs エンキューを合計します。 NULL 値は許可されません。|  
|read_io_issued_total|**int**|リソース ガバナー統計がリセットされた後に発行された読み取り IO の合計。 NULL 値は許可されません。|  
|read_ios_completed_total|**int**|リソース ガバナー統計がリセットされた後に完了した読み取り IO の合計。 NULL 値は許可されません。|  
|read_ios_throttled_total|**int**|リソース ガバナー統計がリセットされた後に調整された読み取り IO の合計。 NULL 値は許可されません。|  
|read_bytes_total|**bigint**|リソース ガバナー統計がリセットされた後に読み取られたバイト数の合計。 NULL 値は許可されません。|  
|read_io_stall_total_ms|**bigint**|読み取り IO の到着から完了までの合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|read_io_stall_queued_ms|**bigint**|読み取り IO の到着から発行までの合計時間 (ミリ秒単位)。 これは、IO リソース管理によって発生した遅延です。 NULL 値は許可されません。|  
|write_io_queued_total|**int**|リソース ガバナー統計がリセットされた後にエンキューされた書き込み IO の合計。 NULL 値は許可されません。|  
|write_io_issued_total|**int**|リソース ガバナー統計がリセットされた後に発行された書き込み IO の合計。 NULL 値は許可されません。|  
|write_io_completed_total|**int**|リソース ガバナー統計がリセットされた後に完了した書き込み IO の合計。 値が許容されません。|  
|write_io_throttled_total|**int**|リソース ガバナー統計がリセットされた後に調整された書き込み IO の合計。 値が許容されません。|  
|write_bytes_total|**bigint**|リソース ガバナー統計がリセットされた後に書き込まれたバイト数の合計。 NULL 値は許可されません。|  
|write_io_stall_total_ms|**bigint**|書き込み IO の発行から完了までの合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|write_io_stall_queued_ms|**bigint**|書き込み IO の到着から発行までの合計時間 (ミリ秒単位)。 これは、IO リソース管理によって発生した遅延です。 NULL 値は許可されません。|  
|io_issue_violations_total|**int**|IO 発行違反の合計。 つまり、IO の発行レートが予約レートを下回った回数です。 NULL 値は許可されません。|  
|io_issue_delay_total_ms|**bigint**|IO の発行予定時間から実際に発行されるまでの合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

