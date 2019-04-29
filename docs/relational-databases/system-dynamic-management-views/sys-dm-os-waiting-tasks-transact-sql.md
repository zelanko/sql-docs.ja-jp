---
title: sys.dm_os_waiting_tasks (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 10a17dba594359ca83fbc3b15e148fb72356e162
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998005"
---
# <a name="sysdmoswaitingtasks-transact-sql"></a>sys.dm_os_waiting_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  いくつかのリソースで待機しているタスクの待機キューに関する情報を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_waiting_tasks**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**waiting_task_address**|**varbinary(8)**|待機中のタスクのアドレスです。|  
|**session_id**|**smallint**|タスクに関連付けられているセッションの ID。|  
|**exec_context_id**|**int**|タスクに関連付けられている実行コンテキストの ID。|  
|**wait_duration_ms**|**bigint**|合計待機時間 (ミリ秒単位)、この待機の種類。 この時間には**signal_wait_time**します。|  
|**wait_type**|**nvarchar(60)**|待機の種類の名前。|  
|**resource_address**|**varbinary(8)**|タスクが待機しているリソースのアドレス。|  
|**blocking_task_address**|**varbinary(8)**|このリソースが現在保持しているタスク|  
|**blocking_session_id**|**smallint**|要求をブロックしているセッションの ID。 この列が NULL の場合は、要求がブロックされていないか、ブロックしているセッションのセッション情報が使用または識別できません。<br /><br /> -2 = ブロックしているリソースは、孤立した分散トランザクションが所有しています。<br /><br /> -3 ブロック = 遅延復旧トランザクションが所有するリソースです。<br /><br /> -4 セッション ID を = ブロックしているラッチの所有者が指定されていません内部ラッチの状態遷移が発生したためです。|  
|**blocking_exec_context_id**|**int**|ブロックしているタスクの実行コンテキストの ID です。|  
|**resource_description**|**nvarchar(3072)**|消費されるリソースの説明です。 詳細については、以下の説明を参照してください。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="resourcedescription-column"></a>resource_description 列  
 Resource_description 列は、値は、次のとおりです。  
  
 **スレッド プール リソース所有者:**  
  
-   threadpool id=scheduler\<hex-address>  
  
 **並列クエリ リソース所有者:**  
  
-   exchangeEvent id={Port|Pipe}\<hex-address> WaitType=\<exchange-wait-type> nodeId=\<exchange-node-id>  
  
 **Exchange-wait-type:**  
  
-   e_waitNone  
  
-   e_waitPipeNewRow  
  
-   e_waitPipeGetRow  
  
-   e_waitSynchronizeConsumerOpen  
  
-   e_waitPortOpen  
  
-   e_waitPortClose  
  
-   e_waitRange  
  
 **ロック リソース所有者:**  
  
-   \<型固有の説明 > id = ロック\<ロックから 16 進アドレス > モード =\<モード > associatedObjectId =\<関連付けられているオブジェクト id >  
  
     **\<型固有の説明 > することができます。**  
  
    -   データベース: databaselock subresource =\<databaselock subresource > dbid =\<db id >  
  
    -   ファイル: filelock ファイルの id =\<ファイル id > subresource =\<filelock subresource > dbid =\<db id >  
  
    -   オブジェクト: objectlock lockPartition =\<ロック パーティション id > objid =\<オブジェクト id > subresource =\<objectlock subresource > dbid =\<db id >  
  
    -   Pagelock ファイルのページの場合 =\<ファイル id > pageid =\<ページ id > dbid =\<db id > subresource =\<pagelock subresource >  
  
    -   キー: キーロック hobtid =\<hobt id > dbid =\<db id >  
  
    -   範囲: extentlock ファイルの id =\<ファイル id > pageid =\<ページ id > dbid =\<db id >  
  
    -   RID: の ridlock ファイルの id =\<ファイル id > pageid =\<ページ id > dbid =\<db id >  
  
    -   Applicationlock ハッシュのアプリケーション: =\<ハッシュ > databasePrincipalId =\<ロール id > dbid =\<db id >  
  
    -   メタデータ: metadatalock subresource =\<メタデータ subresource > クラス id =\<metadatalock 説明 > dbid =\<db id >  
  
    -   HOBT: の hobtlock hobtid =\<hobt id > subresource =\<hobt subresource > dbid =\<db id >  
  
    -   Allocation_unit の場合: allocunitlock hobtid =\<hobt id > subresource =\<アロケーション-単位-subresource > dbid =\<db id >  
  
     **\<モード > することができます。**  
  
     SCH-S、Sch M、S、U、X、IS、IU、IX、SIU、6、UIX、BU、範囲の範囲 U、RangeI N、RangeI S、RangeI、U、X、RangeX、RangeI、RangeX U、RangeX X  
  
 **外部リソースの所有者:**  
  
-   External ExternalResource=\<wait-type>  
  
 **汎用リソースの所有者:**  
  
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
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
 
## <a name="example"></a>例
この例では、ブロックされたセッションを識別します。  実行、[!INCLUDE[tsql](../../includes/tsql-md.md)]でクエリを[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。
```sql
SELECT * FROM sys.dm_os_waiting_tasks 
WHERE blocking_session_id IS NOT NULL; 
``` 
  
## <a name="see-also"></a>参照  
  [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


