---
title: "Synchronize a Push Subscription | Microsoft Docs"
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
  - "synchronization [SQL Server replication], push subscriptions"
  - "subscriptions [SQL Server replication], push"
  - "プッシュ サブスクリプション [SQL Server レプリケーション]、同期"
ms.assetid: 0cfa7ae5-91d3-4a4f-9edf-a852d45783b5
caps.latest.revision: 43
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 43
---
# Synchronize a Push Subscription
  このトピックでのプッシュ サブスクリプションを同期する方法について説明 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 、[レプリケーション エージェント](../../relational-databases/replication/agents/replication-agents-overview.md), 、またはレプリケーション管理オブジェクト (RMO)。  
  
 **このトピックの内容**  
  
-   **プッシュ サブスクリプションを同期するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [レプリケーション エージェント](#ReplProg)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 サブスクリプションは、ディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) で同期されます。 エージェントは継続的に実行、要求時に実行、またはスケジュールで実行できます。 同期スケジュールを指定する方法の詳細については、次を参照してください。 [同期スケジュールの指定](../../relational-databases/replication/specify-synchronization-schedules.md)します。  
  
 オンデマンドでサブスクリプションを同期する、 **ローカル パブリケーション** と **ローカル サブスクリプション** 内のフォルダー [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と **すべてのサブスクリプション** レプリケーション モニターでタブをクリックします。 Oracle パブリケーションに対するサブスクリプションは、サブスクライバーから要求時に同期することはできません。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
#### Management Studio で要求時にプッシュ サブスクリプションを同期するには (パブリッシャー側)  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  サブスクリプションを同期するパブリケーションを展開します。  
  
4.  クリックして、同期するサブスクリプションを右クリックして **[同期の状態**します。  
  
5.   **同期状態の表示 - \< サブスクライバー>: \< SubscriptionDatabase>** ダイアログ ボックスで、をクリックして **開始**します。 同期が完了したら、" **同期処理が完了しました** " というメッセージが表示されます。  
  
6.  **[閉じる]**をクリックします。  
  
#### Management Studio で要求時にプッシュ サブスクリプションを同期するには (サブスクライバー側)  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  クリックして、同期するサブスクリプションを右クリックして **[同期の状態**します。  
  
4.  ディストリビューターへの接続の確立に関するメッセージが表示されます。 クリックして **OK**です。  
  
5.   **同期状態の表示 - \< サブスクライバー>: \< SubscriptionDatabase>** ダイアログ ボックスで、をクリックして **開始**します。 同期が完了したら、" **同期処理が完了しました** " というメッセージが表示されます。  
  
6.  **[閉じる]**をクリックします。  
  
#### レプリケーション モニターで要求時にプッシュ サブスクリプションを同期するには  
  
1.  レプリケーション モニターで、左ペインのパブリッシャー グループを展開し、パブリッシャーを展開してパブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  クリックして、同期するサブスクリプションを右クリックして **同期の開始**します。  
  
4.  同期の進行状況の表示をサブスクリプションを右クリックしてをクリックして **詳細の表示**します。  
  
##  <a name="ReplProg"></a> レプリケーション エージェントの使用  
 コマンド プロンプトから適切なレプリケーション エージェント実行可能ファイルを呼び出すことにより、プッシュ サブスクリプションを要求時にプログラムで同期できます。 呼び出されるレプリケーション エージェント実行可能ファイルは、プッシュ サブスクリプションが属するパブリケーションの種類によって異なります。  
  
#### ディストリビューション エージェントを開始してプッシュ サブスクリプションをトランザクション パブリケーションに同期するには  
  
1.  コマンド プロンプトから、またはディストリビューターからバッチ ファイルで、 **distrib.exe**を実行します。 次のコマンド ライン引数を指定します。  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     SQL Server 認証を使用する場合は、次の引数も指定する必要があります。  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
#### マージ エージェントを開始してプッシュ サブスクリプションをマージ パブリケーションに同期するには  
  
1.  コマンド プロンプトから、またはディストリビューターからバッチ ファイルで、 **replmerg.exe**を実行します。 次のコマンド ライン引数を指定します。  
  
    -   **-Publisher**  
  
    -   **-PublisherDB**  
  
    -   **-Publication**  
  
    -   **-Distributor**  
  
    -   **-Subscriber**  
  
    -   **-SubscriberDB**  
  
    -   **-SubscriptionType = 0**  
  
     SQL Server 認証を使用する場合は、次の引数も指定する必要があります。  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-DistributorSecurityMode = 0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-PublisherSecurityMode = 0**  
  
    -   **-SubscriberLogin**  
  
    -   **-SubscriberPassword**  
  
    -   **-SubscriberSecurityMode = 0**  
  
        > [!IMPORTANT]  
        >  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
###  <a name="TsqlExample"></a> 例 (レプリケーション エージェント)  
 次の例では、ディストリビューション エージェントを開始してプッシュ サブスクリプションを同期します。  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksProductsTran  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4  
  
```  
  
 次の例では、マージ エージェントを開始してプッシュ サブスクリプションを同期します。  
  
```  
  
REM -- Declare the variables.  
SET Publisher=%instancename%  
SET Subscriber=%instancename%  
SET PublicationDB=AdventureWorks2012  
SET SubscriptionDB=AdventureWorks2012Replica   
SET Publication=AdvWorksSalesOrdersMerge  
  
REM -- Start the Merge Agent.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher %Publisher%   
-Subscriber  %Subscriber%  -Distributor %Publisher% -PublisherDB  %PublicationDB%   
-SubscriberDB %SubscriptionDB% -Publication %Publication% -PublisherSecurityMode 1   
-OutputVerboseLevel 3  -Output -SubscriberSecurityMode 1  -SubscriptionType 0   
-DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) およびマネージ コードを使用してレプリケーション エージェント機能にアクセスすることで、プッシュ サブスクリプションをプログラムから同期できます。 プッシュ サブスクリプションを同期する際に使用するクラスは、サブスクリプションが属しているパブリケーションの種類によって異なります。  
  
> [!NOTE]  
>  アプリケーションに影響を及ぼすことなく、自立的に実行される同期を開始するには、エージェントを非同期的に起動します。 ただし、同期処理中に同期の結果を監視し、エージェントからのコールバックを受け取る場合 (たとえば、進行状況バーを表示する場合)、エージェントを同期的に起動する必要があります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] サブスクライバーの場合、エージェントを同期的に起動する必要があります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを同期するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスし、次のプロパティを設定します。  
  
    -   パブリケーション データベース名を <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>します。  
  
    -   サブスクリプションが所属するパブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>します。  
  
    -   サブスクリプション データベースの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>します。  
  
    -   場合は、サブスクライバーの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>します。  
  
    -   手順 1. で作成した接続 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 残りのサブスクリプションのプロパティを取得します。 このメソッドが **false**を返す場合、サブスクリプションが存在するかどうかをご確認ください。  
  
4.  次のいずれかの方法で、ディストリビューターのディストリビューション エージェントを起動します。  
  
    -   呼び出す、 <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizeWithJob%2A> メソッドのインスタンスを <xref:Microsoft.SqlServer.Replication.TransSubscription> 手順 2. でします。 このメソッドは、ディストリビューション エージェントを非同期的に起動するため、エージェント ジョブの実行中、制御が直ちにアプリケーションに返されます。 値は、サブスクリプションが作成された場合、このメソッドを呼び出すことができない **false** の <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>します。  
  
    -   インスタンスを取得、 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> クラスからの <xref:Microsoft.SqlServer.Replication.TransSubscription.SynchronizationAgent%2A> プロパティ、および呼び出し、 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Synchronize%2A> メソッドです。 このメソッドにより、エージェントが同期的に起動され、制御は実行中のエージェント ジョブに残ります。 同期の実行中に処理することができます、 <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent.Status> イベント、エージェントを実行します。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを同期するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスし、次のプロパティを設定します。  
  
    -   パブリケーション データベース名を <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>します。  
  
    -   サブスクリプションが所属するパブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>します。  
  
    -   サブスクリプション データベースの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>します。  
  
    -   場合は、サブスクライバーの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>します。  
  
    -   手順 1. で作成した接続 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 残りのサブスクリプションのプロパティを取得します。 このメソッドが **false**を返す場合、サブスクリプションが存在するかどうかをご確認ください。  
  
4.  次のいずれかの方法で、ディストリビューターのマージ エージェントを起動します。  
  
    -   呼び出す、 <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizeWithJob%2A> メソッドのインスタンスを <xref:Microsoft.SqlServer.Replication.MergeSubscription> 手順 2. でします。 このメソッドは、マージ エージェントを非同期的に起動するため、エージェント ジョブの実行中、制御が直ちにアプリケーションに返されます。 値は、サブスクリプションが作成された場合、このメソッドを呼び出すことができない **false** の <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A>します。  
  
    -   インスタンスを取得、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> クラスからの <xref:Microsoft.SqlServer.Replication.MergeSubscription.SynchronizationAgent%2A> プロパティ、および呼び出し、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Synchronize%2A> メソッドです。 このメソッドにより、マージ エージェントが同期的に起動され、制御は実行中のエージェント ジョブに残ります。 同期の実行中に処理することができます、 <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent.Status> イベント、エージェントを実行します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションへのプッシュ サブスクリプションを同期します。エージェントはエージェント ジョブを使用して非同期的に起動されます。  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub_withjob)]  
  
 次の例では、トランザクション パブリケーションへのプッシュ サブスクリプションを同期します。エージェントは同期的に起動されます。  
  
 [!code-csharp[HowTo#rmo_SyncTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_synctranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_synctranpushsub)]  
  
 次の例では、マージ パブリケーションへのプッシュ サブスクリプションを同期します。エージェントはエージェント ジョブを使用して非同期的に起動されます。  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub_withjob)]  
  
 次の例では、マージ パブリケーションへのプッシュ サブスクリプションを同期します。エージェントは同期的に起動されます。  
  
 [!code-csharp[HowTo#rmo_SyncMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_syncmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_SyncMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_syncmergepushsub)]  
  
## 参照  
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [データの同期](../../relational-databases/replication/synchronize-data.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  