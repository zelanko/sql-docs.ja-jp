---
title: sys.dm_os_sys_info (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 04/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_sys_info_TSQL
- dm_os_sys_info
- dm_os_sys_info_TSQL
- sys.dm_os_sys_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_info dynamic management view
- time [SQL Server], instance started
- starting time
ms.assetid: 20f6bc9c-839a-4fa4-b3f3-a6c47d1b69af
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c56eeab15da21b4c202cd217b0df009db1391616
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265671"
---
# <a name="sysdmossysinfo-transact-sql"></a>sys.dm_os_sys_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  コンピューターに関する有用な情報のセット、および [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で使用/消費されるリソースに関する有用な情報のセットを返します。  
  
> **注:** これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_sys_info**します。  
  
|列名|データ型|説明とバージョン固有の注意事項 |  
|-----------------|---------------|-----------------|  
|**cpu_ticks**|**bigint**|現在の CPU のティック数を指定します。 CPU のティックは、プロセッサの RDTSC カウンターから取得されます。 この数値は単純に増加します。 Null を許容しません。|  
|**ms_ticks**|**bigint**|コンピューターを起動した時点から経過した時間を指定します (ミリ秒単位)。 Null を許容しません。|  
|**cpu_count**|**int**|システム上の論理 CPU の数を指定します。 Null を許容しません。|  
|**hyperthread_ratio**|**int**|1 つの物理プロセッサ パッケージによって公開されている論理コアまたは物理コアの数の比率を指定します。 Null を許容しません。|  
|**physical_memory_in_bytes**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> コンピューターに搭載されている物理メモリの合計を指定します。 Null を許容しません。|  
|**physical_memory_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> コンピューターに搭載されている物理メモリの合計を指定します。 Null を許容しません。|  
|**virtual_memory_in_bytes**|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> ユーザー モードのプロセスで使用できる仮想メモリの量。 これを使用すると、SQL Server が 3-GB スイッチを使用して起動されたかどうかを判別できます。|  
|**virtual_memory_kb**|**bigint**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ユーザー モードのプロセスで使用できる仮想アドレス空間の合計量を指定します。 Null を許容しません。|  
|**bpool_commited**|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> メモリ マネージャーでコミット済みのメモリの量を表します (KB 単位)。 メモリ マネージャー内の予約済みメモリは含まれません。 Null を許容しません。|  
|**committed_kb**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> メモリ マネージャーでコミット済みのメモリの量を表します (KB 単位)。 メモリ マネージャー内の予約済みメモリは含まれません。 Null を許容しません。|  
|**bpool_commit_target**|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> SQL Server のメモリ マネージャーによって使用できるメモリの量を表します (KB 単位)。|  
|**committed_target_kb**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> SQL Server のメモリ マネージャーによって使用できるメモリの量を表します (KB 単位)。 ターゲットの量は、次のような各種の入力を使用して計算されます。<br /><br /> 負荷を含む、システムの現在の状態<br /><br /> -現在のプロセスによって要求されたメモリ<br /><br /> -コンピューターにインストールされているメモリの量<br /><br /> -構成パラメーター<br /><br /> 場合**committed_target_kb**よりも大きい**committed_kb**、メモリ マネージャーは追加のメモリを取得を試みます。 場合**committed_target_kb**よりも小さい**committed_kb**、メモリ マネージャーは、コミットされたメモリの量を縮小しようとしています。 **Committed_target_kb**盗難にあったと予約済みのメモリを常に含まれます。 Null を許容しません。|  
|**bpool_visible**|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<br /><br /> プロセス仮想アドレス空間内で直接アクセスできる、バッファー プールの 8 KB バッファーの数。 AWE (Address Windowing Extensions) を使用していない状態で、バッファー プールで目標とするメモリが確保された場合 (bpool_committed = bpool_commit_target)、bpool_visible の値は bpool_committed の値に等しくなります。SQL Server の 32 ビット環境で AWE を使用している場合、bpool_visible は、バッファー プールによって割り当てられている物理メモリへのアクセスに使用される AWE マッピング ウィンドウのサイズを表します。 このマッピング ウィンドウのサイズはプロセスのアドレス空間にバインドされています。したがって、参照可能なメモリの量はコミット済みメモリの量よりも小さくなります。また、データベース ページ以外の目的でメモリを使用する初期コンポーネントによって、さらに小さくなる可能性があります。 bpool_visible の値が小さ過ぎる場合は、メモリ不足のエラーが返されることがあります。|  
|**visible_target_kb**|**int**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 同じ**committed_target_kb**します。 Null を許容しません。|  
|**stack_size_in_bytes**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成された各スレッドの呼び出し履歴のサイズを指定します。 Null を許容しません。|  
|**os_quantum**|**bigint**|非プリエンプティブ タスクのクォンタムを表します (ミリ秒単位)。 クォンタム (秒) = **os_quantum** CPU クロック速度/。 Null を許容しません。|  
|**os_error_mode**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスのエラー モードを指定します。 Null を許容しません。|  
|**os_priority_class**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの優先度クラスを指定します。 Null 値を許容します。<br /><br /> 32 = 通常 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は通常の優先度ベース (= 7) で起動しています)。<br /><br /> 128 = 高 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は高い優先度ベースで実行しています。  (=13).)<br /><br /> 詳細については、「 [priority boost サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md)」を参照してください。|  
|**max_workers_count**|**int**|作成可能なワーカーの最大数を表します。 Null を許容しません。|  
|**scheduler_count**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス内で構成されたユーザー スケジューラの数を表します。 Null を許容しません。|  
|**scheduler_total_count**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のスケジューラの総数を表します。 Null を許容しません。|  
|**deadlock_monitor_serial_number**|**int**|現在のデッドロック監視シーケンスの ID を指定します。 Null を許容しません。|  
|**sqlserver_start_time_ms_ticks**|**bigint**|表す、 **ms_tick**数と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最後に起動します。 現在の ms_ticks 列と比較します。 Null を許容しません。|  
|**sqlserver_start_time**|**datetime**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が最後に起動された日時を指定します。 Null を許容しません。|  
|**affinity_type**|**int**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 現在使用中のサーバー CPU プロセス関係の種類を指定します。 Null を許容しません。 詳細については、次を参照してください。 [ALTER SERVER CONFIGURATION &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)します。<br /><br /> 1 = MANUAL<br /><br /> 2 = AUTO|  
|**affinity_type_desc**|**varchar(60)**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> について説明します、 **affinity_type**列。 Null を許容しません。<br /><br /> MANUAL = 少なくとも 1 台の CPU に関係が設定されています。<br /><br /> AUTO = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は CPU 間で自由にスレッドを移動できます。|  
|**process_kernel_time_ms**|**bigint**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スレッドがカーネル モードで費やした合計時間 (ミリ秒)。 この値にはサーバー上のすべてのプロセッサの時間が含まれるため、単一のプロセッサ クロックより大きくなる場合があります。 Null を許容しません。|  
|**process_user_time_ms**|**bigint**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スレッドがユーザー モードで費やした合計時間 (ミリ秒)。 この値にはサーバー上のすべてのプロセッサの時間が含まれるため、単一のプロセッサ クロックより大きくなる場合があります。 Null を許容しません。|  
|**time_source**|**int**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がウォール クロック時間の取得に使用している API を示します。 Null を許容しません。<br /><br /> 0 = QUERY_PERFORMANCE_COUNTER<br /><br /> 1 = MULTIMEDIA_TIMER|  
|**time_source_desc**|**nvarchar(60)**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> について説明します、 **time_source**列。 Null を許容しません。<br /><br /> QUERY_PERFORMANCE_COUNTER =、 [QueryPerformanceCounter](https://go.microsoft.com/fwlink/?LinkId=163095) API がウォール クロック時間を取得します。<br /><br /> MULTIMEDIA_TIMER =、[マルチ メディア タイマー](https://go.microsoft.com/fwlink/?LinkId=163094) API がウォール クロック時間を取得します。|  
|**virtual_machine_type**|**int**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が仮想化環境で実行されているかどうかを示します。  Null を許容しません。<br /><br /> 0 = NONE<br /><br /> 1 = HYPERVISOR<br /><br /> 2 = OTHER|  
|**virtual_machine_type_desc**|**nvarchar(60)**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> について説明します、 **virtual_machine_type**列。 Null を許容しません。<br /><br /> NONE =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が仮想マシン内で実行されていません。<br /><br /> HYPERVISOR = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ハードウェアの支援による仮想化を意味するハイパーバイザー内で実行されています。 Hyper_V ロールがインストールされている場合、ホストの OS で実行されているインスタンスが、ハイパーバイザーで実行されるように、ハイパーバイザーは、OS をホストします。<br /><br /> OTHER = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ハードウェアの支援を必要としない、Microsoft Virtual PC などの仮想マシン内で実行されています。|  
|**softnuma_configuration**|**int**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 方法の NUMA ノードが構成されているを指定します。 Null を許容しません。<br /><br /> 0 = OFF ハードウェアの既定値を示します<br /><br /> 1 = 自動のソフト NUMA<br /><br /> 2 = レジストリを介して手動ソフト NUMA|  
|**softnuma_configuration_desc**|**nvarchar(60)**|**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> ソフト NUMA をオフ = 機能はオフ<br /><br /> =[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ソフト NUMA の NUMA ノードのサイズを自動的に決定します<br /><br /> 手動ソフト NUMA を手動で構成されているを =|
|**process_physical_affinity**|**nvarchar(3072)** |**適用対象:** 以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]します。<br /><br />今後登場する情報です。 |
|**sql_memory_model**|**int**|**適用対象:** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて SP1[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br /><br />によって使用されるメモリ モデルを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリを割り当てることです。 Null を許容しません。<br /><br />1 = コンベンショナル メモリ モデル<br />2 = lock Pages in Memory<br /> 3 = メモリ内の大きなページ|
|**sql_memory_model_desc**|**nvarchar(120)**|**適用対象:** [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて SP1[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。<br /><br />によって使用されるメモリ モデルを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリを割り当てることです。 Null を許容しません。<br /><br />**従来** =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンベンショナル メモリ モデルを使用してメモリを割り当てることができます。 これは、既定の sql メモリ モデル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス アカウントがページのロック メモリの特権で起動中にします。<br />**LOCK_PAGES**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリを割り当てることのメモリ内のページのロックが使用されます。 これは、SQL Server サービス アカウントは、SQL Server の起動中に in Memory 特権のページのロックを所有しているときの既定の sql メモリ マネージャーです。<br /> **LARGE_PAGES**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メモリを割り当てることで大きなページをメモリ内使用します。 SQL Server では、大きなページ アロケーターを使用して、サーバーの起動時に、トレース フラグ 834 をオンにすると、SQL Server サービス アカウントが in Memory 特権のページのロックを所有しているときは、Enterprise edition でのみメモリを割り当てます。|
|**pdw_node_id**|**int**|**適用対象:** [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
|**socket_count** |**int** | **適用対象:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br />システムで使用可能なプロセッサ ソケットの数を指定します。 |  
|**cores_per_socket** |**int** | **適用対象:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br />システム上の 1 つのソケットの使用可能なプロセッサの数を指定します。 |  
|**numa_node_count** |**int** | **適用対象:** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br />システムで使用可能な numa ノードの数を指定します。 この列には、ソフト numa ノードだけでなく、物理 numa ノードが含まれています。 |  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium レベルでは、必要があります、`VIEW DATABASE STATE`データベースの権限。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   

## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  



