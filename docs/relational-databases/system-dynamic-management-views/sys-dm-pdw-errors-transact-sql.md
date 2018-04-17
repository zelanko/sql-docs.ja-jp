---
title: sys.dm_pdw_errors (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 944eac31-5691-432b-b9f5-f1e11c05191f
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1252b0774293048a3eecc16882bef45b38cb7c66
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwerrors-transact-sql"></a>sys.dm_pdw_errors (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  要求またはクエリの実行中に発生したすべてのエラーに関する情報を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|このビューのキーです。<br /><br /> エラーに関連付けられている一意の数値 id です。|システム内のすべてのクエリ エラーの間で一意です。|  
|source|**nvarchar(64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|型|**nvarchar (4000)**|発生したエラーの種類です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|エラーが発生した時刻。|小さいまたは現在の時刻を等しくします。|  
|pwd_node_id|**int**|特定のノードが存在する場合は、関連の識別子です。 ノード id の詳細については、次を参照してください。 [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)です。||  
|session_id|**nvarchar(32)**|存在する場合は、関連のセッションの識別子です。 セッション id の詳細については、次を参照してください。 [sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)です。||  
|request_id|**nvarchar(32)**|存在する場合は、関連の要求の識別子です。 要求 id の詳細については、次を参照してください。 [sys.dm_pdw_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)です。||  
|spid|**int**|存在する場合は、関連の SQL Server セッションの spid。||  
|thread_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|詳細情報|**nvarchar (4000)**|完全なエラーの説明テキストを保持します。||  
  
 このビューで保持される最大行数のについてを参照してくださいシステム ビューの最大値、[最小値と最大値 (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9)トピックです。  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
