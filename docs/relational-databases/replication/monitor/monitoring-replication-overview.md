---
title: "レプリケーションの監視 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- Replication Monitor, about Replication Monitor
ms.assetid: 81f596d2-27a5-489d-bf8d-0f4361decd02
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2dc65ac3d6356ff9c2a69d0a30a8c5a1ecc76782
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="monitoring-replication-overview"></a>レプリケーションの監視の概要
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor is a graphical tool that allows you to monitor the overall health of a replication topology. レプリケーション モニターは、パブリケーションとサブスクリプションの状態とパフォーマンスに関する詳細な情報を提供し、以下のような一般的な疑問に対する回答を得ることができます。  
  
-   レプリケーション システムは正常に動作していますか。  
  
-   処理の遅いサブスクリプションはどれですか。  
  
-   トランザクション サブスクリプションでどのくらい未処理のデータが残っていますか。  
  
-   トランザクション レプリケーションにおいて、コミットされたトランザクションがサブスクライバーに伝達されるまでどれくらいの時間が必要ですか。  
  
-   なぜマージ サブスクリプションの処理が遅いのですか。  
  
-   なぜエージェントが実行されないのですか。  
  
 レプリケーションを監視するためには、ユーザーが、ディストリビューターで **sysadmin** 固定サーバー ロールのメンバーか、ディストリビューション データベースの **replmonitor** 固定データベース ロールのメンバーであることが必要です。 システム管理者は、 **replmonitor** ロールに任意のユーザーを追加することが可能で、これによりユーザーがレプリケーション モニターでレプリケーションの動作状況を表示できるようになります。ただし、レプリケーションを管理することはできません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 以下のトピックでは、レプリケーション モニターの機能について説明しています。  
  
 [レプリケーション モニター インターフェイスの概要](../../../relational-databases/replication/monitor/overview-of-the-replication-monitor-interface.md)  
 レプリケーション モニターの各ウィンドウおよびタブと、上記の疑問に対する回答を得る方法について説明しています。  
  
 [レプリケーション モニターの開始](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)  
 レプリケーション モニターを起動する方法について説明します。  
  
 [管理者以外のユーザーがレプリケーション モニターを使用できるようにする](../../../relational-databases/replication/monitor/allow-non-administrators-to-use-replication-monitor.md)  
 レプリケーション モニターを使用できるように、管理者以外のユーザーにアクセス許可を割り当てる方法について説明します。  
  
 [レプリケーション モニターのパブリッシャーの追加および削除](../../../relational-databases/replication/monitor/add-and-remove-publishers-from-replication-monitor.md)  
 レプリケーション モニターでパブリッシャーを追加または削除する方法について説明します。  
  
 [レプリケーション モニターのデータの更新](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md)  
 レプリケーション モニターでデータを最新の情報に更新する方法について説明します。  
  
 [レプリケーション モニターを使用したパフォーマンスの監視](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)  
 パフォーマンスしきい値の設定方法など、レプリケーション モニターでパフォーマンスを監視する方法を説明しています。 マージ レプリケーションに対するアーティクル レベルでの統計に関する情報では、処理を詳細に説明しています。  
  
 [トランザクション レプリケーションの待機時間の計測および接続の検証](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
 トランザクション レプリケーション トポロジのパフォーマンスを計測するトレーサー トークンについて説明しています。  
  
 [レプリケーション エージェントの監視](../../../relational-databases/replication/monitor/monitor-replication-agents.md)  
 各レプリケーション エージェントに関する情報を見つける方法について説明しています。  
  
 [レプリケーション モニターのしきい値と警告の設定](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
 レプリケーション モニターで設定可能な警告としきい値について説明しています。 トポロジに対する警告を有効にすることをお勧めします。この警告を有効にすると、状態やパフォーマンスに関する情報をタイムリーに受け取ることができます。  
  
 [キャッシュ、更新、およびレプリケーション モニターのパフォーマンス](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md)  
 パフォーマンスを向上させるために、レプリケーション モニターがデータと計算をキャッシュする方法について説明しています。また、ユーザー インターフェイスの更新がキャッシュの更新とどのように関係しているかについても説明しています。  
  
 [レプリケーション モニターでのパブリケーションおよびサブスクリプションの状態の表示](../../../relational-databases/replication/monitor/view-publication-and-subscription-status-in-replication-monitor.md)  
 レプリケーション モニターを使用して、パブリケーションやサブスクリプションの状態情報を表示する方法について説明します。  
  
 [パブリッシャーの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)  
 レプリケーション モニターを使用して、パブリッシャーの情報を表示してタスクを実行する方法について説明します。  
  
 [パブリケーションの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)  
 レプリケーション モニターを使用して、パブリケーションの情報を表示してタスクを実行する方法について説明します。  
  
 [パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)  
 レプリケーション モニターを使用して、パブリケーションに関連付けられたエージェントの情報を表示してタスクを実行する方法について説明します。  
  
 [サブスクリプションの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)  
 レプリケーション モニターを使用して、サブスクリプションの情報を表示してタスクを実行する方法について説明します。  
  
 [サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)  
 レプリケーション モニターを使用して、サブスクリプションに関連付けられたエージェントの情報を表示してタスクを実行する方法について説明します。  
  
  
