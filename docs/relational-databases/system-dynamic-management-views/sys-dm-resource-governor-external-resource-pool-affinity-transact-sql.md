---
title: "sys.dm_resource_governor_external_resource_pool_affinity (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
caps.latest.revision: "8"
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1f5fa2851b5b03708eb28c42d4e2496258d187b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_external_resource_pool_affinity (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**適用されます:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]と[!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

CPU アフィニティ、現在の外部リソース プールの構成情報を返します。
  
|列名|データ型|Description|
|----------------|---------------|-----------------|
|pool_id|**int**|外部リソース プールの ID。 NULL 値は許可されません。|
|processor_group|**smallint**|Windows の論理プロセッサ グループの ID。 NULL 値は許可されません。|
|cpu_mask|**bigint**|このプールに関連付けられている Cpu を表すバイナリ マスク。 NULL 値は許可されません。|
  
## <a name="remarks"></a>解説

アフィニティで作成されたプールに`AUTO`アフィニティがないためにこのビューに表示されません。 詳細については、次を参照してください。、 [CREATE EXTERNAL RESOURCE POOL &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-external-resource-pool-transact-sql.md)と[外部リソース プール &#40; を ALTERTRANSACT-SQL と #41 です。](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)ステートメントです。

## <a name="permissions"></a>Permissions

必要があります`VIEW SERVER STATE`権限です。

## <a name="see-also"></a>参照

[SQL Server での機械学習用リソース ガバナンス](../../advanced-analytics/r/resource-governance-for-r-services.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
