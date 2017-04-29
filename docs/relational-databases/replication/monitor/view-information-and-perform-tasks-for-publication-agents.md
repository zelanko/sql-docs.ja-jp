---
title: "パブリケーション エージェントの情報の表示とタスクの実行 | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3d2896e84ecfba28325f559da8e9391315c21046
ms.lasthandoff: 04/11/2017

---
# <a name="view-information-and-perform-tasks-for-publication-agents"></a>パブリケーション エージェントの情報の表示とタスクの実行
  レプリケーション モニターの **[エージェント]** タブには、選択したパブリケーションに関連付けられているエージェントの情報が含まれています。 ディストリビューション エージェントとマージ エージェントは、サブスクリプションに関連付けられいます。詳細については、[サブスクリプションに関連付けられているエージェントに関する情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-subscription-agents.md) に関するページをご覧ください。  
  
 このタブには、以下のエージェントの情報が表示されます。  
  
-   すべてのパブリケーションで使用されるスナップショット エージェント  
  
-   すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント  
  
-   キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されるキュー リーダー エージェント  
  
 このタブの各オプションに関する情報を表示するには、メニュー バーの **[ヘルプ]** をクリックしてください。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)」(レプリケーション モニターの開始) をご覧ください。  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-publication"></a>パブリケーションに関連付けられているエージェントの情報を表示したりタスクを実行するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[エージェント]** タブをクリックします。エージェントの情報が表示されます。 このタブで、さらに詳しい情報を表示したり、タスクを実行することができます。  
  
    -   エージェントの詳細情報 (情報メッセージやエラー メッセージなど) を表示するには、エージェントを右クリックし、 **[詳細表示]**をクリックします。  
  
    -   エージェントを実行するジョブの詳細情報 (スケジュールやジョブ ステップの詳細など) を表示するには、エージェントを右クリックし、 **[プロパティ]**をクリックします。  
  
    -   エージェントのプロファイルを管理するには、エージェントを右クリックし、 **[エージェント プロファイル]**をクリックします。 詳細については、「[Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)」(レプリケーション エージェント プロファイルの操作) をご覧ください。  
  
    -   実行されていないエージェントを開始するには、エージェントを右クリックし、 **[エージェントの開始]**をクリックします。  
  
    -   実行中のエージェントを停止するには、エージェントを右クリックし、 **[エージェントの停止]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターのしきい値と警告の設定](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)   
 [パブリケーションの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
