---
title: dm_pdw_errors (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 944eac31-5691-432b-b9f5-f1e11c05191f
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0ce09955508fa3743be9d8ef600e05f0e36c4467
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86197100"
---
# <a name="sysdm_pdw_errors-transact-sql"></a>dm_pdw_errors (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  要求またはクエリの実行中に発生したすべてのエラーに関する情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar (36)**|このビューのキー。<br /><br /> エラーに関連付けられている一意の数値 id。|システム内のすべてのクエリエラー間で一意です。|  
|ソース|**nvarchar (64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|型|**nvarchar (4000)**|発生したエラーの種類です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|エラーが発生した時刻。|小または現在の時刻と等しい。|  
|pwd_node_id|**int**|関連する特定のノードの識別子 (存在する場合)。 ノード id の詳細については、「 [sys. dm_pdw_nodes &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)」を参照してください。||  
|session_id|**nvarchar(32)**|関連するセッションの識別子 (存在する場合)。 セッション id の詳細については、「 [sys. dm_pdw_exec_sessions &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)」を参照してください。||  
|request_id|**nvarchar(32)**|含まれている場合は、関連する要求の識別子。 要求 id の詳細については、「 [sys. dm_pdw_exec_requests &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)」を参照してください。||  
|調べる|**int**|関連する SQL Server セッションの spid。||  
|thread_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|details|**nvarchar (4000)**|完全なエラーテキストの説明を保持します。||  
  
 このビューで保持される最大行数の詳細については、「[容量制限](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)」トピックの「メタデータ」セクションを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
