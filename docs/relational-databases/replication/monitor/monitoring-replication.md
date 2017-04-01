---
title: "監視 (レプリケーション) | Microsoft Docs"
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
  - "パフォーマンスの監視 [SQL Server レプリケーション]、レプリケーションの監視について"
  - "トランザクション レプリケーション、監視"
  - "監視 [SQL Server レプリケーション]"
  - "マージ レプリケーションの監視 [SQL Server レプリケーション]"
  - "スナップショット レプリケーション [SQL Server]、監視"
  - "レプリケーション [SQL Server]、監視"
  - "レプリケーションの管理、監視"
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# 監視 (レプリケーション)
  レプリケーション トポロジの監視は、レプリケーションの配置における重要な側面です。 レプリケーション処理は分散環境で行われるため、レプリケーションに関連するすべてのコンピューターについてその利用状況と状態を追跡することが不可欠です。 レプリケーションの監視には以下のツールを使用できます。  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニター  
  
     レプリケーションの監視を行うにあたり、最も重要なツールがレプリケーション モニターです。すべてのレプリケーションの利用状況がパブリッシャー関連のビューで表示されます。 詳しくは、「 [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)」をご覧ください。  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] レプリケーション モニターにアクセスを提供します。 また、ログ リーダー エージェント、スナップショット エージェント、マージ エージェント、およびディストリビューション エージェントの各エージェントを開始および停止したり、現在の状態や各エージェントによってログに記録された最後のメッセージを表示することができます。 詳細については、次を参照してください。 [レプリケーション エージェントの監視](../../../relational-databases/replication/monitor/monitor-replication-agents.md)します。  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] およびレプリケーション管理オブジェクト (RMO)  
  
     どちらのインターフェイスでも、ディストリビューターからすべての種類のレプリケーションを監視できます。 マージ レプリケーションでは、サブスクライバーからレプリケーションを監視することもできます。  
  
-   レプリケーション エージェント イベントに対する警告  
  
     レプリケーションには、レプリケーション エージェント イベントに対する定義済みの警告が多数用意されています。また、必要に応じて追加の警告を作成することもできます。 警告を使用して、イベントに対する自動応答のトリガーを起動したり、管理者に通知することができます。 詳細については、次を参照してください。 [レプリケーション エージェント イベントに対する警告を使用する](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)です。  
  
-   システム モニター  
  
     システム モニターには、レプリケーションに関するさまざまなカウンターが表示されるので、パフォーマンスを監視する場合に便利です。 詳細については、「 [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md)」を参照してください。  
  
## 参照  
 [管理と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/administration/administration-replication.md)   
 [レプリケーション管理の推奨事項](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  