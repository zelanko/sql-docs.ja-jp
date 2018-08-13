---
title: sys.dm_exec_query_memory_grants (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_query_memory_grants_TSQL
- sys.dm_exec_query_memory_grants
- sys.dm_exec_query_memory_grants_TSQL
- dm_exec_query_memory_grants
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_memory_grants dynamic management view
ms.assetid: 2c417747-2edd-4e0d-8a9c-e5f445985c1a
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 0c0d13ebbda9f8031987b5545715de96fc37c12a
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559592"
---
# <a name="sysdmexecquerymemorygrants-transact-sql"></a>sys.dm_exec_query_memory_grants (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  要求したメモリ許可を待機しているし、メモリ許可が与えられているすべてのクエリに関する情報を返します。 メモリ許可を必要としないクエリは、このビューでは表示されません。 たとえば、並べ替えし、ハッシュ結合の操作なしのクエリ中に、クエリ実行メモリ許可がある、 **ORDER BY**句には、メモリ許可がありません。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、動的管理ビューは、データベースの包含に影響を与えるまたはユーザーがアクセスを他のデータベースに関する情報が公開される情報を公開できません。 この情報が公開されないように、接続されたテナントに属していないデータを含む行はすべてフィルターで除外されます。さらに、列の値**scheduler_id**、 **wait_order**、 **pool_id**、 **group_id**フィルター処理され、列の値の設定NULL です。  
  
> [!NOTE]  
> これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_exec_query_memory_grants**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**session_id**|**smallint**|このクエリを実行中のセッションの ID (SPID)。|  
|**request_id**|**int**|要求の ID。 セッションのコンテキスト内で一意です。|  
|**scheduler_id**|**int**|このクエリのスケジュールを設定しているスケジューラの ID。|  
|**dop**|**smallint**|このクエリの並行処理の程度。|  
|**request_time**|**datetime**|このクエリがメモリ許可を要求した日付と時刻。|  
|**grant_time**|**datetime**|このクエリにメモリが許可された日付と時刻。 メモリがまだ許可されていない場合は NULL です。|  
|**requested_memory_kb**|**bigint**|メモリの要求量の合計 (KB 単位)。|  
|**granted_memory_kb**|**bigint**|実際に許可されたメモリの総量 (KB 単位)。 メモリがまだ許可されていない場合、NULL になることがあります。 一般的な状況では、この値は同じ**requested_memory_kb**します。 インデックス作成では、最初に許可されたメモリ量を超えて、追加のオンデマンド メモリが許可される場合があります。|  
|**required_memory_kb**|**bigint**|このクエリを実行するために必要な最小メモリ (KB 単位)。 **requested_memory_kb**は、この量よりも小さい場合。|  
|**used_memory_kb**|**bigint**|この時点で使用されている物理メモリ (KB 単位)。|  
|**max_used_memory_kb**|**bigint**|この時点までに使用された最大物理メモリ (KB 単位)。|  
|**query_cost**|**float**|推定クエリ コスト。|  
|**timeout_sec**|**int**|このクエリがメモリ許可要求をやめるまでのタイムアウト (秒単位)。|  
|**resource_semaphore_id**|**smallint**|このクエリが待機しているリソース セマフォの非一意の ID。<br /><br /> **注:** この ID は一意のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より前[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]します。 この変更は、クエリの実行のトラブルシューティングに影響する可能性があります。 詳細については、このトピックの後半の「解説」セクションを参照してください。|  
|**queue_id**|**smallint**|このクエリがメモリ許可を待機している待機キューの ID。 メモリが既に与えられている場合は NULL です。|  
|**wait_order**|**int**|指定した待機クエリの順番**queue_id**します。 他のクエリがメモリ許可を取得するか、タイムアウトになった場合、個々のクエリのこの値は変化する可能性があります。メモリが既に許可されている場合は NULL です。|  
|**is_next_candidate**|**bit**|次のメモリ許可の候補。<br /><br /> 1 = はい<br /><br /> 0 = いいえ<br /><br /> NULL = メモリが既に許可されている|  
|**wait_time_ms**|**bigint**|待機時間 (ミリ秒単位)。 メモリが既に与えられている場合は NULL です。|  
|**plan_handle**|**varbinary(64)**|このクエリ プランの識別子。 使用**sys.dm_exec_query_plan**を実際の XML プランを抽出します。|  
|**sql_handle**|**varbinary(64)**|このクエリの [!INCLUDE[tsql](../../includes/tsql-md.md)] テキストの識別子。 使用**sys.dm_exec_sql_text** 、実際に取得する[!INCLUDE[tsql](../../includes/tsql-md.md)]テキスト。|  
|**group_id**|**int**|このクエリが実行されているワークロード グループの ID。|  
|**pool_id**|**int**|このワークロード グループが属するリソース プールの ID。|  
|**is_small**|**tinyint**|1 に設定すると、この許可で小さなリソース セマフォが使用されます。 0 に設定すると、通常のセマフォが使用されます。|  
|**ideal_memory_kb**|**bigint**|物理メモリ内にすべてを収めるために必要なメモリ許可のサイズ (KB 単位)。 これはカーディナリティの推定値に基づいています。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
   
## <a name="remarks"></a>コメント  
 クエリ タイムアウトの一般的なデバッグ方法は、次のようになります。  
  
-   全体的なシステム メモリを使用して状態を確認[sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)、 [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)、およびさまざまなパフォーマンス カウンター。  
  
-   クエリ実行メモリ予約確認**sys.dm_os_memory_clerks**場所`type = 'MEMORYCLERK_SQLQERESERVATIONS'`します。  
  
-   確認を待機しているクエリ<sup>1</sup>を使用して許可**sys.dm_exec_query_memory_grants**します。  
  
    ```sql  
    --Find all queries waiting in the memory queue  
    SELECT * FROM sys.dm_exec_query_memory_grants where grant_time is null  
    ```  
    
    <sup>1</sup> このシナリオの場合、待機の種類は一般的に RESOURCE_SEMAPHORE になります。 詳細については、「[sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)」を参照してください。 
  
-   使用して、メモリ許可を使用したクエリのキャッシュを検索[sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)と[sys.dm_exec_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
  
    ```sql  
    -- retrieve every query plan from the plan cache  
    USE master;  
    GO  
    SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
    GO  
    ```  
  
-   使用してメモリを消費するクエリをさらに調べたり[sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)します。  
  
    ```sql  
    --Find top 5 queries by average CPU time  
    SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
      plan_handle, query_plan   
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
    ORDER BY total_worker_time/execution_count DESC;  
    GO  
    ```  
  
-   ランナウェイ クエリが疑いがある場合、確認のプラン表示から[sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)バッチからのテキストと[sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)します。  
  
 含む動的管理ビューを使用するクエリ`ORDER BY`または集計がメモリ使用量が増えるし、問題のある問題をそれによって可能性があります。  
  
 データベース管理者は、リソース ガバナー機能を使用することで、サーバー リソースを最大 64 個までのリソース プールに分散できます。 以降で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、各プールが小規模の独立したサーバー インスタンスのように動作し、2 つのセマフォを必要とします。 返される行の数**sys.dm_exec_query_resource_semaphores**できる最大 20 倍に返される行より[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。  
  
## <a name="see-also"></a>参照  
 [sys.dm_exec_query_resource_semaphores &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql.md)     
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)     
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
