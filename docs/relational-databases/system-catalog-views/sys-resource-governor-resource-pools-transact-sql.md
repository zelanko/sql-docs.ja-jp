---
title: "sys.resource_governor_resource_pools (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_resource_pools
- resource_governor_resource_pools
- sys.resource_governor_resource_pools_TSQL
- resource_governor_resource_pools_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.resource_governor_resource_pools catalog view
ms.assetid: 56793e9c-aa90-452e-88c6-d9b799239888
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b8c30e6f3298e73a61484ecf9488d71e17701f7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysresourcegovernorresourcepools-transact-sql"></a>sys.resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で格納されているリソース プール構成を返します。 ビューの各行によってプールの構成が決定されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|リソース プールの一意の ID。 NULL 値は許可されません。|  
|name|**sysname**|リソース プールの名前です。 NULL 値は許可されません。|  
|min_cpu_percent|**int**|CPU の競合がある場合にリソース プールのすべての要求に保証される平均 CPU 帯域幅。 NULL 値は許可されません。|  
|max_cpu_percent|**int**|CPU の競合がある場合にリソース プールのすべての要求に許可される最大平均 CPU 帯域幅。 NULL 値は許可されません。|  
|min_memory_percent|**int**|リソース プールのすべての要求に保証されるメモリ量。 これは、他のリソース プールとは共有されません。 NULL 値は許可されません。|  
|max_memory_percent|**int**|このリソース プールの要求で使用できる合計サーバー メモリの割合。 NULL 値は許可されません。 効果的な最大値はプールの最小値によって異なります。 たとえば、max_memory_percent を 100 に設定することは可能ですが、効果的な最大値はそれより小さな値になります。|  
|cap_cpu_percent|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース プールのすべての要求に割り当てられる、CPU 帯域幅のハード キャップ。 CPU の最大帯域幅を、指定したレベルに制限します。 値の許容範囲は 1 ～ 100 です。|  
|min_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのボリューム設定ごとの、1 秒あたりの最小 I/O 操作 (IOPS)。 0 = 予約なし。 null にすることはできません。|  
|max_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのボリューム設定ごとの、1 秒あたりの最大 I/O 操作 (IOPS)。 0 = 無制限。 null にすることはできません。|  
  
## <a name="remarks"></a>解説  
 カタログ ビューには、格納されているメタデータが表示されます。 メモリ内の構成を参照して、対応する動的管理ビューを使用して[sys.dm_resource_governor_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 内容を表示するには VIEW ANY DEFINITION 権限が必要です。内容を変更するには CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [リソース ガバナーのカタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.resource_governor_external_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)  
  
  
