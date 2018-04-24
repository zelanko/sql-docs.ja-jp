---
title: パブリッシャーの情報を表示し、タスクを実行する (レプリケーション モニター) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Publishers [SQL Server replication], Replication Monitor tasks
- viewing Publisher information
- Publishers [SQL Server replication], viewing information
ms.assetid: 1e777e95-377a-4de3-b965-867464aadaaf
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0084f2e6288cb2a09810499c38a8c5e1a346fa7f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="view-information-and-perform-tasks-for-a-publisher-replication-monitor"></a>パブリッシャーの情報を表示し、タスクを実行する (レプリケーション モニター)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  レプリケーション モニターには、選択したパブリッシャーに関する情報を表示する次のタブがあります。  
  
-   **パブリケーション**  
  
     このタブには、選択したパブリッシャーのすべてのパブリケーションに関する情報が表示されます。  
  
-   **[サブスクリプション ウォッチ リスト]**  
  
     このタブには、選択したパブリッシャーの中で、エラーや警告が存在するパブリッシャーまたはパフォーマンスが最低のパブリッシャーで利用可能なすべてのパブリケーションから、サブスクリプションに関する情報が表示されます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]より前のバージョンを実行しているディストリビューターでは、このタブが表示されません。  
  
-   **[エージェント]** タブ  
  
     このタブには、すべての種類のレプリケーションで使用されるエージェントおよびジョブに関する詳細情報が表示されます。 また、各エージェントとジョブを開始および停止することもできます。  
  
 それぞれのタブのオプションの詳細を表示するには、右ペインでタブをクリックしてから、メニュー バーの **[ヘルプ]** をクリックします。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor (レプリケーション モニターの開始)](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)」をご覧ください。  
  
### <a name="to-view-information-and-perform-tasks-for-a-publisher"></a>パブリッシャーの情報を表示し、タスクを実行するには  
  
1.  左ペインでパブリッシャー グループを展開してから、パブリッシャーをクリックします。  
  
2.  すべてのパブリケーションに関する情報を表示するには、 **[パブリケーション]** タブをクリックします。  
  
3.  サブスクリプションの情報を表示するには、 **[サブスクリプション ウォッチ リスト]** タブをクリックします。このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。  
  
    -   サブスクリプションに関連するエージェントの詳細を表示するには、サブスクリプションを右クリックし、 **[詳細表示]**をクリックします。  
  
    -   サブスクリプションのプロパティを表示するには、サブスクリプションを右クリックし、 **[プロパティ]**をクリックします。  
  
    -   プッシュ サブスクリプションを同期するには、サブスクリプションを右クリックし、 **[同期の開始]**をクリックします。  
  
    -   サブスクリプションを再初期化するには、サブスクリプションを右クリックし、 **[サブスクリプションの再初期化]**をクリックします。  
  
4.  エージェントの情報を表示するには、 **[エージェント]** タブをクリックします。このタブで、さらに詳しい情報を表示したり、タスクを実行することができます。  
  
    -   エージェントの詳細情報 (情報メッセージやエラー メッセージなど) を表示するには、エージェントを右クリックし、 **[詳細表示]**をクリックします。  
  
    -   エージェントを実行するジョブの詳細情報 (スケジュールやジョブ ステップの詳細など) を表示するには、エージェントを右クリックし、 **[プロパティ]**をクリックします。  
  
    -   エージェントのプロファイルを管理するには、エージェントを右クリックし、 **[エージェント プロファイル]**をクリックします。 詳細については、「[Work with Replication Agent Profiles](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)」(レプリケーション エージェント プロファイルの操作) をご覧ください。  
  
    -   実行されていないエージェントを開始するには、エージェントを右クリックし、 **[エージェントの開始]**をクリックします。  
  
    -   実行中のエージェントを停止するには、エージェントを右クリックし、 **[エージェントの停止]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
