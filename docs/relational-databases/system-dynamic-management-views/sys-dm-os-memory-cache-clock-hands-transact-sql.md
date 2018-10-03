---
title: sys.dm_os_memory_cache_clock_hands (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6b39f40a36a9b9a639b8b6c90f6a6a37f7a32a4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815116"
---
# <a name="sysdmosmemorycacheclockhands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のキャッシュ クロックに関する各ハンドの状態を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_memory_cache_clock_hands**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|クロックに関連付けられたキャッシュのアドレス。 NULL 値は許可されません。|  
|**name**|**nvarchar (256)**|キャッシュの名前。 NULL 値は許可されません。|  
|**type**|**nvarchar(60)**|キャッシュ保存の種類。 同じ種類のキャッシュが複数存在することが可能です。 NULL 値は許可されません。|  
|**clock_hand**|**nvarchar(60)**|ハンドの種類。 これは、次のいずれかです。<br /><br /> External<br /><br /> Internal<br /><br /> NULL 値は許可されません。|  
|**clock_status**|**nvarchar(60)**|クロックの状態。 これは、次のいずれかです。<br /><br /> 中断<br /><br /> 実行中<br /><br /> NULL 値は許可されません。|  
|**rounds_count**|**bigint**|エントリを削除するため、キャッシュ経由で行われたスイープの数。 NULL 値は許可されません。|  
|**removed_all_rounds_count**|**bigint**|すべてのスイープで削除されたエントリの数。 NULL 値は許可されません。|  
|**updated_last_round_count**|**bigint**|前回のスイープ中に更新されたエントリの数。 NULL 値は許可されません。|  
|**removed_last_round_count**|**bigint**|前回のスイープ中に削除されたエントリの数。 NULL 値は許可されません。|  
|**last_tick_time**|**bigint**|クロック ハンドが前回移動した時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|**round_start_time**|**bigint**|前回のスイープの時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|**last_round_start_time**|**bigint**|前回のラウンドの完了でクロックに使用された合計時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] メモリ キャッシュと呼ばれる構造体でメモリ内の情報を格納します。 キャッシュには、データ、インデックス エントリ、コンパイル済みプロシージャ プランなど、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に関するさまざまな種類の情報が格納されます。 再作成の回数を最小限に抑えるため、これらの情報は可能な限り長くメモリ キャッシュに保持されます。これらの情報がキャッシュから削除されるのは、古くなりすぎて使えなくなった場合や、新しい情報を格納するためのメモリ領域が必要になった場合です。 この古くなった情報を削除する処理をメモリ スイープといいます。 メモリ スイープは頻繁に行われる処理ですが、連続的ではありません。 メモリ キャッシュのスイープはクロック アルゴリズムによって制御され、 1 つのクロックで複数のメモリ スイープを制御できます。この単位をハンドといいます。 メモリ キャッシュのクロック ハンドは、メモリ スイープの 1 つのハンドの現在位置を示します。  

## <a name="see-also"></a>参照  
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys.dm_os_memory_cache_counters &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

