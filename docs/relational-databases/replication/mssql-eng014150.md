---
title: MSSQL_ENG014150 | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014150 error
ms.assetid: c3dd3109-abf3-4b38-a4e9-ef48d0235656
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 222ab67a59cad879dde9b6c823170ffed10a5338
ms.lasthandoff: 04/11/2017

---
# <a name="mssqleng014150"></a>MSSQL_ENG014150
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14150|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション-%s: エージェント %s が成功しました。 %s|  
  
## <a name="explanation"></a>説明  
 このメッセージは、レプリケーション エージェントの実行が正常に完了したことを示しています。 レプリケーションでは、次のエージェントを使用します。  
  
-   スナップショット エージェント。 すべてのパブリケーションで使用されます。  
  
-   ログ リーダー エージェント。 すべてのトランザクション パブリケーションで使用されます。  
  
-   キュー リーダー エージェント。 キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されます。  
  
-   ディストリビューション エージェント。 サブスクリプションをトランザクション パブリケーションおよびスナップショット パブリケーションと同期します。  
  
-   マージ エージェント。 サブスクリプションをマージ パブリケーションと同期します。  
  
-   レプリケーション メンテナンス ジョブ。  
  
## <a name="user-action"></a>ユーザーの操作  
 通常、ログ リーダー エージェント、キュー リーダー エージェント、およびディストリビューション エージェントは連続実行しますが、他のエージェントは、要求時に実行するかスケジュールに合わせて実行します。 エージェントが実行を完了したかどうかわからない場合は、エージェントの状態を確認します。 詳細については、「[レプリケーション エージェントの監視](../../relational-databases/replication/monitor/monitor-replication-agents.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [レプリケーション ディストリビューション エージェント](../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)   
 [レプリケーション キュー リーダー エージェント](../../relational-databases/replication/agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  
