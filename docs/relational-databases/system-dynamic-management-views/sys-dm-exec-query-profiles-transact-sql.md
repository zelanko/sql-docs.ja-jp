---
title: sys.dm_exec_query_profiles (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 2598c37c60955a93f2aed426db705d2b2ca7f204
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmexecqueryprofiles-transact-sql"></a>sys.dm_exec_query_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  クエリの実行中にリアルタイムでクエリの進行状況を監視します。 たとえば、この DMV を使用して、クエリで実行が遅い部分を判別します。 この DMV をシステムの他の DMV と結合するには、説明フィールドで特定されている列を使用します。 または、この DMV を他のパフォーマンス カウンター (パフォーマンス モニター、xperf など) と結合するには、タイムスタンプ列を使用します。  
  
## <a name="table-returned"></a>返されるテーブル  
 返されるカウンターは、演算子別、スレッド別です。 結果は動的であり、クエリの終了時にのみ出力を作成する SET STATISTICS XML ON などの既存のオプションの結果とは一致しません。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|このクエリが実行されるセッションを識別します。 dm_exec_sessions.session_id を参照します。|  
|request_id|**int**|対象の要求を識別します。 dm_exec_sessions.request_id を参照します。|  
|sql_handle|**varbinary(64)**|対象のクエリを識別します。 dm_exec_query_stats.sql_handle を参照します。|  
|plan_handle|**varbinary(64)**|対象のクエリを識別します。dm_exec_query_stats.plan_handle を参照します。|  
|physical_operator_name|**nvarchar (256)**|物理演算子の名前。|  
|node_id|**int**|クエリ ツリー内の演算子ノードを識別します。|  
|thread_id|**int**|同じクエリ演算子ノードに属するスレッド (並列クエリ用) を区別します。|  
|task_address|**varbinary(8)**|このスレッドが使用している SQLOS タスクを識別します。 dm_os_tasks.task_address を参照します。|  
|row_count|**bigint**|これまでに演算子によって返された行の数。|  
|rewind_count|**bigint**|これまでの巻き戻しの数。|  
|rebind_count|**bigint**|これまでの再バインドの数。|  
|end_of_scan_count|**bigint**|これまでのスキャンの終了の数。|  
|estimate_row_count|**bigint**|推定される行の数。 estimated_row_count を実際の row_count と比較することが役立つ場合があります。|  
|first_active_time|**bigint**|演算子が初めて呼び出された時刻 (ミリ秒単位)。|  
|last_active_time|**bigint**|演算子が最後に呼び出された時刻 (ミリ秒単位)。|  
|open_time|**bigint**|開いたときのタイムスタンプ (ミリ秒単位)。|  
|first_row_time|**bigint**|最初の行を開いたときのタイムスタンプ (ミリ秒単位)。|  
|last_row_time|**bigint**|最後の行を開いたときのタイムスタンプ (ミリ秒単位)。|  
|close_time|**bigint**|閉じたときのタイムスタンプ (ミリ秒単位)。|  
|elapsed_time_ms|**bigint**|これまでに対象のノードの操作によって使用された経過時間の合計 (ミリ秒単位)。|  
|cpu_time_ms|**bigint**|これまでに対象のノードの操作によって使用された CPU 時間の合計 (ミリ秒単位)。|  
|database_id|**smallint**|読み取りおよび書き込みが実行されたオブジェクトを含むデータベースの ID。|  
|object_id|**int**|読み取りおよび書き込みが実行されたオブジェクトの識別子。 sys.objects.object_id を参照します。|  
|index_id|**int**|行セットが開かれている対象のインデックス (ある場合)。|  
|scan_count|**bigint**|これまでのテーブル/インデックス スキャンの数。|  
|logical_read_count|**bigint**|これまでの論理読み取りの数。|  
|physical_read_count|**bigint**|これまでの物理読み取りの数。|  
|read_ahead_count|**bigint**|これまでの先行読み取りの数。|  
|write_page_count|**bigint**|これまでのスピルによるページ書き込みの数。|  
|lob_logical_read_count|**bigint**|これまでの LOB 論理読み取りの数。|  
|lob_physical_read_count|**bigint**|これまでの LOB 物理読み取りの数。|  
|lob_read_ahead_count|**bigint**|これまでの LOB 先行読み取りの数。|  
|segment_read_count|**int**|これまでのセグメント先行読み取りの数。|  
|segment_skip_count|**int**|これまでのセグメント スキップの数。| 
|actual_read_row_count|**bigint**|残余述語が適用される前に、演算子によって読み取られる行の数。| 
|estimated_read_row_count|**bigint**|**適用されます:** で始まる[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]SP1。 <br/>残余述語が適用される前に、演算子で読み取られる行の数が推定されます。|  
  
## <a name="general-remarks"></a>全般的な解説  
 クエリ プラン ノードで IO がない場合、IO 関連のすべてのカウンターは NULL に設定されます。  
  
 この DMV でレポートされる IO 関連のカウンターは、次の 2 つの点で、SET STATISTICS IO でレポートされるものよりも詳細です。  
  
-   SET STATISTICS IO では、特定のテーブルに対するすべての IO のカウンターはグループ化されます。 この DMV では、テーブルに対する IO を実行するクエリ プランのそれぞれのノードについて、個別のカウンターを取得します。  
  
-   並列スキャンがある場合、この DMV では、スキャンで使用される並列スレッドごとにカウンターがレポートされます。
 
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 では、標準的なクエリ実行の統計がプロファイリング インフラストラクチャでは、プロファイリング インフラストラクチャ軽量のクエリ実行の統計のサイド バイ サイドが存在します。 新しいクエリ実行統計プロファイル インフラストラクチャでは、行の実際の数など、演算子ごとのクエリ実行の統計を収集する場合のパフォーマンスのオーバーヘッドが大幅に削減します。 グローバルを使用してこの機能を有効にすることができますスタートアップ[トレース フラグ 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)が自動的にオン query_thread_profile 拡張イベントを使用する場合またはします。

>[!NOTE]
> CPU と経過時間は、パフォーマンスに与える影響を軽減する軽量なクエリ実行統計プロファイル インフラストラクチャではサポートされていません。

 STATISTICS XML ON および SET STATISTICS PROFILE ON プロファイリング インフラストラクチャ従来のクエリ実行の統計を常に使用を設定します。
  
## <a name="permissions"></a>権限  

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   
   
## <a name="examples"></a>使用例  
 Sys.dm_exec_query_profiles を分析するクエリを実行することを計画しているセッションに手順 1: ログインします。 構成するのには、プロファイルのクエリは、SET STATISTICS PROFILE を使用します。 この同じセッションでクエリを実行します。  
  
```  
--Configure query for profiling with sys.dm_exec_query_profiles  
SET STATISTICS PROFILE ON;  
GO  

--Or enable query profiling globally under SQL Server 2016 SP1 or above  
DBCC TRACEON (7412, -1);  
GO 
  
--Next, run your query in this session, or in any other session if query profiling has been enabled globally 
```  
  
 クエリが実行されているセッションとは異なる 2 つ目のセッションに手順 2: ログインします。  
  
 次のステートメントでは、セッション 54 で現在実行されているクエリの進行状況が要約されます。 これを実行するために、各ノードのすべてのスレッドからの出力行の総数が計算され、そのノードの出力行の予測数と比較されます。  
  
```  
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
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  

