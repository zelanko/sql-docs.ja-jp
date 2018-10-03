---
title: sys.dm_exec_dms_services (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_DMS_SERVICES_TSQL
- SYS.DM_EXEC_DMS_SERVICES_TSQL
- DM_EXEC_DMS_SERVICES
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_dms_services management view
- sys.dm_exec_dms_services management view
ms.assetid: 6ac47eef-4293-46b8-8555-07a614837504
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 98e970b1c786b15308c85fdb97222b6936173b6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595190"
---
# <a name="sysdmexecdmsservices-transact-sql"></a>sys.dm_exec_dms_services (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  すべての PolyBase コンピューティング ノードで実行されている DMS サービスに関する情報を保持します。 これには、サービス インスタンスごとに 1 行が一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|DMS コアに関連付けられている一意の数値 id です。 このビューのキーです。|一意の id。|  
|compute_node_id|**int**|この DMS サービスが実行されているノードの ID|参照してください*compute_node_id*で[sys.dm_exec_compute_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)します。|  
|status|**nvarchar(32)**|DMS サービスの現在の状態||  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
