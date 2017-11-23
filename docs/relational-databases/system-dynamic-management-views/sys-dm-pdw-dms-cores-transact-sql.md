---
title: "sys.dm_pdw_dms_cores (TRANSACT-SQL) |Microsoft ドキュメント"
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
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c1194f0f370d947e14a93f1ebc33f05fb8517f1e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwdmscores-transact-sql"></a>sys.dm_pdw_dms_cores (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  アプライアンスの計算ノードで実行されているすべての DMS サービスに関する情報を保持します。 これには、現在のノードごとに 1 行には、サービスのインスタンスごとに 1 行が一覧表示します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|この DMS コアに関連付けられている一意の数値 id です。<br /><br /> このビューのキーです。|この DMS コアが実行されているノードの pdw_node_id に設定されます。|  
|pdw_node_id|**int**|この DMS サービスが実行されているノードの ID。|Node_id を参照してください[sys.dm_pdw_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|ステータス|**nvarchar (32)**|DMS サービスの現在の状態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 このビューで保持される最大行数のについてを参照してくださいシステム ビューの最大値、[最小値と最大値 (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)トピックです。  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
