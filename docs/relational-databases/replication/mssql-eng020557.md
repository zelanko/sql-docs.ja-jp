---
title: MSSQL_ENG020557 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1384d7cf516de638b1c73b864875ca288fb1b80d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mssqleng020557"></a>MSSQL_ENG020557
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|20557|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|エージェントがシャットダウンされました。 詳細については、ジョブ '%s' の SQL Server エージェントのジョブ履歴を参照してください。|  
  
## <a name="explanation"></a>説明  
 レプリケーション エージェントは、原因を適切な履歴テーブルに書き込むことなくシャットダウンされました。つまり、このエージェントは処理の途中でシャットダウンされました。  
  
## <a name="user-action"></a>ユーザーの操作  
  
-   エージェントを再起動し、問題なく実行されるかどうかを確認します。 詳細については、「[レプリケーション エージェントを起動および停止する &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)」および「[レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)」を参照してください。  
  
-   エージェント履歴およびジョブ履歴を参照し、同時期に発生したその他のエラーを確認します。 レプリケーション モニターでエージェントの状態およびエラーの詳細を表示する方法については、次のトピックを参照してください。  
  
    -   スナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントについては、「[パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)」を参照してください。  
  
    -   ディストリビューション エージェントおよびマージ エージェントについては、「[サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md)」を参照してください。  
  
-   エージェントがアクセスするコンピューター間で基本的な接続が機能していることを確認し、 **sqlcmd** ユーティリティなどのユーティリティを使用して各コンピューターに接続します。 接続時には、エージェントが接続に使用するものと同じアカウントを使用します。 各エージェント アカウントで必要な権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
-   スナップショットの作成中または適用中にエラーが発生した場合は、スナップショット ディレクトリのファイルにエラーがないかどうかを確認します。  
  
-   エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージを発生させる手順が示される場合もあります。 レプリケーションのログ記録を構成する方法については、サポート技術情報の資料 [312292](http://support.microsoft.com/kb/312292)を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
