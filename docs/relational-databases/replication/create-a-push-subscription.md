---
title: "プッシュ サブスクリプションの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "push subscriptions [SQL Server replication], creating"
  - "merge replication subscribing [SQL Server replication], push subscriptions"
  - "subscriptions [SQL Server replication], push"
  - "snapshot replication [SQL Server], subscribing"
  - "トランザクション レプリケーション、サブスクライブ"
ms.assetid: adfbbc61-58d1-4330-9ad6-b14ab1142e2b
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# プッシュ サブスクリプションの作成
  このトピックでのプッシュ サブスクリプションを作成する方法について説明 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 、[!INCLUDE[tsql](../../includes/tsql-md.md)], 、またはレプリケーション管理オブジェクト (RMO)。 以外のプッシュ サブスクリプションを作成する方法について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーを参照してください [非 SQL Server サブスクライバーのサブスクリプションを作成](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)します。  
  
 
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 サブスクリプションの新規作成ウィザードを使用して、パブリッシャーまたはサブスクライバーでプッシュ サブスクリプションを作成します。 ウィザードのページに従って、次の操作を実行します。  
  
-   パブリッシャーとパブリケーションを指定します。  
  
-   レプリケーション エージェントが実行される場所を選択します。 プッシュ サブスクリプションを選択 **ディストリビューター (プッシュ サブスクリプション) ですべてのエージェントを実行** で、 **ディストリビューション エージェントの場所** ページまたは **マージ エージェントの場所** ] ページで、パブリケーションの種類によって異なります。  
  
-   サブスクライバーとサブスクリプション データベースを指定します。  
  
-   レプリケーション エージェントによって作成された接続に対して使用されるログインとパスワードを指定します。  
  
    -   スナップショット パブリケーションとトランザクション パブリケーションに対するサブスクリプションでは、 **[ディストリビューション エージェント セキュリティ]** ページで資格情報を指定します。  
  
    -   マージ パブリケーションに対するサブスクリプションでは、 **[マージ エージェント セキュリティ]** ページで資格情報を指定します。  
  
     各エージェントで必要な権限については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
-   同期スケジュール、およびサブスクライバーをいつ初期化するかを指定します。  
  
-   マージ パブリケーションの追加オプションとして、サブスクリプションの種類、およびパラメーター化されたフィルターの値を指定します。  
  
-   サブスクリプションの更新が許可されるトランザクション パブリケーションの追加オプションを指定します。サブスクライバーがパブリッシャーで変更をすぐにコミットするかどうか、変更をキューに書き込むかどうか、およびサブスクライバーからパブリッシャーへの接続に使用される資格情報を指定します。  
  
-   必要に応じて、サブスクリプションのスクリプトを作成します。  
  
#### パブリッシャーからプッシュ サブスクリプションを作成するには  
  
1.   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、1 つまたは複数のサブスクリプションを作成するパブリケーションを右クリックして **新規サブスクリプション**します。  
  
4.  サブスクリプションの新規作成ウィザードのページに従って操作を実行します。  
  
#### サブスクライバーからプッシュ サブスクリプションを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開します。  
  
3.  右クリックし、 **ローカル サブスクリプション** フォルダー、およびクリック **新規サブスクリプション**します。  
  
4.   **パブリケーション** の新しいサブスクリプション ウィザード、[選択] ページ **\< SQL Server パブリッシャーの検索>** または **\< Oracle パブリッシャーの検索>** から、 **パブリッシャー** ボックスの一覧です。  
  
5.  **[サーバーへの接続]** ダイアログ ボックスでパブリッシャーに接続します。  
  
6.  **[パブリケーション]** ページでパブリケーションを選択します。  
  
7.  サブスクリプションの新規作成ウィザードのページに従って操作を実行します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 プッシュ サブスクリプションは、レプリケーション ストアド プロシージャを使用してプログラムで作成できます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって変わります。  
  
> **重要: ** 可能であれば、実行時にセキュリティ資格情報の入力を求めるメッセージをユーザーに対して表示します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを作成するには  
  
1.  パブリッシャー側でパブリケーション データベースで実行することによって、パブリケーションがプッシュ サブスクリプションをサポートしていることを確認します [sp_helppublication](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)します。  
  
    -   場合の値 **allow_push** は **1**, 、プッシュ サブスクリプションはサポートされています。  
  
    -   場合の値 **allow_push** は **0**, 、実行 [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), を指定して **allow_push** の **@property** と **true** の **@value**します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addsubscription](https://msdn.microsoft.com/library/ms181702.aspx)します。 指定 **@publication**, 、**@subscriber** と **@destination_db**します。 値を指定して **プッシュ** の **@subscription_type**します。 サブスクリプションを更新する方法については、次を参照してください。 [トランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](https://msdn.microsoft.com/library/ms152769.aspx)です。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)します。 次の指定を行います。  
  
    -    **@Subscriber**, 、**@subscriber_db**, 、および **@publication** パラメーター。  
  
    -    [!INCLUDE[msCoName](../../includes/msconame-md.md)] のディストリビューターでディストリビューション エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**します。  
  
        > **注:** 常に Windows 統合認証を使用して確立された接続で指定された Windows 資格情報を使用して **@job_login** と **@job_password**します。 ディストリビューション エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。 既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。  
  
    -   (省略可能)値 **0** の **@subscriber_security_mode** と [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@subscriber_login** と **@subscriber_password**します。 サブスクライバーに接続するときに SQL Server 認証を使用する必要がある場合、これらのパラメーターを指定します。  
  
    -   このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。 詳しくは、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。  
  
    > **重要!!** リモート ディストリビューター、すべてのパラメーターの指定された値を使用するパブリッシャー側でプッシュ サブスクリプションを作成するときに含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)」を参照してください。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを作成するには  
  
1.  パブリッシャー側でパブリケーション データベースで実行することによって、パブリケーションがプッシュ サブスクリプションをサポートしていることを確認します [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)します。  
  
    -   場合の値 **allow_push** は **1**, 、パブリケーションがプッシュ サブスクリプションをサポートしています。  
  
    -   場合の値 **allow_push** は **1**, 、実行 [sp_changemergepublication](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), を指定して **allow_push** の **@property** と **true** の **@value**します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergesubscription](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md), 、次のパラメーターを指定します。  
  
    -   **@publication**。 これはパブリケーションの名前です。  
  
    -   **@subscriber_type**します。 クライアント サブスクリプションの場合は **local** を指定し、サーバー サブスクリプションの場合は **global**を指定します。  
  
    -   **@subscription_priority**します。 サーバー サブスクリプションでは、サブスクリプションの優先順位を指定します (**0.00** に **99.99**)。  
  
         詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepushsubscription-agent-transact-sql.md)します。 次の指定を行います。  
  
    -    **@Subscriber**, 、**@subscriber_db**, 、および **@publication** パラメーター。  
  
    -   ディストリビューターでマージ エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**します。  
  
        > **注:**  常に Windows 統合認証を使用して確立された接続で指定された Windows 資格情報を使用して **@job_login** と **@job_password**します。 マージ エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。 既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。  
  
    -   (省略可能)値 **0** の **@subscriber_security_mode** と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@subscriber_login** と **@subscriber_password**します。 サブスクライバーに接続するときに SQL Server 認証を使用する必要がある場合、これらのパラメーターを指定します。  
  
    -   (省略可能)値 **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 パブリッシャーに接続するときに SQL Server 認証を使用する必要がある場合、これらの値を指定します。  
  
    -   このサブスクリプションでのマージ エージェント ジョブのスケジュール。 詳しくは、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。  
  
    > **重要!!** リモート ディストリビューター、すべてのパラメーターの指定された値を使用するパブリッシャー側でプッシュ サブスクリプションを作成するときに含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)」を参照してください。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、トランザクション パブリケーションに対するプッシュ サブスクリプションを作成します。 ログインとパスワードの値は、実行時に **sqlcmd** スクリプト変数を使用して入力されます。  
  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_1.sql)]  
  
 次の例では、マージ パブリケーションに対するプッシュ サブスクリプションを作成します。 ログインとパスワードの値は、実行時に **sqlcmd** スクリプト変数を使用して入力されます。  
  
 [!code-sql[HowTo#sp_addmergepushsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/create-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってプッシュ サブスクリプションを作成できます。 プッシュ サブスクリプションを作成する際に使用する RMO クラスは、作成するサブスクリプションの対象となるパブリケーションの種類によって異なります。  
  
> **重要: ** 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを作成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> 手順 1. のパブリッシャーの接続を使用してクラスです。 指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, 、および <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、手順 2. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。  
  
4.  ビットごとの論理 AND を実行 (**&** Visual C# の場合と **と** Visual Basic で) の間、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティと <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>します。 結果の場合 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, 、設定されて <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> の論理和演算の結果に (**|** Visual C# の場合と **または** Visual Basic で) の間で <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> と <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>します。 次に、呼び出す <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> プッシュ サブスクリプションを有効にします。  
  
5.  サブスクリプション データベースが存在しない場合は作成を使用して、 <xref:Microsoft.SqlServer.Management.Smo.Database> クラスです。 詳細については、次を参照してください。 [の作成、変更、および削除するデータベース](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md)します。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスです。  
  
7.  次のサブスクリプション プロパティを設定します。  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> で作成したパブリッシャーには、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   サブスクリプション データベースの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>します。  
  
    -   場合は、サブスクライバーの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>します。  
  
    -   パブリケーション データベースの名前 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>します。  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> または <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> の資格情報を提供する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ディストリビューターでディストリビューション エージェントを実行する Windows アカウントです。 このアカウントは、ディストリビューターとのローカル接続を確立したり、Windows 認証を使用したリモート接続を確立するときに使用されます。  
  
        > **注:** 設定 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> のメンバーによって、サブスクリプションが作成された場合は必要ありません、 **sysadmin** 固定サーバー ロールを推奨します。 この場合、エージェントは SQL Server エージェントのアカウントを借用します。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能)値 **true** (既定値) の <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> サブスクリプションの同期に使用されるエージェント ジョブを作成します。 **false**を指定した場合、サブスクリプションはプログラムでのみ同期が可能になります。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> SQL Server 認証を使用してサブスクライバーに接続する場合。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> メソッドです。  
  
    > **重要な!!**リモート ディストリビューター、すべてのプロパティの指定された値を使用するパブリッシャー側でプッシュ サブスクリプションを作成するときに含む <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, 、ディストリビューターにプレーン テキストとして送信されます。 発行元と呼び出しの前にリモート ディストリビューター間の接続を暗号化する必要があります、 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> メソッドです。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)」を参照してください。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを作成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 1. のパブリッシャーの接続を使用してクラスです。 指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, 、および <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、手順 2. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。  
  
4.  ビットごとの論理 AND を実行 (**&** Visual C# の場合と **と** Visual Basic で) の間、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティと <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>します。 結果の場合 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, 、設定されて <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> の論理和演算の結果に (**|** Visual C# の場合と **または** Visual Basic で) の間で <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> と <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPush>します。 次に、呼び出す <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> プッシュ サブスクリプションを有効にします。  
  
5.  サブスクリプション データベースが存在しない場合は作成を使用して、 <xref:Microsoft.SqlServer.Management.Smo.Database> クラスです。 詳細については、次を参照してください。 [の作成、変更、および削除するデータベース](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md)します。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスです。  
  
7.  次のサブスクリプション プロパティを設定します。  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> で作成したパブリッシャーには、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   サブスクリプション データベースの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>します。  
  
    -   場合は、サブスクライバーの名前 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>します。  
  
    -   パブリケーション データベースの名前 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>します。  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> または <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> の資格情報を提供する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、ディストリビューター側でマージ エージェントが実行される Windows アカウントです。 このアカウントは、ディストリビューターとのローカル接続を確立したり、Windows 認証を使用したリモート接続を確立するときに使用されます。  
  
        > **注:** 設定 <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A> のメンバーによって、サブスクリプションが作成された場合は必要ありません、 **sysadmin** 固定サーバー ロールを推奨します。 この場合、エージェントは SQL Server エージェントのアカウントを借用します。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能)値 **true** (既定値) の <xref:Microsoft.SqlServer.Replication.Subscription.CreateSyncAgentByDefault%2A> サブスクリプションの同期に使用されるエージェント ジョブを作成します。 **false**を指定した場合、サブスクリプションはプログラムでのみ同期が可能になります。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberSecurity%2A> SQL Server 認証を使用してサブスクライバーに接続する場合。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> SQL Server 認証を使用してパブリッシャーに接続する場合。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> メソッドです。  
  
    > **重要: **  リモート ディストリビューター、すべてのプロパティの指定された値を使用するパブリッシャー側でプッシュ サブスクリプションを作成するときに含む <xref:Microsoft.SqlServer.Replication.Subscription.SynchronizationAgentProcessSecurity%2A>, 、ディストリビューターにプレーン テキストとして送信されます。 発行元と呼び出しの前にリモート ディストリビューター間の接続を暗号化する必要があります、 <xref:Microsoft.SqlServer.Replication.Subscription.Create%2A> メソッドです。 詳細については、「[データベース エンジンへの暗号化接続の有効化 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)」を参照してください。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションに対する新しいプッシュ サブスクリプションを作成します。 ディストリビューション エージェント ジョブを実行するために使用される Windows アカウントの資格情報は、実行時に渡されます。  
  
 [!code-csharp[HowTo#rmo_CreateTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpushsub)]  
  
 次の例では、マージ パブリケーションに対する新しいプッシュ サブスクリプションを作成します。 マージ エージェント ジョブを実行するために使用される Windows アカウントの資格情報は、実行時に渡されます。  
  
 [!code-csharp[HowTo#rmo_CreateMergePushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepushsub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepushsub)]  
  
## 参照  
 [プッシュ サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [プッシュ サブスクリプションの同期](../../relational-databases/replication/synchronize-a-push-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sqlcmd でのスクリプト変数の使用](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  