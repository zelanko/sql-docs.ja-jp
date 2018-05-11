---
title: sys.dm_db_task_space_usage (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_task_space_usage_TSQL
- sys.dm_db_task_space_usage_TSQL
- dm_db_task_space_usage
- sys.dm_db_task_space_usage
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_task_space_usage dynamic management view
ms.assetid: fb0c87e5-43b9-466a-a8df-11b3851dc6d0
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0ea57f1f83b280087f239ad2672c60bed11171d7
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmdbtaskspaceusage-transact-sql"></a>sys.dm_db_task_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースに対するタスクごとに、ページの割り当てと割り当て解除の処理に関する情報を返します。  
  
> [!NOTE]  
>  このビューはのみに適用できる、 [tempdb データベース](../../relational-databases/databases/tempdb-database.md)です。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_db_task_space_usage**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|セッション ID。|  
|**request_id**|**int**|セッション内の要求 ID。<br /><br /> 要求はバッチとも呼ばれ、1 つ以上のクエリを含めることができます。 複数の要求を同時にアクティブなセッションがあります。 並列実行プランが使用されている場合、要求内の各クエリでは複数のスレッド (タスク) を開始できます。|  
|**exec_context_id**|**int**|タスクの実行コンテキスト ID。 詳細については、次を参照してください。 [sys.dm_os_tasks と組み合わせます&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)です。|  
|**database_id**|**smallint**|データベース ID。|  
|**user_objects_alloc_page_count**|**bigint**|タスクで、ユーザー オブジェクト用に予約された、または割り当てられたページの数。|  
|**user_objects_dealloc_page_count**|**bigint**|タスクで、ユーザー オブジェクトへの割り当てが解除され、予約されなくなったページの数。|  
|**internal_objects_alloc_page_count**|**bigint**|タスクで、内部オブジェクト用に予約された、または割り当てられたページの数。|  
|**internal_objects_dealloc_page_count**|**bigint**|タスクで、内部オブジェクトへの割り当てが解除され、予約されなくなったページの数。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="remarks"></a>解説  
 このビューでレポートされるページの数に、IAM ページは含まれません。  
  
 ページ カウンターは要求の開始時にゼロ (0) に初期化されます。 これらの値は要求が完了したときにセッション レベルで集計されます。 詳細については、次を参照してください。 [sys.dm_db_session_space_usage & #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)。  
  
 指定したタスクで割り当てられるページ数と割り当て解除されるページ数は、作業テーブル キャッシュ、一時テーブル キャッシュ、および延期された削除操作によって影響を受けます。  
  
## <a name="user-objects"></a>ユーザー オブジェクト  
 次のオブジェクトは、ユーザー オブジェクト ページ カウンターに含まれます。  
  
-   ユーザー定義テーブルとインデックス  
  
-   システム テーブルとインデックス  
  
-   グローバル一時テーブルとインデックス  
  
-   ローカル一時テーブルとインデックス  
  
-   テーブル変数  
  
-   テーブル値関数で返されるテーブル  
  
## <a name="internal-objects"></a>内部オブジェクト  
 内部オブジェクトにのみ含まれる**tempdb**です。 次のオブジェクトは、内部オブジェクト ページ カウンターに含まれます。  
  
-   カーソルまたはスプール操作と一時的なラージ オブジェクト (LOB) の記憶域用の作業テーブル  
  
-   ハッシュ結合などの操作用の作業ファイル  
  
-   並べ替え実行結果  
  
## <a name="physical-joins"></a>物理結合  
 ![Sys.dm_db_session_task_usage の物理結合](../../relational-databases/system-dynamic-management-views/media/join-dm-db-task-space-usage-1.gif "sys.dm_db_session_task_usage の物理の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|dm_db_task_space_usage.request_id|dm_exec_requests.request_id|一対一|  
|dm_db_task_space_usage.session_id|dm_exec_requests.session_id|一対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks と組み合わせます&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  


