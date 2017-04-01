---
title: "システム モニターによるレプリケーションの監視 | Microsoft Docs"
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
  - "パフォーマンスの監視 [SQL Server レプリケーション], システム モニター"
  - "システム モニター [SQL Server], レプリケーション"
  - "パフォーマンス カウンター [SQL Server レプリケーション]"
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# システム モニターによるレプリケーションの監視
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows システム モニターでは、グラフ、棒グラフ、およびレポートを使用して、コンピューターの効率性を評価、識別し、(リソース使用の不均衡、ハードウェアの不足、またはプログラム設計) などの考えられる問題のトラブルシューティングおよび追加のハードウェア要件の計画にすることができます。 詳細については、次を参照してください。 [リソース使用量を監視する (&) #40 です。システム モニターと #41;](../../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)します。  
  
 システム モニターでは、さまざまなプロセスのパフォーマンスについての情報を提供するパフォーマンス オブジェクトおよびカウンターを使用します。 レプリケーション エージェントに関連するカウンターにより、レプリケーション パフォーマンスを計測できます。  
  
|エージェント|パフォーマンス オブジェクト|カウンター|説明|  
|-----------|------------------------|-------------|-----------------|  
|すべてのエージェント|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Agents|実行中|現在実行されているレプリケーション エージェントの数。|  
|スナップショット エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション スナップショット|Snapshot: Delivered Cmds/sec|ディストリビューターに 1 秒間に配信されたコマンド数。|  
|スナップショット エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション スナップショット|Snapshot: Delivered Trans/sec|ディストリビューターに 1 秒間に配信されたトランザクション数。|  
|ログ リーダー エージェント (Log Reader Agent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション ログ リーダー|Logreader:Delivered Cmds/sec|ディストリビューターに 1 秒間に配信されたコマンド数。|  
|ログ リーダー エージェント (Log Reader Agent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション ログ リーダー|Logreader:Delivered Trans/sec|ディストリビューターに 1 秒間に配信されたトランザクション数。|  
|ログ リーダー エージェント (Log Reader Agent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション ログ リーダー|Logreader: Delivery Latency|パブリッシャーでトランザクションが適用されてから、ディストリビューターに配信されるまでの現在のミリ秒単位の経過時間。|  
|ディストリビューション エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication 版|Dist: Delivered Cmds/sec|サブスクライバーに 1 秒間に配信されたコマンド数。|  
|ディストリビューション エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication 版|Dist: Delivered Trans/sec|サブスクライバーに 1 秒間に配信されたトランザクション数。|  
|ディストリビューション エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication 版|Dist: Delivery Latency|トランザクションがディストリビューターに配信されてから、サブスクライバーで適用されるまでの現在のミリ秒単位の経過時間。|  
|[マージ エージェント]|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション マージ|Conflicts/sec|マージ プロセス中に 1 秒間に発生した競合数。|  
|[マージ エージェント]|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション マージ|Downloaded Changes/sec|パブリッシャーからサブスクライバーに 1 秒間にレプリケートされた行数。|  
|[マージ エージェント]|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーション マージ|Uploaded Changes/sec|サブスクライバーからパブリッシャーに 1 秒間にレプリケートされた行数。|  
  
## 参照  
 [監視と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  