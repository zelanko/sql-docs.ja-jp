---
title: "sys.dm_exec_dms_services (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DMS_SERVICES_TSQL
- SYS.DM_EXEC_DMS_SERVICES_TSQL
- DM_EXEC_DMS_SERVICES
dev_langs: TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_services management view
- sys.dm_exec_dms_services management view
ms.assetid: 6ac47eef-4293-46b8-8555-07a614837504
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c4a8bbdafc5674cd2257fa151ae24683d5d8a69
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecdmsservices-transact-sql"></a>sys.dm_exec_dms_services (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  すべての PolyBase コンピューティング ノードで実行されている DMS サービスに関する情報を保持します。 これには、サービス インスタンスごとに 1 行が一覧表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|DMS コアに関連付けられている一意の数値 id です。 このビューのキーです。|一意の id。|  
|compute_node_id|**int**|この DMS サービスが実行されているノードの ID|参照してください*compute_node_id*で[sys.dm_exec_compute_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md).|  
|ステータス|**nvarchar (32)**|DMS サービスの現在の状態||  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
