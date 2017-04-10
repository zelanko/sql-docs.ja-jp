---
title: "サブスクリプションの再初期化 | Microsoft Docs"
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
  - "サブスクリプションの初期化 [SQL Server レプリケーション]、再初期化"
  - "サブスクリプション [SQL Server レプリケーション]、再初期化"
  - "サブスクリプションの再初期化"
ms.assetid: ca3625c5-c62e-4ab7-9829-d511f838e385
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# サブスクリプションの再初期化
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、サブスクリプションを再初期化する方法について説明します。 次回の同期で新しいスナップショットが適用されるように、個別のサブスクリプションに再初期化のマークを付けることができます。  
  
 **このトピックの内容**  
  
-   **サブスクリプションを再初期化するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 サブスクリプションの再初期化には、2 段階の処理があります。  
  
1.  パブリケーションの単一のサブスクリプションまたはすべてのサブスクリプションが再初期化対象として *マーク* されます。 サブスクリプションの再初期化用にマーク、 **サブスクリプションの再初期化** ] ダイアログ ボックスから利用できる、 **ローカル パブリケーション** フォルダーおよび **ローカル サブスクリプション** フォルダーに [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 また、 **[すべてのサブスクリプション]** タブやレプリケーション モニターのパブリケーション ノードからマークを設定することもできます。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。 サブスクリプションの再初期化の設定には、以下のオプションがあります。  
  
     **[現在のスナップショットを使用する]**  
     このオプションを選択すると、次にディストリビューション エージェントまたはマージ エージェントが実行されたときに、現在のスナップショットがサブスクライバーに適用されます。 有効なスナップショットが使用できない場合、このオプションは選択できません。  
  
     **[新しいスナップショットを使用する]**  
     このオプションを選択すると、新しいスナップショットによってサブスクリプションが再初期化されます。 スナップショットは、スナップショット エージェントによって生成された後にだけ、サブスクライバーに適用できます。 スナップショットがスケジュールに従って実行されるように設定している場合は、スナップショット エージェントが次回実行されて終了するまでサブスクリプションを再初期化できません。 スナップショット エージェントをすぐに開始するには、 **[今すぐ新しいスナップショットを生成する]** を選択します。  
  
     **[再初期化する前に、同期されていない変更をアップロード]**  
     マージ レプリケーションのみです。 このオプションを選択すると、サブスクライバーのデータがスナップショットで上書きされる前に、保留中の変更がサブスクリプション データベースからアップロードされます。  
  
     パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
2.  サブスクリプションは、次回同期されるときに再初期化されます。ディストリビューション エージェント (トランザクション レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) により、再初期化するように設定されている各サブスクライバーに最新のスナップショットが適用されます。 サブスクリプションの同期の詳細については、次を参照してください。 [プッシュ サブスクリプションを同期する](../../relational-databases/replication/synchronize-a-push-subscription.md) と [プル サブスクリプションを同期する](../../relational-databases/replication/synchronize-a-pull-subscription.md)です。  
  
#### Management Studio で単一のプッシュ サブスクリプションまたはプル サブスクリプションに再初期化を設定するには (パブリッシャーで実行)  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  再初期化するサブスクリプションが含まれているパブリケーションを展開します。  
  
4.  サブスクリプションの場合を右クリックし、をクリックし、 **を再初期化**します。  
  
5.   **サブスクリプションの再初期化** ] ダイアログ ボックスでオプションを選択し、をクリックし、 **再初期化のマークを付ける**します。  
  
#### Management Studio で単一のプル サブスクリプションに再初期化を設定するには (サブスクライバーで実行)  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  サブスクリプションの場合を右クリックし、をクリックし、 **を再初期化**します。  
  
4.  表示される確認のダイアログ ボックスで、 **[はい]**をクリックします。  
  
#### Management Studio ですべてのサブスクリプションに再初期化を設定するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、再初期化するサブスクリプションを含むパブリケーションを右クリックして **すべてのサブスクリプションを再初期化**します。  
  
4.   **サブスクリプションの再初期化** ] ダイアログ ボックスでオプションを選択し、をクリックし、 **再初期化のマークを付ける**します。  
  
#### レプリケーション モニターで単一のプッシュ サブスクリプションまたはプル サブスクリプションに再初期化を設定するには  
  
1.  レプリケーション モニターで、左ペインのパブリッシャー グループを展開し、パブリッシャーを展開してパブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  クリックして、再初期化するサブスクリプションを右クリックして **サブスクリプションの再初期化**します。  
  
4.   **サブスクリプションの再初期化** ] ダイアログ ボックスでオプションを選択し、をクリックし、 **再初期化のマークを付ける**します。  
  
#### レプリケーション モニターですべてのサブスクリプションに再初期化を設定するには  
  
1.  レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。  
  
2.  クリックして、再初期化するサブスクリプションを含むパブリケーションを右クリックして **すべてのサブスクリプションを再初期化**します。  
  
3.   **サブスクリプションの再初期化** ] ダイアログ ボックスでオプションを選択し、をクリックし、 **再初期化のマークを付ける**します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 サブスクリプションは、プログラムでレプリケーション ストアド プロシージャを使用して再初期化できます。 使用するストアド プロシージャは、サブスクリプションの種類 (プッシュまたはプル) およびサブスクリプションが属しているパブリケーションの種類によって変わります。  
  
#### トランザクション パブリケーションに対するプル サブスクリプションを再初期化するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_reinitpullsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-reinitpullsubscription-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、および **@publication**します。 これにより、ディストリビューション エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。  
  
2.  (省略可) サブスクライバーでディストリビューション エージェントを起動し、サブスクリプションを同期します。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
#### トランザクション パブリケーションに対するプッシュ サブスクリプションを再初期化するには  
  
1.  パブリッシャーで実行 [sp_reinitsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-reinitsubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, 、および **@destination_db**します。 これにより、ディストリビューション エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。  
  
2.  (省略可) ディストリビューターでディストリビューション エージェントを起動し、サブスクリプションを同期します。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
#### マージ パブリケーションに対するプル サブスクリプションを再初期化するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_reinitmergepullsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、および **@publication**します。 再初期化を実行する前に、サブスクライバーからの変更をアップロードするには、値を指定 **true** の **@upload_first**します。 これにより、マージ エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。  
  
    > [!IMPORTANT]  
    >  パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
2.  (省略可) サブスクライバーでマージ エージェントを起動し、サブスクリプションを同期します。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを再初期化するには  
  
1.  パブリッシャーで実行 [sp_reinitmergesubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-reinitmergesubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, 、および **@subscriber_db**します。 再初期化を実行する前に、サブスクライバーからの変更をアップロードするには、値を指定 **true** の **@upload_first**します。 これにより、ディストリビューション エージェントの次回実行時に再初期化するようにサブスクリプションにマークが付けられます。  
  
    > [!IMPORTANT]  
    >  パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
2.  (省略可) ディストリビューターでマージ エージェントを起動し、サブスクリプションを同期します。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
#### 新しいマージ パブリケーションを作成するときに再初期化ポリシーを設定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md), 、次のいずれかの値を指定する **@automatic_reinitialization_policy**:。  
  
    -   **1** -サブスクリプションが自動的に再初期化される前に、サブスクライバーから変更をアップロード、パブリケーションへの変更で必要とします。  
  
    -   **0** -サブスクリプションが自動的に再初期化されると、サブスクライバーの変更は破棄されます、パブリケーションへの変更で必要とします。  
  
    > [!IMPORTANT]  
    >  パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
     詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### 既存のマージ パブリケーションの再初期化ポリシーを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), を指定して **automatic_reinitialization_policy** の **@property** し、次のいずれかの値を **@value**:。  
  
    -   **1** -サブスクリプションが自動的に再初期化される前に、サブスクライバーから変更をアップロード、パブリケーションへの変更で必要とします。  
  
    -   **0** -サブスクリプションが自動的に再初期化されると、サブスクライバーの変更は破棄されます、パブリケーションへの変更で必要とします。  
  
    > [!IMPORTANT]  
    >  パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
     詳しくは、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」をご覧ください。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 次回の同期で新しいスナップショットが適用されるように、個別のサブスクリプションに再初期化のマークを付けることができます。 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってサブスクリプションを再初期化できます。 使用するクラスは、サブスクリプションが属するパブリケーションの種類と、サブスクリプションの種類 (プッシュ サブスクリプションまたはプル サブスクリプション) に応じて変わります。  
  
#### トランザクション パブリケーションに対するプル サブスクリプションを再初期化するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラス <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, 、および手順 1. の接続 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。  
  
    > [!NOTE]  
    >  このメソッドが戻る場合 **false**, 、手順 2. でサブスクリプション プロパティが正しく定義されていないか、プル サブスクリプションが存在しません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.Reinitialize%2A> メソッドです。 このメソッドにより、サブスクリプションを再初期化するようにマークされます。  
  
5.  プル サブスクリプションを同期します。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
#### トランザクション パブリケーションに対するプッシュ サブスクリプションを再初期化するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> クラス <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, 、および手順 1. の接続 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。  
  
    > [!NOTE]  
    >  このメソッドが戻る場合 **false**, 、手順 2. でサブスクリプション プロパティが正しく定義されていないか、プッシュ サブスクリプションが存在しません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.TransSubscription.Reinitialize%2A> メソッドです。 このメソッドにより、サブスクリプションを再初期化するようにマークされます。  
  
5.  プッシュ サブスクリプションを同期します。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
#### マージ パブリケーションに対するプル サブスクリプションを再初期化するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラス <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>, 、および手順 1. の接続 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。  
  
    > [!NOTE]  
    >  このメソッドが戻る場合 **false**, 、手順 2. でサブスクリプション プロパティが正しく定義されていないか、プル サブスクリプションが存在しません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.Reinitialize%2A> メソッドです。 再初期化の前に **true** を渡してサブスクライバーの変更をアップロードするか、 **false** を渡して再初期化し、サブスクライバーの保留中の変更をすべて破棄します。 このメソッドにより、サブスクリプションを再初期化するようにマークされます。  
  
    > [!NOTE]  
    >  サブスクリプションの有効期限が切れると、変更をアップロードできません。 詳しくは、「 [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md)」をご覧ください。  
  
5.  プル サブスクリプションを同期します。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを再初期化するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラス <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, 、および手順 1. の接続 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。  
  
    > [!NOTE]  
    >  このメソッドが戻る場合 **false**, 、手順 2. でサブスクリプション プロパティが正しく定義されていないか、プッシュ サブスクリプションが存在しません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergeSubscription.Reinitialize%2A> メソッドです。 再初期化の前に **true** を渡してサブスクライバーの変更をアップロードするか、 **false** を渡して再初期化し、サブスクライバーの保留中の変更をすべて破棄します。 このメソッドにより、サブスクリプションを再初期化するようにマークされます。  
  
    > [!NOTE]  
    >  サブスクリプションの有効期限が切れると、変更をアップロードできません。 詳しくは、「 [Set the Expiration Period for Subscriptions](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md)」をご覧ください。  
  
5.  プッシュ サブスクリプションを同期します。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションに対するプル サブスクリプションを再初期化します。  
  
 [!code-csharp[HowTo#rmo_ReinitTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinittranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinittranpullsub)]  
  
 次の例では、最初にサブスクライバーの保留中の変更をアップロードした後、マージ パブリケーションに対するプル サブスクリプションを初期化します。  
  
 [!code-csharp[HowTo#rmo_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_reinitmergepullsub_withupload)]  
  
 [!code-vb[HowTo#rmo_vb_ReinitMergePullSub_WithUpload](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_reinitmergepullsub_withupload)]  
  
## 参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  