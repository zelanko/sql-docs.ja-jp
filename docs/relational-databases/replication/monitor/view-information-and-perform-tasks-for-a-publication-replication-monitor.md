---
title: "パブリケーションの情報を表示し、タスクを実行する (レプリケーション モニター) | Microsoft Docs"
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
  - "パブリケーション情報の表示"
  - "パブリケーション [SQL Server レプリケーション], 情報の表示"
  - "パブリケーション [SQL Server レプリケーション], レプリケーション モニター タスク"
ms.assetid: 92e28a07-d6a7-461b-a0b3-bd9bc6afcbe5
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# パブリケーションの情報を表示し、タスクを実行する (レプリケーション モニター)
  レプリケーション モニターには、選択したパブリケーションについての情報を含む以下のタブが用意されています。  
  
-   **[すべてのサブスクリプション]**  
  
     このタブには、選択されたパブリケーションのすべてのサブスクリプションに関する情報が表示されます。  
  
-   **[エージェント]**  
  
     このタブには、パブリケーションで使用されるすべてのエージェントに関する情報が表示されます。  
  
    -   すべてのパブリケーションで使用されるスナップショット エージェント  
  
    -   すべてのトランザクション パブリケーションで使用されるログ リーダー エージェント  
  
    -   キュー更新サブスクリプションを持つトランザクション パブリケーションで使用されるキュー リーダー エージェント  
  
-   **警告** (実行しているディストリビューター [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降)  
  
    -   このタブを使用して、エージェントに対する警告とアラートを指定できます。  
  
-   **トレーサー トークン** (トランザクション レプリケーションを実行するディストリビューターに対してのみ、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降)  
  
     このタブでは、待機時間、つまりパブリッシャーでトランザクションがコミットされてから、対応するトランザクションがサブスクライバーでコミットされるまでの経過時間を測定できます。  
  
 各タブでオプションの詳細については、右側のウィンドウ] タブをクリックし、をクリックして **ヘルプ** メニュー バーでします。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
### パブリケーションの情報を表示し、タスクを実行するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  表示し、パブリケーションのプロパティを変更、パブリケーションを右クリックし、をクリックし、 **プロパティ**します。  
  
3.  サブスクリプションに関する情報を表示する] をクリックして、 **すべてのサブスクリプション** ] タブをクリックします。  
  
     表示し、サブスクリプションのプロパティを変更、サブスクリプションを右クリックし、をクリックして **プロパティ**です。 このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。 詳細については、次を参照してください。 [情報を表示したりタスクを実行する、エージェント関連付けられているサブスクリプションに関連付け & #40 です。レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)です。  
  
4.  エージェントの情報を表示する] をクリックして、 **エージェント** ] タブをクリックします。 このタブで、さらに詳しい情報を表示したり、タスクを実行したりできます。 詳細については、次を参照してください。 [情報を表示したりタスクを実行するエージェント関連付けられていると、パブリケーションと #40 です。レプリケーション モニターと #41;](../../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)します。  
  
5.  エージェントの警告としきい値に関する情報を表示する] をクリックして、 **警告** ] タブをクリックします。 詳細については、次を参照してください。 [しきい値の設定とレプリケーション モニターで警告](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)します。  
  
6.  トレーサー トークンに関する情報を表示する] をクリックして、 **トレーサー トークン** ] タブをクリックします。 トレーサー トークンを使用する方法の詳細については、次を参照してください。 [メジャーの待機時間とトランザクション レプリケーション用の接続の検証](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)します。  
  
## 参照  
 [パブリケーション プロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  