---
title: dm_pdw_wait_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 2d5815783528b89716cc8bfb426ea7c1b274802e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088717"
---
# <a name="sysdm_pdw_wait_stats-transact-sql"></a>dm_pdw_wait_stats (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  異なるノードで実行さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れているインスタンスに関連する OS の状態に関連する情報を保持します。 待機の種類とその説明の一覧については、「 [dm_os_wait_stats](https://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx)」を参照してください。  
  
|列名|データ型|[説明]|Range|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|このエントリが参照するノードの ID。||  
|**wait_name**|**nvarchar(255)**|待機の種類の名前。||  
|**max_wait_time**|**bigint**|この待機の種類の最大待機時間。||  
|**request_count**|**bigint**|この待機の種類が未解決である待機の数。||  
|**signal_time**|**bigint**|待機スレッドがシグナルを受け取ってから実行を開始するまでの時間。||  
|**completed_count**|**bigint**|前回のサーバーの再起動以降に完了したこの型の待機の合計数。||  
|**wait_time**|**bigint**|Millisecons でのこの待機の種類の合計待機時間。 Signal_time を含みます。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [dm_pdw_waits &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
