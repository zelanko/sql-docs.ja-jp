---
title: システム モニターによるレプリケーションの監視 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], System Monitor
- System Monitor [SQL Server], replication
- performance counters [SQL Server replication]
ms.assetid: 8cd3a270-0328-4bfd-bf23-b1d759cc120c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b5d1a63937a11da4703ec4ef0338dee89a5c33f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62667307"
---
# <a name="monitoring-replication-with-system-monitor"></a>システム モニターによるレプリケーションの監視
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)]Windows システムモニターを使用すると、グラフ、グラフ、およびレポートを使用して、コンピューターの効率を測定し、考えられる問題 (リソース使用の不均衡、ハードウェアの不足、プログラム設計の不備など) を特定してトラブルシューティングを行うことができます。追加のハードウェアが必要です。 詳細については、「[リソースの利用状況の監視 &#40;システム モニター&#41;](../../performance-monitor/monitor-resource-usage-system-monitor.md)」を参照してください。  
  
 システム モニターでは、さまざまなプロセスのパフォーマンスについての情報を提供するパフォーマンス オブジェクトおよびカウンターを使用します。 レプリケーション エージェントに関連するカウンターにより、レプリケーション パフォーマンスを計測できます。  
  
|エージェント|パフォーマンス オブジェクト|カウンター|[説明]|  
|-----------|------------------------|-------------|-----------------|  
|すべてのエージェント|[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: レプリケーションエージェント|実行中|現在実行されているレプリケーション エージェントの数。|  
|スナップショット エージェント|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Snapshot|Snapshot: Delivered Cmds/sec|ディストリビューターに 1 秒間に配信されたコマンド数。|  
|スナップショット エージェント|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Snapshot|Snapshot: Delivered Trans/sec|ディストリビューターに 1 秒間に配信されたトランザクション数。|  
|ログ リーダー エージェント (Log Reader Agent)|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Logreader|Logreader:Delivered Cmds/sec|ディストリビューターに 1 秒間に配信されたコマンド数。|  
|ログ リーダー エージェント (Log Reader Agent)|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Logreader|Logreader:Delivered Trans/sec|ディストリビューターに 1 秒間に配信されたトランザクション数。|  
|ログ リーダー エージェント (Log Reader Agent)|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Logreader|Logreader: Delivery Latency|パブリッシャーでトランザクションが適用されてから、ディストリビューターに配信されるまでの現在のミリ秒単位の経過時間。|  
|ディストリビューション エージェント|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Dist.|Dist: Delivered Cmds/sec|サブスクライバーに 1 秒間に配信されたコマンド数。|  
|ディストリビューション エージェント|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Dist.|Dist: Delivered Trans/sec|サブスクライバーに 1 秒間に配信されたトランザクション数。|  
|ディストリビューション エージェント|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Dist.|Dist: Delivery Latency|トランザクションがディストリビューターに配信されてから、サブスクライバーで適用されるまでの現在のミリ秒単位の経過時間。|  
|[マージ エージェント]|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Merge|Conflicts/sec|マージ プロセス中に 1 秒間に発生した競合数。|  
|[マージ エージェント]|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Merge|Downloaded Changes/sec|パブリッシャーからサブスクライバーに 1 秒間にレプリケートされた行数。|  
|[マージ エージェント]|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: Replication Merge|Uploaded Changes/sec|サブスクライバーからパブリッシャーに 1 秒間にレプリケートされた行数。|  
  
## <a name="see-also"></a>参照  
 [&#40;レプリケーション&#41;の監視](../monitoring-replication.md)  
  
  
