---
title: dm_clr_tasks (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 00b37550b9a5d121d395f94d4810a4a093c3125d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68266001"
---
# <a name="sysdm_clr_tasks-transact-sql"></a>sys.dm_clr_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在実行中のすべての共通言語ランタイム (CLR) タスクの行を返します。 CLR [!INCLUDE[tsql](../../includes/tsql-md.md)]ルーチンへの参照を含むバッチは、そのバッチ内のすべてのマネージコードを実行するための個別のタスクを作成します。 バッチ内に、マネージド コードの実行を必要とするステートメントが複数ある場合は、それらのステートメントで同じ CLR タスクが使用されます。 CLR タスクは、マネージコードの実行に関連するオブジェクトと状態を維持すると共に、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスと共通言語ランタイムの間の遷移を保持します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary (8)**|CLR タスクのアドレス。|  
|**sos_task_address**|**varbinary (8)**|基になる[!INCLUDE[tsql](../../includes/tsql-md.md)] batch タスクのアドレス。|  
|**appdomain_address**|**varbinary (8)**|このタスクが実行されているアプリケーションドメインのアドレス。|  
|**state**|**nvarchar(128)**|タスクの現在の状態。|  
|**abort_state**|**nvarchar(128)**|中止の現在の状態 (タスクが取り消された場合)。タスクの中止中に複数の状態が関係しています。|  
|**type**|**nvarchar(128)**|タスクの種類。|  
|**affinity_count**|**int**|タスクの関係。|  
|**forced_yield_count**|**int**|タスクが強制的に生成された回数。|  
  
## <a name="permissions"></a>アクセス許可  

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の動的管理ビューおよび関数](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Transact-sql&#41;&#40;共通言語ランタイム関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  

