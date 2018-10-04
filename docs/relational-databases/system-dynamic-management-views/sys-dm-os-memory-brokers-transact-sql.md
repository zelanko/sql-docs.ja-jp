---
title: sys.dm_os_memory_brokers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc48ab35ce0a2897b0167fd8609c21f46926966a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802900"
---
# <a name="sysdmosmemorybrokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内部的な割り当て[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ マネージャー。 プロセス メモリ カウンター間の差を追跡**sys.dm_os_process_memory**内部カウンターは、外部コンポーネントからメモリ使用量を示すことができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリ領域です。  
  
 メモリ ブローカー内のさまざまなコンポーネント間のメモリ割り当てを適切に配分[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在と予想される使用量に基づきます。 メモリ ブローカーは割り当てを実行しません。 配分を計算するために割り当てを追跡するだけです。  
  
 次の表は、メモリ ブローカーに関する情報を示しています。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_memory_brokers**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|リソース ガバナー プールに関連付けられているリソース プールの ID。|  
|**memory_broker_type**|**nvarchar(60)**|メモリ ブローカーの種類。 現在は、次の 3 つの種類でのメモリ ブローカーの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]とその説明の下に表示されています。<br /><br /> **MEMORYBROKER_FOR_CACHE** : で使用するために割り当てられたメモリにキャッシュされたオブジェクト (キャッシュのバッファー プールではありません)。<br /><br /> **MEMORYBROKER_FOR_STEAL** : バッファー プールから盗用されたメモリ。 このメモリは、現在の所有者が解放するまで、他のコンポーネントで再利用できません。<br /><br /> **MEMORYBROKER_FOR_RESERVE** : メモリの現在の要求を実行することによって将来使用するために予約されています。|  
|**allocations_kb**|**bigint**|この種類のブローカーに割り当てられたメモリ量 (KB 単位)。|  
|**allocations_kb_per_sec**|**bigint**|1 秒あたりのメモリ割り当て率 (KB 単位)。 メモリの割り当て解除の場合、この値は負になることがあります。|  
|**predicted_allocations_kb**|**bigint**|ブローカーによるメモリの予想割り当て量。 メモリ使用パターンに基づいて決定されます。|  
|**target_allocations_kb**|**bigint**|推奨されるメモリ割り当て量 (KB 単位)。現在の設定とメモリの使用パターンに基づいて決定されます。 このブローカーは、この数値まで割り当てを増加または減少させる必要があります。|  
|**future_allocations_kb**|**bigint**|次の数秒間に行われると予想される割り当て数 (KB 単位)。|  
|**overall_limit_kb**|**bigint**|ブローカーが割り当てることができる最大メモリ容量 (KB 単位)。|  
|**last_notification**|**nvarchar(60)**|メモリ使用量の推奨値。現在の設定と使用パターンに基づいて決定されます。 有効な値は次のとおりです。<br /><br /> grow<br /><br /> shrink<br /><br /> stable|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
  
## <a name="see-also"></a>参照  

  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


