---
title: "sys.dm_pdw_diag_processing_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ab28a8e13851642b11a5f465365ab2b48b51bd9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  管理者が定義されている診断のセッションに組み込むことができるすべての内部診断のイベントに関連する情報を表示します。 そのドライブの他のすべての Dmv の設定、診断とイベントのサブシステムの背後にある統計を理解するには、このビューをクエリします。 各ノード上の各プロセスのキューのグループがある場合します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|アプライアンスのノードがこのログはからです。|  
|**process_id**|**int**|この統計情報を送信する実行中のプロセスの識別子です。|  
|**target_name**|**nvarchar (255)**|キューの名前。|  
|**queue_size**|**int**|プロセスのキュー内の項目の数。 キューのサイズは通常は 0 です。 正の数値は、システムがストレス条件下では、イベントのバックログの構築はことを示します。 他の列で正の数は、その特定のキューのシステムが破損しているいずれかの関連の Dmv を示します。|  
|**lost_events_count**|**bigint**|イベントの数が失われました。|  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
