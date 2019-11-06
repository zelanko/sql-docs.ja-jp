---
title: アプライアンスの監視 - Analytics Platform System |Microsoft Docs
description: このアプライアンスの監視のガイドでは、ツールと Analytics Platform System appliance の監視のタスクについて説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cb25a5eccd1e77f08cedc74ad8042e0dc573605c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961508"
---
# <a name="appliance-monitoring-for-analytics-platform-system"></a>Analytics Platform System のアプライアンスの監視
このアプライアンスの監視のガイドでは、ツールと Analytics Platform System appliance の監視のタスクについて説明します。  
  
## <a name="Basics"></a>監視機能とツール  
値と、SQL Server PDW アプライアンスで監視できる情報があります。 など、次の一般的なタスクを監視します。  
  
-   SQL Server PDW によって発行されたすべてのアラートを確認します。  
  
-   故障したハードウェアを監視します。  
  
-   ネットワーク接続の問題を監視します。  
  
-   クエリの処理中にユーザーに返されるエラーを確認します。  
  
-   現在アクティブなセッションとクエリの数を表示します。  
  
-   読み込み、バックアップ、および復元の状態を確認します。  
  
### <a name="appliance-monitoring-tools"></a>アプライアンスの監視ツール  
アプライアンスの監視に使用できる複数のツールがあります。  
  
管理コンソール  
SQL Server PDW 管理コンソールをしています これは web ベースのツールで、クエリ、読み込み、バックアップと復元、ロック、セッション、アラート、およびアプライアンスの状態に関する情報が表示されます。 アプライアンス; で、管理コンソールを実行します。ユーザーは、Internet explorer の管理コンソールに接続します。 詳細については、以下をご覧ください。  
  
-   [アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![PDW 管理コンソールの警告](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
システム ビュー  
SQL Server PDW には、アプライアンスの正常性、状態、およびパフォーマンスに関する詳細情報を取得するための包括的なシステム ビューが含まれています。 タスクを監視するためのシステム ビューの一覧を参照してください。  
  
-   [システム ビューを使用してアプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW では、広範な Systems Center Operations Manager 統合が。 SQL Server PDW 用の管理パックは、無料でダウンロードとして入手できます。 System Center を使用して、SQL Server PDW を監視する方法の詳細については、次を参照してください。  
  
-   [System Center Operations Manager を使用して、アプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
カスタム ソリューション  
状況の監視ツール、データ センターでは System Center が利用できない場合監視できますアプライアンス サード パーティ製の監視ソリューションを使用しています。 外部のソフトウェアのエージェントのインストールが、PDW でサポートされていません現在がほとんどの監視ソリューションをサポートして Transact\-SQL 統合、システム管理者が直接 Transact を実装できるように\-PDW に対して SQL クエリアプライアンスです。  
  
監視ソリューションでは、直接 Transact をサポートしていない場合\-SQL クエリ、または監視のツールがないし、アラートが発生したときに電子メールを送信するなどの監視タスクを実行するスクリプトを使用することができます。  TechNet wiki には、スクリプト化された監視ソリューションの例が含まれています。  
  
-   [Power Shell が SQL Server PDW の監視の例](https://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>監視タスクに関連  
  
|監視タスク|説明|  
|-------------------|---------------|  
|アプライアンスの管理コンソールを使用して監視します。|[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|アプライアンスのシステム ビューを使用して監視します。|[システム ビューを使用してアプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)|  
|System Center を使用して、アプライアンスを監視します。|[System Center Operations Manager を使用して、アプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|アプライアンスの状態を監視します。|[モニターのアプライアンスの正常性状態&#40;Analytics Platform System&#41;](monitor-appliance-health-state.md)|  
|ハートビートを監視します。|[テレメトリのフィードバックをマイクロソフトに送信&#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|アプライアンスの警告を追跡します。|[アプライアンスの警告を追跡&#40;Analytics Platform System&#41;](track-appliance-alerts.md)|  
|容量が使用されているかを決定します。|[容量使用率を表示&#40;Analytics Platform System&#41;](view-capacity-utilization.md)|  
|アプライアンスをポーリングする頻度を決定します。|[ポーリング間隔の決定&#40;Analytics Platform System&#41;](determine-polling-frequency.md)|  
|クラスターの障害が発生したときに特定のクラスター ノードが失敗しました。|[特定のクラスター ノードが失敗した&#40;Analytics Platform System&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>関連項目  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンスの管理タスク&#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
