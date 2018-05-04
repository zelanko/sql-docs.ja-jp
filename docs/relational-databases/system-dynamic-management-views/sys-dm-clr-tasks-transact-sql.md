---
title: sys.dm_clr_tasks (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_tasks
- sys.dm_clr_tasks_TSQL
- dm_clr_tasks
- dm_clr_tasks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_tasks dynamic management view
ms.assetid: 462b9061-09fa-4858-9707-03d6cc19c769
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5ae63389310a8100c75e008e6d4e508d55800424
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmclrtasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在実行中のすべての共通言語ランタイム (CLR) タスクについて、1 行のデータを返します。 A [!INCLUDE[tsql](../../includes/tsql-md.md)] CLR ルーチンへの参照が含まれたバッチは、そのバッチのタスクは、すべてのマネージ コードの実行を作成します。 バッチ内に、マネージ コードの実行を必要とするステートメントが複数ある場合は、それらのステートメントで同じ CLR タスクが使用されます。 オブジェクトと、マネージ コードの実行だけでなく、インスタンスの間の遷移に関連する状態を維持するため、CLR タスクは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と共通言語ランタイム。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|CLR タスクのアドレス。|  
|**sos_task_address**|**varbinary(8)**|基になるアドレス[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ タスクです。|  
|**appdomain_address**|**varbinary(8)**|このタスクが実行されているアプリケーション ドメインのアドレス。|  
|**状態**|**nvarchar(128)**|タスクの現在の状態。|  
|**abort_state**|**nvarchar(128)**|タスクが取り消された場合の、現在の中止の状態。中止には複数の状態があります。|  
|**type**|**nvarchar(128)**|タスクの種類。|  
|**affinity_count**|**int**|タスクの関係。|  
|**forced_yield_count**|**int**|タスクが強制的に解放された回数。|  
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [共通言語ランタイム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

