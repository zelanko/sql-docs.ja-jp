---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b6ff7b1cd07bfb91ab44ced875fc321c7b9ae34b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng014151"></a>MSSQL_ENG014151
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14151|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション-%s: エージェント %s は失敗しました。 %s|  
  
## <a name="explanation"></a>説明  
 このエラーは、すべてのレプリケーション エージェントのエラーに対して発生します。 メッセージの最後のテキストは、エラーのコンテキストに依存します。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーはさまざまな状況で発生します。必要に応じて、以下の方法を使用してください。  
  
-   失敗したエージェントを再起動し、問題なく実行されるかどうかを確認します。 詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
-   エージェント履歴およびジョブ履歴を参照し、同時期に発生したその他のエラーを確認します。 レプリケーション モニターにおけるエージェントの状態およびエラーの詳細の表示については、以下のトピックを参照してください。  
  
    -   スナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントについては、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)」を参照してください。  
  
    -   ディストリビューション エージェントおよびマージ エージェントについては、「[サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)」を参照してください。  
  
-   エージェントがアクセスするコンピューター間で基本的な接続が機能していることを確認し、 [sqlcmd Utility](../../tools/sqlcmd-utility.md)などのユーティリティにより各コンピューターを接続します。 接続の際には、エージェントが接続に使用するものと同じアカウントを使用します。 各エージェント アカウントで必要な権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
-   スナップショットの作成中または適用中にエラーが発生した場合は、スナップショット ディレクトリのファイルにエラーがないかどうかを確認します。  
  
-   エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [レプリケーション ディストリビューション エージェント](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [レプリケーション キュー リーダー エージェント](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
