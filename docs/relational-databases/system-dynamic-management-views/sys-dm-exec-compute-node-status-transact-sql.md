---
title: sys.dm_exec_compute_node_status (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1a219ab9606327bd67e26d237a9f8b7b5c2cb8fa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097872"
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>sys.dm_exec_compute_node_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  パフォーマンスと PolyBase のすべてのノードの状態に関する追加情報を保持します。 ノードごとに 1 行を一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|ノードに関連付けられている一意の数値 id。|種類に関係なく、スケール アウト クラスター全体にわたって一意です。|  
|process_id|**int**|||  
|process_name|**nvarchar (255)**|ノードの論理名です。|適切な長さの文字列は任意です。|  
|allocated_memory|**bigint**|このノード上のメモリを割り当てられた合計数。||  
|available_memory|**bigint**|このノードで使用可能なメモリを合計します。||  
|process_cpu_usage|**bigint**|合計のプロセス CPU 使用率、タイマー刻みで。||  
|total_cpu_usage|**bigint**|合計 CPU 使用率、タイマー刻みで。||  
|thread_count|**bigint**|このノードで使用しているスレッドの合計数。||  
|handle_count|**bigint**|このノードで使用中のハンドルの合計数。||  
|total_elapsed_time|**bigint**|システムを起動または再起動後の経過時間の合計です。|システムを起動または再起動後の経過時間の合計です。 Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超える、それをオーバーフローしました期日の実体化エラーが発生します。最大値をミリ秒単位は 24.8 日に相当します。|  
|is_available|**bit**|このノードが使用できるかどうかを示すフラグします。||  
|sent_time|**datetime**|最後に、ネットワークのパッケージは、これによって送信されました||  
|received_time|**datetime**|最後に、ネットワークのパッケージは、このノードに送信されました。||  
|error_id|**nvarchar(36)**|このノードで発生した最後のエラーの一意の識別子。||  
  
## <a name="see-also"></a>関連項目  
 [PolyBase 動的管理ビューでのトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
