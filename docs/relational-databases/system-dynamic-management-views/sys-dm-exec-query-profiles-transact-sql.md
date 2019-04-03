---
title: sys.dm_exec_query_profiles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_profiles_TSQL
- sys.dm_exec_query_profiles_TSQL
- dm_exec_query_profiles
- sys.dm_exec_query_profiles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_profiles dynamic management view
ms.assetid: 54efc6cb-eea8-4f6d-a4d0-aa05eeb54081
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 87488f36a4b4b01181cd973a75d6e5c7f2e233d7
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860723"
---
# <a name="sysdmexecqueryprofiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

クエリの実行中にリアルタイムでクエリの進行状況を監視します。 たとえば、この DMV を使用して、クエリのどの部分が低速に実行されているかを判断します。 この DMV をシステムの他の DMV と結合するには、説明フィールドで特定されている列を使用します。 または、タイムスタンプ列を使用してこの DMV を他のパフォーマンス カウンター (パフォーマンス モニター、xperf など) とを結合します。  
  
## <a name="table-returned"></a>返されるテーブル  
返されるカウンタでは、演算子別、スレッド別です。 結果は動的でありなど、既存のオプションの結果を一致しない`SET STATISTICS XML ON`クエリの終了時にのみ出力を作成します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|session_id|**SMALLINT**|このクエリを実行するセッションを識別します。 dm_exec_sessions.session_id を参照します。|  
|request_id|**ssNoversion**|対象の要求を識別します。 Dm_exec_sessions.request_id を参照します。|  
|sql_handle|**varbinary (64)**|バッチを一意に識別するトークンまたはクエリの一部であるストアド プロシージャです。 Dm_exec_query_stats.sql_handle を参照します。|  
|plan_handle|**varbinary (64)**|実行されるバッチのクエリ実行プランを一意に識別するトークンと、そのプランがプラン キャッシュ内に存在または現在実行しています。 Dm_exec_query_stats.plan_handle を参照します。|  
|physical_operator_name|**nvarchar (256)**|物理演算子の名前。|  
|node_id|**ssNoversion**|クエリ ツリー内の演算子ノードを識別します。|  
|thread_id|**ssNoversion**|(並列クエリの場合) に対して、同じクエリ演算子のノードに属するスレッドを識別します。|  
|task_address|**varbinary (8)**|このスレッドが使用している SQLOS タスクを識別します。 Dm_os_tasks.task_address を参照します。|  
|row_count|**BIGINT**|これまでに演算子によって返される行の数。|  
|rewind_count|**BIGINT**|これまでの巻き戻しの数。|  
|rebind_count|**BIGINT**|これまでの再バインドの数。|  
|end_of_scan_count|**BIGINT**|これまでのスキャンの終了の数。|  
|estimate_row_count|**BIGINT**|行の推定数。 Estimated_row_count を実際の row_count と比較すると解決することができます。|  
|first_active_time|**BIGINT**|演算子が最初に呼び出されたときに、ミリ秒単位の時間。|  
|last_active_time|**BIGINT**|演算子が最後に呼び出された時刻 (ミリ秒単位)。|  
|open_time|**BIGINT**|開いたときのタイムスタンプ (ミリ秒単位)。|  
|first_row_time|**BIGINT**|ミリ秒単位で最初の行を開いたときのタイムスタンプ。|  
|last_row_time|**BIGINT**|最後の行を開いたときのタイムスタンプ (ミリ秒単位)。|  
|close_time|**BIGINT**|(ミリ秒) を閉じるときのタイムスタンプ。|  
|elapsed_time_ms|**BIGINT**|経過時間の合計 (ミリ秒) をターゲット ノードの操作によってこれまでに使用します。|  
|cpu_time_ms|**BIGINT**|これまでにターゲット ノードの操作によって CPU 使用率 (ミリ秒単位) の時間の合計数します。|  
|database_id|**SMALLINT**|読み取りおよび書き込みが実行されたオブジェクトを含むデータベースの ID。|  
|object_id|**ssNoversion**|読み取りおよび書き込みが実行されたオブジェクトの識別子。 sys.objects.object_id を参照します。|  
|index_id|**ssNoversion**|行セットが開かれている対象のインデックス (ある場合)。|  
|scan_count|**BIGINT**|これまでのテーブル/インデックス スキャンの数。|  
|logical_read_count|**BIGINT**|これまでの論理読み取りの数。|  
|physical_read_count|**BIGINT**|これまでに物理の数を読み取ります。|  
|read_ahead_count|**BIGINT**|これまでの先行読み取りの数。|  
|write_page_count|**BIGINT**|これまでのスピルによるページ書き込みの数。|  
|lob_logical_read_count|**BIGINT**|これまでに論理 LOB の数を読み取ります。|  
|lob_physical_read_count|**BIGINT**|LOB 物理読み取りの数これまでにします。|  
|lob_read_ahead_count|**BIGINT**|LOB 先行読み取りのこれまでに数です。|  
|segment_read_count|**ssNoversion**|これまでのセグメント先行読み取りの数。|  
|segment_skip_count|**ssNoversion**|セグメントの数は、これまでにスキップされます。| 
|actual_read_row_count|**BIGINT**|残余述語が適用される前に、演算子によって読み取られた行の数。| 
|estimated_read_row_count|**BIGINT**|**適用対象:** 以降で[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]SP1。 <br/>残余述語が適用される前に、演算子によって読み取られる行の数が推定されます。|  
  
## <a name="general-remarks"></a>全般的な解説  
 クエリ プランのノードが、I/O を持たない場合、O 関連のすべてのカウンターは、NULL に設定されます。  
  
 この DMV によって報告された O 関連のカウンターがレポートされるものより細かい`SET STATISTICS IO`次の 2 つの方法で。  
  
-   `SET STATISTICS IO` すべての I/O をまとめて、特定のテーブルのカウンターをグループ化します。 この DMV でテーブルに I/O を実行するクエリ プランのノードごとに個別のカウンターが表示されます。  
  
-   並列スキャンがある場合、この DMV では、スキャンで使用される並列スレッドごとにカウンターがレポートされます。
 
以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、SP1、*標準クエリ実行統計プロファイリング インフラストラクチャ*と並行して存在する、*軽量なクエリ実行統計プロファイリング インフラストラクチャ*. `SET STATISTICS XML ON` `SET STATISTICS PROFILE ON`常に使用して、*標準クエリ実行統計プロファイリング インフラストラクチャ*します。 `sys.dm_exec_query_profiles`値を入力するインフラストラクチャをプロファイリングするクエリの 1 つ有効にします。 詳細については、「[クエリ プロファイリング インフラストラクチャ](../../relational-databases/performance/query-profiling-infrastructure.md)」を参照してください。    

>[!NOTE]
> 調査中のクエリを開始する必要があります**後**プロファイリング インフラストラクチャ クエリが有効になって、クエリが開始された後に有効にするで結果が得られない`sys.dm_exec_query_profiles`します。 クエリのインフラストラクチャのプロファイリングを有効にする方法の詳細については、次を参照してください。[クエリ プロファイリング インフラストラクチャ](../../relational-databases/performance/query-profiling-infrastructure.md)します。

## <a name="permissions"></a>アクセス許可  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   
   
## <a name="examples"></a>使用例  
 手順 1:分析するクエリを実行するセッションにログイン`sys.dm_exec_query_profiles`します。 クエリの使用のプロファイリングを構成する`SET STATISTICS PROFILE ON`します。 この同じセッションでは、クエリを実行します。  
  
```sql  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above (not needed in SQL Server 2019)  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 手順 2:クエリが実行されているセッションとは異なる 2 番目のセッションにログインします。  
  
 次のステートメントでは、セッション 54 で現在実行されているクエリの進行状況をまとめたものです。 これを行うには、各ノードでは、すべてのスレッドからの出力行の合計数を計算し、そのノードの出力行の推定数を比較します。  
  
```sql  
--Run this in a different session than the session in which your query is running. 
--Note that you may need to change session id 54 below with the session id you want to monitor.
SELECT node_id,physical_operator_name, SUM(row_count) row_count, 
  SUM(estimate_row_count) AS estimate_row_count, 
  CAST(SUM(row_count)*100 AS float)/SUM(estimate_row_count)  
FROM sys.dm_exec_query_profiles   
WHERE session_id=54
GROUP BY node_id,physical_operator_name  
ORDER BY node_id;  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
 
