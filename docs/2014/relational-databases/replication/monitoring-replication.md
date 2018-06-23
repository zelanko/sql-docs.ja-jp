---
title: 監視 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring performance [SQL Server replication], about monitoring replication
- transactional replication, monitoring
- monitoring [SQL Server replication]
- merge replication monitoring [SQL Server replication]
- snapshot replication [SQL Server], monitoring
- replication [SQL Server], monitoring
- administering replication, monitoring
ms.assetid: f182f43a-6af8-45bc-a708-08d5f7a6984a
caps.latest.revision: 38
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7434a211de780ab5a363aeec97b8914bb587f5a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072759"
---
# <a name="monitoring-replication"></a>監視 (レプリケーション)
  レプリケーション トポロジの監視は、レプリケーションの配置における重要な側面です。 レプリケーション処理は分散環境で行われるため、レプリケーションに関連するすべてのコンピューターについてその利用状況と状態を追跡することが不可欠です。 レプリケーションの監視には以下のツールを使用できます。  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] Replication Monitor  
  
     レプリケーションの監視を行うにあたり、最も重要なツールがレプリケーション モニターです。すべてのレプリケーションの利用状況がパブリッシャー関連のビューで表示されます。 詳細については、次を参照してください。[レプリケーションの監視](monitor/monitoring-replication-overview.md)です。  
  
-   [!INCLUDE[msCoName](../../includes/msCoName-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssManStudioFull-md.md)]  
  
     [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] を使用して、レプリケーション モニターにアクセスできます。 また、ログ リーダー エージェント、スナップショット エージェント、マージ エージェント、およびディストリビューション エージェントの各エージェントを開始および停止したり、現在の状態や各エージェントによってログに記録された最後のメッセージを表示することができます。 詳細については、「 [Monitor Replication Agents](agents/replication-agents.md)」を参照してください。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] およびレプリケーション管理オブジェクト (RMO)  
  
     どちらのインターフェイスでも、ディストリビューターからすべての種類のレプリケーションを監視できます。 マージ レプリケーションでは、サブスクライバーからレプリケーションを監視することもできます。  
  
-   レプリケーション エージェント イベントに対する警告  
  
     レプリケーションには、レプリケーション エージェント イベントに対する定義済みの警告が多数用意されています。また、必要に応じて追加の警告を作成することもできます。 警告を使用して、イベントに対する自動応答のトリガーを起動したり、管理者に通知することができます。 詳細については、「[レプリケーション エージェント イベントに対する警告の使用](agents/use-alerts-for-replication-agent-events.md)」を参照してください。  
  
-   システム モニター  
  
     システム モニターには、レプリケーションに関するさまざまなカウンターが表示されるので、パフォーマンスを監視する場合に便利です。 詳細については、「 [Monitoring Replication with System Monitor](monitor/monitoring-replication-with-system-monitor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [管理 &#40;レプリケーション&#41;](administration/administration-replication.md)   
 [Best Practices for Replication Administration](administration/best-practices-for-replication-administration.md)   
 [レプリケーションの監視](monitor/monitoring-replication-overview.md)  
  
  