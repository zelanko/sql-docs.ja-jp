---
title: "レプリケーションの監視 | Microsoft Docs"
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
  - "パフォーマンスの監視 [SQL Server レプリケーション], レプリケーション モニター"
  - "レプリケーション モニター, レプリケーション モニターについて"
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# レプリケーションの監視
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターは、レプリケーション トポロジの全体的なヘルスを監視できるようにするグラフィカル ツールです。 レプリケーション モニターは、パブリケーションとサブスクリプションの状態とパフォーマンスに関する詳細な情報を提供し、以下のような一般的な疑問に対する回答を得ることができます。  
  
-   レプリケーション システムは正常に動作していますか。  
  
-   処理の遅いサブスクリプションはどれですか。  
  
-   トランザクション サブスクリプションでどのくらい未処理のデータが残っていますか。  
  
-   トランザクション レプリケーションにおいて、コミットされたトランザクションがサブスクライバーに伝達されるまでどれくらいの時間が必要ですか。  
  
-   なぜマージ サブスクリプションの処理が遅いのですか。  
  
-   なぜエージェントが実行されないのですか。  
  
 ユーザーのレプリケーションを監視するのメンバーである必要があります、 **sysadmin** 固定サーバー ロールのメンバーか、ディストリビューター、 **replmonitor** ディストリビューション データベースの固定データベース ロール。 システム管理者がすべてのユーザーを追加、 **replmonitor** 役割は、レプリケーション モニターでレプリケーションの利用状況を表示するには、そのユーザーは、ただし、ユーザーがレプリケーションを管理できません。  
  
## このセクションの内容  
 以下のトピックでは、レプリケーション モニターの機能について説明しています。  
  
 [レプリケーション モニターのインターフェイスの概要](../../../relational-databases/replication/monitor/overview-of-the-replication-monitor-interface.md)  
 レプリケーション モニターの各ウィンドウおよびタブと、上記の疑問に対する回答を得る方法について説明しています。  
  
 [レプリケーション モニターの開始](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)  
 レプリケーション モニターを起動する方法について説明します。  
  
 [Allow Non-Administrators to Use Replication Monitor](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
 レプリケーション モニターを使用できるように、管理者以外のユーザーにアクセス許可を割り当てる方法について説明します。  
  
 [レプリケーション モニターのパブリッシャーの追加および削除](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)  
 レプリケーション モニターでパブリッシャーを追加または削除する方法について説明します。  
  
 [レプリケーション モニターのデータの更新](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md)  
 レプリケーション モニターでデータを最新の情報に更新する方法について説明します。  
  
 [レプリケーション モニターを使用したパフォーマンスの監視](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
 パフォーマンスしきい値の設定方法など、レプリケーション モニターでパフォーマンスを監視する方法を説明しています。 マージ レプリケーションに対するアーティクル レベルでの統計に関する情報では、処理を詳細に説明しています。  
  
 [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
 トランザクション レプリケーション トポロジのパフォーマンスを計測するトレーサー トークンについて説明しています。  
  
 [レプリケーション エージェントの監視](../../../relational-databases/replication/monitor/monitor-replication-agents.md)  
 各レプリケーション エージェントに関する情報を見つける方法について説明しています。  
  
 [Set Thresholds and Warnings in Replication Monitor](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
 レプリケーション モニターで設定可能な警告としきい値について説明しています。 トポロジに対する警告を有効にすることをお勧めします。この警告を有効にすると、状態やパフォーマンスに関する情報をタイムリーに受け取ることができます。  
  
 [キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)  
 パフォーマンスを向上させるために、レプリケーション モニターがデータと計算をキャッシュする方法について説明しています。また、ユーザー インターフェイスの更新がキャッシュの更新とどのように関係しているかについても説明しています。  
  
 [レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示](../../../relational-databases/replication/monitor/view-publication-and-subscription-status-in-replication-monitor.md)  
 レプリケーション モニターを使用して、パブリケーションやサブスクリプションの状態情報を表示する方法について説明します。  
  
 [情報を表示し、パブリッシャーおよび #40; のタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 レプリケーション モニターを使用して、パブリッシャーの情報を表示してタスクを実行する方法について説明します。  
  
 [情報を表示し、パブリケーションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 レプリケーション モニターを使用して、パブリケーションの情報を表示してタスクを実行する方法について説明します。  
  
 [情報を表示し、パブリケーションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)  
 レプリケーション モニターを使用して、パブリケーションに関連付けられたエージェントの情報を表示してタスクを実行する方法について説明します。  
  
 [情報を表示し、サブスクリプションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 レプリケーション モニターを使用して、サブスクリプションの情報を表示してタスクを実行する方法について説明します。  
  
 [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)  
 レプリケーション モニターを使用して、サブスクリプションに関連付けられたエージェントの情報を表示してタスクを実行する方法について説明します。  
  
  