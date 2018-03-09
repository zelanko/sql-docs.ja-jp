---
title: "sys.dm_exec_query_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_query_stats_TSQL
- dm_exec_query_stats
- sys.dm_exec_query_stats
- sys.dm_exec_query_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_stats dynamic management view
ms.assetid: eb7b58b8-3508-4114-97c2-d877bcb12964
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 8874b5ba3eca2f3e9d72874af7440934fc2ec20f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecquerystats-transact-sql"></a>sys.dm_exec_query_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  キャッシュされたクエリ プランの集計パフォーマンス統計を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 このビューには、キャッシュされたプラン内のクエリ ステートメントごとに 1 行が含まれており、その行の有効期間はプラン自体に関連付けられています。 つまり、プランがキャッシュから削除されると、対応する行もこのビューから削除されます。  
  
> [!NOTE]
> 最初のクエリ**sys.dm_exec_query_stats**サーバーで現在実行中のワークロードがある場合、不正確な結果を生じる可能性があります。 クエリを再実行すると、より正確な結果を確認できます。  
  
> [!NOTE]
> これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_exec_query_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**sql_handle**|**varbinary(64)**  |クエリが含まれているバッチまたはストアド プロシージャを参照するトークンを指定します。<br /><br /> **sql_handle**と連携して、 **statement_start_offset**と**statement_end_offset**、呼び出すことによって、クエリの SQL テキストを取得するために使用する、 **sys.dm_exec_sql_text**動的管理関数です。|  
|**statement_start_offset**|**int**|バッチまたは保存されるオブジェクトのテキスト内での、行が示すクエリの開始位置 (バイト単位)。0 で始まります。|  
|**statement_end_offset**|**int**|バッチまたは保存されるオブジェクトのテキスト内での、行が示すクエリの終了位置 (バイト単位)。0 で始まります。 前に、のバージョンの[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、値-1 はバッチの終わりを示します。 末尾のコメントは含まれません。|  
|**plan_generation_num**|**bigint**|再コンパイル後、プランのインスタンスを区別するために使用できるシーケンス番号。|  
|**plan_handle**|**varbinary(64)**|クエリが含まれているコンパイル済みのプランを参照するトークン。 この値に渡されることができます、 [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)動的管理関数をクエリ プランを取得します。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0x000 になります。|  
|**creation_time**|**datetime**|プランがコンパイルされた時刻。|  
|**last_execution_time**|**datetime**|前回プランの実行が開始された時刻。|  
|**execution_count**|**bigint**|前回のコンパイル時以降に、プランが実行された回数。|  
|**total_worker_time**|**bigint**|コンパイル後にプランの実行で使用された CPU 時間の合計 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。<br /><br /> ネイティブ コンパイル ストアド プロシージャに関して、多くの実行が 1 ミリ秒未満である場合は、 **total_worker_time** は精度が高くない可能性があります。|  
|**last_worker_time**|**bigint**|プランを前回実行したときに使用された CPU 時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|プランの 1 回の実行で使用された最小 CPU 時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|プランの 1 回の実行で使用された最大 CPU 時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。 <sup>1</sup>|  
|**total_physical_reads**|**bigint**|コンパイル後にこのプランの実行で行われた物理読み取りの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_physical_reads**|**bigint**|プランを前回実行したときに行われた物理読み取りの数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_physical_reads**|**bigint**|プランの 1 回の実行で行われた物理読み取りの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_physical_reads**|**bigint**|プランの 1 回の実行で行われた物理読み取りの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_writes**|**bigint**|コンパイル後にプランの実行で行われた論理書き込みの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_writes**|**bigint**|前回プランが実行されたときにダーティになったバッファー プール ページの数。 ページが既にダーティの場合 (変更された場合)、書き込みはカウントされません。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_writes**|**bigint**|プランの 1 回の実行で行われた論理書き込みの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_writes**|**bigint**|プランの 1 回の実行で行われた論理書き込みの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_logical_reads**|**bigint**|コンパイル後にこのプランの実行で行われた論理読み取りの合計数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_logical_reads**|**bigint**|プランを前回実行したときに行われた論理読み取りの数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_logical_reads**|**bigint**|プランの 1 回の実行で行われた論理読み取りの最小数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_logical_reads**|**bigint**|プランの 1 回の実行で行われた論理読み取りの最大数。<br /><br /> メモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**total_clr_time**|**bigint**|内部で使用されたマイクロ秒 (ただし、精度はミリ秒単位まで)、単位時間[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]コンパイルされた後に、このプランの実行で共通言語ランタイム (CLR) オブジェクトします。 CLR オブジェクトには、ストアド プロシージャ、関数、トリガー、型、および集計を指定できます。|  
|**last_clr_time**|**bigint**|内で実行に使用されたマイクロ秒 (ただし、精度はミリ秒単位) で報告時刻[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]このプランの前回の実行中に CLR オブジェクト。 CLR オブジェクトには、ストアド プロシージャ、関数、トリガー、型、および集計を指定できます。|  
|**min_clr_time**|**bigint**|プランの 1 回の実行で、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR オブジェクト内部で使用された最小時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。 CLR オブジェクトには、ストアド プロシージャ、関数、トリガー、型、および集計を指定できます。|  
|**max_clr_time**|**bigint**|プランの 1 回の実行で、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 内部で使用された最大時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。 CLR オブジェクトには、ストアド プロシージャ、関数、トリガー、型、および集計を指定できます。|  
|**total_elapsed_time**|**bigint**|このプランの実行完了までの経過時間の合計 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。|  
|**last_elapsed_time**|**bigint**|このプランの前回の実行完了までの経過時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。|  
|**min_elapsed_time**|**bigint**|任意のプランの実行完了までの最小経過時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。|  
|**max_elapsed_time**|**bigint**|任意のプランの実行完了までの最大経過時間 (マイクロ秒単位)。ただし、精度はミリ秒単位までです。|  
|**query_hash**|**Binary(8)**|クエリで計算され、同様のロジックを持つクエリを識別するために使用される、バイナリのハッシュ値です。 クエリ ハッシュを使用して、リテラル値だけが異なるクエリの全体的なリソース使用率を決定できます。|  
|**query_plan_hash**|**binary(8)**|クエリ実行プランで計算され、同様のクエリ実行プランを識別するために使用される、バイナリのハッシュ値です。 クエリ プラン ハッシュを使用して、同様の実行プランを持つクエリの累積コストを確認できます。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0x000 になります。|  
|**total_rows**|**bigint**|クエリによって返される行の合計数。 null にすることはできません。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**last_rows**|**bigint**|クエリの前回の実行で返された行数。 null にすることはできません。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**min_rows**|**bigint**|1 つの実行中に、クエリによって返された行の最小数。 null にすることはできません。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**max_rows**|**bigint**|1 つの実行中に、クエリによって返された行の最大数。 null にすることはできません。<br /><br /> ネイティブ コンパイル ストアド プロシージャがメモリ最適化テーブルに対してクエリを実行するときは、常に 0 になります。|  
|**statement_sql_handle**|**varbinary(64)**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> クエリ ストアがオンになっている場合にのみ NULL 以外の値に設定され、その特定のクエリの統計情報を収集します。|  
|**statement_context_id**|**bigint**|**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> クエリ ストアがオンになっている場合にのみ NULL 以外の値に設定され、その特定のクエリの統計情報を収集します。|  
|**total_dop**|**bigint**|並列処理の次数の合計の合計このプランは、コンパイルされた後に使用されます。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**last_dop**|**bigint**|このプランの前回の実行時に並列処理の次数。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**min_dop**|**bigint**|並列処理の最小限度このプランは、1 つの実行中にこれまで使用します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**max_dop**|**bigint**|並列処理の最大限度このプランは、1 つの実行時にこれまで使用します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**total_grant_kb**|**bigint**|予約済みメモリの合計量は、サポート技術情報でこのプランをコンパイルした後に受信したを付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**last_grant_kb**|**bigint**|予約済みメモリの量は、このプランが最後に実行されたときに、サポート技術情報で付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**min_grant_kb**|**bigint**|予約済みメモリの最小量は、サポート技術情報でこのプランの 1 つの実行中に受信したことを付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**max_grant_kb**|**bigint**|予約済みメモリの最大量は、サポート技術情報でこのプランの 1 つの実行中に受信したことを付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**total_used_grant_kb**|**bigint**|予約済みメモリの総量では、このプランがコンパイルされた後に使用される (KB 単位) 許可します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**last_used_grant_kb**|**bigint**|このプランが最後に実行されたときに、サポート技術情報で使用されたメモリ許可の量。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**min_used_grant_kb**|**bigint**|最小メモリ使用量は、サポート技術情報でこのプランの 1 つの実行中に使用することを付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**max_used_grant_kb**|**bigint**|最大メモリ使用量は、サポート技術情報でこのプランの 1 つの実行中に使用することを付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**total_ideal_grant_kb**|**bigint**|理想的なメモリの合計量は、このプランがコンパイルされた後に推定 KB で付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**last_ideal_grant_kb**|**bigint**|理想的なメモリの量は、このプランが最後に実行されたときに、サポート技術情報で付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**min_ideal_grant_kb**|**bigint**|理想的なメモリの最小量は、このプランの 1 つの実行時にこれまで推定 kb 単位で付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**max_ideal_grant_kb**|**bigint**|理想的なメモリの最大量は、このプランの 1 つの実行時にこれまで推定 KB で付与します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**total_reserved_threads**|**bigint**|予約済みの並列の合計は、このプランがコンパイルされて以降を使用することをスレッドです。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**last_reserved_threads**|**bigint**|このプランが最後に実行されたときに、予約済みの並列スレッドの数。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**min_reserved_threads**|**bigint**|予約済みの並列の最小数は、このプランの 1 つの実行中に使用することをスレッドです。  これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**max_reserved_threads**|**bigint**|予約済みの並列の最大数は、このプランの 1 つの実行中に使用することをスレッドです。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**total_used_threads**|**bigint**|合計の合計は、このプランがコンパイルされて以降を使用することの並列スレッドを使用します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**last_used_threads**|**bigint**|このプランが最後に実行されたときに使用される並列スレッドの数。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**min_used_threads**|**bigint**|最小数は、このプランの 1 つの実行中に使用することの並列スレッドを使用します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**max_used_threads**|**bigint**|最大数は、このプランの 1 回の実行中に使用される並列スレッドを使用します。 これは常に、メモリ最適化テーブルのクエリを実行する場合は 0 です。<br /><br /> **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
|**total_columnstore_segment_reads**|**bigint**|列ストア セグメントが、クエリで読み取りの合計。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**last_columnstore_segment_reads**|**bigint**|クエリの前回の実行によって読み取られた列ストア セグメントの数。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**min_columnstore_segment_reads**|**bigint**|1 つの実行中に、クエリによって読み取られた列ストア セグメントの最小数。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**max_columnstore_segment_reads**|**bigint**|1 つの実行中に、クエリによって読み取られた列ストア セグメントの最大数。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**total_columnstore_segment_skips**|**bigint**|クエリによってスキップされた列ストア セグメントの合計。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**last_columnstore_segment_skips**|**bigint**|クエリの前回の実行によってスキップされた列ストア セグメントの数。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**min_columnstore_segment_skips**|**bigint**|1 つの実行中に、クエリによってこれまでスキップ列ストア セグメントの最小数。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|    
|**max_columnstore_segment_skips**|**bigint**|1 つの実行中に、クエリによってこれまでスキップ列ストア セグメントの最大数。 null にすることはできません。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|
|**total_spills**|**bigint**|コンパイルされた後に、このクエリの実行によって書き込まれたページの合計数。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**last_spills**|**bigint**|ページの数には、クエリが実行された最終時刻が書き込まれました。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**min_spills**|**bigint**|このクエリ 1 回の実行中に書き込まれたページの最小数。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**max_spills**|**bigint**|このクエリ 1 回の実行中に書き込まれたページの最大数。<br /><br /> **適用されます**: で始まる[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3|  
|**pdw_node_id**|**int**|この分布はでは、ノードの識別子。<br /><br /> **適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]| 

> [!NOTE]
> <sup>1</sup>ネイティブ コンパイル ストアド プロシージャに対する統計コレクションを有効にすると、ワーカー時間がミリ秒単位で収集します。 クエリを 1 ミリ秒未満で実行した場合、値は 0 になります。  
  
## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。
  
## <a name="remarks"></a>解説  
 ビュー内の統計は、クエリが完了したときに更新されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-finding-the-top-n-queries"></a>A. TOP N クエリを確認する  
 次の例では、CPU の平均時間で順位付けされた上位 5 つのクエリに関する情報を返します。 この例では、クエリ ハッシュに従ってクエリを集計して、論理的に等価のクエリを累積リソース使用量別にグループ化しています。  
  
```sql  
SELECT TOP 5 query_stats.query_hash AS "Query Hash",   
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time",  
    MIN(query_stats.statement_text) AS "Statement Text"  
FROM   
    (SELECT QS.*,   
    SUBSTRING(ST.text, (QS.statement_start_offset/2) + 1,  
    ((CASE statement_end_offset   
        WHEN -1 THEN DATALENGTH(ST.text)  
        ELSE QS.statement_end_offset END   
            - QS.statement_start_offset)/2) + 1) AS statement_text  
     FROM sys.dm_exec_query_stats AS QS  
     CROSS APPLY sys.dm_exec_sql_text(QS.sql_handle) as ST) as query_stats  
GROUP BY query_stats.query_hash  
ORDER BY 2 DESC;  
```  
  
### <a name="b-returning-row-count-aggregates-for-a-query"></a>B. クエリの行数集計を返す  
 次の例では、クエリに対して行数の集計情報 (行の総数、最小行数、最大行数、および最後の行) を返します。  
  
```sql  
SELECT qs.execution_count,  
    SUBSTRING(qt.text,qs.statement_start_offset/2 +1,   
                 (CASE WHEN qs.statement_end_offset = -1   
                       THEN LEN(CONVERT(nvarchar(max), qt.text)) * 2   
                       ELSE qs.statement_end_offset end -  
                            qs.statement_start_offset  
                 )/2  
             ) AS query_text,   
     qt.dbid, dbname= DB_NAME (qt.dbid), qt.objectid,   
     qs.total_rows, qs.last_rows, qs.min_rows, qs.max_rows  
FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS qt   
WHERE qt.text like '%SELECT%'   
ORDER BY qs.execution_count DESC;  
```  
  
## <a name="see-also"></a>参照  
[実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)    
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)    
[sys.dm_exec_query_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_procedure_stats および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)     
[sys.dm_exec_trigger_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)     
[sys.dm_exec_cached_plans &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  


