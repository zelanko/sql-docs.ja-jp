---
title: "sys.dm_os_waiting_tasks (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_waiting_tasks
- sys.dm_os_waiting_tasks_TSQL
- dm_os_waiting_tasks_TSQL
- sys.dm_os_waiting_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_waiting_tasks dynamic management view
ms.assetid: ca5e6844-368c-42e2-b187-6e5f5afc8df3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5b3a3122f9f0908e063685941f58bb03281659e0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmoswaitingtasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  リソースを待機しているタスクの待機キューに関する情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_waiting_tasks**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|待機中のタスクのアドレス。|  
|**session_id**|**smallint**|タスクに関連付けられているセッションの ID。|  
|**exec_context_id**|**int**|タスクに関連付けられている実行コンテキストの ID。|  
|**wait_duration_ms**|**bigint**|この待機の種類における総待機時間 (ミリ秒単位)。 この時間には**signal_wait_time**です。|  
|**wait_type**|**nvarchar(60)**|待機の種類の名前。|  
|**resource_address**|**varbinary(8)**|タスクが待機しているリソースのアドレス。|  
|**blocking_task_address**|**varbinary(8)**|リソースを現在保持しているタスク。|  
|**blocking_session_id**|**smallint**|要求をブロックしているセッションの ID。 この列が NULL の場合は、要求がブロックされていないか、ブロックしているセッションのセッション情報が使用または識別できません。<br /><br /> -2 = ブロックしているリソースは、孤立した分散トランザクションが所有しています。<br /><br /> -3 = ブロックしているリソースは、遅延復旧トランザクションが所有しています。<br /><br /> -4 = 内部ラッチの状態遷移のため、ブロックしているラッチの所有者のセッション ID を特定できませんでした。|  
|**blocking_exec_context_id**|**int**|タスクをブロックしている実行コンテキストの ID。|  
|**resource_description**|**nvarchar(3072)**|使用されているリソースの説明。 詳細については、以下の説明を参照してください。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="resourcedescription-column"></a>resource_description 列  
 Resource_description 列は、値は、次のとおりです。  
  
 **スレッド プール リソース所有者:**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **並列クエリ リソース所有者:**  
  
-   exchangeEvent id = {ポート |パイプ}\<16 進 アドレス > WaitType =\<exchange の待機の種類 > nodeId =\<exchange ノード id >  
  
 **Exchange-wait-type:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **ロック リソース所有者:**  
  
-   \<type-specific-description> id=lock\<lock-hex-address> mode=\<mode> associatedObjectId=\<associated-obj-id>  
  
     **\<型の説明固有 & > を指定できます。**  
  
    -   データベースの場合: databaselock subresource =\<databaselock subresource > dbid =\<db id >  
  
    -   ファイルの場合: filelock fileid =\<ファイル id > subresource =\<filelock subresource > dbid =\<db id >  
  
    -   オブジェクト: objectlock lockPartition =\<ロックのパーティションの id > objid =\<obj id > subresource =\<objectlock subresource > dbid =\<db id >  
  
    -   ページ: pagelock fileid =\<ファイル id > pageid =\<ページ id > dbid =\<db id > subresource =\<pagelock subresource >  
  
    -   キー: keylock hobtid =\<hobt id > dbid =\<db id >  
  
    -   EXTENT: extentlock fileid =\<ファイル id > pageid =\<ページ id > dbid =\<db id >  
  
    -   RID の場合: ridlock fileid =\<ファイル id > pageid =\<ページ id > dbid =\<db id >  
  
    -   アプリケーション: applicationlock ハッシュ =\<ハッシュ > databasePrincipalId =\<ロール id > dbid =\<db id >  
  
    -   メタデータ: metadatalock subresource =\<メタデータ subresource & > classid =\<metadatalock 説明 > dbid =\<db id >  
  
    -   HOBT の場合: hobtlock hobtid =\<hobt id > subresource =\<hobt subresource > dbid =\<db id >  
  
    -   Allocation_unit の場合: allocunitlock hobtid =\<hobt id > subresource =\<アロケーション-単位-subresource > dbid =\<db id >  
  
     **\<モード > を指定できます。**  
  
     Sch-S、Sch-M、S、U、X、IS、IU、IX、SIU、SIX、UIX、BU、RangeS-S、RangeS-U、RangeI-N、RangeI-S、RangeI-U、RangeI-X、RangeX-、RangeX-U、RangeX-X  
  
 **外部リソース所有者:**  
  
-   External ExternalResource=\<wait-type>  
  
 **汎用リソース所有者:**  
  
-   TransactionMutex TransactionInfo ワークスペース =\<ワークスペース id >  
  
-   Mutex  
  
-   CLRTaskJoin  
  
-   CLRMonitorEvent  
  
-   CLRRWLockEvent  
  
-   resourceWait  
  
 **ラッチ リソース所有者:**  
  
-   \<db-id>:\<file-id>:\<page-in-file>  
  
-   \<GUID>  
  
-   \<latch-class> (\<latch-address>)  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。  
 
## <a name="example"></a>例
この例では、ブロックされているセッションを識別します。  実行、[!INCLUDE[tsql](../../includes/tsql-md.md)]内のクエリを[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。
```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


