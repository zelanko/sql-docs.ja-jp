---
title: sys.dm_pdw_waits (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a19e82707797c50f4180f7f5ef6090a9f52f6419
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716731"
---
# <a name="sysdmpdwwaits-transact-sql"></a>sys.dm_pdw_waits (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  すべてに関する情報は、要求の実行中に発生した状態を待機するか、転送キューでは、上のロックを含めて、クエリの待機を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|待機状態に関連付けられている一意の数値 id です。<br /><br /> このビューのキーです。|システム内のすべての待機時間の間で一意です。|  
|session_id|**nvarchar(32)**|待機状態が発生したセッションの ID です。|Session_id を参照してください。 [sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)します。|  
|type|**nvarchar (255)**|このエントリが表す待機の種類。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar (255)**|待機によって影響を受けるオブジェクトの型。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386)**|名前または待機の影響を受けたを指定したオブジェクトの GUID。||  
|request_id|**nvarchar(32)**|待機状態が発生した要求の ID。|Request_id 内を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)します。|  
|request_time|**datetime**|時間が待機状態が要求されました。||  
|acquire_time|**datetime**|これで、ロックまたはリソースが取得された時刻です。||  
|state|**nvarchar (50)**|待機状態の状態です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|待機中の項目の優先度。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
