---
title: "sys.dm_exec_compute_node_status (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f898f754f0b39b0f5746d8ed076c75d26354bccd
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>sys.dm_exec_compute_node_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  パフォーマンスと PolyBase のすべてのノードの状態に関する追加情報を保持します。 ノードごとに 1 行の一覧を表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|ノードに関連付けられている一意の数値 id です。|種類に関係なく、スケール アウト クラスター全体にわたって一意です。|  
|process_id|**int**|||  
|process_name|**nvarchar (255)**|ノードの論理名です。|適切な長さの任意の文字列。|  
|allocated_memory|**bigint**|合計では、このノード上のメモリが割り当てられます。||  
|available_memory|**bigint**|このノードで使用可能なメモリの合計。||  
|process_cpu_usage|**bigint**|合計のプロセス CPU 使用率、タイマー刻みで。||  
|total_cpu_usage|**bigint**|合計 CPU 使用率、タイマー刻みで。||  
|thread_count|**bigint**|このノードで使用しているスレッドの合計数。||  
|handle_count|**bigint**|このノードで使用中のハンドルの合計数。||  
|total_elapsed_time|**bigint**|時間の合計には、システムを起動または再起動からが経過しました。|時間の合計には、システムを起動または再起動からが経過しました。 Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。最大値をミリ秒単位は 24.8 日に相当します。|  
|is_available|**bit**|このノードが使用できるかどうかを示すフラグします。||  
|sent_time|**datetime**|最後にこのネットワークのパッケージが送信されました||  
|received_time|**datetime**|最後に、ネットワークのパッケージは、このノードが送信されました。||  
|error_id|**nvarchar(36)**|このノードで発生した最後のエラーの一意の識別子。||  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
