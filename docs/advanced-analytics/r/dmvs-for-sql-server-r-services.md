---
title: "SQL Server の Machine Learning のサービスの Dmv |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3643ea0-d9f3-463f-8ece-572127f32a24
caps.latest.revision: "13"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: afb49793e4744afa3d18efa16bd780f28f76edf9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="dmvs-for-sql-server-machine-learning-services"></a>SQL Server の Machine Learning のサービスの Dmv

トピックには、システム カタログ ビューおよび SQL Server での機械学習に関連する Dmv が一覧表示します。

拡張イベントについては、次を参照してください。[機械学習の拡張イベント](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md)です。

> [!TIP]
> 製品チームは、machine learning のセッションおよびパッケージの使用率を監視に使用できるカスタムのレポートが用意されています。 詳細については、次を参照してください。 [Management Studio でカスタム レポートを使用する機械学習の監視](../../advanced-analytics/r/monitor-r-services-using-custom-reports-in-management-studio.md)です。

## <a name="system-configuration-and-system-resources"></a>システム構成とシステム リソース

監視しを使用して外部スクリプトで使用したリソースを分析する[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]システム カタログ ビューおよび Dmv。

+ [ sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)

  ユーザー接続とシステム セッションの両方の情報を返します。 システム セッションは、*session_id* 列を見ることで識別できます。51 以上の値はユーザー接続を、51 未満の値はシステム プロセスです。

+ [sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)

  サーバーで使用されている各システム パフォーマンス カウンターの行を返します。  この情報を使用して、実行されたスクリプトの数、実行されたスクリプトで使用された認証モード、またはインスタンスで発行された R 呼び出しの総数を確認できます。

  次の例は、R スクリプトに関連するカウンターだけを取得します。

  ```SQL
  SELECT * from sys.dm_os_performance_counters WHERE object_name LIKE '%External Scripts%'
  ```

  この DMV によって、インスタンスごとの外部スクリプトの次のカウンターが報告されます。

  + **実行の合計**: ローカルまたはリモートの呼び出しによって開始された外部プロセスの数
  + **並列実行**: スクリプトが含まれている回数、  _@parallel_ 仕様と[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]生成して、並列クエリ プランを使用することが
  + **実行のストリーミング**: ストリーミング機能が呼び出された回数
  + **CC の SQL 実行**: 外部のスクリプトを実行、呼び出しがリモートでインスタンス化され、計算コンテキストとして使用された SQL Server
  + **Implied Auth.ログイン**: を使用して ODBC ループバック呼び出しが行われた回数を超える暗黙の認証ですつまり、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]スクリプト要求を送信するユーザーに代わって呼び出すを実行。
  + **合計実行時間 (ミリ秒)**: 呼び出しと呼び出しの完了までの経過時間
  + **実行エラー**: スクリプトがエラーを報告した回数。 この数には R エラーは含まれません。


+ [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)

  この DMV は、現在外部スクリプトを実行中のワーカー アカウントごとに 1 つの行を報告します。 このワーカー アカウントは、スクリプトを送信しているユーザーの資格情報とは異なることに注意してください。 1 人の Windows ユーザーが複数のスクリプト要求を送信している場合は、そのユーザーからのすべての要求を処理するワーカー アカウントが 1 つだけ割り当てられます。 別の Windows ユーザーが外部スクリプトを実行するためにログオンした場合、要求は別のワーカー アカウントによって処理されます。

  現在実行されているスクリプトがない場合、この DMV は結果を返しません。したがって、もっとも有用のは、実行時間の長いスクリプトを監視することです。 次の値が返されます。

  + **external_script_request_id**: GUID、スクリプトおよび中間結果を格納するために使用する作業ディレクトリの一時的な名前としても使用されます
  + **言語**: などの値`R`外部スクリプトの言語を表す
  + **degree_of_parallelism**: プロセスの並列の数を示す整数が使用されました。
  + **external_user_name**: A スタート パッドのワーカー アカウントなど**SQLRUser01**

+ [sys.dm_external_script_execution_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)

  この DMV は、内部インスタンスに対する外部スクリプトの呼び出しの数を追跡する (製品利用統計情報) を監視するために提供されます。 製品利用統計情報サービスの開始時に[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、特定の machine learning 関数が呼び出されるたびにディスクに基づくカウンターをインクリメントします。

  カウンターは、特定の追跡の関数呼び出しごとに増やされます。 たとえば、 `rxLinMod` が呼び出されて並列で実行された場合、このカウンターは 1 だけ増やされます。
  
  一般に、パフォーマンス カウンターは、それを生成したプロセスがアクティブな間だけ有効です。 したがって、DMV に対するクエリは、実行を停止したサービスの詳細なデータを表示できません。 たとえば、スタート パッドが複数の並列 R ジョブを作成し、それらのジョブが非常に高速で実行された後、Windows ジョブ オブジェクトによってクリーンアップされた場合、DMV にはデータが表示されない可能性があります。
 
  ただし、インスタンスがシャットダウンされた場合でも、この DMV によって追跡されるカウンターは実行状態を維持し、dm_external_script _execution counter の状態はディスクへの書き込みを使用して保持されます。
 
 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] によって使用されるシステム パフォーマンス カウンターの詳細については、「[SQL Server オブジェクトの使用](../../relational-databases/performance-monitor/use-sql-server-objects.md)」を参照してください。

## <a name="resource-governor-views"></a>リソース ガバナー ビュー

リソース ガバナーをサポートするエディションでは、R、または Python のワークロード用の外部リソース プールを作成するとリソースを追跡および管理 en 効果的な方法があります。

+ [sys.resource_governor_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-resource-pools-transact-sql.md)

  リソース プールの現在の状態、現在の構成、および統計に関する情報を返します。

  > [!IMPORTANT]
  > 
  > R Services に追加リソースを割り当てる前に、その他のサーバー サービスに適用するリソース プールを変更する必要があります。

+ [sys.resource_governor_external_resource_pools](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)

  外部リソース プールの現在の構成値を表示する新しいカタログ ビュー。
  Enterprise Edition では、追加の外部リソース プールを構成できます。たとえば、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で実行する R ジョブのリソースを、リモート クライアントのリソースとは別に処理することを決定できます。

  > [!NOTE]
  > 
  > Standard Edition では、外部スクリプトのすべてのジョブは、同じ外部の既定のリソース プール内で実行します。

+ [sys.resource_governor_workload_groups](../../relational-databases/system-catalog-views/sys-resource-governor-workload-groups-transact-sql.md)

  ワークロード グループ統計とワークロード グループの現在の構成を返します。 このビューに参加させる`sys.dm_resource_governor_resource_pools`リソース プール名を取得します。
  外部スクリプトに対しては、ワークロード グループに関連付けられている外部プールの ID を表示する新しい列が追加されています。

+ [sys.dm_resource_governor_external_resource_pool_affinity](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)

  特定のリソース プールに関係付けられているプロセッサとリソースを確認できる新しいシステム カタログ ビュー。

  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のスケジューラごとに 1 行のデータを返します。各スケジューラは個別のプロセッサにマップされています。 このビューは、スケジューラの状況の監視やランナウェイ タスクの特定に使用できます。

  既定の構成では、ワークロード プールは自動的にプロセッサに割り当てられるため、返されるアフィニティ値はありません。

  アフィニティ スケジュールは、リソース プールを、指定された ID によって識別される [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] スケジュールにマップします。 これらの Id の値にマップで、`scheduler_id`内の列`sys.dm_os_schedulers`です。


> [!NOTE] 
> 
> リソース プールの構成とカスタマイズを行う機能は Enterprise Edition と Developer Edition でのみ使用できますが、既定のプールと DMV はすべてのエディションで使用できます。 そのため、Standard Edition でこれらの Dmv を使用するには、外部スクリプトのジョブに対するリソース cap を決定します。

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスの監視の一般的な情報については、「[カタログ ビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)」と「[リソース ガバナー関連の動的管理ビュー](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)」を参照してください。

## <a name="monitoring-script-execution"></a>監視スクリプトの実行

実行される R と Python スクリプト[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]によって開始された、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]インターフェイスです。 ただし、スタート パッドは、リソースを適切に管理する Microsoft 提供のセキュリティで保護されたサービスとみなされているため、リソース管理の対象ではなく、別に監視されることもありません。

使用して、スタート パッド サービスの下で実行される個々 のスクリプトは、管理、 [Windows ジョブ オブジェクト](https://msdn.microsoft.com/library/windows/desktop/ms684161.aspx)です。 ジョブ オブジェクトによって、プロセス グループをユニットとして管理できます。 各ジョブ オブジェクトは階層的であり、それに関連付けられているすべてのプロセスの属性を制御します。 ジョブ オブジェクトに対して実行される操作は、そのジョブ オブジェクトに関連付けられているすべてのプロセスに影響します。

したがって、オブジェクトに関連付けられている 1 つのジョブを終了する必要がある場合は、関連するすべてのプロセスも終了されることに注意してください。 Windows ジョブ オブジェクトに割り当てられている R スクリプトを実行しているときに、終了する必要がある関連する ODBC ジョブをそのスクリプトが実行している場合は、親の R スクリプトのプロセスも終了します。

並列処理を使用する外部のスクリプトを開始する場合、1 つの Windows ジョブ オブジェクトはすべての並列の子プロセスを管理します。

プロセスがジョブで実行されているかどうかを調べるには、`IsProcessInJob` 関数を使用します。

## <a name="next-steps"></a>次の手順

[Machine Learning ソリューションの管理と監視](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)
