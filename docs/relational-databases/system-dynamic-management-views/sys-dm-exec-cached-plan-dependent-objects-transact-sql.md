---
title: sys.dm_exec_cached_plan_dependent_objects (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
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
- sys.dm_exec_cached_plan_dependent_objects
- dm_exec_cached_plan_dependent_objects_TSQL
- sys.dm_exec_cached_plan_dependent_objects_TSQL
- dm_exec_cached_plan_dependent_objects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cached_plan_dependent_objects dynamic management function
ms.assetid: 9b6cf5f7-b267-44fb-aac8-f49c9aa10cc1
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cfa8eb9681552557fbed1a251ef9b8fad7fec0c7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmexeccachedplandependentobjects-transact-sql"></a>sys.dm_exec_cached_plan_dependent_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  各 [!INCLUDE[tsql](../../includes/tsql-md.md)] 実行プラン、共通言語ランタイム (CLR) 実行プラン、およびプランに関連付けられたカーソルの行を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dm_exec_cached_plan_dependent_objects(plan_handle)  
```  
  
## <a name="arguments"></a>引数  
 *plan_handle*  
 バッチに関するクエリ実行プランの一意識別子を指定します。このバッチは既に実行されていて、そのプランはプラン キャッシュに格納されています。 *plan_handle*は**varbinary (64)**です。 *Plan_handle*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**usecounts**|**int**|実行コンテキストまたはカーソルが使用された回数。<br /><br /> 列値が許容されません。|  
|**memory_object_address**|**varbinary(8)**|実行コンテキストまたはカーソルのメモリ アドレス。<br /><br /> 列値が許容されません。|  
|**cacheobjtype**|**nvarchar (50)**|プラン キャッシュのオブジェクトの型。 列値が許容されません。 次のいずれかが返されます。<br /><br /> 実行プラン<br /><br /> CLR コンパイル済みの関数<br /><br /> CLR コンパイル済みのプロシージャ<br /><br /> カーソル|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="physical-joins"></a>物理結合  
 ![リレーションシップ ダイアグラム](../../relational-databases/system-dynamic-management-views/media/dm-dependent-objects.gif "リレーションシップ ダイアグラム")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|基準|リレーションシップ|  
|----------|--------|--------|------------------|  
|**dm_exec_cached_plan_dependent_objects**|**dm_os_memory_objects**|**memory_object_address**|一対一|  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.syscacheobjects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)  
  
  
