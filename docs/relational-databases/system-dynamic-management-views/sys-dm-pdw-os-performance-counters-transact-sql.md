---
description: sys.dm_pdw_os_performance_counters (Transact-sql)
title: sys.dm_pdw_os_performance_counters (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: markingmyname
ms.author: maghan
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 67a0bf0b52b0fc4d31400bf009476d76fdc1b1f5
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440767"
---
# <a name="sysdm_pdw_os_performance_counters-transact-sql"></a>sys.dm_pdw_os_performance_counters (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  のノードの Windows パフォーマンスカウンターに関する情報が含まれてい [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ます。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|カウンターを含むノードの ID。<br /><br /> このビューのキーは pdw_node_id と counter_name によって形成されます。|[Transact-sql&#41;&#40;sys.dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|counter_name|**nvarchar (255)**|Windows パフォーマンスカウンターの名前。||  
|counter_category|**nvarchar (255)**|Windows パフォーマンスカウンターカテゴリの名前。||  
|instance_name|**nvarchar (255)**|カウンターの特定のインスタンスの名前。||  
|counter_value|**10進数 (38, 10)**|カウンターの現在の値。||  
|last_update_time|**Datetime2 (3)**|値が最後に更新されたときのタイムスタンプ。||  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics と並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
