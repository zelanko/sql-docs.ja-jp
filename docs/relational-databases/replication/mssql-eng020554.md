---
title: "MSSQL_ENG020554 | Microsoft Docs"
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
  - "MSSQL_ENG020554 エラー"
ms.assetid: ef1a1b88-b2ab-43e8-99cd-163a973262d6
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG020554
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20554|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション エージェントでは、進捗状況メッセージが %ld 分間ログに記録されていません。 この現象は、エージェントの応答が止まったか、システムの使用率が高いことを示している場合があります。 レコードがレプリケーション先にレプリケートされていること、およびサブスクライバー、パブリッシャー、ディストリビューターへの接続がアクティブなままであることを確認してください。|  
  
## 説明  
  **レプリケーション エージェントの検査** ジョブを各レプリケーション エージェントの状態を確認する (既定で 10 分) の指定された間隔で実行します。 エージェントが、最後の検査ジョブを実行してからまったく進捗状況メッセージを記録していない場合は、MSSQL_ENG020554 エラーが発生する可能性があります。 他のレプリケーション処理が実行されていない場合でも、エージェントは少なくとも履歴メッセージだけは記録する必要があります。 レプリケーション エージェントは、予想どおり応答していない場合でも、停止したり障害が発生するとは限りません (エージェントで障害が発生すると、エラー MSSQL_ENG020536 が発生します)。  
  
 MSSQL_ENG020554 は、次のような問題が原因で発生する可能性があります。  
  
-   エージェントがビジーである場合  
  
     エージェントの検査ジョブでポーリングが実行されているときにエージェントがビジーで応答できない場合、エージェントの検査ジョブは、レプリケーション エージェントが正しく機能しているかどうかについて報告できません。 レプリケーション エージェントがビジーになるのは、レプリケートされているデータの量が多すぎたり、アプリケーションの設計または構成の問題が原因でプロセスが長時間実行されるなど、さまざまな原因があります。  
  
-   エージェントがトポロジ内のコンピューターのいずれにもログインできない場合  
  
     すべてのエージェントには、パラメーターが含まれている **-logintimeout** (15 秒に既定で設定)、マージ エージェント パブリッシャーにログインするなどのレプリケーション ノードにログインしようとして、どのくらいの期間のエージェントが決定します。 場合、 **-logintimeout** 値は、レプリケーション エージェントの検査ジョブを実行する間隔より大きく設定されて、ログインで問題がエラーの根本原因になる可能性があります。 エージェントが、具体的なエラーが発生する前にエラー MSSQL_ENG020554 が発生します。  
  
## ユーザーの操作  
 必要な操作は、エラーが発生した原因によって異なります。  
  
-   このエラーが発生するすべてのケースで、次のアクションを実行します。  
  
     レプリケーション モニターでエラーの詳細を確認してから、エージェントが停止している場合は再起動します。 エラーの詳細には、エージェントが正しく実行されなかった原因について追加の情報が示されている場合があります。 エージェントが実行中の場合は、エージェントを停止および再起動しないでください。停止および再起動すると、問題がさらに悪化する可能性があります。 レプリケーション モニターにおけるエージェントの状態およびエラーの詳細の表示については、以下のトピックを参照してください。  
  
    -   スナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントを参照してください。 [情報を表示したりタスクを実行するエージェント関連付けられていると、パブリケーションと #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)します。  
  
    -   ディストリビューション エージェントおよびマージ エージェントでは、「 [情報を表示したりタスクを実行する、エージェント関連付けられているサブスクリプションに関連付け & #40 です。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)します。  
  
-   エージェントがビジーであるためにこのエラーが頻繁に発生する場合は、次の操作を実行します。  
  
     場合によっては、エージェントの処理時間が短くなるように、アプリケーションを再設計する必要があります。  
  
     **[ジョブのプロパティ]** ダイアログ ボックスを使用してエージェントの状態を確認する間隔を長くすることができます。 レプリケーション ジョブの場合は、このダイアログ ボックスにアクセスする方法については、次を参照してください [情報を表示し、パブリッシャーおよび #40; のタスクを実行します。。レプリケーション モニターと #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)します。  
  
-   エージェントがトポロジ内のコンピューターのいずれにもログインできない場合には、次の操作を実行します。  
  
     お勧めします **-logintimeout** 値をレプリケーション エージェントの検査ジョブを実行する間隔よりも短く設定します。 場合によっては、値で **-logintimeout** ログインがタイムアウトとなるネットワークの問題により大きく設定されています。 場合、 **-logintimeout** の設定を低く、レプリケーションは、権限、ネットワークの問題、またはその他の問題によって発生することがあるログインの問題をトラブルシューティングすることができますより具体的なエラーを報告できます。 エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。 詳細については、以下をご覧ください。  
  
    -   [Work with Replication Agent Profiles](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
    -   [表示および変更のレプリケーション エージェント コマンド プロンプト パラメーターと #40 です。SQL Server Management Studio と #41 です。](../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md)  
  
    -   [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)します。  
  
## 参照  
 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [レプリケーション ディストリビューション エージェント](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [レプリケーション キュー リーダー エージェント](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [レプリケーション スナップショット エージェント](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  