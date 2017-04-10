---
title: "SQL Server R サービス用の Dmv | Microsoft Docs"
ms.custom: ""
ms.date: "11/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b3643ea0-d9f3-463f-8ece-572127f32a24
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# SQL Server R サービス用の Dmv

システム カタログ ビューおよび Dmv に関連するトピックが一覧表示 [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]します。 


拡張イベントについては、次を参照してください。 [SQL Server の R のサービスの拡張イベント](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md)です。

> [!TIP]
> 製品チームは、R のサービスのセッションとパッケージを監視に使用できるカスタム レポートを提供しています。 詳細については、次を参照してください。 [Management Studio でカスタム レポートを使用して R サービスの監視](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md)します。
> 

## <a name="system-configuration-and-system-resources"></a>システム構成、およびシステム リソース

監視しを使用して、R スクリプトで使用されているリソースを分析する [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] システム カタログ ビューおよび Dmv。


**全般**
+ [ sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  ユーザー接続とシステム セッションの両方の情報を返します。 参照してシステム セッションを識別する、 *session_id* 列; より大きい値と等しい 51、またはユーザー接続 51 がシステム プロセスより低い場合の値。 



+ [sys.dm_os_performance_counters (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  サーバーで使用されている各システムのパフォーマンス カウンターの行を返します。  この情報を使用するにはどのように多くのスクリプトの実行を表示するスクリプトがどの認証モード、または全体のインスタンス上で実行された R 呼び出しの数を使用して実行されました。

  この例では、R スクリプトに関連するカウンターだけを取得します。

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%Extended Scripts%'
  ```

  インスタンスごとの外部のスクリプトには、この DMV では、次のカウンターがレポートされます。

  + **実行の合計**: R プロセスの数は、ローカルまたはリモートの呼び出しによって起動
  + **並列実行**: スクリプトが含まれている回数、 @parallel 仕様と [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 生成し、並列クエリ プランを使用することができました
  + **実行のストリーミング**: ストリーミング機能が呼び出された回数。 
  + **CC の SQL 実行**: 数の R スクリプトの呼び出しがリモートでインスタンス化、および計算コンテキストとして使用される SQL Server の実行 
  + **暗黙の認証ログイン**: を使用して ODBC ループバック呼び出しが行われた回数を超える暗黙の認証、つまり、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] スクリプトの要求を送信するユーザーの代わりに、呼び出しの実行
  + **合計実行時間 (ミリ秒)**: 呼び出しと呼び出しの完了までの経過時間。
  + **実行エラー**: スクリプトにエラーが報告された時間数。 この数には、R のエラーは含まれません。


+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  この DMV では、外部のスクリプトを現在実行中のワーカー アカウントごとに 1 つの行を報告します。 このワーカー アカウントは、スクリプトを送信するユーザーの資格情報と異なることに注意してください。 単一の Windows ユーザーは、スクリプトの複数の要求を送信した場合、複数のワーカー アカウントがそのユーザーからのすべての要求を処理する割り当てられます。 外部スクリプトを実行する別の Windows ユーザーをログオンした場合、個別のワーカー アカウントによって、要求を処理とします。 
  この DMV で結果が返されない場合、スクリプトは現在実行されていません。したがって、実行時間の長いスクリプトを監視するため便利です。 これらの値が返されます。
  + **external_script_request_id**: GUID はスクリプトや中間結果を格納するために使用する作業ディレクトリの一時的な名前としても使用します。  
  + **言語**: などの値 `R` 外部スクリプトの言語を表します。
  + **degree_of_parallelism**: プロセスの並列の数を示す整数を使用します。 
  + **external_user_name**: SQLRUser01 などのスタート パッド ワーカー アカウントです。 
  

+ [sys.dm_external_script_execution_stats (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  この DMV は、内部インスタンスに対する R 呼び出しの数を追跡する (製品利用統計情報) を監視するために提供されます。 製品利用統計情報サービスが開始 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] は、ディスク ベースのカウンターをインクリメントするには、特定の R 関数が呼び出されるたびにします。

  このカウンターは、関数の呼び出しごとにインクリメントされます。 たとえば、 `rxLinMod` が呼び出されて並列で実行された場合、このカウンターは 1 だけ増やされます。
  
  一般に、パフォーマンス カウンターは、それを生成したプロセスがアクティブな間だけ有効です。 したがって、DMV に対するクエリは、実行を停止したサービスの詳細なデータを表示できません。 たとえば、スタート パッドは、複数の並列 R のジョブを作成して、非常に高速に実行され、Windows ジョブ オブジェクトによってクリーンアップのまだ、する場合、DMV 可能性があります、データは表示されません。
 
  しかし、この DMV で追跡するカウンターが保護して実行し dm_external_script _execution カウンターは、インスタンスがシャット ダウンした場合でも、ディスクに書き込みに使用では保存の状態。
 
 使用するシステムのパフォーマンス カウンターの詳細については [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], を参照してください [を使用して SQL Server オブジェクト](../../relational-databases/performance-monitor/use-sql-server-objects.md)します。

**リソース ガバナー ビュー**

+ [sys.resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  リソース プールの現在の状態、現在の構成、および統計に関する情報を返します。

  > [!IMPORTANT]
  > 
  > R のサービスにその他のリソースを割り当てることができます前に、他のサーバー サービスに適用されるリソース プールを変更する必要があります。


+ [sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  外部のリソース プールの現在の構成値を表示する新しいカタログ ビュー。
  Enterprise Edition では、その他の外部リソースのプールを構成できます。 たとえば、R のジョブで実行するためのリソースを処理することが [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] リモート クライアントから送られたものから個別にします。 

  > [!NOTE]
  > 
  > Standard Edition では、すべての R のジョブは同じ外部の既定のリソース プールで実行されます。

+ [sys.resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  ワークロード グループ統計とワークロード グループの現在の構成を返します。 このビューを sys.dm_resource_governor_resource_pools と結合すると、リソース プール名を取得できます。
  外部スクリプトには、新しい列が追加されました、ワークロード グループに関連付けられている外部のプールの id を表示します。 


+ [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  新しいシステム カタログを表示できるようにするプロセッサとは、特定のリソース プールに関連付けられリソースを参照してください。

  スケジューラごとに 1 行を返す [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 各スケジューラが個別のプロセッサに割り当てられています。 このビューは、スケジューラの状況の監視やランナウェイ タスクの特定に使用できます。

  既定の構成 [ワークロード プールは自動的にプロセッサに割り当てられ、したがって、返される値のアフィニティはありません。

  アフィニティ スケジュールにリソース プールをマップする、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 、指定した Id によって識別されます。 これらの Id は、sys.dm_os_schedulers (TRANSACT-SQL) の scheduler_id column 内の値にマップします。


> [!NOTE] 
> 
> 構成し、リソース プールをカスタマイズする機能は Enterprise でのみ使用可能なと開発者のエディション、既定のプールだけでなく、Dmv はすべてのエディションで使用できます。 したがって、R のジョブのリソース設定の決定、Standard Edition でこれらの Dmv を使用できます。 

監視の全般については [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスを参照してください [カタログ ビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) と [リソース ガバナー関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)します。

## <a name="r-script-execution-and-monitoring"></a>R スクリプトの実行と監視

R スクリプトで実行されている [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] によって開始された、 [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] インターフェイスです。 ただし、スタート パッドは、管理されるようにリソースを適切に管理する Microsoft によって提供されるセキュリティで保護されたサービスを使用することが前提とは別に、監視リソースではありません。

スタート パッド サービスで実行される個々 の R スクリプトの管理を使用して、 [Windows ジョブ オブジェクト](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx)します。 ジョブ オブジェクトでは、ユニットとして管理するプロセスのグループを使用します。 各ジョブ オブジェクトは、階層的し、それに関連付けられているすべてのプロセスの属性を制御します。 ジョブ オブジェクトに対して実行される操作では、ジョブ オブジェクトに関連付けられているすべてのプロセスに影響します。 

したがって、オブジェクトに関連付けられている 1 つのジョブを終了する必要がある場合はするすべての関連するプロセスも終了することに注意してください。 Windows ジョブ オブジェクトに割り当てられている R スクリプトを実行するスクリプトを終了する必要があります関連 ODBC ジョブを実行する場合は、親の R スクリプトのプロセスも終了します。 

並列処理を使用する R スクリプトを開始する場合、1 つの Windows ジョブ オブジェクトは、すべての並列の子プロセスを管理します。

調べるには、プロセスが、ジョブで実行されているかどうかを使用して、 `IsProcessInJob` 関数です。

## <a name="see-also"></a>参照
[管理と監視](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)

