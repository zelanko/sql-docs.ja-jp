---
title: sys.dm_pdw_wait_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cfb8d905-c34f-44de-9574-dde81e170916
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 52a9b00f7c2bda0b0bd488e94d1674019b9fc5cb
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36806687"
---
# <a name="sysdmpdwwaitstats-transact-sql"></a>sys.dm_pdw_wait_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  関連する情報を保持、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OS の状態は、さまざまなノードで実行されているインスタンスに関連します。 待機の種類とその説明の一覧は、次を参照してください。 [sys.dm_os_wait_stats](http://msdn.microsoft.com/en-us/library/ms179984\(v=sql.120\).aspx)します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|このエントリが指すノードの ID。||  
|**wait_name**|**nvarchar (255)**|待機の種類の名前。||  
|**max_wait_time**|**bigint**|この待機の種類の最大待機時間。||  
|**request_count**|**bigint**|この待機の数は、未解決の型を待機します。||  
|**signal_time**|**bigint**|待機スレッドがシグナルを受け取ってから実行を開始するまでの時間。||  
|**completed_count**|**bigint**|最後のサーバーから完了したこの型の待機数の合計を再起動します。||  
|**wait_time**|**bigint**|この待機の種類で millisecons 合計待機時間。 Signal_time も含まれます。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_waits &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
