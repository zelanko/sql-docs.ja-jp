---
title: sys.resource_governor_workload_groups (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 199ef10970da1f2bb9b10e716ecc5e9f894aa448
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysresourcegovernorworkloadgroups-transact-sql"></a>sys.resource_governor_workload_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で格納されているワークロード グループの構成を返します。 各ワークロード グループは、1 つのリソース プールにだけサブスクライブできます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|group_id|**int**|ワークロード グループの一意の ID。 NULL 値は許可されません。|  
|name|**sysname**|ワークロード グループの名前。 NULL 値は許可されません。|  
|importance|**sysname**|**注:**重要度が同じリソース プール内のワークロード グループにのみ適用されます。<br /><br /> このワークロード グループでの要求の相対的な重要度。 次のいずれかの重要度は、メディアで既定値: 低、中、高です。<br /><br /> NULL 値は許可されません。|  
|request_max_memory_grant_percent|**int**|1 つの要求に対する最大メモリ許可 (%)。 既定値は、25 です。 NULL 値は許可されません。<br /><br /> **注:**の大規模なクエリと 1 つずつこの設定が 50% より大きい場合は、実行します。 そのため、クエリの実行中にメモリが不足する危険性が高くなります。|  
|request_max_cpu_time_sec|**int**|1 つの要求に対する最大 CPU 使用制限 (秒単位)。 既定値は 0 で、制限がないことを示します。 NULL 値は許可されません。<br /><br /> **注:**詳細については、次を参照してください。 [CPU しきい値 Exceeded イベント クラス](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)です。|  
|request_memory_grant_timeout_sec|**int**|1 つの要求に対するメモリ許可のタイムアウト (秒単位)。 既定値は 0 で、クエリ コストに基づく内部の計算が使用されます。 NULL 値は許可されません。|  
|max_dop|**int**|ワークロード グループの並列処理の最大限度。 既定値は 0 で、グローバル設定が使用されます。 NULL 値は許可されません。<br /><br /> **ノード:**この設定は、クエリ オプションをオーバーライド**maxdop**です。|  
|group_max_requests|**int**|同時要求の最大数。 既定値は 0 で、制限がないことを示します。 NULL 値は許可されません。|  
|pool_id|**int**|このワークロード グループが使用するリソース プールの ID。|  
|external_pool_id|**int**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このワークロード グループを使用して外部リソース プールの ID です。|  
  
## <a name="remarks"></a>解説  
 カタログ ビューには、格納されているメタデータが表示されます。 メモリ内の構成を参照して、対応する動的管理ビューを使用して[sys.dm_resource_governor_workload_groups &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)です。  
  
 リソース ガバナーの構成を変更したにもかかわらず、ALTER RESOURCE GOVERNOR RECONFIGURE ステートメントを適用していない場合、異なる構成がメモリ内に格納されている可能性があります。  
  
## <a name="permissions"></a>権限  
 内容を表示するには VIEW ANY DEFINITION 権限が必要です。内容を変更するには CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.dm_resource_governor_workload_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)  
  
  
