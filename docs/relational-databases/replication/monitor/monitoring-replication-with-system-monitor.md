---
title: "システム モニターによるレプリケーションの監視 | Microsoft Docs"
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
- monitoring performance [SQL Server replication], System Monitor
- System Monitor [SQL Server], replication
- performance counters [SQL Server replication]
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 54dd40c16f8ee720f32b6775c54e7245eb5ed978
ms.lasthandoff: 04/11/2017

---
# <a name="monitoring-replication-with-system-monitor"></a>システム モニターによるレプリケーションの監視
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows のシステム モニターにより、グラフ、図およびレポートを使って、使用しているコンピューターの効率の評価、考えられる問題 (リソース使用の不均衡、ハードウェアの不足、プログラム設計の問題など) の識別とトラブルシューティング、およびハードウェアの追加計画の作成を行うことができます。 詳細については、「[リソースの利用状況の監視 &#40;システム モニター&#41;](../../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)」を参照してください。  
  
 システム モニターでは、さまざまなプロセスのパフォーマンスについての情報を提供するパフォーマンス オブジェクトおよびカウンターを使用します。 レプリケーション エージェントに関連するカウンターにより、レプリケーション パフォーマンスを計測できます。  
  
|エージェント|パフォーマンス オブジェクト|カウンター|説明|  
|-----------|------------------------|-------------|-----------------|  
|すべてのエージェント|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Agents|実行中|現在実行されているレプリケーション エージェントの数。|  
|スナップショット エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Snapshot|Snapshot: Delivered Cmds/sec|ディストリビューターに 1 秒間に配信されたコマンド数。|  
|スナップショット エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Snapshot|Snapshot: Delivered Trans/sec|ディストリビューターに 1 秒間に配信されたトランザクション数。|  
|ログ リーダー エージェント (Log Reader Agent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Logreader|Logreader:Delivered Cmds/sec|ディストリビューターに 1 秒間に配信されたコマンド数。|  
|ログ リーダー エージェント (Log Reader Agent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Logreader|Logreader:Delivered Trans/sec|ディストリビューターに 1 秒間に配信されたトランザクション数。|  
|ログ リーダー エージェント (Log Reader Agent)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Logreader|Logreader: Delivery Latency|パブリッシャーでトランザクションが適用されてから、ディストリビューターに配信されるまでの現在のミリ秒単位の経過時間。|  
|ディストリビューション エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Dist.|Dist: Delivered Cmds/sec|サブスクライバーに 1 秒間に配信されたコマンド数。|  
|ディストリビューション エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Dist.|Dist: Delivered Trans/sec|サブスクライバーに 1 秒間に配信されたトランザクション数。|  
|ディストリビューション エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Dist.|Dist: Delivery Latency|トランザクションがディストリビューターに配信されてから、サブスクライバーで適用されるまでの現在のミリ秒単位の経過時間。|  
|マージ エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Merge|Conflicts/sec|マージ プロセス中に 1 秒間に発生した競合数。|  
|マージ エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Merge|Downloaded Changes/sec|パブリッシャーからサブスクライバーに 1 秒間にレプリケートされた行数。|  
|マージ エージェント|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Merge|Uploaded Changes/sec|サブスクライバーからパブリッシャーに 1 秒間にレプリケートされた行数。|  
  
## <a name="see-also"></a>参照  
 [監視 &#40;レプリケーション&#41;](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
