---
title: sys.dm_pdw_dms_cores (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-objects
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2c0d681ef3b1d5a7843a955f9e5e0e4a3f69c4e9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037310"
---
# <a name="sysdmpdwdmscores-transact-sql"></a>sys.dm_pdw_dms_cores (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  アプライアンスの計算ノードで実行されているすべての DMS サービスに関する情報を保持します。 これには、現在のノードごとに 1 行には、サービスのインスタンスごとに 1 行が一覧表示します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|この DMS コアに関連付けられている一意の数値 id です。<br /><br /> このビューのキーです。|この DMS コアがで実行されているノードの pdw_node_id に設定します。|  
|pdw_node_id|**int**|この DMS サービスが実行されているノードの ID。|Node_id を参照してください。 [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)します。|  
|status|**nvarchar(32)**|DMS サービスの現在の状態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 このビューで保持される最大行数は、詳細については、システム ビューの最大値」セクションを参照してください、[最小値と最大値 (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)トピック。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
