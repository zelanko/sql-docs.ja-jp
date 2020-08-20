---
description: dm_pdw_query_stats_xe (Transact-sql)
title: dm_pdw_query_stats_xe (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1c141fef15f052b87db4c09d735c0217d45cb10a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474697"
---
# <a name="sysdm_pdw_query_stats_xe-transact-sql"></a>dm_pdw_query_stats_xe (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  この DMV は非推奨とされており、今後のリリースでは削除される予定です。 このリリースでは、0行が返されます。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|event|**nvarchar(60)**|このビューのキー。||  
|event_id|**nvarchar (36)**|||  
|create_time|**datetime**|||  
|session_id|**int**|セッションの id。|『 [Transact-sql&#41;&#40;dm_pdw_exec_sessions ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)の session_id を参照してください。|  
|cpu|**int**|||  
|読み取り|**int**|イベントの開始以降の論理読み取りの数。||  
|書き込み|**int**|イベントの開始以降の論理書き込みの数。||  
|sql_text|**nvarchar (4000)**|||  
|client_app_name|**nvarchar (255)**|||  
|tsql_stack|**nvarchar (255)**|||  
|pdw_node_id|**int**|この Xevent インスタンスが実行されているノード。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
