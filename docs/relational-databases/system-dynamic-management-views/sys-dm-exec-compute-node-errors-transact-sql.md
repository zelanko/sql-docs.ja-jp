---
title: sys.dm_exec_compute_node_errors (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SYS.DM_EXEC_COMPUTE_NODE_ERRORS_TSQL
- DM_EXEC_COMPUTE_NODE_ERRORS
- DM_EXEC_COMPUTE_NODE_ERRORS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase
- PolyBase, views
- dm_exec_compute_node_errors
- sys.dm_exec_compute_node_errors management view
ms.assetid: 9a03c039-70e4-4974-95d8-d3fa45984ffb
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ca01e2b67d4443c1ac1efa03fa86542b46d3de34
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexeccomputenodeerrors-transact-sql"></a>sys.dm_exec_compute_node_errors (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  PolyBase で発生したを返します。 エラーは、ノードを計算します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|エラーに関連付けられている一意の数値 id です。|システム内のすべてのクエリ エラーにおいては一意で|  
|source|**nvarchar (255)**|ソース スレッドまたはプロセスの説明||  
|型|**nvarchar (255)**|エラーの種類。||  
|create_time|**datetime**|エラーの発生場所の時間||  
|compute_node_id|**int**|特定のコンピューティング ノードの識別子|Compute_node_id を参照してください[sys.dm_exec_compute_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)|  
|rexecution_id|**nvarchar(36)**|PolyBase クエリでは、存在する場合の識別子です。||  
|spid|**int**|SQL Server セッションの識別子||  
|thread_id|**int**|エラーが発生したスレッドの数値識別子。||  
|詳細情報|nvarchar (4000)|エラーの詳細の詳細な説明。||  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
