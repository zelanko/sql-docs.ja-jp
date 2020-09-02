---
description: dm_exec_compute_nodes (Transact-sql)
title: dm_exec_compute_nodes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 62591df1ce4a2a048c544b219f7efcc3fe18aa61
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283661"
---
# <a name="sysdm_exec_compute_nodes-transact-sql"></a>dm_exec_compute_nodes (Transact-sql)

[!INCLUDE [sqlserver2016-asa-pdw](../../includes/applies-to-version/sqlserver2016-asa-pdw.md)]

  PolyBase データ管理で使用されるノードに関する情報を保持します。 ノードごとに1つの行が表示されます。  
  
 この DMV を使用すると、スケールアウトクラスター内のすべてのノードの一覧と、それらのロール、名前、および IP アドレスが表示されます。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|ノードに関連付けられている一意の数値 id。 このビューのキー。|種類に関係なく、スケールアウトクラスター全体で一意です。|  
|type|**nvarchar(32)**|ノードの種類。|' COMPUTE '、' HEAD '|  
|name|**nvarchar(32)**|ノードの論理名。|適切な長さの任意の文字列。|  
|address|**nvarchar(32)**|このノードの IP アドレス。|IP アドレスの範囲|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューを使用した PolyBase のトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;データベース関連の動的管理ビュー ](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
