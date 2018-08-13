---
title: sys.dm_exec_compute_nodes (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODES_TSQL
- DM_EXEC_COMPUTE_NODES
- SYS.DM_EXEC_COMPUTE_NODES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_compute_nodes management view
- PolyBase, views
- PolyBase management views
- dm_exec_compute_nodes management view
ms.assetid: 0de4b7a4-401f-4e2d-9ab0-c54587e05154
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 7d66ff5e30a34cec0e64f4ad1eea5b9d7ac6cfb1
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39547662"
---
# <a name="sysdmexeccomputenodes-transact-sql"></a>sys.dm_exec_compute_nodes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  PolyBase データ管理で使用されるノードに関する情報を保持します。 これには、ノードごとに 1 行が一覧表示します。  
  
 この DMV を使用して、そのロール、名と IP アドレスを使用して、スケール アウト クラスターのすべてのノードの一覧を参照してください。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|ノードに関連付けられている一意の数値 id です。 このビューのキーです。|種類に関係なく、スケール アウト クラスター全体にわたって一意です。|  
|type|**nvarchar(32)**|ノードの型。|' COMPUTE'、'ヘッド'|  
|NAME|**nvarchar(32)**|ノードの論理名です。|適切な長さの任意の文字列。|  
|address|**nvarchar(32)**|このノードの P アドレスです。|IP アドレスの範囲|  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
