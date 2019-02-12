---
title: sys.dm_pdw_os_performance_counters (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 820027ee5bf893d7df81c51f90b431daa7c0af07
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56027343"
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  内のノードで Windows パフォーマンス カウンターに関する情報を格納 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|カウンターが含まれているノードの ID。<br /><br /> pdw_node_id と counter_name は、このビューのキーを形成します。|Node_id を参照してください。 [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)します。|  
|counter_name|**nvarchar (255)**|Windows のパフォーマンス カウンターの名前です。||  
|counter_category|**nvarchar (255)**|Windows パフォーマンス カウンターのカテゴリの名前です。||  
|instance_name|**nvarchar (255)**|カウンターの特定インスタンスの名前。||  
|counter_value|**Decimal(38,10)**|カウンターの現在の値。||  
|last_update_time|**Datetime2(3)**|最後に、値の更新日時のタイムスタンプです。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
