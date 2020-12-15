---
description: sys.dm_pdw_wait_stats (Transact-sql)
title: sys.dm_pdw_wait_stats (Transact-sql) |Microsoft Docs
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
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest'
ms.openlocfilehash: 417b5f5d88d5a150653e6910eabb8f7692657b2c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461573"
---
# <a name="sysdm_pdw_wait_stats-transact-sql"></a>sys.dm_pdw_wait_stats (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]異なるノードで実行されているインスタンスに関連する OS の状態に関連する情報を保持します。 待機の種類とその説明の一覧については、「 [sys.dm_os_wait_stats](https://msdn.microsoft.com/library/ms179984\(v=sql.120\).aspx)」を参照してください。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|**pdw_node_id**|**int**|このエントリが参照するノードの ID。||  
|**wait_name**|**nvarchar (255)**|待機の種類の名前。||  
|**max_wait_time**|**bigint**|この待機の種類の最大待機時間。||  
|**request_count**|**bigint**|この待機の種類が未解決である待機の数。||  
|**signal_time**|**bigint**|待機スレッドがシグナルを受け取ってから実行を開始するまでの時間。||  
|**completed_count**|**bigint**|前回のサーバーの再起動以降に完了したこの型の待機の合計数。||  
|**wait_time**|**bigint**|Millisecons でのこの待機の種類の合計待機時間。 Signal_time を含みます。||  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics と並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_waits &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
  
