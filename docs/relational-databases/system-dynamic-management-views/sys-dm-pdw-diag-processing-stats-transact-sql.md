---
title: dm_pdw_diag_processing_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a765e591e3b55bb4be2e2b6d7431873702910f6f
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394357"
---
# <a name="sysdm_pdw_diag_processing_stats-transact-sql"></a>dm_pdw_diag_processing_stats (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  管理者によって定義された診断セッションに組み込むことができるすべての内部診断イベントに関連する情報を表示します。 このビューにクエリを実行し、他のすべての Dmv の作成を推進する診断およびイベントサブシステムの背後にある統計を確認します。 各ノード上の各プロセスに対して、キューのグループがあります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|このログの基になっているアプライアンスノード。|  
|**process_id**|**int**|この統計情報の送信を実行しているプロセスの識別子。|  
|**target_name**|**nvarchar (255)**|キューの名前。|  
|**queue_size**|**int**|プロセスキュー内の項目の数。 通常、キューのサイズは0です。 正の数値は、システムがストレスを受けていて、イベントのバックログを構築していることを示します。 他の列の正の数は、その特定のキューおよび関連する Dmv のシステムが破損していることを意味します。|  
|**lost_events_count**|**bigint**|失われたイベントの数。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
