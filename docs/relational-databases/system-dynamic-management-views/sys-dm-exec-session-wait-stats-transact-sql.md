---
title: dm_exec_session_wait_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d668fbabc20ef6e7acf8b38064378f74a3b15c6
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833776"
---
# <a name="sysdm_exec_session_wait_stats-transact-sql"></a>dm_exec_session_wait_stats (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  各セッションで実行されたスレッドによって検出されたすべての待機に関する情報を返します。 このビューを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セッション、および特定のクエリとバッチに関するパフォーマンスの問題を診断できます。  このビューでは、 [transact-sql&#41;&#40;dm_os_wait_stats](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)に対して集計されたものと同じ情報が返されますが、 **session_id**番号も表示されます。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降)。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|セッションの id。|  
|wait_type|**nvarchar(60)**|待機の種類の名前。 詳細については、「[sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)」を参照してください。|  
|waiting_tasks_count|**bigint**|この待機の種類における待機の数。 このカウンターは、待機が開始するたび増加します。|  
|wait_time_ms|**bigint**|この待機の種類における総待機時間 (ミリ秒単位)。 この時間には signal_wait_time_ms が含まれます。|  
|max_wait_time_ms|**bigint**|この待機の種類における最大待機時間。|  
|signal_wait_time_ms|**bigint**|待機スレッドがシグナルを受け取ってから実行を開始するまでの時間。|  
  
## <a name="remarks"></a>解説  
 この DMV は、セッションが開かれたとき、またはセッションがリセットされたとき (接続プールがある場合) に、セッションの情報をリセットします。  
  
 待機の種類の詳細については、「 [sys. dm_os_wait_stats &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 ユーザーがサーバーに対する**VIEW SERVER STATE**権限を持っている場合、ユーザーにはのインスタンスで実行中のすべてのセッションが表示されます。それ以外の場合、ユーザーには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 現在のセッションのみが表示されます。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
