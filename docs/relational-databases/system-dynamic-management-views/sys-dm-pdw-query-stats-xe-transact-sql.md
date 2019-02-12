---
title: sys.dm_pdw_query_stats_xe (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d4ade9fe6cb13ae26823a399678e994edc69a3f8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020663"
---
# <a name="sysdmpdwquerystatsxe-transact-sql"></a>sys.dm_pdw_query_stats_xe (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  この DMV は非推奨とされており、将来のリリースでは削除されます。 このリリースでは、0 行を返します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|イベント|**nvarchar(60)**|このビューのキーです。||  
|event_id|**nvarchar(36)**|||  
|create_time|**datetime**|||  
|session_id|**int**|セッションの id。|Session_id を参照してください。 [sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)します。|  
|cpu|**int**|||  
|reads|**int**|イベントの開始以降の論理読み取りの数。||  
|writes|**int**|イベントの開始以降の論理書き込みの数。||  
|sql_text|**nvarchar (4000)**|||  
|client_app_name|**nvarchar (255)**|||  
|tsql_stack|**nvarchar (255)**|||  
|pdw_node_id|**int**|この Xevent のインスタンスが実行されているノードです。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
