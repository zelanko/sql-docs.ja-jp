---
title: サブスクリプションの情報を表示し、タスクを実行する (レプリケーション モニター) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- subscriptions [SQL Server replication], viewing information
- subscriptions [SQL Server replication], Replication Monitor tasks
- viewing subscription information
ms.assetid: 54aac83b-6f29-40d7-8901-cf059749867f
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: af378e30b8bf33abea688dd9cc36019d18835bed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072756"
---
# <a name="view-information-and-perform-tasks-for-a-subscription-replication-monitor"></a>サブスクリプションの情報を表示し、タスクを実行する (レプリケーション モニター)
  レプリケーション モニターには、サブスクリプションについての情報を含む以下のタブが用意されています。  
  
-   **[すべてのサブスクリプション]**  
  
     このタブには、選択されたパブリケーションのすべてのサブスクリプションに関する情報が表示されます。  
  
-   **[サブスクリプション ウォッチ リスト]**  
  
     このタブには、選択したパブリッシャーの中で、エラーや警告が存在するパブリッシャーまたはパフォーマンスが最低のパブリッシャーで利用可能なすべてのパブリケーションから、サブスクリプションに関する情報が表示されます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]より前のバージョンを実行しているディストリビューターでは、このタブが表示されません。  
  
 それぞれのタブのオプションの詳細については、右ペインでタブをクリックしてから、メニュー バーで **[ヘルプ]** をクリックします。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-all-subscriptions-tab"></a>[すべてのサブスクリプション] タブのサブスクリプションの情報を表示したりタスクを実行したりするには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  サブスクリプションの情報を表示するには、 **[すべてのサブスクリプション]** タブをクリックします。同期中など、特定の状態のサブスクリプションのみを表示するには、 **[表示]** ボックスからオプションを選択します。  
  
3.  サブスクリプションのプロパティを表示および変更するには、サブスクリプションを右クリックしてから、 **[プロパティ]** をクリックします。 このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。詳細については、「[サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-subscription-agents.md)」を参照してください。  
  
### <a name="to-view-information-and-perform-tasks-for-subscriptions-in-the-subscription-watch-list-tab"></a>[サブスクリプション ウォッチ リスト] タブのサブスクリプションの情報を表示したりタスクを実行したりするには  
  
1.  左ペインでパブリッシャー グループを展開してから、パブリッシャーをクリックします。  
  
2.  サブスクリプションの情報を表示するには、 **[サブスクリプション ウォッチ リスト]** タブをクリックします。  
  
3.  **[\<SubscriptionType> サブスクリプションの表示]** ボックスから表示するサブスクリプションの種類を選択します。 同期中など、特定の状態のサブスクリプションのみを表示するには、 **[表示]** ボックスからオプションを選択します。  
  
4.  サブスクリプションのプロパティを表示および変更するには、サブスクリプションを右クリックしてから、 **[プロパティ]** をクリックします。 このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。詳細については、「[サブスクリプションに関連付けられているエージェントの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](view-information-and-perform-tasks-for-subscription-agents.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プッシュ サブスクリプションのプロパティの表示または変更](../view-and-modify-push-subscription-properties.md)   
 [プル サブスクリプションのプロパティの表示または変更](../view-and-modify-pull-subscription-properties.md)   
 [レプリケーションの監視](../monitoring-replication.md)  
  
  