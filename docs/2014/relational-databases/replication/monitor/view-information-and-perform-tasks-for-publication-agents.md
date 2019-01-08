---
title: 情報を表示し、パブリケーション (レプリケーション モニター) に関連付けられているエージェントのタスクを実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a92f56a6a9c68d984323ba8801755f87a1eaaec7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52758034"
---
# <a name="view-information-and-perform-tasks-for-the-agents-associated-with-a-publication-replication-monitor"></a>パブリケーションに関連付けられているエージェントの情報を表示し、タスクを実行する (レプリケーション モニター)
  レプリケーション モニターの **[エージェント]** タブには、選択したパブリケーションに関連付けられているエージェントの情報が含まれています。 ディストリビューション エージェントとマージ エージェントは、サブスクリプションに関連付けられいます。詳細については、[サブスクリプションに関連付けられているエージェントに関する情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-subscription-agents.md) に関するページをご覧ください。  
  
 このタブには、以下のエージェントの情報が表示されます。  
  
-   すべてのパブリケーションで使用されるスナップショット エージェント  
  
-   すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント  
  
-   キュー更新サブスクリプションに有効なトランザクション パブリケーションで使用されるキュー リーダー エージェント  
  
 このタブの各オプションに関する情報を表示するには、メニュー バーの **[ヘルプ]** をクリックしてください。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-publication"></a>パブリケーションに関連付けられているエージェントの情報を表示したりタスクを実行するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[エージェント]** タブをクリックします。エージェントの情報が表示されます。 このタブで、さらに詳しい情報を表示したり、タスクを実行することができます。  
  
    -   エージェントの詳細情報 (情報メッセージやエラー メッセージなど) を表示するには、エージェントを右クリックし、 **[詳細表示]** をクリックします。  
  
    -   エージェントを実行するジョブの詳細情報 (スケジュールやジョブ ステップの詳細など) を表示するには、エージェントを右クリックし、 **[プロパティ]** をクリックします。  
  
    -   エージェントのプロファイルを管理するには、エージェントを右クリックし、 **[エージェント プロファイル]** をクリックします。 詳細については、「[Work with Replication Agent Profiles](../agents/replication-agent-profiles.md)」(レプリケーション エージェント プロファイルの操作) をご覧ください。  
  
    -   実行されていないエージェントを開始するには、エージェントを右クリックし、 **[エージェントの開始]** をクリックします。  
  
    -   実行中のエージェントを停止するには、エージェントを右クリックし、 **[エージェントの停止]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターのしきい値と警告の設定](set-thresholds-and-warnings-in-replication-monitor.md)   
 [パブリケーションの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [レプリケーション エージェントの管理](../agents/replication-agent-administration.md)   
 [レプリケーションの監視](../monitoring-replication.md)  
  
  
