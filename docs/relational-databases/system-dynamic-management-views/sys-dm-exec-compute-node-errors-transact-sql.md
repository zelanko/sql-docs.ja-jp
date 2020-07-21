---
title: dm_exec_compute_node_errors (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5de36530fcf50a403558cb97fa72ad6a2d126e32
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830694"
---
# <a name="sysdm_exec_compute_node_errors-transact-sql"></a>dm_exec_compute_node_errors (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  PolyBase 計算ノードで発生したエラーを返します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|error_id|`nvarchar(36)`|エラーに関連付けられている一意の数値 id。|システム内のすべてのクエリエラー間で一意|  
|ソース|`nvarchar(255)`|ソーススレッドまたはプロセスの説明||  
|型|`nvarchar(255)`|エラーの種類。||  
|create_time|`datetime`|エラーが発生した時刻||  
|compute_node_id|`int`|特定の計算ノードの識別子|[Dm_exec_compute_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)の compute_node_id を参照してください。|  
|rexecution_id|`nvarchar(36)`|PolyBase クエリの識別子 (存在する場合)。||  
|調べる|`int`|SQL Server セッションの識別子||  
|thread_id|`int`|エラーが発生したスレッドの数値識別子。||  
|details|nvarchar(4000)|エラーの詳細の詳細な説明。||
|compute_pool_id|`int`|プールの一意の識別子。|

  
## <a name="see-also"></a>参照  
 [動的管理ビューを使用した PolyBase のトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;データベース関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
