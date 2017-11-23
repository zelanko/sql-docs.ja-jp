---
title: "sys.dm_pdw_query_stats_xe (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a3f1258ca3c15d7910bb52206c4b7e8e7b2d1845
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwquerystatsxe-transact-sql"></a>sys.dm_pdw_query_stats_xe (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  この DMV は推奨されておらず、将来のリリースでは削除されます。 このリリースでは、0 行を返します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|イベント|**nvarchar (60)**|このビューのキーです。||  
|event_id|**nvarchar (36)**|||  
|create_time|**datetime**|||  
|session_id|**int**|セッションの id。|Session_id を参照してください[sys.dm_pdw_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|cpu|**int**|||  
|reads|**int**|イベントの開始以降の論理読み取りの数。||  
|writes|**int**|イベントの開始以降の論理書き込みの数。||  
|sql_text|**nvarchar (4000)**|||  
|client_app_name|**nvarchar (255)**|||  
|tsql_stack|**nvarchar (255)**|||  
|pdw_node_id|**int**|この Xevent のインスタンスが実行されているノードです。|  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
