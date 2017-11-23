---
title: "sys.dm_pdw_sys_info (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2bd97fc3499d0bb240be35ffe92ac8869fd7ccf6
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwsysinfo-transact-sql"></a>sys.dm_pdw_sys_info (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  アプライアンス上の全体的なアクティビティを反映するアプライアンス レベルのカウンターのセットを提供します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|システムの現在のセッションの数。|max_active_sessions (下記参照) に 0 を返します。|  
|idle_sessions|**int**|現在のアイドル状態のセッションの数。||  
|active_requests|**int**|現在実行中のアクティブな要求の数。||  
|queued_requests|**int**|現在キューに置かれた要求の数。||  
|active_loads|**int**|負荷は、システムで現在実行中の数です。||  
|queued_loads|**int**|キューに登録された読み込みの実行を待機の数です。||  
|active_backups|**int**|現在実行中のバックアップの数。||  
|active_restores|**int**|バックアップの数は、現在実行中を復元します。||  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
