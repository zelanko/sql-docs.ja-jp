---
title: "パブリケーション情報、[すべてのサブスクリプション] (スナップショット パブリケーション) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1"
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# パブリケーション情報、[すべてのサブスクリプション] (スナップショット パブリケーション)
   **すべてのサブスクリプション** ] タブでは、選択したスナップショット パブリケーションに対するすべてのサブスクリプションに関する情報を表示します。  
  
## オプション  
 サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。  
  
-   **[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。  
  
-   **[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。  
  
-   **[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **[表示]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。 たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。  
  
 **[状態]**  
 各サブスクリプションの状態です。スナップショット エージェントまたはディストリビューション エージェントの状態 (より高い優先度の状態が表示されます) によって決定されます。  
  
 既定では、サブスクリプション情報を含むグリッドに並べ替えて、 **ステータス** 列です。 表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。  
  
-   [エラー]  
  
-   [まもなく期限切れ/期限切れ] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [初期化されていないサブスクリプション] ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [失敗したコマンドの再試行]  
  
-   [同期中]  
  
-   [同期されていません]  
  
 特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。 たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]**と表示されます。  
  
 状態値 **まもなく期限切れ/期限切れ** と **初期化されていないサブスクリプション** 警告します。 警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。 たとえば、状態がある可能性があります **実行中、まもなく期限切れ/期限切れ**します。  
  
 状態値 **まもなく期限切れ/期限切れ** しきい値が設定されている場合にのみが表示されます。 しきい値の設定については、次を参照してください。 [しきい値の設定とレプリケーション モニターで警告](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)します。  
  
 **サブスクリプション**  
 サブスクリプションごとに、フォームでの名前: *SubscriberName: SubscriptionDatabaseName*します。  
  
 **[最後の同期]**  
 ディストリビューション エージェントが最後に実行された時刻です。 同期が進行中の場合は、 **[実行中]** と表示されます。  
  
## 参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [情報を表示し、サブスクリプションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [情報を表示し、サブスクリプションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  