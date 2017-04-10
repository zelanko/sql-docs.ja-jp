---
title: "レプリケーション エージェントを起動および停止する (SQL Server Management Studio) | Microsoft Docs"
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
  - "エージェント [SQL Server レプリケーション], 停止"
  - "エージェント [SQL Server レプリケーション], 起動"
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# レプリケーション エージェントを起動および停止する (SQL Server Management Studio)
  起動し、エージェントからの停止、 **ジョブ** フォルダーおよび **レプリケーション** フォルダーに [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] およびレプリケーション モニターからです。 以下のエージェントおよびジョブの開始と停止を行うことができます。  
  
-   すべてのパブリケーションで使用されるスナップショット エージェント  
  
-   すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント  
  
-   キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されるキュー リーダー エージェント  
  
-   トランザクション パブリケーションやスナップショット パブリケーションに対するサブスクリプションを同期するディストリビューション エージェント  
  
-   マージ パブリケーションに対するサブスクリプションを同期するマージ エージェント  
  
-   レプリケーション メンテナンス ジョブ。  
  
 マージ エージェントおよびディストリビューション エージェントを開始する方法の詳細については、次を参照してください。 [プッシュ サブスクリプションを同期する](../../../relational-databases/replication/synchronize-a-push-subscription.md) と [プル サブスクリプションを同期する](../../../relational-databases/replication/synchronize-a-pull-subscription.md)です。 メンテナンス ジョブの詳細については、次を参照してください。 [レプリケーション メンテナンス ジョブの実行と #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)です。  
  
 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
### Management Studio からスナップショット エージェントまたはログ リーダー エージェントを開始および停止するには  
  
1.  パブリッシャーに接続 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], 、サーバー ノードを展開し、 **レプリケーション** フォルダーです。  
  
2.  展開、 **ローカル パブリケーション** フォルダー、およびし、パブリケーションを右クリックします。  
  
3.  クリックして **スナップショット エージェントの状態を表示** または **ログ リーダー エージェントの状態を表示**します。  
  
4.  クリックして **開始** または **停止**です。  
  
### Management Studio からキュー リーダー エージェントを開始および停止するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  エージェントは、ジョブを右クリックし、をクリックし、 **ジョブの開始** または **ジョブの停止**です。 キュー リーダー エージェントのジョブの名前が、 **[\< ディストリビューター>] です。 \< 整数>**です。  
  
### レプリケーション モニターからスナップショット エージェント、ログ リーダー エージェント、またはキュー リーダー エージェントを開始および停止するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  クリックして、 **エージェント** ] タブをクリックします。  
  
3.  エージェントを右クリックし、をクリックし、 **エージェントの開始** または **エージェントの停止**します。  
  
## 参照  
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [レプリケーション エージェントの概要](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  