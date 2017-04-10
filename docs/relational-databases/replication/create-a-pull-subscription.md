---
title: "プル サブスクリプションの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pull subscriptions [SQL Server replication], creating"
  - "merge replication subscribing [SQL Server replication], pull subscriptions"
  - "subscriptions [SQL Server replication], pull"
  - "snapshot replication [SQL Server], subscribing"
  - "トランザクション レプリケーション、サブスクライブ"
ms.assetid: 41d1886d-59c9-41fc-9bd6-a59b40e0af6e
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# プル サブスクリプションの作成
  このトピックの説明でプル サブスクリプションを作成する方法 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], 、[!INCLUDE[tsql](../../includes/tsql-md.md)], 、またはレプリケーション管理オブジェクト (RMO)。  
  
 P2P レプリケーションのプル サブスクリプションの設定にはスクリプトを使用できますが、ウィザードは使用できません。  
 
  ##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 サブスクリプションの新規作成ウィザードを使用して、パブリッシャーまたはサブスクライバーでプル サブスクリプションを作成します。 ウィザードのページに従って、次の操作を実行します。  
  
-   パブリッシャーとパブリケーションを指定します。  
  
-   レプリケーション エージェントが実行される場所を選択します。 プル サブスクリプションを選択 **サブスクライバー (プル サブスクリプション) で各エージェントを実行** で、 **ディストリビューション エージェントの場所** ページまたは **マージ エージェントの場所**  ページで、パブリケーションの種類によって異なります。  
  
-   サブスクライバーとサブスクリプション データベースを指定します。  
  
-   レプリケーション エージェントによって作成された接続に対して使用されるログインとパスワードを指定します。  
  
    -   スナップショット パブリケーションとトランザクション パブリケーションに対するサブスクリプションでは、 **[ディストリビューション エージェント セキュリティ]** ページで資格情報を指定します。  
  
    -   マージ パブリケーションに対するサブスクリプションでは、 **[マージ エージェント セキュリティ]** ページで資格情報を指定します。  
  
     各エージェントで必要な権限については、次を参照してください。 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)します。  
  
-   同期スケジュール、およびサブスクライバーをいつ初期化するかを指定します。  
  
-   マージ パブリケーションの追加オプションである、サブスクリプションの種類、パラメーター化されたフィルターの値、およびパブリケーションが Web 同期に対して有効になっている場合の HTTPS を使用した同期に関する情報を指定します。  
  
-   サブスクリプションの更新が許可されるトランザクション パブリケーションの追加オプションを指定します。サブスクライバーがパブリッシャーで変更をすぐにコミットするかどうか、変更をキューに書き込むかどうか、およびサブスクライバーからパブリッシャーへの接続に使用される資格情報を指定します。  
  
-   必要に応じて、サブスクリプションのスクリプトを作成します。  
  
#### パブリッシャーからプル サブスクリプションを作成するには  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、1 つまたは複数のサブスクリプションを作成するパブリケーションを右クリックして **新規サブスクリプション**します。  
  
4.  サブスクリプションの新規作成ウィザードのページに従って操作を実行します。  
  
#### サブスクライバーからプル サブスクリプションを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開します。  
  
3.  右クリックし、 **ローカル サブスクリプション** フォルダー、およびクリック **新規サブスクリプション**します。  
  
4.  **パブリケーション** の新しいサブスクリプション ウィザード、[選択] ページ **\< SQL Server パブリッシャーの検索>** または **\< Oracle パブリッシャーの検索>** から、 **パブリッシャー** ボックスの一覧です。  
  
5.  **[サーバーへの接続]** ダイアログ ボックスでパブリッシャーに接続します。  
  
6.  **[パブリケーション]** ページでパブリケーションを選択します。  
  
7.  サブスクリプションの新規作成ウィザードのページに従って操作を実行します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーション ストアド プロシージャを使用して、プル サブスクリプションをプログラムで作成できます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって変わります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを作成するには  
  
1.  パブリッシャーで実行することによって、パブリケーションがプル サブスクリプションをサポートしていることを確認します [sp_helppublication &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)します。  
  
    -   場合の値 **allow_pull** 結果セットが **1**, 、パブリケーションはプル サブスクリプションをサポートし、します。  
  
    -   場合の値 **allow_pull** は **0**, 、実行 [sp_changepublication &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), を指定して **allow_pull** の **@property** と **true** の **@value**します。  
  
2.  サブスクライバーで、次のように実行します。 [sp_addpullsubscription &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)します。 **@publisher** と **@publication**を指定します。 サブスクリプションの更新については、次を参照してください。 [トランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](https://msdn.microsoft.com/library/ms152769.aspx)です。  
  
3.  サブスクライバーで、次のように実行します。 [sp_addpullsubscription_agent &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)します。 次の指定を行います。  
  
    -   **@Publisher**, 、**@publisher_db**, 、および **@publication** パラメーター。  
  
    -   [!INCLUDE[msCoName](../../includes/msconame-md.md)] のサブスクライバーでディストリビューション エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**します。  
  
        > [!NOTE]  
        >  常に Windows 統合認証を使用して確立された接続で指定された Windows 資格情報を使用して **@job_login** と **@job_password**します。 ディストリビューション エージェントは、常に Windows 統合認証を使用してサブスクライバーへのローカル接続を作成します。 既定では、エージェントは Windows 統合認証を使用してディストリビューターに接続します。  
  
    -   (省略可能)値 **0** の **@distributor_security_mode** との SQL Server ログイン情報 **@distributor_login** と **@distributor_password**, 、ディストリビューターに接続するときに、SQL Server 認証を使用する必要がある場合、します。  
  
    -   このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。 詳しくは、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。  
  
4.  パブリッシャーで実行 [sp_addsubscription &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) プル サブスクリプションを登録します。 指定 **@publication**, 、**@subscriber**, 、および **@destination_db**します。 値を指定して **プル** の **@subscription_type**します。  
  
#### マージ パブリケーションに対するプル サブスクリプションを作成するには  
  
1.  パブリッシャーで実行することによって、パブリケーションがプル サブスクリプションをサポートしていることを確認します [sp_helpmergepublication &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)します。  
  
    -   場合の値 **allow_pull** 結果セットが **1**, 、パブリケーションはプル サブスクリプションをサポートし、します。  
  
    -   場合の値 **allow_pull** は **0**, 、実行 [sp_changemergepublication &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), を指定して **allow_pull** の **@property** と **true** の **@value**します。  
  
2.  サブスクライバーで、次のように実行します。 [sp_addmergepullsubscription &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、および次のパラメーター。  
  
    -   **@subscriber_type** – 指定 **ローカル** クライアント サブスクリプションに対すると **グローバル** サーバー サブスクリプションです。  
  
    -   **@subscription_priority** – サブスクリプションの優先順位を指定 (**0.00** に **99.99**)。 これは、サーバー サブスクリプションにのみ必要です。  
  
         詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。  
  
3.  サブスクライバーで、次のように実行します。 [sp_addmergepullsubscription_agent &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)します。 次のパラメーターを指定します。  
  
    -   **@publisher**, 、**@publisher_db**, 、および **@publication**します。  
  
    -   サブスクライバーでマージ エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**します。  
  
        > [!NOTE]  
        >  常に Windows 統合認証を使用して確立された接続で指定された Windows 資格情報を使用して **@job_login** と **@job_password**します。 マージ エージェントは、常に Windows 統合認証を使用してサブスクライバーへのローカル接続を作成します。 既定では、エージェントは Windows 統合認証を使用してディストリビューターおよびパブリッシャーに接続します。  
  
    -   (省略可能)値 **0** の **@distributor_security_mode** と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@distributor_login** と **@distributor_password**, を使用する必要がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ディストリビューターに接続するときに認証します。  
  
    -   (省略可能)値 **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**, を使用する必要がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、パブリッシャーに接続するときに認証します。  
  
    -   このサブスクリプションでのマージ エージェント ジョブのスケジュール。 詳細については、次を参照してください。 [トランザクション パブリケーションに対する更新可能なサブスクリプションを作成する](https://msdn.microsoft.com/library/ms152769.aspx)です。  
  
4.  パブリッシャーで実行 [sp_addmergesubscription &#40; です。Transact SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, 、**@subscriber_db**, の値との **プル** の **@subscription_type**します。 これにより、プル サブスクリプションが登録されます。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、トランザクション パブリケーションに対するプル サブスクリプションを作成します。 最初のバッチはサブスクライバーで実行され、2 番目のバッチはパブリッシャーで実行されます。 ログインとパスワードの値は、実行時に sqlcmd スクリプト変数を使用して入力されます。  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
  
-- At the subscription database, create a pull subscription   
-- to a transactional publication.  
USE [AdventureWorksReplica]  
EXEC sp_addpullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.  
EXEC sp_addpullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password);  
GO  
```  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Publisher.  
DECLARE @publication AS sysname;  
DECLARE @subscriber AS sysname;  
DECLARE @subscriptionDB AS sysname;  
SET @publication = N'AdvWorksProductTran';  
SET @subscriber = $(SubServer);  
SET @subscriptionDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
EXEC sp_addsubscription   
  @publication = @publication,   
  @subscriber = @subscriber,   
  @destination_db = @subscriptionDB,   
  @subscription_type = N'pull',  
  @status = N'subscribed';  
GO  
  
```  
  
 次の例では、マージ パブリケーションに対するプル サブスクリプションを作成します。 最初のバッチはサブスクライバーで実行され、2 番目のバッチはパブリッシャーで実行されます。 ログインとパスワードの値は、実行時に **sqlcmd** スクリプト変数を使用して入力されます。  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Execute this batch at the Subscriber.  
DECLARE @publication AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @publicationDB AS sysname;  
DECLARE @hostname AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @publisher = $(PubServer);  
SET @publicationDB = N'AdventureWorks';  
SET @hostname = N'adventure-works\david8';  
  
-- At the subscription database, create a pull subscription   
-- to a merge publication.  
USE [AdventureWorksReplica]  
EXEC sp_addmergepullsubscription   
  @publisher = @publisher,   
  @publication = @publication,   
  @publisher_db = @publicationDB;  
  
-- Add an agent job to synchronize the pull subscription.   
EXEC sp_addmergepullsubscription_agent   
  @publisher = @publisher,   
  @publisher_db = @publicationDB,   
  @publication = @publication,   
  @distributor = @publisher,   
  @job_login = $(Login),   
  @job_password = $(Password),  
  @hostname = @hostname;  
GO  
```  
  
```  
-- Execute this batch at the Publisher.  
DECLARE @myMergePub  AS sysname;  
DECLARE @mySub       AS sysname;  
DECLARE @mySubDB     AS sysname;  
  
SET @myMergePub = N'AdvWorksSalesOrdersMerge';  
SET @mySub = N'MYSUBSERVER';  
SET @mySubDB = N'AdventureWorksReplica';  
  
-- At the Publisher, register the subscription, using the defaults.  
USE [AdventureWorks]  
EXEC sp_addmergesubscription @publication = @myMergePub,   
@subscriber = @mySub, @subscriber_db = @mySubDB,   
@subscription_type = N'pull';  
GO  
```  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 プル サブスクリプションの作成に使用する RMO のクラスは、サブスクリプションが属しているパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを作成するには  
  
1.  使用して、サブスクライバーとパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> 手順 1. のパブリッシャーの接続を使用してクラスです。 指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> と <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、手順 2. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。  
  
4.  ビットごとの論理 AND を実行 (**&** Visual C# の場合と **と** Visual Basic で) の間、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティと <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>します。 結果の場合 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, 、設定されて <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> の論理和演算の結果に (**|** Visual C# の場合と **または** Visual Basic で) の間で <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> と <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>します。 次に、呼び出す <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> プル サブスクリプションを有効にします。  
  
5.  サブスクリプション データベースが存在しない場合は作成を使用して、 <xref:Microsoft.SqlServer.Management.Smo.Database> クラスです。 詳細については、次を参照してください。 [の作成、変更、および削除するデータベース](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md)します。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスです。  
  
7.  次のサブスクリプション プロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Management.Common.ServerConnection> で作成されたサブスクライバーには、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   サブスクリプション データベースの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>します。  
  
    -   パブリッシャーの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>します。  
  
    -   パブリケーション データベースの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>します。  
  
    -   <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> または <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> の資格情報を提供する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、サブスクライバーでディストリビューション エージェントを実行する Windows アカウントです。 このアカウントは、サブスクライバーとのローカル接続を確立したり、Windows 認証を使用したリモート接続を確立するときに使用されます。  
  
        > [!NOTE]  
        >  設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> のメンバーによって、サブスクリプションが作成された場合は必要ありません、 **sysadmin** 固定サーバー ロールを推奨します。 この場合、エージェントは SQL Server エージェントのアカウントを借用します。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能)値 **true** の <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> サブスクリプションの同期に使用されるエージェント ジョブを作成します。 指定した場合 **false** (既定)、サブスクリプションはプログラムでのみ同期しての他のプロパティを指定する必要があります <xref:Microsoft.SqlServer.Replication.TransSynchronizationAgent> から、このオブジェクトにアクセスするときに、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription.SynchronizationAgent%2A> プロパティです。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
        > [!NOTE]  
        >  SQL Server エージェントは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[SQL Server 2016 の各エディションがサポートする機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」を参照してください。 Express のサブスクライバーに対して値 **true** を指定しても、エージェント ジョブは作成されません。 ただし、サブスクリプション関連の重要なメタデータについてはサブスクライバーに保存されます。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> SQL Server 認証を使用してディストリビューターに接続する場合。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> メソッドです。  
  
9. インスタンスを使用して、 <xref:Microsoft.SqlServer.Replication.TransPublication> 手順 2 の呼び出しからクラスを <xref:Microsoft.SqlServer.Replication.TransPublication.MakePullSubscriptionWellKnown%2A> 、パブリッシャーにプル サブスクリプションを登録します。 既に登録されている場合は、例外が発生します。  
  
#### マージ パブリケーションに対するプル サブスクリプションを作成するには  
  
1.  使用して、サブスクライバーとパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 1. のパブリッシャーの接続を使用してクラスです。 指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>, 、および <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、手順 2. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。  
  
4.  ビットごとの論理 AND を実行 (**&** Visual C# の場合と **と** Visual Basic で) の間、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティと <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>します。 結果の場合 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.None>, 、設定されて <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> の論理和演算の結果に (**|** Visual C# の場合と **または** Visual Basic で) の間で <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> と <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowPull>します。 次に、呼び出す <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> プル サブスクリプションを有効にします。  
  
5.  サブスクリプション データベースが存在しない場合は作成を使用して、 <xref:Microsoft.SqlServer.Management.Smo.Database> クラスです。 詳細については、次を参照してください。 [の作成、変更、および削除するデータベース](../../relational-databases/server-management-objects-smo/tasks/creating-altering-and-removing-databases.md)します。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスです。  
  
7.  次のサブスクリプション プロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Management.Common.ServerConnection> で作成されたサブスクライバーには、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   サブスクリプション データベースの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>します。  
  
    -   パブリッシャーの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>します。  
  
    -   パブリケーション データベースの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>します。  
  
    -   <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> または <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> の資格情報を提供する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 、サブスクライバーでマージ エージェントを実行する Windows アカウントです。 このアカウントは、サブスクライバーとのローカル接続を確立したり、Windows 認証を使用したリモート接続を確立するときに使用されます。  
  
        > [!NOTE]  
        >  設定 <xref:Microsoft.SqlServer.Replication.PullSubscription.SynchronizationAgentProcessSecurity%2A> のメンバーによって、サブスクリプションが作成された場合は必要ありません、 **sysadmin** 固定サーバー ロールを推奨します。 この場合、エージェントは SQL Server エージェントのアカウントを借用します。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能)値 **true** の <xref:Microsoft.SqlServer.Replication.PullSubscription.CreateSyncAgentByDefault%2A> サブスクリプションの同期に使用されるエージェント ジョブを作成します。 指定した場合 **false** (既定)、サブスクリプションはプログラムでのみ同期しての他のプロパティを指定する必要があります <xref:Microsoft.SqlServer.Replication.MergeSynchronizationAgent> から、このオブジェクトにアクセスするときに、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription.SynchronizationAgent%2A> プロパティです。 詳しくは、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md)」をご覧ください。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.DistributorSecurity%2A> SQL Server 認証を使用してディストリビューターに接続する場合。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherSecurity%2A> SQL Server 認証を使用してパブリッシャーに接続する場合。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PullSubscription.Create%2A> メソッドです。  
  
9. インスタンスを使用して、 <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 2 の呼び出しからクラスを <xref:Microsoft.SqlServer.Replication.MergePublication.MakePullSubscriptionWellKnown%2A> 、パブリッシャーにプル サブスクリプションを登録します。 既に登録されている場合は、例外が発生します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションに対するプル サブスクリプションを作成します。 ディストリビューション エージェント ジョブを作成するために使用する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントの資格情報は実行時に渡されます。  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksProductTran";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
TransPublication publication;  
TransPullSubscription subscription;  
  
try  
{  
    // Connect to the Publisher and Subscriber.  
    subscriberConn.Connect();  
    publisherConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new TransPublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.IsExistingObject)  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new TransPullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // By default, subscriptions to transactional publications are synchronized   
        // continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (TransSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                TransSubscriberType.ReadOnly);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksProductTran"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As TransPublication  
Dim subscription As TransPullSubscription  
  
Try  
    ' Connect to the Publisher and Subscriber.  
    subscriberConn.Connect()  
    publisherConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New TransPublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.IsExistingObject Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New TransPullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.Description = "Pull subscription to " + publicationDbName _  
        + " on " + subscriberName + "."  
  
        ' Specify the Windows login credentials for the Distribution Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' By default, subscriptions to transactional publications are synchronized   
        ' continuously, but in this case we only want to synchronize on demand.  
        subscription.AgentSchedule.FrequencyType = ScheduleFrequencyType.OnDemand  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As TransSubscription In publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName And _  
                existing.SubscriptionDBName = subscriptionDbName Then  
                registered = True  
            End If  
        Next existing  
        If Not registered Then  
            ' Register the subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             TransSubscriberType.ReadOnly)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
  
```  
  
 次の例では、マージ パブリケーションに対するプル サブスクリプションを作成します。 マージ エージェント ジョブを作成するために使用する Windows アカウントの資格情報は実行時に渡されます。  
  
```cpp#  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Make sure that the agent job for the subscription is created.  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
        "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 この例では、マージ パブリケーションに対するプル サブスクリプションを作成せずに関連付けられているエージェント ジョブやサブスクリプション メタデータを作成する [MSsubscription_properties](../../relational-databases/system-tables/mssubscription-properties-transact-sql.md)します。 マージ エージェント ジョブを作成するために使用する Windows アカウントの資格情報は実行時に渡されます。  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
  
        // Specify that an agent job not be created for this subscription. The  
        // subscription can only be synchronized by running the Merge Agent directly.  
        // Subscripition metadata stored in MSsubscription_properties will not  
        // be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = false;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
  
        ' Specify that an agent job not be created for this subscription. The  
        ' subscription can only be synchronized by running the Merge Agent directly.  
        ' Subscripition metadata stored in MSsubscription_properties will not  
        ' be available and must be specified at run time.  
        subscription.CreateSyncAgentByDefault = False  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
 次の例では、Web 同期によるインターネットを介した同期が可能な、マージ パブリケーションに対するプル サブスクリプションを作成しています。 マージ エージェント ジョブを作成するために使用する Windows アカウントの資格情報は実行時に渡されます。 詳しくは、「 [Configure Web Synchronization](../../relational-databases/replication/configure-web-synchronization.md)」をご覧ください。  
  
```csharp  
// Define the Publisher, publication, and databases.  
string publicationName = "AdvWorksSalesOrdersMerge";  
string publisherName = publisherInstance;  
string subscriberName = subscriberInstance;  
string subscriptionDbName = "AdventureWorksReplica";  
string publicationDbName = "AdventureWorks";  
string hostname = @"adventure-works\garrett1";  
string webSyncUrl = "https://" + publisherInstance + "/WebSync/replisapi.dll";  
  
//Create connections to the Publisher and Subscriber.  
ServerConnection subscriberConn = new ServerConnection(subscriberName);  
ServerConnection publisherConn = new ServerConnection(publisherName);  
  
// Create the objects that we need.  
MergePublication publication;  
MergePullSubscription subscription;  
  
try  
{  
    // Connect to the Subscriber.  
    subscriberConn.Connect();  
  
    // Ensure that the publication exists and that   
    // it supports pull subscriptions and Web synchronization.  
    publication = new MergePublication();  
    publication.Name = publicationName;  
    publication.DatabaseName = publicationDbName;  
    publication.ConnectionContext = publisherConn;  
  
    if (publication.LoadProperties())  
    {  
        if ((publication.Attributes & PublicationAttributes.AllowPull) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowPull;  
        }  
        if ((publication.Attributes & PublicationAttributes.AllowWebSynchronization) == 0)  
        {  
            publication.Attributes |= PublicationAttributes.AllowWebSynchronization;  
        }  
  
        // Define the pull subscription.  
        subscription = new MergePullSubscription();  
        subscription.ConnectionContext = subscriberConn;  
        subscription.PublisherName = publisherName;  
        subscription.PublicationName = publicationName;  
        subscription.PublicationDBName = publicationDbName;  
        subscription.DatabaseName = subscriptionDbName;  
        subscription.HostName = hostname;  
  
        // Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin;  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword;  
  
        // Enable Web synchronization.  
        subscription.UseWebSynchronization = true;  
        subscription.InternetUrl = webSyncUrl;  
  
        // Specify the same Windows credentials to use when connecting to the  
        // Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication;  
        subscription.InternetLogin = winLogin;  
        subscription.InternetPassword = winPassword;  
  
        // Ensure that we create a job for this subscription.  
        subscription.CreateSyncAgentByDefault = true;  
  
        // Create the pull subscription at the Subscriber.  
        subscription.Create();  
  
        Boolean registered = false;  
  
        // Verify that the subscription is not already registered.  
        foreach (MergeSubscription existing  
            in publication.EnumSubscriptions())  
        {  
            if (existing.SubscriberName == subscriberName  
                && existing.SubscriptionDBName == subscriptionDbName  
                && existing.SubscriptionType == SubscriptionOption.Pull)  
            {  
                registered = true;  
            }  
        }  
        if (!registered)  
        {  
            // Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown(  
                subscriberName, subscriptionDbName,  
                SubscriptionSyncType.Automatic,  
                MergeSubscriberType.Local, 0);  
        }  
    }  
    else  
    {  
        // Do something here if the publication does not exist.  
        throw new ApplicationException(String.Format(  
            "The publication '{0}' does not exist on {1}.",  
            publicationName, publisherName));  
    }  
}  
catch (Exception ex)  
{  
    // Implement the appropriate error handling here.  
    throw new ApplicationException(String.Format(  
        "The subscription to {0} could not be created.", publicationName), ex);  
}  
finally  
{  
    subscriberConn.Disconnect();  
    publisherConn.Disconnect();  
}  
```  
  
```vb  
' Define the Publisher, publication, and databases.  
Dim publicationName As String = "AdvWorksSalesOrdersMerge"  
Dim publisherName As String = publisherInstance  
Dim subscriberName As String = subscriberInstance  
Dim subscriptionDbName As String = "AdventureWorksReplica"  
Dim publicationDbName As String = "AdventureWorks"  
Dim hostname As String = "adventure-works\garrett1"  
Dim webSyncUrl As String = "https://" + publisherInstance + "/WebSync/replisapi.dll"  
  
'Create connections to the Publisher and Subscriber.  
Dim subscriberConn As ServerConnection = New ServerConnection(subscriberName)  
Dim publisherConn As ServerConnection = New ServerConnection(publisherName)  
  
' Create the objects that we need.  
Dim publication As MergePublication  
Dim subscription As MergePullSubscription  
  
Try  
    ' Connect to the Subscriber.  
    subscriberConn.Connect()  
  
    ' Ensure that the publication exists and that   
    ' it supports pull subscriptions and Web synchronization.  
    publication = New MergePublication()  
    publication.Name = publicationName  
    publication.DatabaseName = publicationDbName  
    publication.ConnectionContext = publisherConn  
  
    If publication.LoadProperties() Then  
        If (publication.Attributes And PublicationAttributes.AllowPull) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowPull  
        End If  
        If (publication.Attributes And PublicationAttributes.AllowWebSynchronization) = 0 Then  
            publication.Attributes = publication.Attributes _  
            Or PublicationAttributes.AllowWebSynchronization  
        End If  
  
        ' Define the pull subscription.  
        subscription = New MergePullSubscription()  
        subscription.ConnectionContext = subscriberConn  
        subscription.PublisherName = publisherName  
        subscription.PublicationName = publicationName  
        subscription.PublicationDBName = publicationDbName  
        subscription.DatabaseName = subscriptionDbName  
        subscription.HostName = hostname  
        subscription.CreateSyncAgentByDefault = True  
  
        ' Specify the Windows login credentials for the Merge Agent job.  
        subscription.SynchronizationAgentProcessSecurity.Login = winLogin  
        subscription.SynchronizationAgentProcessSecurity.Password = winPassword  
  
        ' Enable Web synchronization.  
        subscription.UseWebSynchronization = True  
        subscription.InternetUrl = webSyncUrl  
  
        ' Specify the same Windows credentials to use when connecting to the  
        ' Web server using HTTPS Basic Authentication.  
        subscription.InternetSecurityMode = AuthenticationMethod.BasicAuthentication  
        subscription.InternetLogin = winLogin  
        subscription.InternetPassword = winPassword  
  
        ' Create the pull subscription at the Subscriber.  
        subscription.Create()  
  
        Dim registered As Boolean = False  
  
        ' Verify that the subscription is not already registered.  
        For Each existing As MergeSubscription In _  
        publication.EnumSubscriptions()  
            If existing.SubscriberName = subscriberName Then  
                registered = True  
            End If  
        Next  
        If Not registered Then  
            ' Register the local subscription with the Publisher.  
            publication.MakePullSubscriptionWellKnown( _  
             subscriberName, subscriptionDbName, _  
             SubscriptionSyncType.Automatic, _  
             MergeSubscriberType.Local, 0)  
        End If  
    Else  
        ' Do something here if the publication does not exist.  
        Throw New ApplicationException(String.Format( _  
         "The publication '{0}' does not exist on {1}.", _  
         publicationName, publisherName))  
    End If  
Catch ex As Exception  
    ' Implement the appropriate error handling here.  
    Throw New ApplicationException(String.Format( _  
     "The subscription to {0} could not be created.", publicationName), ex)  
Finally  
    subscriberConn.Disconnect()  
    publisherConn.Disconnect()  
End Try  
```  
  
## 参照  
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [プル サブスクリプションのプロパティの表示または変更](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Web 同期を構成します。](../../relational-databases/replication/configure-web-synchronization.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  