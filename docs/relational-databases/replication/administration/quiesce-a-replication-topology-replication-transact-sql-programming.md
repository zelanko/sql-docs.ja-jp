---
title: "レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "レプリケーションの管理, 停止"
  - "停止 [SQL Server レプリケーション]"
  - "トランザクション レプリケーション, バックアップと復元"
ms.assetid: 7626d575-9994-47be-b772-5b6f1b7ef7ca
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# レプリケーション トポロジの停止 (レプリケーション Transact-SQL プログラミング)
  *停止* システムでは、パブリッシュされたテーブルのすべてのノードでアクティビティを停止して、各ノードが他のすべてのノードからのすべての変更を受け取っていることを確認します。 このトピックでは、いくつかの管理タスクで必要とされる、レプリケーション トポロジの停止方法や、他のノードからのすべての変更をノードが受け取ったことを確認する方法について説明します。  
  
### 読み取り専用サブスクライバーを含むトランザクション レプリケーション トポロジを停止するには  
  
1.  パブリッシャーで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_posttracertoken & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md)します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)します。  
  
4.  各サブスクライバーがトレーサー トークンを受け取ったことを確認します。  
  
### 更新可能サブスクリプションを含むトランザクション レプリケーション トポロジを停止するには  
  
1.  パブリッシャーおよびすべてのサブスクライバーで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  キュー更新サブスクリプションを使用するサブスクライバーがある場合  
  
    1.  キュー リーダー エージェントが連続モードで実行されていない場合は、エージェントを実行します。 エージェントの実行の詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) または [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
    2.  キューが空であることを確認するには実行 [sp_replqueuemonitor](../../../relational-databases/system-stored-procedures/sp-replqueuemonitor-transact-sql.md) サブスクライバーごとにします。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_posttracertoken](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md)します。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helptracertokenhistory](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)します。  
  
5.  各サブスクライバーがトレーサー トークンを受け取ったことを確認します。  
  
### ピア ツー ピアのトランザクション レプリケーション トポロジを停止するには  
  
1.  すべてのノードで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  実行 [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) トポロジ内の各パブリケーション データベースです。  
  
3.  ログ リーダー エージェントまたはディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。 ログ リーダー エージェントは、ディストリビューション エージェントの前に開始する必要があります。 エージェントの実行の詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) または [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
4.  実行 [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) トポロジ内の各パブリケーション データベースです。 結果セットに他のノードからの応答が含まれていることを確認します。  
  
### ピア ツー ピア ノードが前の変更をすべて受け取ったことを確認するには  
  
1.  実行 [sp_requestpeerresponse](../../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) でチェックするノードでパブリケーション データベースです。  
  
2.  ログ リーダー エージェントまたはディストリビューション エージェントが連続モードで実行されていない場合は、エージェントを実行します。 ログ リーダー エージェントは、ディストリビューション エージェントの前に開始する必要があります。 エージェントの実行の詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) または [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
3.  実行 [sp_helppeerresponses](../../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) でチェックするノードでパブリケーション データベースです。 結果セットに他のノードからの応答が含まれていることを確認します。  
  
### マージ レプリケーション トポロジを停止するには  
  
1.  パブリッシャーおよびすべてのサブスクライバーで、すべてのパブリッシュされたテーブルの処理を停止します。  
  
2.  各サブスクリプションに対して、マージ エージェントを 2 回実行します。すべてのサブスクリプションを 1 回同期させてから、各サブスクリプションをもう 1 回同期させます。 これにより、すべての変更がすべてのノードに確実にレプリケートされます。 エージェントの実行の詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md) または [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
    > [!NOTE]  
    >  同期中に競合が発生した場合は、マージ エージェントを 2 回実行した後でも、競合の解決に必要な変更が全ノードに反映されない可能性があります。  
  
## 参照  
 [#40; (&)、ピア ツー ピア トポロジを管理します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Measure Latency and Validate Connections for Transactional Replication](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  