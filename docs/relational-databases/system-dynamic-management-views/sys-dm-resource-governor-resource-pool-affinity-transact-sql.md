---
title: sys.dm_resource_governor_resource_pool_affinity (Transact-SQL) | Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 547a1dd14eab2a5627dbd8e3b8b6e09a4c5143b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62680290"
---
# <a name="sysdmresourcegovernorresourcepoolaffinity-transact-sql"></a>sys.dm_resource_governor_resource_pool_affinity (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  リソース プールの関係を追跡します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
|Colmn 名|データ型|説明|  
|----------------|---------------|-----------------|  
|Pool_id|**int**|リソース プールの ID。 NULL 値は許可されません。|  
|Processor_group|**smallint**|Windows の論理プロセッサ グループの ID。 NULL 値は許可されません。|  
|Scheduler_mask|**bigint**|このプールに関連付けられたスケジューラを表すバイナリ マスク。 NULL 値は許可されません。|  
  
## <a name="remarks"></a>コメント  
 AUTO アフィニティで作成されたプールはアフィニティがないために、このビューでは表示されません。 詳細については、次を参照してください。、 [CREATE RESOURCE POOL &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/create-resource-pool-transact-sql.md)と[ALTER RESOURCE POOL &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-resource-pool-transact-sql.md)ステートメント。  
  
## <a name="see-also"></a>参照  
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
