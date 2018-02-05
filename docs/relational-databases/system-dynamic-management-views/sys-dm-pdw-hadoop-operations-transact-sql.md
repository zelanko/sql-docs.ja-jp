---
title: sys.dm_pdw_hadoop_operations (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d2337d4-e2c7-48de-9c26-cdc7e6eb5d55
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ccb851fc349e31206ca5e76f050a1413c8c7405
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwhadoopoperations-transact-sql"></a>sys.dm_pdw_hadoop_operations (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  各 map-reduce ジョブ実行の一部として Hadoop に適用されている行が含まれています、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]外部の Hadoop テーブルに対するクエリ。 各 map-reduce ジョブでは、クエリで述語の 1 つを表します。 これは、Hadoop の外部テーブルに対するクエリの述語のプッシュ ダウンが有効になっているときにのみ使用されます。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|この外部の Hadoop 操作の ID。|ID と同じ[sys.dm_pdw_exec_requests &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)。|  
|step_index|**int**|この Hadoop 操作に関係するクエリの手順のインデックスです。|Step_index と同じ[sys.dm_pdw_request_steps &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)。|  
|operation_type|**nvarchar (255)**|外部の操作の種類について説明します。|' 外部 Hadoop Operation'|  
|operation_name|**nvarchar (4000)**|Map-reduce のジョブのジョブ ID。 これは、後に Hadoop によって返される[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ジョブを送信します。||  
|map_progress|**float**|これまで、マップのジョブで消費された入力のデータの割合。|浮動小数点数の間、および 0 ～ 100 です。|  
|reduce_progress|**int**|Reduce ジョブが完了したことの割合。|浮動小数点数の間、および 0 ～ 100 です。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  
