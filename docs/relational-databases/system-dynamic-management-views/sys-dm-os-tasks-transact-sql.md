---
title: sys.dm_os_tasks と組み合わせます (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e71af56ba845cc2b011196fadce6d7c1a3684b15
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265647"
---
# <a name="sysdmostasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  インスタンスでアクティブになっているタスクごとに 1 行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_tasks**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|オブジェクトのメモリ アドレス。|  
|**task_state**|**nvarchar(60)**|タスクの状態。 これは、次のいずれかを指定できます。<br /><br /> 保留中。ワーカー スレッドを待機しています。<br /><br /> 実行可能。Runnable]、[がクォンタムの受信を待機しています。<br /><br /> 実行されています。スケジューラで現在実行中です。<br /><br /> 中断。ワーカーが、イベント待機しています。<br /><br /> 完成です：完了しました。<br /><br /> SPINLOOP:スピンロックでスタックします。|  
|**context_switches_count**|**int**|タスクによって完了されたスケジューラ コンテキスト スイッチの数。|  
|**pending_io_count**|**int**|タスクによって実行された物理 I/O の数。|  
|**pending_io_byte_count**|**bigint**|タスクによって実行された I/O の総バイト数。|  
|**pending_io_byte_average**|**int**|タスクによって実行された I/O の平均バイト数。|  
|**scheduler_id**|**int**|親スケジューラの ID。 タスクのスケジューラ情報に対するハンドルです。 詳細については、次を参照してください。 [sys.dm_os_schedulers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)します。|  
|**session_id**|**smallint**|タスクに関連付けられているセッションの ID。|  
|**exec_context_id**|**int**|タスクに関連付けられている実行コンテキスト ID。|  
|**request_id**|**int**|タスクの要求の ID。 詳細については、次を参照してください。 [sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)します。|  
|**worker_address**|**varbinary(8)**|タスクを実行しているワーカーのメモリ アドレス。<br /><br /> NULL = タスクがワーカーの実行待ちとなっているか、完了したばかりであることを表します。<br /><br /> 詳細については、次を参照してください。 [sys.dm_os_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)します。|  
|**host_address**|**varbinary(8)**|ホストのメモリ アドレス。<br /><br /> 0 = ホストがタスクの作成に使用されなかったことを表します。 このタスクの作成に使用されたホストを特定する場合に役立ちます。<br /><br /> 詳細については、次を参照してください。 [sys.dm_os_hosts &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md)します。|  
|**parent_task_address**|**varbinary(8)**|オブジェクトの親であるタスクのメモリ アドレス。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

## <a name="examples"></a>使用例  
  
### <a name="a-monitoring-parallel-requests"></a>A. 並列要求を監視する  
 並列で実行される要求の場合の同じ組み合わせに対して複数の行が表示されます (\<**session_id**>、 \< **request_id**>)。 検索する次のクエリを使用して、 [max degree of parallelism サーバー構成オプションを構成する](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)のすべてのアクティブな要求。  
  
> [!NOTE]  
>  A **request_id**セッション内で一意です。  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. セッション ID を Windows のスレッドに関連付ける  
 次のクエリを使用して、セッション ID を Windows スレッド ID に関連付けることができます。 これにより、Windows パフォーマンス モニターでスレッドのパフォーマンスを監視できます。 このクエリでは、休止しているセッションの情報は返されません。  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


