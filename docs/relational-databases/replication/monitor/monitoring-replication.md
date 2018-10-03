---
title: 監視 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d3e1b64c1c03a1e81fa83983427efbb60a399418
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810940"
---
# <a name="monitoring-replication"></a>監視 (レプリケーション)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  レプリケーション トポロジの監視は、レプリケーションの配置における重要な側面です。 レプリケーション処理は分散環境で行われるため、レプリケーションに関連するすべてのコンピューターについてその利用状況と状態を追跡することが不可欠です。 レプリケーションの監視には以下のツールを使用できます。  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] &#xA0;レプリケーション モニター  
  
     レプリケーションの監視を行うにあたり、最も重要なツールがレプリケーション モニターです。すべてのレプリケーションの利用状況がパブリッシャー関連のビューで表示されます。 詳しくは、「 [Monitoring Replication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)」をご覧ください。  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] を使用して、レプリケーション モニターにアクセスできます。 また、ログ リーダー エージェント、スナップショット エージェント、マージ エージェント、およびディストリビューション エージェントの各エージェントを開始および停止したり、現在の状態や各エージェントによってログに記録された最後のメッセージを表示することができます。 詳細については、「 [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md)」を参照してください。  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] およびレプリケーション管理オブジェクト (RMO)  
  
     どちらのインターフェイスでも、ディストリビューターからすべての種類のレプリケーションを監視できます。 マージ レプリケーションでは、サブスクライバーからレプリケーションを監視することもできます。  
  
-   レプリケーション エージェント イベントに対する警告  
  
     レプリケーションには、レプリケーション エージェント イベントに対する定義済みの警告が多数用意されています。また、必要に応じて追加の警告を作成することもできます。 警告を使用して、イベントに対する自動応答のトリガーを起動したり、管理者に通知することができます。 詳細については、「[レプリケーション エージェント イベントに対する警告の使用](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)」を参照してください。  
  
-   システム モニター  
  
     システム モニターには、レプリケーションに関するさまざまなカウンターが表示されるので、パフォーマンスを監視する場合に便利です。 詳細については、「 [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [管理 &#40;レプリケーション&#41;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
