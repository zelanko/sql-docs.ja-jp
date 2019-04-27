---
title: sys.dm_resource_governor_external_resource_pool_affinity (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4439cddb4af80a5d76a5b4e3600fd5e5ede6b900
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62744064"
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_external_resource_pool_affinity (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**適用対象:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] および [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

現在、外部リソース プールの構成について、CPU アフィニティ情報を返します。
  
|列名|データ型|説明|
|----------------|---------------|-----------------|
|pool_id|**int**|外部リソース プールの ID。 NULL 値は許可されません。|
|processor_group|**smallint**|Windows の論理プロセッサ グループの ID。 NULL 値は許可されません。|
|cpu_mask|**bigint**|このプールに関連付けられている Cpu を表すバイナリ マスク。 NULL 値は許可されません。|
  
## <a name="remarks"></a>コメント

アフィニティで作成されたプール`AUTO`アフィニティがないためにこのビューに表示されません。 詳細については、次を参照してください。、 [CREATE EXTERNAL RESOURCE POOL &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md)と[ALTER EXTERNAL RESOURCE POOL &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)ステートメント。

## <a name="permissions"></a>アクセス許可

`VIEW SERVER STATE` 権限が必要です。

## <a name="see-also"></a>関連項目

[SQL Server での Machine Learning のリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
