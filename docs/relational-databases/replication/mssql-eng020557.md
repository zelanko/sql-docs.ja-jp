---
title: "MSSQL_ENG020557 | Microsoft Docs"
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
  - "MSSQL_ENG020557 エラー"
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# MSSQL_ENG020557
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20557|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|エージェントがシャットダウンされました。 詳細については、ジョブ '%s' の SQL Server エージェントのジョブ履歴を参照してください。|  
  
## 説明  
 レプリケーション エージェントは、原因を適切な履歴テーブルに書き込むことなくシャットダウンされました。つまり、このエージェントは処理の途中でシャットダウンされました。  
  
## ユーザーの操作  
  
-   エージェントを再起動し、問題なく実行されるかどうかを確認します。 詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
-   エージェント履歴およびジョブ履歴を参照し、同時期に発生したその他のエラーを確認します。 レプリケーション モニターでエージェントの状態およびエラーの詳細を表示する方法については、次のトピックを参照してください。  
  
    -   スナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントを参照してください。 [情報を表示したりタスクを実行するエージェント関連付けられていると、パブリケーションと #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)します。  
  
    -   ディストリビューション エージェントおよびマージ エージェントでは、「 [情報を表示したりタスクを実行する、エージェント関連付けられているサブスクリプションに関連付け & #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
-   エージェントがアクセスするなどのユーティリティを使用して、各コンピューターに接続し、コンピューター間で基本的な接続が動作していることを確認、 **sqlcmd** ユーティリティです。 接続時には、エージェントが接続に使用するものと同じアカウントを使用します。 各エージェント アカウントに必要なアクセス許可の詳細については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
-   スナップショットの作成中または適用中にエラーが発生した場合は、スナップショット ディレクトリのファイルにエラーがないかどうかを確認します。  
  
-   エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージを発生させる手順が示される場合もあります。 レプリケーションのログ出力を構成する方法の詳細については、マイクロソフト サポート技術情報の記事を参照してください。 [312292](http://support.microsoft.com/kb/312292)します。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  