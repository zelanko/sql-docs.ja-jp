---
title: "初期スナップショットの作成および適用 | Microsoft Docs"
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
  - "スナップショット [SQL Server レプリケーション]、作成"
  - "スナップショット レプリケーション [SQL Server]、初期スナップショット"
ms.assetid: 742727a1-5189-44ec-b3ae-6fd7aa1f5347
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# 初期スナップショットの作成および適用
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、初期スナップショットを作成および適用する方法について説明します。 パラメーター化されたフィルターを使用するマージ パブリケーションでは、2 つの部分から成るスナップショットが必要です。 詳しくは、「 [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。  
  
 **このトピックの内容**  
  
-   **初期スナップショットを作成および適用するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されている場合、パブリケーションの新規作成ウィザードでパブリケーションが作成された直後に、スナップショット エージェントによってスナップショットが生成されます。 既定では、スナップショットはディストリビューション エージェント (スナップショット レプリケーションおよびトランザクション レプリケーションの場合) またはマージ エージェント (マージ サブスクリプションの場合) によって、すべてのサブスクリプションに対して適用されます。 スナップショットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] およびレプリケーション モニターを使用して生成することもできます。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
#### Management Studio でスナップショットを作成するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、スナップショットを作成するパブリケーションを右クリックして **[スナップショット エージェントの状態**します。  
  
4.   **スナップショット エージェントの状態の表示 - \< パブリケーション>** ダイアログ ボックスで、をクリックして **開始**します。  
  
 スナップショット エージェントによるスナップショットの生成が完了すると、"[100%] 17 個のアーティクルのスナップショットが生成されました。" などのメッセージが表示されます。  
  
#### レプリケーション モニターでスナップショットを作成するには  
  
1.  レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。  
  
2.  クリックして、スナップショットを生成するパブリケーションを右クリックして **スナップショットの生成**します。  
  
3.  スナップショット エージェントの状態を表示するには、 **[エージェント]** タブをクリックします。 詳細については、グリッドで、スナップショット エージェントを右クリックし、 **の詳細の表示**します。  
  
#### スナップショットを適用するには  
  
1.  生成したスナップショットは、ディストリビューション エージェントまたはマージ エージェントによるサブスクリプションの同期によって適用されます。  
  
    -   エージェントを連続して実行するように設定している場合 (トランザクション レプリケーションの既定の動作)、スナップショットは生成後に自動的に適用されます。  
  
    -   スケジュールに基づいてエージェントを実行するように設定している場合、スナップショットは、スケジュールによる次回のエージェント実行時に適用されます。  
  
    -   要求時にエージェントを実行するように設定している場合、スナップショットは、次回のエージェント実行時に適用されます。  
  
     サブスクリプションの同期の詳細については、次を参照してください。 [プッシュ サブスクリプションを同期する](../../relational-databases/replication/synchronize-a-push-subscription.md) と [プル サブスクリプションを同期する](../../relational-databases/replication/synchronize-a-pull-subscription.md)です。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 初期スナップショットは、スナップショット エージェント ジョブを作成、実行するか、スナップショット エージェントの実行可能ファイルをバッチ ファイルから実行することによってプログラムから作成できます。 生成された初期スナップショットは、サブスクリプションの初回同期時にサブスクライバーに転送されて適用されます。 スナップショット エージェントをコマンド プロンプトまたはバッチ ファイルから実行する場合、既存のスナップショットが無効になるたびにエージェントを再実行する必要があります。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
#### スナップショット エージェント ジョブを作成、実行して初期スナップショットを生成するには  
  
1.  スナップショット パブリケーション、トランザクション パブリケーション、またはマージ パブリケーションを作成します。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
2.  実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 このとき、 **@publication** パラメーターを指定したうえで、次のパラメーターを指定します。  
  
    -   **指定すると、@job_login** スナップショット エージェントがディストリビューターで実行する Windows 認証の資格情報。  
  
    -   **@Job_password**, は、指定された Windows 資格情報のパスワード。  
  
    -   (省略可能)値 **0** の **@publisher_security_mode** 場合は、エージェントは、パブリッシャーに接続するときに、SQL Server 認証が使用されます。 この場合、する必要がありますも SQL Server 認証ログインの情報を指定 **@publisher_login** と **@publisher_password**します。  
  
    -   (省略可) スナップショット エージェント ジョブの同期スケジュールを指定します。 詳しくは、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
3.  パブリケーションにアーティクルを追加します。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_startpublication_snapshot & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md), の値を指定する **@publication** 手順 1. のです。  
  
#### スナップショット エージェントを実行して初期スナップショットを生成するには  
  
1.  スナップショット パブリケーション、トランザクション パブリケーション、またはマージ パブリケーションを作成します。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
2.  パブリケーションにアーティクルを追加します。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
3.  コマンド プロンプトから、またはバッチ ファイルでは、開始、 [レプリケーション スナップショット エージェント](../../relational-databases/replication/agents/replication-snapshot-agent.md) を実行して、 **snapshot.exe**, 、次のコマンドライン引数を指定します。  
  
    -   **-Publication**  
  
    -   **-Publisher**  
  
    -   **-Distributor**  
  
    -   **-PublisherDB**  
  
    -   **-ReplicationType**  
  
     SQL Server 認証を使用する場合は、次の引数も指定する必要があります。  
  
    -   **-DistributorLogin**  
  
    -   **-DistributorPassword**  
  
    -   **-Distributorsecuritymode** = **0**  
  
    -   **-PublisherLogin**  
  
    -   **-PublisherPassword**  
  
    -   **-Publishersecuritymode** = **0**  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例は、トランザクション パブリケーションを作成し、新しいパブリケーションのスナップショット エージェント ジョブを追加する方法を示します (を使用して **sqlcmd** スクリプト変数)。 ジョブを開始するコードも含まれています。  
  
 [!code-sql[HowTo#sp_trangenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_1.sql)]  
  
 この例は、マージ パブリケーションを作成し、スナップショット エージェント ジョブの追加 (を使用して **sqlcmd** 変数)、パブリケーションのです。 ジョブを開始するコードも含まれています。  
  
 [!code-sql[HowTo#sp_mergegenerate_snapshot](../../relational-databases/replication/codesnippet/tsql/create-and-apply-the-ini_2.sql)]  
  
 次のコマンド ライン引数は、スナップショット エージェントを起動して、マージ パブリケーション用のスナップショットを生成します。  
  
> [!NOTE]  
>  読みやすくするために、改行が追加されています。 バッチ ファイルの場合、コマンドは 1 行で入力する必要があります。  
  
```  
  
REM -- Declare variables  
SET Publisher=%InstanceName%  
SET PublicationDB=AdventureWorks2012   
SET Publication=AdvWorksSalesOrdersMerge   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1  
  
```  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 スナップショット エージェントは、パブリッシャーが作成された後でスナップショットを生成します。 レプリケーション管理オブジェクト (RMO) およびレプリケーション エージェント機能への直接的なマネージ コード アクセスを使用して、これらのスナップショットをプログラムで生成できます。 使用するオブジェクトは、レプリケーションの種類によって異なります。 スナップショット エージェントを同期的に開始する場合は <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> オブジェクトを使用し、非同期的に開始する場合はエージェント ジョブを使用します。 初期スナップショットの生成後、サブスクリプションを最初に同期するときに、初期スナップショットをサブスクライバーに転送して適用することができます。 既存のスナップショットに最新の有効なデータが含まれていない場合は、エージェントを再実行する必要があります。 詳細については、次を参照してください。 [維持パブリケーション](../../relational-databases/replication/publish/maintain-publications.md)します。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。  
  
#### スナップショット エージェント ジョブを非同期的に開始して、スナップショット パブリケーションまたはトランザクション パブリケーションの初期スナップショットを生成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトの残りのプロパティを読み込みます。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  場合の値 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> は **false**, 、呼び出す <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> このパブリケーションに対してスナップショット エージェント ジョブを作成します。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> このパブリケーションのスナップショットを生成するエージェント ジョブを開始します。  
  
6.  (省略可能)時の値 <xref:Microsoft.SqlServer.Replication.TransPublication.SnapshotAvailable%2A> は **true**, 、スナップショットはサブスクライバーに使用します。  
  
#### スナップショット エージェント ジョブを同期的に実行して、スナップショット パブリケーションまたはトランザクション パブリケーションの初期スナップショットを生成するには  
  
1.  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> クラスのインスタンスを作成し、次の必須プロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - パブリッシャーの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - パブリケーション データベースの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - パブリケーションの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - ディストリビューターの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -の値 <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> パブリッシャーかの値に接続するときに、Windows 認証を使用する <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> の値と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに認証します。 推奨されるのは、Windows 認証です。  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -の値 <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> ディストリビューターまたはの値に接続するときに、Windows 認証を使用する <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> の値と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ディストリビューターに接続するときに認証します。 推奨されるのは、Windows 認証です。  
  
2.  値を設定 <xref:Microsoft.SqlServer.Replication.ReplicationType.Transactional> または <xref:Microsoft.SqlServer.Replication.ReplicationType.Snapshot> の <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>します。  
  
3.  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> メソッドを呼び出します。  
  
#### スナップショット エージェント ジョブを非同期的に開始して、マージ パブリケーションの初期スナップショットを生成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトの残りのプロパティを読み込みます。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  場合の値 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> は **false**, 、呼び出す <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> このパブリケーションに対してスナップショット エージェント ジョブを作成します。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> このパブリケーションのスナップショットを生成するエージェント ジョブを開始します。  
  
6.  (省略可能)時の値 <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> は **true**, 、スナップショットはサブスクライバーに使用します。  
  
#### スナップショット エージェントを同期的に実行して、マージ パブリケーションの初期スナップショットを生成するには  
  
1.  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> クラスのインスタンスを作成し、次の必須プロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - パブリッシャーの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - パブリケーション データベースの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - パブリケーションの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - ディストリビューターの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -の値 <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> パブリッシャーかの値に接続するときに、Windows 認証を使用する <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> の値と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherLogin%2A> と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherPassword%2A> を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに認証します。 推奨されるのは、Windows 認証です。  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -の値 <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> ディストリビューターまたはの値に接続するときに、Windows 認証を使用する <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> の値と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorLogin%2A> と <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorPassword%2A> を使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ディストリビューターに接続するときに認証します。 推奨されるのは、Windows 認証です。  
  
2.  値を設定 <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> の <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>します。  
  
3.  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> メソッドを呼び出します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、スナップショット エージェントを同期的に実行して、トランザクション パブリケーションの初期スナップショットを生成します。  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot)]  
  
 次の例では、エージェント ジョブを非同期的に開始して、トランザクション パブリケーションの初期スナップショットを生成します。  
  
 [!code-csharp[HowTo#rmo_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatesnapshot_withjob)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateSnapshot_WithJob](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatesnapshot_withjob)]  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)   
 [スナップショットの作成および適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [sqlcmd でのスクリプト変数の使用](../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)  
  
  