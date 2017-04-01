---
title: "MSSQL_ENG018752 | Microsoft Docs"
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
  - "MSSQL_ENG018752 エラー"
ms.assetid: 405b2655-acb4-4e15-bcc6-b8f86bb22b37
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# MSSQL_ENG018752
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|18752|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|同時にデータベースに接続できるログ リーダー エージェントまたはログ関連のプロシージャ (sp_repldone、sp_replcmds、および sp_replshowcmds) は 1 つだけです。 ログ関連のプロシージャを実行した場合、そのプロシージャが実行された接続を削除するか、その接続に対して sp_replflush を実行してから、ログ リーダー エージェントを開始するか、別のログ関連のプロシージャを実行してください。|  
  
## 説明  
 次のいずれかを実行しようとして 1 つ以上の現在の接続: **sp_repldone**, 、**sp_replcmds**, 、または **sp_replshowcmds**します。 ストアド プロシージャ [sp_repldone & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)  [sp_replcmds & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) ストアド プロシージャを使って、ログ リーダー エージェントを見つけて、パブリッシュされたデータベースにレプリケートされたトランザクションに関する情報を更新します。 ストアド プロシージャ [sp_replshowcmds & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md) 特定の種類のトランザクション レプリケーションの問題のトラブルシューティングに使用します。  
  
 このエラーは、次の状況で発生します。  
  
-   パブリッシュされたデータベースのログ リーダー エージェントが実行されており、2 番目のログ リーダー エージェントの実行を同じデータベースに対して試みた場合、2 番目のエージェントに対してエラーが発生し、エージェント履歴に表示されます。  
  
     複数のエージェントが存在する状況では、いずれかのエージェントは孤立したプロセスが原因の可能性があります。  
  
-   パブリッシュされたデータベースに対するログ リーダー エージェントを起動し、ユーザーが実行 **sp_repldone**, 、**sp_replcmds**, 、または **sp_replshowcmds** ストアド プロシージャが実行されたアプリケーションで同じデータベースに対して、エラーが発生 (よう **sqlcmd**)。  
  
-   ユーザーが実行している、パブリッシュされたデータベースに対してログ リーダー エージェントが実行されていない場合 **sp_repldone**, 、**sp_replcmds**, 、または **sp_replshowcmds** とし、閉じない、ログ リーダー エージェントがデータベースに接続しようとしたときに、プロシージャの実行対象で接続エラーが発生します。  
  
## ユーザーの操作  
 次の手順を実行して、この問題に対するトラブルシューティングに役立てることができます。 いずれかの手順によって、ログ リーダー エージェントをエラーを発生させないで起動できるようになった場合は、残りの手順を実行する必要はありません。  
  
-   このエラーの発生原因となる可能性があるその他のエラーについて、ログ リーダー エージェントの履歴を確認します。 レプリケーション モニターでエージェントの状態やエラーの詳細を表示する方法については、次を参照してください。 [情報を表示したりタスクを実行するエージェント関連付けられていると、パブリケーションと #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)します。  
  
-   出力を確認 [sp_who & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) 特定のプロセス識別番号 (Spid) のパブリッシュされたデータベースに接続されています。 発生した可能性があるすべての接続切断 **sp_repldone**, 、**sp_replcmds**, 、または **sp_replshowcmds**します。  
  
-   ログ リーダー エージェントを再起動します。 詳細については、次を参照してください。 [の開始と停止のレプリケーション エージェントと #40 です。SQL Server Management Studio と #41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)します。  
  
-   ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを再起動します (クラスター内でオフラインまたはオンラインにします)。 スケジュールされたジョブが実行した可能性があるかどうかは **sp_repldone**, 、**sp_replcmds**, 、または **sp_replshowcmds** 、他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの再起動、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] それらのインスタンスにもエージェント。 詳細については、次を参照してください。 [開始、停止、または SQL Server エージェント サービスを一時停止](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)します。  
  
-   実行 [sp_replflush & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md) パブリッシャーのパブリケーション データベースとログ リーダー エージェントを再起動します。  
  
-   エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
  