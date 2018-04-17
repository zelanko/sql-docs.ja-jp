---
title: sys.dm_pdw_node_status (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2ff2f23fcfc6314d06f55bca2b918d954f43514e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwnodestatus-transact-sql"></a>sys.dm_pdw_node_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  追加情報を保持 (経由で[sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) のパフォーマンスとアプライアンスのすべてのノードの状態に関するします。 アプライアンス内のノードごとに 1 行が一覧表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id です。<br /><br /> このビューのキーです。|種類に関係なく、アプライアンスの間で一意です。|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar (255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|合計では、このノード上のメモリが割り当てられます。||  
|available_memory|**bigint**|このノードで使用可能なメモリの合計。||  
|process_cpu_usage|**bigint**|合計のプロセス CPU 使用率、タイマー刻みで。||  
|total_cpu_usage|**bigint**|合計 CPU 使用率、タイマー刻みで。||  
|thread_count|**bigint**|このノードで使用しているスレッドの合計数。||  
|handle_count|**bigint**|このノードで使用中のハンドルの合計数。||  
|total_elapsed_time|**bigint**|時間の合計には、システムを起動または再起動からが経過しました。|時間の合計には、システムを起動または再起動からが経過しました。 Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|is_available|**bit**|このノードが使用できるかどうかを示すフラグします。||  
|sent_time|**datetime**|最後に、ネットワークのパッケージは、このノードが送信されました。||  
|received_time|**datetime**|最後に、ネットワークのパッケージは、このノードによって受信されました。||  
|error_id|**nvarchar(36)**|このノードで発生した最後のエラーの一意の識別子。||  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
