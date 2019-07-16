---
title: sys.resource_governor_resource_pools (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_resource_pools
- resource_governor_resource_pools
- sys.resource_governor_resource_pools_TSQL
- resource_governor_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_resource_pools catalog view
ms.assetid: 56793e9c-aa90-452e-88c6-d9b799239888
author: stevestein
ms.author: sstein
ms.openlocfilehash: 06ed4b4820ce7a6e6483df6efd1de2e8fbadf954
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904466"
---
# <a name="sysresourcegovernorresourcepools-transact-sql"></a>sys.resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で格納されているリソース プール構成を返します。 ビューの各行は、プールの構成を決定します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|リソース プールの一意の ID。 NULL 値は許可されません。|  
|NAME|**sysname**|リソース プールの名前。 NULL 値は許可されません。|  
|min_cpu_percent|**int**|CPU の競合がある場合にリソース プールのすべての要求に保証される平均 CPU 帯域幅。 NULL 値は許可されません。|  
|max_cpu_percent|**int**|最大平均 CPU 帯域幅 CPU の競合がある場合に、リソース プールのすべての要求に許可します。 NULL 値は許可されません。|  
|min_memory_percent|**int**|すべての要求にリソース プール メモリの量を保証します。 これは、他のリソース プールとは共有されません。 NULL 値は許可されません。|  
|max_memory_percent|**int**|このリソース プールの要求で使用できる合計サーバー メモリの割合。 NULL 値は許可されません。 効果的な最大値は、プールの最小値に依存します。 たとえば、max_memory_percent を 100 に設定できますが、効果的な最大値は低くなります。|  
|cap_cpu_percent|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> リソース プール内のすべての要求を受信する、CPU 帯域幅のハード キャップ。 CPU の最大帯域幅を、指定したレベルに制限します。 値の許容範囲は 1 ~ 100 です。|  
|min_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのボリューム設定ごと秒 (IOPS) あたりの最小 I/O 操作。 0 = 予約なし。 null にすることはできません。|  
|max_iops_per_volume|**int**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> このプールのボリューム設定ごとの、1 秒あたりの最大 I/O 操作 (IOPS)。 0 = 無制限です。 null にすることはできません。|  
  
## <a name="remarks"></a>コメント  
 カタログ ビューには、格納されているメタデータが表示されます。 メモリ内の構成を参照してください、対応する動的管理ビューを使用する[sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 内容を表示するには VIEW ANY DEFINITION 権限が必要です。内容を変更するには CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)  
  
  
