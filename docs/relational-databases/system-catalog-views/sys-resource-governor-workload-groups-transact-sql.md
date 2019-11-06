---
title: sys.resource_governor_workload_groups (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_workload_groups
- resource_governor_workload_groups_TSQL
- sys.resource_governor_workload_groups_TSQL
- resource_governor_workload_groups
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_workload_groups catalog view
ms.assetid: 619ba4b7-868f-4784-b527-ec1dfd703c4f
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0f80d9ba8f5b5a1e81949d0fb2ea4b1d9bca59d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904441"
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で格納されているワークロード グループの構成を返します。 各ワークロード グループは、1 つのリソース プールにだけサブスクライブできます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ワークロード グループの一意の ID。 NULL 値は許可されません。|  
|NAME|**sysname**|ワークロード グループの名前。 NULL 値は許可されません。|  
|importance|**sysname**|**注:** 重要度は、同じリソース プール内のワークロード グループにのみ適用されます。<br /><br /> このワークロード グループでの要求の相対的な重要度。 重要度は次のいずれかで、MEDIUM が既定値です。低、中、高。<br /><br /> NULL 値は許可されません。|  
|request_max_memory_grant_percent|**int**|1 つの要求に対する最大メモリ許可 (%)。 既定値は、25 です。 NULL 値は許可されません。<br /><br /> **注:** この設定は、50% より高く、大規模なクエリには一度に 1 つずつ実行されます。 そのため、クエリの実行中にメモリが不足する危険性が高くなります。|  
|request_max_cpu_time_sec|**int**|1 つの要求に対する最大 CPU 使用制限 (秒単位)。 既定値は 0 で、制限がないことを示します。 NULL 値は許可されません。<br /><br /> **注:** 詳細については、「[CPU Threshold Exceeded イベント クラス](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)」を参照してください。|  
|request_memory_grant_timeout_sec|**int**|1 つの要求に対するメモリ許可のタイムアウト (秒単位)。 既定値は 0 で、クエリ コストに基づく内部の計算が使用されます。 NULL 値は許可されません。|  
|max_dop|**int**|ワークロード グループの並列処理の最大限度。 既定値は 0 で、グローバル設定が使用されます。 NULL 値は許可されません。<br /><br /> **ノードの場合:** この設定は、クエリ オプションをオーバーライド**maxdop**します。|  
|group_max_requests|**int**|同時要求の最大数。 既定値は 0 で、制限がないことを示します。 NULL 値は許可されません。|  
|pool_id|**int**|このワークロード グループが使用するリソース プールの ID。|  
|external_pool_id|**int**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このワークロード グループを使用する外部リソース プールの ID。|  
  
## <a name="remarks"></a>コメント  
 カタログ ビューには、格納されているメタデータが表示されます。 メモリ内の構成を参照してください、対応する動的管理ビューを使用する[sys.dm_resource_governor_workload_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)します。  
  
 リソース ガバナーの構成を変更したにもかかわらず、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを適用していない場合、異なる構成がメモリ内に格納されている可能性があります。  
  
## <a name="permissions"></a>アクセス許可  
 内容を表示するには VIEW ANY DEFINITION 権限が必要です。内容を変更するには CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
