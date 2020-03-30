---
title: 監視 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: d884bfe3517fa8b45c19f1d4d286992c2e5453c1
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "76288052"
---
# <a name="monitoring-replication"></a>監視 (レプリケーション)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  レプリケーション トポロジの監視は、レプリケーションの配置における重要な側面です。 レプリケーション処理は分散環境で行われるため、レプリケーションに関連するすべてのコンピューターについてその利用状況と状態を追跡することが不可欠です。 さまざまな監視ツールを使用することで、次のような一般的な質問に答えることができます。 

-   レプリケーション システムは正常に動作していますか。
-   処理の遅いサブスクリプションはどれですか。
-   トランザクション サブスクリプションでどのくらい未処理のデータが残っていますか。
-   トランザクション レプリケーションにおいて、コミットされたトランザクションがサブスクライバーに伝達されるまでどれくらいの時間が必要ですか。
-   なぜマージ サブスクリプションの処理が遅いのですか。
-   なぜエージェントが実行されないのですか。  
  

レプリケーションの監視には以下のツールを使用できます。  
  
-   **SQL Server レプリケーション モニター** - すべてのレプリケーション動作をパブリッシャーに重点をおいて表示する、レプリケーションを監視するための最も重要なツールです。 詳しくは、「 [Monitoring Replication](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)」をご覧ください。 
-   **SQL Server Management Studio** - レプリケーション モニターへのアクセスを可能にします。 また、ログ リーダー エージェント、スナップショット エージェント、マージ エージェント、およびディストリビューション エージェントの各エージェントを開始および停止したり、現在の状態や各エージェントによってログに記録された最後のメッセージを表示することができます。 詳細については、「 [Monitor Replication Agents](../../../relational-databases/replication/monitor/monitor-replication-agents.md)」を参照してください。  
  
-   **Transact-SQL (T-SQL) およびレプリケーション管理オブジェクト (RMO)** - どちらのインターフェイスも、ディストリビューターからのあらゆる種類のレプリケーションを監視できるようにします。 マージ レプリケーションでは、サブスクライバーからレプリケーションを監視することもできます。  
  
-   **レプリケーション エージェント イベントのアラート** - レプリケーションには、レプリケーション エージェント イベントに対する定義済みの警告が多数用意されています。また、必要に応じて追加の警告を作成することもできます。 警告を使用して、イベントに対する自動応答のトリガーを起動したり、管理者に通知することができます。 詳細については、「[レプリケーション エージェント イベントに対する警告の使用](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)」を参照してください。  
  
-   **システム モニター** - レプリケーションに関するさまざまなカウンターが表示されるので、パフォーマンスを監視する場合に便利です。 詳細については、「 [Monitoring Replication with System Monitor](../../../relational-databases/replication/monitor/monitoring-replication-with-system-monitor.md)」を参照してください。  
  

## <a name="see-also"></a>参照  
 [Best Practices for Replication Administration](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   

  
  
