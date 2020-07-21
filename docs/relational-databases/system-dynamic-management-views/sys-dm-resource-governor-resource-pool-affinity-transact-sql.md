---
title: dm_resource_governor_resource_pool_affinity (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_resource_pool_affinity_TSQL
- sys.dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity
- dm_resource_governor_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_resource_pool_affinity
- sys.dm_resource_governor_resource_pool_affinity
ms.assetid: a197ec19-a2ba-44f5-a4f2-3eee33ebd77d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 649bb3d5278337db4bda4b3f3622823bd3b35a17
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784888"
---
# <a name="sysdm_resource_governor_resource_pool_affinity-transact-sql"></a>dm_resource_governor_resource_pool_affinity (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  リソースプールの関係を追跡します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
|名前の指定|データの種類|説明|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|リソースプールの ID。 NULL 値は許可されません。|  
|Processor_group|**smallint**|Windows 論理プロセッサグループの ID。 NULL 値は許可されません。|  
|Scheduler_mask|**bigint**|このプールに関連付けられているスケジューラを表すバイナリマスク。 NULL 値は許可されません。|  
  
## <a name="remarks"></a>Remarks  
 [自動] のアフィニティを使用して作成されたプールは、アフィニティがないため、このビューに表示されません。 詳細については、「 [CREATE RESOURCE pool &#40;transact-sql&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md) 」および「 [ALTER Resource pool &#40;transact-sql&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)ステートメント」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
