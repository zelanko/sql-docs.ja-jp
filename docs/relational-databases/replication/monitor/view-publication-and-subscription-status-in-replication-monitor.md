---
title: "レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ リーダー エージェント, 監視"
  - "マージ エージェント, 監視"
  - "キュー リーダー エージェント, 監視"
  - "パブリケーション [SQL Server レプリケーション], 情報の表示"
  - "スナップショット エージェント, 監視"
  - "ディストリビューション エージェント, 監視"
  - "パフォーマンスの監視 [SQL Server レプリケーション], パブリケーションの状態"
  - "パフォーマンスの監視 [SQL Server レプリケーション], サブスクリプションの状態"
  - "サブスクリプション [SQL Server レプリケーション], 状態の表示"
  - "レプリケーション モニター, パブリケーションおよびサブスクリプションの状態"
ms.assetid: 16590771-9867-463e-a973-36a5c145ac16
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターには、パブリケーションおよびサブスクリプションの状態情報が表示されます。  
  
-   パブリケーションの状態は、そのサブスクリプションの最も優先度の高い状態によって決定されます。 たとえば、あるパブリケーションに対する 1 つのサブスクリプションにエラーが発生し、別のサブスクリプションにはパフォーマンス上の問題がある場合、そのパブリケーションに対してはエラーの状態が表示されます。  
  
-   サブスクリプションの状態は、そのサブスクリプションにサービスを提供するエージェントの状態によって決定されます。 マージ レプリケーションの場合はマージ エージェントです。 トランザクション レプリケーションの場合は、ログ リーダー エージェントまたはディストリビューション エージェントです (優先度の高い方の状態が表示されます。キュー更新サブスクリプションが使用されている場合は、状態はキュー リーダー エージェントによっても決定されます)。 スナップショット レプリケーションの場合は、スナップショット エージェントまたはディストリビューション エージェントです (優先度の高い方の状態が表示されます)。  
  
 以下に、パブリケーションおよびサブスクリプションの状態の値の一覧を示します。 しきい値に達したか、超えた場合にのみ、3 つの状態値が表示されます。  
  
-   有効期限切れサブスクリプション  
  
     この状態値は、すべての種類のレプリケーションに適用されます。 詳細については、次を参照してください。 [しきい値の設定とレプリケーション モニターで警告](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)します。  
  
-   [パフォーマンス クリティカル]  
  
     この状態値は、トランザクション レプリケーションとマージ レプリケーションに適用されます。 詳細については、次を参照してください。 [レプリケーション モニターを使用してパフォーマンスを監視する](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)です。  
  
-   [長期マージ]  
  
     この状態値はマージ レプリケーションに適用されます。 詳細については、次を参照してください。 [レプリケーション モニターを使用してパフォーマンスを監視する](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)です。  
  
 パブリケーションおよびサブスクリプションの状態の他に、マージ レプリケーションではアーティクル レベルの統計が使用できます。この情報は、マージ フェーズの完了までに要する時間、指定されたアーティクルの処理に費やされた時間、サブスクライバーが使用している接続の種類、およびその他の重要な情報についての詳細を提供します。 統計情報は、レプリケーション モニターの [マージ エージェント] ウィンドウに表示されます。 スナップショット レプリケーションおよびトランザクション レプリケーションでは、ディストリビューション エージェントの処理に関する詳細が提供されます。  
  
 **パブリケーションおよびサブスクリプションの状態を表示するには**  
  
-   レプリケーション モニター: [情報を表示し、パブリケーションと #40; のタスクを実行レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  [情報を表示し、サブスクリプションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
  
 **エージェントの詳細情報を表示するには**  
  
-   レプリケーション モニター: [情報を表示し、パブリケーションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)  [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
## パブリケーションの状態の値  
 次の表は、パブリケーションの状態の値と対応するアイコンを優先度順に示しています。  
  
|[状態]|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン:error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "UI アイコン:error")|  
|[パフォーマンス クリティカル]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[失敗したコマンドの再試行]|![UI アイコン:レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "UI アイコン:レプリケーション エージェントの再試行")|  
|OK|なし|  
  
## サブスクリプションの状態値  
 次の表は、サブスクリプションの状態値と対応するアイコンを優先度順に示しています。 サブスクリプションなど、同時に 2 つの状態である可能性が **まもなく期限切れ/期限切れ** と **失敗したコマンドの再試行**; 最高の優先順位のステータスが表示されます。  
  
 状態値 **パフォーマンス クリティカル**, 、**まもなく期限切れ/期限切れ**, 、および **初期化されていない** 警告します。 警告が表示されるとき、レプリケーション モニターにはエージェントが実行中であるかどうかも表示されます。 たとえば、 **[実行中]、[パフォーマンス クリティカル]**という形で状態が表示されます。  
  
### トランザクション サブスクリプション  
  
|[状態]|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン:error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "UI アイコン:error")|  
|[パフォーマンス クリティカル]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[まもなく期限切れ/期限切れ]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[初期化されていないサブスクリプション]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[失敗したコマンドの再試行]|![UI アイコン:レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "UI アイコン:レプリケーション エージェントの再試行")|  
|[実行されていません]|![UI アイコン:レプリケーション エージェントの停止](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "UI アイコン:レプリケーション エージェントの停止")|  
|実行中|![UI アイコン:レプリケーション エージェントの実行](../../../relational-databases/replication/monitor/media/repl-icon-running.png "UI アイコン:レプリケーション エージェントの実行")|  
  
### マージ サブスクリプション  
  
|[状態]|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン:error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "UI アイコン:error")|  
|[パフォーマンス クリティカル]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[長期マージ]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[まもなく期限切れ/期限切れ]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[初期化されていないサブスクリプション]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[失敗したコマンドの再試行]|![UI アイコン:レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "UI アイコン:レプリケーション エージェントの再試行")|  
|[同期中]|![UI アイコン:レプリケーション エージェントの実行](../../../relational-databases/replication/monitor/media/repl-icon-running.png "UI アイコン:レプリケーション エージェントの実行")|  
|同期されていません|![UI アイコン:レプリケーション エージェントの停止](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "UI アイコン:レプリケーション エージェントの停止")|  
  
### スナップショット サブスクリプション  
  
|[状態]|アイコン|  
|------------|----------|  
|[エラー]|![UI アイコン:error](../../../database-engine/availability-groups/windows/media/repl-icon-error.png "UI アイコン:error")|  
|[まもなく期限切れ/期限切れ]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[初期化されていないサブスクリプション]|![UI アイコン:warning](../../../database-engine/availability-groups/windows/media/repl-icon-warn.png "UI アイコン:warning")|  
|[失敗したコマンドの再試行]|![UI アイコン:レプリケーション エージェントの再試行](../../../relational-databases/replication/monitor/media/repl-icon-retry.png "UI アイコン:レプリケーション エージェントの再試行")|  
|[同期中]|![UI アイコン:レプリケーション エージェントの実行](../../../relational-databases/replication/monitor/media/repl-icon-running.png "UI アイコン:レプリケーション エージェントの実行")|  
|同期されていません|![UI アイコン:レプリケーション エージェントの停止](../../../relational-databases/replication/monitor/media/repl-icon-stopped.png "UI アイコン:レプリケーション エージェントの停止")|  
  
## 参照  
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  