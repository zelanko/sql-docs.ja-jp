---
title: パブリケーションの情報を表示し、タスクを実行する (レプリケーション モニター) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing publication information
- publications [SQL Server replication], viewing information
- publications [SQL Server replication], Replication Monitor tasks
ms.assetid: 92e28a07-d6a7-461b-a0b3-bd9bc6afcbe5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 148ad2ba9ad0fb6575b787b992744666010fd3e1
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52781204"
---
# <a name="view-information-and-perform-tasks-for-a-publication-replication-monitor"></a>パブリケーションの情報を表示し、タスクを実行する (レプリケーション モニター)
  レプリケーション モニターには、選択したパブリケーションについての情報を含む以下のタブが用意されています。  
  
-   **[すべてのサブスクリプション]**  
  
     このタブには、選択されたパブリケーションのすべてのサブスクリプションに関する情報が表示されます。  
  
-   **[エージェント]**  
  
     このタブには、パブリケーションで使用されるすべてのエージェントに関する情報が表示されます。  
  
    -   すべてのパブリケーションで使用されるスナップショット エージェント  
  
    -   すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント  
  
    -   キュー更新サブスクリプションを持つトランザクション パブリケーションで使用されるキュー リーダー エージェント  
  
-   **[警告]** ( [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降を実行しているディストリビューター)  
  
    -   このタブを使用して、エージェントに対する警告とアラートを指定できます。  
  
-   **[トレーサー トークン]** ( [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降を実行しているディストリビューターのトランザクション レプリケーションのみ)  
  
     このタブでは、待機時間、つまりパブリッシャーでトランザクションがコミットされてから、対応するトランザクションがサブスクライバーでコミットされるまでの経過時間を測定できます。  
  
 それぞれのタブのオプションの詳細については、右ペインでタブをクリックしてから、メニュー バーで **[ヘルプ]** をクリックします。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。  
  
### <a name="to-view-information-and-perform-tasks-for-a-publication"></a>パブリケーションの情報を表示し、タスクを実行するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  パブリケーションのプロパティを表示および変更するには、パブリケーションを右クリックし、 **[プロパティ]** をクリックします。  
  
3.  サブスクリプションの情報を表示するには、 **[すべてのサブスクリプション]** タブをクリックします。  
  
     サブスクリプションのプロパティを表示および変更するには、サブスクリプションを右クリックしてから、 **[プロパティ]** をクリックします。 このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。詳細については、[サブスクリプションに関連付けられているエージェントの情報の表示およびタスクの実行](view-information-and-perform-tasks-for-subscription-agents.md)に関するページを参照してください。  
  
4.  エージェントの情報を表示するには、 **[エージェント]** タブをクリックします。このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。詳細については、[パブリケーションに関連付けられているエージェントの情報の表示およびタスクの実行](view-information-and-perform-tasks-for-publication-agents.md)に関するページを参照してください。  
  
5.  エージェントの警告としきい値の情報を表示するには、 **[警告]** タブをクリックします。詳細については、「 [Set Thresholds and Warnings in Replication Monitor](set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。  
  
6.  トレーサー トークンの情報を表示するには、 **[トレーサー トークン]** タブをクリックします。トレーサー トークンの使用方法の詳細については、「 [トランザクション レプリケーションの待機時間の計測および接続の検証](measure-latency-and-validate-connections-for-transactional-replication.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [パブリケーション プロパティの表示および変更](../publish/view-and-modify-publication-properties.md)   
 [レプリケーションの監視](../monitoring-replication.md)  
  
  
