---
title: sys.dm_pdw_query_stats_xe_file (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.reviewer: 
ms.service: 
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e0cd402f-04d0-4a5b-b725-88b31bb7862e
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2154be22153f17cf8490f081822ee758f6c9bab5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwquerystatsxefile-transact-sql"></a>sys.dm_pdw_query_stats_xe_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  この DMV は推奨されておらず、将来のリリースでは削除されます。 このリリースでは、0 行を返します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|イベント|**nvarchar(60)**|このビューのキーです。||  
|data|**xml**|||  
|pdw_node_id|**int**|この Xevent のインスタンスが実行されているノードです。||  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
