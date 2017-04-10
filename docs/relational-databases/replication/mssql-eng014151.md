---
title: "MSSQL_ENG014151 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014151 エラー"
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# MSSQL_ENG014151
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14151|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション-%s: エージェント %s は失敗しました。 %s|  
  
## 説明  
 このエラーは、すべてのレプリケーション エージェントのエラーに対して発生します。 メッセージの最後のテキストは、エラーのコンテキストに依存します。  
  
## ユーザーの操作  
 このエラーはさまざまな状況で発生します。必要に応じて、以下の方法を使用してください。  
  
-   失敗したエージェントを再起動し、問題なく実行されるかどうかを確認します。 詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
-   エージェント履歴およびジョブ履歴を参照し、同時期に発生したその他のエラーを確認します。 レプリケーション モニターにおけるエージェントの状態およびエラーの詳細の表示については、以下のトピックを参照してください。  
  
    -   スナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントを参照してください。 [情報を表示したりタスクを実行するエージェント関連付けられていると、パブリケーションと #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)します。  
  
    -   ディストリビューション エージェントおよびマージ エージェントでは、「 [情報を表示したりタスクを実行する、エージェント関連付けられているサブスクリプションに関連付け & #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
-   基本的な接続が、エージェントがアクセスするコンピューター間で動作していることを確認しのようなユーティリティを使用して各コンピューターに接続、 [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md)します。 接続の際には、エージェントが接続に使用するものと同じアカウントを使用します。 各エージェント アカウントに必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
-   スナップショットの作成中または適用中にエラーが発生した場合は、スナップショット ディレクトリのファイルにエラーがないかどうかを確認します。  
  
-   エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## 参照  
 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [レプリケーション ディストリビューション エージェント](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [レプリケーション キュー リーダー エージェント](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [レプリケーション スナップショット エージェント](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  