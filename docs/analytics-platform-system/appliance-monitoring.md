---
title: アプライアンス (Analytics Platform System) の監視
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 253864fb-9178-41d2-a0ae-5dd9fd0a4fda
caps.latest.revision: 25
ms.openlocfilehash: f361b56581fd5a8dadb4ff41c387074abc006879
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="appliance-monitoring"></a>アプライアンスの監視
このアプライアンス監視ガイドは、SQL Server PDW アプライアンスを監視するためのタスクとツールについて説明します。  
  
## <a name="Basics"></a>監視の基本とツール  
値と、SQL Server PDW アプライアンスで監視できる情報は、広範なです。 たとえば、次は一般的なタスクを監視します。  
  
-   SQL Server PDW によって発行された任意のアラートを確認します。  
  
-   故障したハードウェアを監視します。  
  
-   ネットワーク接続の問題を監視します。  
  
-   クエリの処理中のユーザーに返されるエラーを確認します。  
  
-   現在アクティブなセッションおよびクエリの数を表示します。  
  
-   読み込み、バックアップ、および復元の状態を確認してください。  
  
### <a name="appliance-monitoring-tools"></a>アプライアンスの監視ツール  
アプライアンスの監視に使用できる複数のツールがあります。  
  
管理コンソール  
SQL Server PDW 管理コンソールがあります。 これは、クエリ、読み込み、バックアップと復元、ロック、セッション、アラート、およびアプライアンスの状態に関する情報を表示する web ベースのツールです。 管理者コンソールを実行してアプライアンスです。ユーザーは、Internet Explorer で、管理コンソールに接続します。 詳細については、以下をご覧ください。  
  
-   [管理者コンソールを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
![PDW 管理コンソールの警告](./media/appliance-monitoring/SQL_Server_PDW_AdminConsol_Queries.png "SQL_Server_PDW_AdminConsol_Queries")  
  
システム ビュー  
SQL Server PDW には、アプライアンスの正常性、状態、およびパフォーマンスに関する詳細情報を取得するための包括的なシステム ビューが含まれています。 タスクを監視するためのシステム ビューの一覧を参照してください。  
  
-   [システム ビューを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-system-views.md)  
  
System Center Operations Manager (SCOM)  
SQL Server PDW では、広範な Systems Center Operations Manager 統合があります。 SQL Server PDW 用の管理パックは、無料でダウンロードとして提供されます。 System Center を使用して、SQL Server PDW を監視する方法の詳細については、次を参照してください。  
  
-   [System Center Operations Manager を使用してアプライアンスを監視する&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
カスタム ソリューション  
状況の監視ツール、データ センターで System Center が利用できない場合を監視できますアプライアンス サード パーティ製の監視ソリューションを使用しています。 外部のソフトウェアのエージェントのインストールは現在サポートされていません、PDW ではほとんどの監視ソリューションをサポートして Transact\-SQL integration、システム管理者が直接 Transact を実装できるように\-PDW に対して SQL クエリアプライアンスです。  
  
監視ソリューションでは、直接 Transact をサポートしていない場合\-SQL クエリ、またはする監視ツールがないし、アラートが発生したときに電子メールを送信するなどの監視タスクを実行するスクリプトを使用することができます。  TechNet wiki には、スクリプト化された監視ソリューションの例が含まれています。  
  
-   [パワー シェルを SQL Server PDW の監視の例](http://go.microsoft.com/fwlink/?LinkId=248020)  
   
## <a name="Tasks"></a>関連するタスクの監視  
  
|監視タスク|Description|  
|-------------------|---------------|  
|管理者コンソールを使用してアプライアンスを監視します。|[管理者コンソールを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-the-admin-console.md)|  
|システム ビューを使用してアプライアンスを監視します。|[システム ビューを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-system-views.md)|  
|System Center を使用してアプライアンスを監視します。|[System Center Operations Manager を使用してアプライアンスを監視する&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)|  
|アプライアンスの状態を監視します。|[モニター アプライアンスの正常性状態&#40;分析プラットフォーム システム&#41;](monitor-appliance-health-state.md)|  
|ハートビートを監視します。|[製品利用統計情報のフィードバックをマイクロソフトに送信&#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)|  
|アプライアンスのアラートを追跡します。|[アプライアンスのアラートを追跡&#40;分析プラットフォーム システム&#41;](track-appliance-alerts.md)|  
|キャパシティの量が使用されているかを決定します。|[容量使用率を表示&#40;分析プラットフォーム システム&#41;](view-capacity-utilization.md)|  
|アプライアンスをポーリングする頻度を決定します。|[ポーリングの頻度を決定&#40;分析プラットフォーム システム&#41;](determine-polling-frequency.md)|  
|クラスターの障害が発生したときに決定するクラスター ノードに失敗しました。|[クラスター ノードでエラーを特定&#40;分析プラットフォーム システム&#41;](determine-which-cluster-node-failed.md)|  


<!-- MISSING LINKS |Monitor loads.|[Monitor Loads &#40;SQL Server PDW&#41;](../sqlpdw/monitor-loads-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor backups and restores.|[Monitor Backups and Restores &#40;SQL Server PDW&#41;](../sqlpdw/monitor-backups-and-restores-sql-server-pdw.md)|  -->  
<!-- MISSING LINKS |Monitor the active queries.|[Monitoring Active Queries &#40;SQL Server PDW&#41;](../sqlpdw/monitoring-active-queries-sql-server-pdw.md)|  -->  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS [Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
[アプライアンスの管理タスク&#40;分析プラットフォーム システム&#41;](appliance-management-tasks.md)  
  
