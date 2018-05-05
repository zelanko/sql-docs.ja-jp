---
title: sys.dm_pdw_os_performance_counters (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 0673a8f8-8bed-41eb-8959-a9e3e9e03a65
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8c1bf0b19bd8123feb0aee479d270a532ab1ee90
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmpdwosperformancecounters-transact-sql"></a>sys.dm_pdw_os_performance_counters (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Windows パフォーマンス カウンター内のノードに関する情報を含む[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|カウンターが含まれているノードの ID。<br /><br /> pdw_node_id と counter_name は、このビューのキーを形成します。|Node_id を参照してください[sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)です。|  
|counter_name|**nvarchar (255)**|Windows のパフォーマンス カウンターの名前です。||  
|counter_category|**nvarchar (255)**|Windows パフォーマンス カウンターのカテゴリの名前です。||  
|instance_name|**nvarchar (255)**|カウンターの特定インスタンスの名前。||  
|counter_value|**Decimal(38,10)**|カウンターの現在の値。||  
|last_update_time|**Datetime2(3)**|最後に、値の更新日時のタイムスタンプです。||  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
