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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62704323"
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Windows パフォーマンス カウンター内のノードに関する情報が含まれます[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|カウンターを含むノードの ID。<br /><br /> pdw_node_id と counter_name は、このビューのキーを形成します。|Node_id を参照してください。 [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)します。|  
|counter_name|**nvarchar (255)**|Windows パフォーマンス カウンターの名前。||  
|counter_category|**nvarchar (255)**|Windows パフォーマンス カウンター カテゴリの名前です。||  
|instance_name|**nvarchar (255)**|カウンターの特定のインスタンスの名前です。||  
|counter_value|**Decimal(38,10)**|カウンターの現在の値。||  
|last_update_time|**Datetime2(3)**|値が更新された最後の時刻のタイムスタンプ。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
