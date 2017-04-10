---
title: "レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エージェント [SQL Server レプリケーション], コマンド プロンプト パラメーター"
ms.assetid: 45f2e781-c21d-4b44-8992-89f60fb3d022
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する (SQL Server Management Studio)
  レプリケーション エージェントは、コマンド ライン パラメーターを使用できる実行可能ファイルです。 既定では、エージェントの実行 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント ジョブ ステップは、これらのパラメーターを使用して変更や表示できるように、 **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックス。 このダイアログ ボックスがある、 **ジョブ** フォルダーに [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] との間、 **エージェント** レプリケーション モニターでタブをクリックします。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
> [!NOTE]  
>  エージェント パラメーターの変更は、エージェントの次回起動時に反映されます。 エージェントを継続して実行している場合は、そのエージェントを停止して再起動する必要があります。  
  
 パラメーターは直接変更することもできますが、エージェント プロファイルを使用して変更する方が一般的です。 詳しくは、「 [Replication Agent Profiles](../../../relational-databases/replication/agents/replication-agent-profiles.md)」をご覧ください。  
  
 エージェント ジョブにアクセスする場合、 **ジョブ** フォルダー、次の表を使用して、各エージェントのエージェントのジョブ名および使用可能なパラメーターを確認します。  
  
|エージェント|ジョブ名|パラメーターの一覧の参照先|  
|-----------|--------------|------------------------------------|  
|スナップショット エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< integer>**|[レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|マージ パブリケーション パーティションに対するスナップショット エージェント|**Dyn_ \< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< GUID>**|[レプリケーション スナップショット エージェント](../../../relational-databases/replication/agents/replication-snapshot-agent.md)|  
|ログ リーダー エージェント (Log Reader Agent)|**\< パブリッシャー>-\< PublicationDatabase>-\< integer>**|[レプリケーション ログ リーダー エージェント](../../../relational-databases/replication/agents/replication-log-reader-agent.md)|  
|プル サブスクリプションに対するマージ エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< SubscriptionDatabase>-\< integer>**|[レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|プッシュ サブスクリプションに対するマージ エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< integer>**|[レプリケーション マージ エージェント](../../../relational-databases/replication/agents/replication-merge-agent.md)|  
|プッシュ サブスクリプションに対するディストリビューション エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< integer>***|[レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|プル サブスクリプションに対するディストリビューション エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< SubscriptionDatabase>-\< GUID>***\*|[レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|SQL Server 以外のサブスクライバーへのプッシュ サブスクリプションに対するディストリビューション エージェント|**\< パブリッシャー>-\< PublicationDatabase>-\< パブリケーション>-\< サブスクライバー>-\< integer>**|[レプリケーション ディストリビューション エージェント](../../../relational-databases/replication/agents/replication-distribution-agent.md)|  
|キュー リーダー エージェント (Queue Reader Agent)|**[\< ディストリビューター>] です。\< 整数>**|[レプリケーション キュー リーダー エージェント](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)|  
  
 \*Oracle パブリケーションに対するプッシュ サブスクリプションの場合は **\< パブリッシャー>-\< Publisher**> なく **\< パブリッシャー>-\< PublicationDatabase>**  
  
 \*\*Oracle パブリケーションに対するプル サブスクリプションの場合は **\< パブリッシャー>-\< DistributionDatabase**> なく **\< パブリッシャー>-\< PublicationDatabase>**  
  
### Management Studio からレプリケーション エージェント コマンド ライン パラメーターを表示または変更するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] で適切なコンピューターに接続して、サーバー ノードを展開します。  
  
    -   プル サブスクリプションに対するディストリビューション エージェントとマージ エージェントの場合は、サブスクライバーに接続します。  
  
    -   その他のエージェントの場合は、ディストリビューターに接続します。  
  
2.  **[SQL Server エージェント]** フォルダーを展開して、 **[ジョブ]** フォルダーを展開します。  
  
3.  ジョブを右クリックし、をクリックし、 **プロパティ**します。  
  
4.   **手順** のページ、 **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックスで、ステップを選択して **エージェントを実行**, 、] をクリックし、 **編集**します。  
  
5.   **ジョブ ステップのプロパティ - エージェントを実行します** ダイアログ ボックスで、編集、 **コマンド** フィールドです。  
  
6.  をクリックして **OK** 両方のダイアログ ボックスにします。  
  
### レプリケーション モニターからディストリビューション エージェントとマージ エージェントのコマンド ライン パラメーターを表示および変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  サブスクリプションの場合を右クリックし、をクリックし、 **の詳細の表示**します。  
  
4.   **サブスクリプション \< SubscriptionName >** ウィンドウで、をクリックして **アクション**, 、] をクリックし、 **\< AgentName> ジョブのプロパティ**します。  
  
5.   **手順** のページ、 **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックスで、ステップを選択して **エージェントを実行**, 、] をクリックし、 **編集**します。  
  
6.   **ジョブ ステップのプロパティ - エージェントを実行します** ダイアログ ボックスで、編集、 **コマンド** フィールドです。  
  
7.  をクリックして **OK** 両方のダイアログ ボックスにします。  
  
### レプリケーション モニターからスナップショット エージェント、ログ リーダー エージェント、およびキュー リーダー エージェントのコマンド ライン パラメーターを表示および変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  クリックして、 **エージェント** ] タブをクリックします。  
  
3.  グリッドで、エージェントを右クリックし、をクリックし、 **プロパティ**します。  
  
4.   **手順** のページ、 **ジョブのプロパティ - \< ジョブ>** ] ダイアログ ボックスで、ステップを選択して **エージェントを実行**, 、] をクリックし、 **編集**します。  
  
5.   **ジョブ ステップのプロパティ - エージェントを実行します** ダイアログ ボックスで、編集、 **コマンド** フィールドです。  
  
6.  をクリックして **OK** 両方のダイアログ ボックスにします。  
  
## 参照  
 [レプリケーション エージェントの管理](../../../relational-databases/replication/agents/replication-agent-administration.md)   
 [レプリケーション エージェント実行可能ファイルの概念](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [レプリケーション エージェントの概要](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  