---
title: resource_governor_external_resource_pools (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_external_resource_pools
- sys.resource_governor_external_resource_pools_TSQL
- resource_governor_external_resource_pools
- resource_governor_external_resource_pools_TSQL
helpviewer_keywords:
- sys.resource_governor_external_resource_pools
- resource_governor_external_resource_pools
ms.assetid: 75063e36-a91b-496f-9936-88f3d57bd447
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4751cb9164d5ca11cfdaca4365fa7156c2c2425e
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80662998"
---
# <a name="sysresource_governor_external_resource_pools-transact-sql"></a>resource_governor_external_resource_pools (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**適用対象:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] および [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]。

に格納されている外部リソース プールの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]構成を返します。 ビューの各行によって、プールの構成が決まります。
  
|列名|データ型|説明|
|-----------------|---------------|-----------------|
|external_pool_id|**int**|リソース プールの一意の ID。 NULL 値は許可されません。|
|name|**Sysname**|リソース プールの名前。 NULL 値は許可されません。|
|max_cpu_percent|**int**|CPU 競合がある場合に、リソース プール内のすべての要求に対して許可される最大平均 CPU 帯域幅。 NULL 値は許可されません。|
|max_memory_percent|**int**|このリソース プール内の要求で使用できるサーバー メモリの合計の割合です。 NULL 値は許可されません。 有効な最大値は、プールの最小値によって異なります。 たとえば、max_memory_percent100 に設定できますが、有効な最大値は低くなります。|
|max_processes|**int**|同時実行外部プロセスの最大数。 既定値の 0 では、制限なしが指定されます。 NULL 値は許可されません。|
|version|**Bigint**|内部バージョン番号。|
  
## <a name="permissions"></a>アクセス許可

VIEW SERVER STATE 権限が必要です。

## <a name="see-also"></a>関連項目

[SQL Server での Machine Learning のリソース管理](../../machine-learning/administration/resource-governor.md)

[Transact-SQL&#41;&#40;リソース ガバナー カタログ ビュー](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)

[sys.dm_resource_governor_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)

[[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)

[トランザクション SQL&#41;&#40;sys.dm_resource_governor_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
