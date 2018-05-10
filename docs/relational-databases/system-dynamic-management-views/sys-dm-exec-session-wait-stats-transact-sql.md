---
title: sys.dm_exec_session_wait_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_session_wait_stats
- sys.dm_exec_session_wait_stats_tsql
- dm_exec_session_wait_stats
- dm_exec_session_wait_stats_tsql
helpviewer_keywords:
- sys.dm_exec_session_wait_stats
ms.assetid: df84842a-71eb-4fda-b448-5953cf9985dc
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d289b0aab18dc20634e7af48a6c69f6ef48a4870
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexecsessionwaitstats-transact-sql"></a>sys.dm_exec_session_wait_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  セッションごとに実行されたスレッドにより検出されたすべての待機に関する情報を返します。 このビューは、パフォーマンスの問題を診断を使用することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セッションと、特定のクエリとバッチです。  このビューは、セッションの集計された同じ情報を返す[sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)が、提供、 **session_id**番号もします。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]まで)。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|セッションの id です。|  
|wait_type|**nvarchar(60)**|待機の種類の名前。 詳細については、「[sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)」を参照してください。|  
|waiting_tasks_count|**bigint**|この待機の種類における待機の数。 このカウンターは、待機が開始するたび増加します。|  
|wait_time_ms|**bigint**|この待機の種類 (ミリ秒単位) の合計待機時間。 この時間には signal_wait_time_ms が含まれます。|  
|max_wait_time_ms|**bigint**|この待機の種類における最大待機時間。|  
|signal_wait_time_ms|**bigint**|待機スレッドがシグナルを受け取ってから実行を開始するまでの時間。|  
  
## <a name="remarks"></a>解説  
 この DMV は、セッションが開かれると、または、セッションがリセットされたときにセッションの情報をリセット (場合接続プール)、  
  
 待機の種類については、次を参照してください。 [sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)です。  
  
## <a name="permissions"></a>権限  
 場合、ユーザーは**VIEW SERVER STATE**サーバーに対する権限をユーザーに表示されるセッションの実行中のすべてのインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 それ以外の場合、ユーザーが現在のセッションのみを表示します。  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
 
