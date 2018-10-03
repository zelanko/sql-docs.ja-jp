---
title: sys.dm_os_schedulers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_schedulers
- sys.dm_os_schedulers_TSQL
- sys.dm_os_schedulers
- dm_os_schedulers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_schedulers dynamic management view
ms.assetid: 3a09d81b-55d5-416f-9cda-1a3a5492abe0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 99a456ee0b2159c7cfebfbb1ac2dff2468c2cdd5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625850"
---
# <a name="sysdmosschedulers-transact-sql"></a>sys.dm_os_schedulers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のスケジューラごとに 1 行のデータを返します。各スケジューラは個別のプロセッサにマップされています。 このビューは、スケジューラの状況の監視やランナウェイ タスクの特定に使用できます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_schedulers**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|scheduler_address|**varbinary(8)**|スケジューラのメモリ アドレス。 NULL 値は許可されません。|  
|parent_node_id|**int**|スケジューラが属するノード (親ノード) の ID。 これは非均質メモリ アクセス (NUMA) ノードを表します。 NULL 値は許可されません。|  
|scheduler_id|**int**|スケジューラの ID。 定期的なクエリの実行に使用されるスケジューラにはすべて、1048576 未満の ID 番号が付いています。 Id が 1048576 以上スケジューラが内部で使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、専用管理者接続のスケジューラなどです。 NULL 値は許可されません。|  
|cpu_id|**smallint**|スケジューラに割り当てられた CPU ID。<br /><br /> NULL 値は許可されません。<br /><br /> **注:** 255 は示しませんありませんアフィニティよう[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。 参照してください[sys.dm_os_threads &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)関係の詳細についてはします。|  
|status|**nvarchar(60)**|スケジューラの状態。 次の値のいずれかです。<br /><br /> 非オンライン<br />非オフライン<br />表示されるオンライン<br />表示されているオフライン<br />表示されるオンライン (DAC)<br />-   HOT_ADDED<br /><br /> NULL 値は許可されません。<br /><br /> 非表示スケジューラが内部的な要求の処理に使用される、[!INCLUDE[ssDE](../../includes/ssde-md.md)]します。 VISIBLE スケジューラは、ユーザーの要求の処理に使用されます。<br /><br /> OFFLINE スケジューラは、関係マスクでオフラインになっているプロセッサにマップされます。そのため、要求の処理には使用されません。 ONLINE スケジューラは、関係マスクでオンラインになっているプロセッサにマップされ、スレッドの処理に使用されます。<br /><br /> DAC は、スケジューラが専用管理者接続で動作していることを示します。<br /><br /> HOT ADDED は、スケジューラがホット アド CPU イベントに応答して追加されたことを示します。|  
|is_online|**bit**|場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が構成されている一部のスケジューラがアフィニティ マスクのないプロセッサにマップされている、サーバーで使用可能なプロセッサの一部のみを使用してこの構成が意味ことができます。 これに該当する場合、この列には 0 が返されます。 この値は、スケジューラがクエリまたはバッチの処理に使用されていないことを意味します。<br /><br /> NULL 値は許可されません。|  
|is_idle|**bit**|1 = スケジューラはアイドル状態です。 現在実行中のワーカーはありません。 NULL 値は許可されません。|  
|preemptive_switches_count|**int**|スケジューラのワーカーがプリエンプティブ モードに切り替えられた回数。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 外部のコード (拡張ストアド プロシージャや分散クエリなど) を実行するには、スレッドを非プリエンプティブ スケジューラの制御外で実行する必要があります。 このとき、ワーカーはプリエンプティブ モードに切り替えられます。|  
|context_switches_count|**int**|スケジューラでコンテキストが切り替えられた回数。 NULL 値は許可されません。<br /><br /> 他のワーカーの実行を許可するには、現在実行しているワーカーでスケジューラの制御を解放するか、コンテキストを切り替える必要があります。<br /><br /> **注:** の作業者と自体ワーカーは、スケジューラが得られます自体を実行可能キューに配置し、他のワーカーが、検出されない、選択します。 この場合、context_switches_count は更新されませんが、yield_count は更新されます。|  
|idle_switches_count|**int**|スケジューラがアイドル中にイベントを待機した回数。 この列は context_switches_count と類似しています。 NULL 値は許可されません。|  
|current_tasks_count|**int**|このスケジューラに関連付けられている現在のタスクの数。 これには次のタスクが含まれます。<br /><br /> -それらを実行するワーカーを待機しているタスク。<br />-現在待機中または (SUSPENDED または RUNNABLE 状態) で実行するタスク。<br /><br /> タスクが完了すると、このカウントは 1 減ります。 NULL 値は許可されません。|  
|runnable_tasks_count|**int**|実行可能キューにあるスケジュール待ちのワーカーで、タスクが割り当てられているワーカーの数。 NULL 値は許可されません。|  
|current_workers_count|**int**|このスケジューラに関連付けられているワーカーの数。 これにはタスクが割り当てられていないワーカーも含まれます。 NULL 値は許可されません。|  
|active_workers_count|**int**|アクティブなワーカーの数。 アクティブなワーカーがプリエンプティブになることはなく、必ずタスクが関連付けられています。また、実行中、実行可能、または中断状態のいずれかになっています。 NULL 値は許可されません。|  
|work_queue_count|**bigint**|保留キュー内のタスクの数。 保留キュー内のタスクは、ワーカーによる取得を待機しています。 NULL 値は許可されません。|  
|pending_disk_io_count|**int**|完了を待機している保留中の I/O の数。 各スケジューラには保留中の I/O の一覧が保持されており、コンテキストが切り替えられるたび、これらの I/O が完了したかどうかを確認するために、この一覧がチェックされます。 要求が挿入されると、カウントは 1 増えます。 要求が完了すると、カウントは 1 減ります。 この数は、I/O の状態を示すわけではありません。 NULL 値は許可されません。|  
|load_factor|**int**|スケジューラで認識されている負荷を示す内部値。 この値は、新しいタスクをこのスケジューラに指定するか、または他のスケジューラに指定するかを決定するために使用されます。 また、スケジューラの負荷が均等でないと思われる場合のデバッグに利用できます。 ルーティングはスケジューラの負荷に基づいて決定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ノードとスケジューラの占有率を最適なリソースを取得するのに場所を決めるにも使用します。 タスクがエンキューされると、占有率は増加します。 タスクが完了すると、占有率は減少します。 占有率を利用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OS で負荷を効率よく分散できます。 NULL 値は許可されません。|  
|yield_count|**int**|スケジューラの進行状況を示すために使用される内部値。 この値は、スケジューラ モニターで、このスケジューラのワーカーが予定どおりに他のワーカーに変更されるかどうかを確認するために使用されます。 ワーカーまたはタスクが新しいワーカーに移行するわけではありません。 NULL 値は許可されません。|  
|last_timer_activity|**bigint**|前回、スケジューラのタイマー キューがスケジューラにより確認された時間 (CPU ティック単位)。 NULL 値は許可されません。|  
|failed_to_create_worker|**bit**|スケジューラで新しいワーカーを作成できなかった場合は 1 になります。 これは通常、メモリ制約が原因で発生します。 NULL 値が許可されます。|  
|active_worker_address|**varbinary(8)**|現在アクティブなワーカーのメモリ アドレス。 NULL 値が許可されます。 詳細については、次を参照してください。 [sys.dm_os_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)します。|  
|memory_object_address|**varbinary(8)**|スケジューラのメモリ オブジェクトのメモリ アドレス。 Null を許容しません。|  
|task_memory_object_address|**varbinary(8)**|タスクのメモリ オブジェクトのメモリ アドレス。 NULL 値は許可されません。 詳細については、次を参照してください。 [sys.dm_os_memory_objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)します。|  
|quantum_length_us|**bigint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]SQLOS によって使用されるスケジューラ クォンタムを公開します。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   

## <a name="examples"></a>使用例  
  
### <a name="a-monitoring-hidden-and-nonhidden-schedulers"></a>A. 非表示スケジューラと表示スケジューラを監視する  
 次のクエリは、ワーカーの状態を出力し、タスクで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]間のすべてのスケジューラでします。 このクエリは、次の要件を満たすコンピューター システムで実行されました。  
  
-   2 つのプロセッサ (CPU)  
  
-   2 つの (NUMA) ノード  
  
-   1 つの NUMA ノードにつき 1 つの CPU  
  
-   関係マスクが `0x03` に設定されている  
  
```  
SELECT  
    scheduler_id,  
    cpu_id,  
    parent_node_id,  
    current_tasks_count,  
    runnable_tasks_count,  
    current_workers_count,  
    active_workers_count,  
    work_queue_count  
  FROM sys.dm_os_schedulers;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
scheduler_id cpu_id parent_node_id current_tasks_count  
------------ ------ -------------- -------------------  
0            1      0              9                    
257          255    0              1                    
1            0      1              10                   
258          255    1              1                    
255          255    32             2                    
  
runnable_tasks_count current_workers_count  
-------------------- ---------------------  
0                    11                     
0                    1                      
0                    18                     
0                    1                      
0                    3                      
  
active_workers_count work_queue_count  
-------------------- --------------------  
6                    0  
1                    0  
8                    0  
1                    0  
1                    0  
```  
  
 この出力では次のことがわかります。  
  
-   スケジューラは 5 つで、 そのうちの 2 つの ID の値は 1048576 未満です。 ID が 1048576 以上のスケジューラは非表示スケジューラです。 スケジューラ`255`専用管理者接続 (DAC) を表します。 インスタンスごとに 1 つの DAC スケジューラが存在します。 メモリの負荷を調整するリソース モニターは、スケジューラを使用して`257`とスケジューラ`258`、NUMA ノードごとに 1 つ  
  
-   出力では、23 のアクティブなタスクが示されています。 これらのタスクは、ユーザーの要求によって開始されたリソースの管理タスクに加えて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 例の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]タスクはリソース モニター (NUMA ノードごとに 1 つ)、LAZY WRITER (NUMA ノードごとに 1 つ)、ロック モニター、チェックポイント、およびログ ライター。  
  
-   NUMA ノード `0` は CPU `1` にマップされており、NUMA ノード `1` は CPU `0` にマップされています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通常、ノード 0 以外の NUMA ノードで開始します。  
  
-   ここでは `runnable_tasks_count` に `0` が返されており、これはアクティブに実行中のタスクが存在しないことを意味します。 ただし、アクティブなセッションは存在する可能性があります。  
  
-   スケジューラ`255`が DAC を表す`3`ワーカーが関連付けられています。 これらのワーカーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動時に割り当てられ、変更されることはありません。 これらのワーカーは DAC クエリの処理のみに使用されます。 このスケジューラ上の 2 つのタスクは、接続マネージャーとアイドル状態のワーカーを表します。  
  
-   `active_workers_count` タスクが関連付けられ、非プリエンプティブ モードで実行されているすべてのワーカーを表します。 ネットワーク リスナーなどの一部のタスクは、プリエンプティブなスケジュール設定で実行されます。  
  
-   非表示スケジューラでは、通常のユーザー要求は処理されません。 ただし、DAC スケジューラは例外です。 この DAC スケジューラには、要求を処理するためのスレッドが 1 つあります。  
  
### <a name="b-monitoring-nonhidden-schedulers-in-a-busy-system"></a>B. 稼働率が高いシステムで表示スケジューラを監視する  
 次のクエリでは、負荷が高い表示スケジューラの状態を示します。このスケジューラでは、利用可能なワーカーの処理数を上回る要求が存在します。 この例では、256 のワーカーにタスクが割り当てられており、 一部のタスクはワーカーへの割り当てを待機中です。 実行可能なタスクの数が少ないということは、複数のタスクがリソースの待機中であることを意味します。  
  
> [!NOTE]  
>  sys.dm_os_workers でクエリを実行すると、ワーカーの状態を確認できます。 詳細については、次を参照してください。 [sys.dm_os_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)します。  
  
 クエリを次に示します。  
  
```  
SELECT  
    scheduler_id,  
    cpu_id,  
    current_tasks_count,  
    runnable_tasks_count,  
    current_workers_count,  
    active_workers_count,  
    work_queue_count  
  FROM sys.dm_os_schedulers  
  WHERE scheduler_id < 255;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
scheduler_id current_tasks_count runnable_tasks_count  
------------ ------------------- --------------------  
0            144                 0                     
1            147                 1                     
  
current_workers_count active_workers_count work_queue_count  
--------------------- -------------------- --------------------  
128                   125                  16  
128                   126                  19  
```  
  
 これに比較して次の結果では、実行可能なタスクが複数あり、ワーカーの取得を待機中のタスクがないことが示されています。 `work_queue_count` は両方のスケジューラで `0` になっています。  
  
```  
scheduler_id current_tasks_count runnable_tasks_count  
------------ ------------------- --------------------  
0            107                 98                    
1            110                 100                   
  
current_workers_count active_workers_count work_queue_count  
--------------------- -------------------- --------------------  
128                   104                  0  
128                   108                  0  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


