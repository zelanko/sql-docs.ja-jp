---
title: dm_resource_governor_external_resource_pool_affinity (トランザクション-SQL) |マイクロソフトドキュメント
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
ms.openlocfilehash: 77d0d322139be1f1c6086622855600a7c24fc4c9
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664320"
---
# <a name="sysdm_resource_governor_external_resource_pool_affinity-transact-sql"></a>dm_resource_governor_external_resource_pool_affinity (トランザクション-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**適用対象:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] および [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]。

現在の外部リソース プール構成に関する CPU アフィニティ情報を返します。
  
|列名|データ型|説明|
|----------------|---------------|-----------------|
|pool_id|**int**|外部リソース プールの ID。 NULL 値は許可されません。|
|processor_group|**smallint**|Windows 論理プロセッサ グループの ID。 NULL 値は許可されません。|
|cpu_mask|**Bigint**|このプールに関連付けられている CPU を表すバイナリ マスク。 NULL 値は許可されません。|
  
## <a name="remarks"></a>解説

アフィニティを使用して作成された`AUTO`プールは、アフィニティーがないため、このビューには表示されません。 詳細については[、「Transact-SQL&#41;&#40;外部リソース プールの作成」および「Transact-SQL](../../t-sql/statements/create-external-resource-pool-transact-sql.md)&#41;ステートメント[&#40;外部リソース プールの変更](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)」を参照してください。

## <a name="permissions"></a>アクセス許可

`VIEW SERVER STATE` 権限が必要です。

## <a name="see-also"></a>関連項目

[SQL Server での Machine Learning のリソース管理](../../machine-learning/administration/resource-governor.md)

[トランザクション SQL&#41;&#40;sys.dm_resource_governor_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[external scripts enabled サーバー構成オプション](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
