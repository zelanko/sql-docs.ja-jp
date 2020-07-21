---
title: dm_pdw_os_performance_counters (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 3cdc9b13203527d3f5a3fe71d0a6b32baf0446ce
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627303"
---
# <a name="sysdm_pdw_os_performance_counters-transact-sql"></a>dm_pdw_os_performance_counters (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  のノードの Windows パフォーマンスカウンターに関する情報が含まれてい [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ます。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|カウンターを含むノードの ID。<br /><br /> このビューのキーは pdw_node_id と counter_name によって形成されます。|『 [Transact-sql&#41;&#40;dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|counter_name|**nvarchar(255)**|Windows パフォーマンスカウンターの名前。||  
|counter_category|**nvarchar(255)**|Windows パフォーマンスカウンターカテゴリの名前。||  
|instance_name|**nvarchar(255)**|カウンターの特定のインスタンスの名前。||  
|counter_value|**10進数 (38, 10)**|カウンターの現在の値。||  
|last_update_time|**Datetime2 (3)**|値が最後に更新されたときのタイムスタンプ。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
