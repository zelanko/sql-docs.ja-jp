---
title: sys.dm_resource_governor_resource_pool_volumes (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
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
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a60bd54400d9e9d82c3abbde9d828c1877b0753b
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmresourcegovernorresourcepoolvolumes-transact-sql"></a>sys.dm_resource_governor_resource_pool_volumes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  現在のリソース プールの IO の統計に関する情報をディスク ボリュームごとに返します。 リソース プール レベルでこの情報が利用可能なも[sys.dm_resource_governor_resource_pools &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|volume_name|**sysname**|ディスク ボリュームの名前。 NULL 値は許可されません。|  
|read_io_queued_total|**int**|リソース ガバナーがリセットされた後、読み取り IOs にキュー入れられたを合計します。 NULL 値は許可されません。|  
|read_io_issued_total|**int**|リソース ガバナー統計がリセットされた後に発行された読み取り IO の合計。 NULL 値は許可されません。|  
|read_ios_completed_total|**int**|リソース ガバナー統計がリセットされた後に完了した読み取り IO の合計。 NULL 値は許可されません。|  
|read_ios_throttled_total|**int**|リソース ガバナー統計がリセットされた後に調整された読み取り IO の合計。 NULL 値は許可されません。|  
|read_bytes_total|**bigint**|リソース ガバナー統計がリセットされた後に読み取られたバイト数の合計。 NULL 値は許可されません。|  
|read_io_stall_total_ms|**bigint**|読み取り IO の到着から完了までの合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|read_io_stall_queued_ms|**bigint**|読み取り IO の到着から発行までの合計時間 (ミリ秒単位)。 これは、IO リソース管理によって発生した遅延です。 NULL 値は許可されません。|  
|write_io_queued_total|**int**|リソース ガバナー統計がリセットされた後にエンキューされた書き込み IO の合計。 NULL 値は許可されません。|  
|write_io_issued_total|**int**|リソース ガバナー統計がリセットされた後に発行された書き込み IO の合計。 NULL 値は許可されません。|  
|write_io_completed_total|**int**|リソース ガバナー統計がリセットされた後に完了した書き込み IO の合計。 Null 値はありません。|  
|write_io_throttled_total|**int**|リソース ガバナー統計がリセットされた後に調整された書き込み IO の合計。 Null 値はありません。|  
|write_bytes_total|**bigint**|リソース ガバナー統計がリセットされた後に書き込まれたバイト数の合計。 NULL 値は許可されません。|  
|write_io_stall_total_ms|**bigint**|書き込み IO の発行から完了までの合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|write_io_stall_queued_ms|**bigint**|書き込み IO の到着から発行までの合計時間 (ミリ秒単位)。 これは、IO リソース管理によって発生した遅延です。 NULL 値は許可されません。|  
|io_issue_violations_total|**int**|IO 発行違反の合計。 つまり、IO の発行レートが予約レートを下回った回数です。 NULL 値は許可されません。|  
|io_issue_delay_total_ms|**bigint**|IO の発行予定時間から実際に発行されるまでの合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>権限  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_resource_governor_workload_groups &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [sys.resource_governor_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  

