---
title: sys.dm_os_memory_brokers (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_brokers
- dm_os_memory_brokers_TSQL
- sys.dm_os_memory_brokers_TSQL
- dm_os_memory_brokers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_brokers dynamic management view
ms.assetid: 48dd6ad9-0d36-4370-8a12-4921d0df4b86
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b05e4105ff23e45bb0e789e7523ba3949639210
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmosmemorybrokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内部的な割り当て[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ マネージャー。 プロセス メモリ カウンター間の違いを追跡**sys.dm_os_process_memory**内部カウンター内の外部コンポーネントからメモリの使用を示すことができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ領域です。  
  
 メモリ ブローカー内のさまざまなコンポーネント間のメモリ割り当てを適切に配分[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在および将来の使用率に基づく、します。 メモリ ブローカーは割り当てを実行しません。 配分を計算するために割り当てを追跡するだけです。  
  
 次の表は、メモリ ブローカーに関する情報を示しています。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_memory_brokers**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|リソース ガバナー プールに関連付けられているリソース プールの ID。|  
|**memory_broker_type**|**nvarchar(60)**|メモリ ブローカーの種類。 現在のメモリ ブローカーの 3 種類がある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]その説明を次に、します。<br /><br /> **MEMORYBROKER_FOR_CACHE** : で使用するために割り当てられているメモリにキャッシュされたオブジェクト。<br /><br /> **MEMORYBROKER_FOR_STEAL** : バッファー プールから盗用されたメモリ。 このメモリは、現在の所有者が解放するまで、他のコンポーネントで再利用できません。<br /><br /> **MEMORYBROKER_FOR_RESERVE** : 現在実行中要求で将来使用するために予約するメモリ。|  
|**allocations_kb**|**bigint**|この種類のブローカーに割り当てられたメモリ量 (KB 単位)。|  
|**allocations_kb_per_sec**|**bigint**|1 秒あたりのメモリ割り当て率 (KB 単位)。 メモリの割り当て解除の場合、この値は負になることがあります。|  
|**predicted_allocations_kb**|**bigint**|ブローカーによるメモリの予想割り当て量。 メモリ使用パターンに基づいて決定されます。|  
|**target_allocations_kb**|**bigint**|推奨されるメモリ割り当て量 (KB 単位)。現在の設定とメモリの使用パターンに基づいて決定されます。 このブローカーは、この数値まで割り当てを増加または減少させる必要があります。|  
|**future_allocations_kb**|**bigint**|次の数秒間に行われると予想される割り当て数 (KB 単位)。|  
|**overall_limit_kb**|**bigint**|ブローカーが割り当てることができる最大メモリ容量 (KB 単位)。|  
|**last_notification**|**nvarchar(60)**|メモリ使用量の推奨値。現在の設定と使用パターンに基づいて決定されます。 有効な値は次のとおりです。<br /><br /> grow<br /><br /> shrink<br /><br /> stable|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="see-also"></a>参照  

  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


