---
title: "パブリケーションの作成 | Microsoft Docs"
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
  - "publications [SQL Server replication], creating"
  - "articles [SQL Server replication], defining"
  - "adding articles"
  - "アーティクル [SQL Server レプリケーション]、追加"
ms.assetid: 52ee6de9-1d58-4cb9-8711-372bddbe7154
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# パブリケーションの作成
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリケーションを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **パブリケーションを作成してアーティクルを定義するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションとアーティクルの名前には、次の文字を含めることはできません: %、 \* , 、[、]、|、:", でしょうか。 , ' , \ , / , \< , >. データベース内のオブジェクトには、次の文字が含まれて、これらをレプリケートする場合でオブジェクト名とは異なるアーティクル名を指定する必要があります、 **アーティクルのプロパティ - \< 記事>** から利用可能なダイアログ ボックス、 **記事** ウィザードのページです。  
  
###  <a name="Security"></a> セキュリティ  
 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] を使用します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードにより、パブリケーションを作成し、アーティクルを定義します。 表示し、[パブリケーションのプロパティを変更、パブリケーションを作成した後、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 Oracle データベースからパブリケーションを作成する方法の詳細については、次を参照してください。 [Oracle データベースからパブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)します。  
  
#### パブリケーションを作成し、アーティクルを定義するには  
  
1.   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  展開、 **レプリケーション** フォルダー、および右クリック、 **ローカル パブリケーション** フォルダーです。  
  
3.  **[新しいパブリケーション]**をクリックします。  
  
4.  パブリケーションの新規作成ウィザードのページに従い、以下の操作を実行します。  
  
    -   サーバーでディストリビューションが構成されていない場合は、ディストリビューターを指定します。 ディストリビューションの構成の詳細については、次を参照してください。 [パブリッシングとディストリビューション](../../../relational-databases/replication/configure-publishing-and-distribution.md)します。  
  
         指定する場合、 **ディストリビューター** 発行元のサーバーは独自のディストリビューター (ローカル ディストリビューター) として機能し、サーバーが構成されていない、ディストリビューター、パブリケーションの新規作成ウィザードは、サーバーを構成するページです。 **[スナップショット フォルダー]** ページで、ディストリビューターの既定のスナップショット フォルダーを指定します。 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 詳細については、フォルダーを適切にセキュリティで保護する、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
         別のサーバーがディストリビューターとして機能するように指定する場合は、パブリッシャーからディストリビューターへの接続のため、 **[管理パスワード]** ページでパスワードを入力する必要があります。 このパスワードは、リモート ディストリビューターでパブリッシャーを有効にしたときに指定したパスワードと一致する必要があります。  
  
         詳細については、次を参照してください。 [ディストリビューションの構成](../../../relational-databases/replication/configure-distribution.md)します。  
  
    -   パブリケーション データベースを選択します。  
  
    -   パブリケーションの種類を選択します。 詳細については、次を参照してください。 [の種類のレプリケーション](../../../relational-databases/replication/types-of-replication.md)します。  
  
    -   パブリッシュするデータおよびデータベース オブジェクトを指定します。必要に応じて、テーブル アーティクルから列をフィルター選択し、アーティクルのプロパティを設定します。  
  
    -   必要に応じて、テーブル アーティクルから行をフィルター選択します。 詳細については、次を参照してください。 [パブリッシュされたデータのフィルター](../../../relational-databases/replication/publish/filter-published-data.md)します。  
  
    -   スナップショット エージェントのスケジュールを設定します。  
  
    -   以下のレプリケーション エージェントの実行および接続に使用される資格情報を指定します。  
  
         \- すべてのパブリケーションのスナップショット エージェント。  
  
         \- ログ リーダー エージェントは、すべてのトランザクション パブリケーション用にします。  
  
         \- キュー リーダー エージェントは、更新サブスクリプションを許可するトランザクション パブリケーション用にします。  
  
         詳細については、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)」を参照してください。  
  
    -   必要に応じて、パブリケーションのスクリプトを作成します。 詳しくは、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
    -   パブリケーションの名前を指定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリケーションは、レプリケーションのストアド プロシージャを使用してプログラムから作成できます。 どのストアド プロシージャを使用するかは、作成するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) スナップショット パブリケーションまたはトランザクション レプリケーションを使用して、現在のデータベースのパブリケーションを有効にするには  
  
2.  トランザクション パブリケーションの場合は、パブリケーション データベースのログ リーダー エージェント ジョブが存在するかどうかを確認します。 スナップショット パブリケーションの場合、この手順は不要です。  
  
    -   パブリケーション データベースのログ リーダー エージェント ジョブが存在する場合は、手順 3. に進みます。  
  
    -   パブリッシュされたデータベースに対するログ リーダー エージェント ジョブが存在するかどうかが不明な場合は実行 [sp_helplogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。  
  
    -   結果セットが空の場合は、ログ リーダー エージェント ジョブを作成します。 パブリッシャーで実行 [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)します。 指定の [!INCLUDE[msCoName](../../../includes/msconame-md.md)] のエージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 手順 3. に進みます。  
  
3.  パブリッシャーで実行 [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)します。 パブリケーション名を指定 **@publication**, との **@repl_freq** パラメーターの値を指定して **スナップショット** スナップショット パブリケーションまたはレジストリの値 **継続的な** トランザクション パブリケーションのです。 必要に応じて、その他のパブリケーション オプションを指定してください。 これにより、パブリケーションが定義されます。  
  
    > [!NOTE]  
    >  パブリケーション名に、次の文字を含めることはできません。  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
4.  パブリッシャーで実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 3 で使用されるパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@snapshot_job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
5.  パブリケーションにアーティクルを追加します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
6.  スナップショット エージェント ジョブを起動して、このパブリケーションの初期スナップショットを生成します。 詳しくは、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
#### マージ パブリケーションを作成するには  
  
1.  パブリッシャーで実行 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) マージ レプリケーションを使用して、現在のデータベースのパブリケーションを有効にするには  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 **@publication** にパブリケーションの名前を指定し、必要に応じて他のパブリケーション オプションを指定します。 これにより、パブリケーションが定義されます。  
  
    > [!NOTE]  
    >  パブリケーション名に、次の文字を含めることはできません。  
    >   
    >  % * [ ] | : " ? \ / \< >  
  
3.  パブリッシャーで実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 2 で使用するパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@snapshot_job_name** と **@password**します。 値を指定する場合は、パブリッシャーに接続するときに、エージェントは SQL Server 認証を使用もする必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
4.  パブリケーションにアーティクルを追加します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
5.  スナップショット エージェント ジョブを起動して、このパブリケーションの初期スナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、トランザクション パブリケーションを作成します。 スナップショット エージェント ジョブおよびログ リーダー エージェント ジョブの作成に必要な Windows 資格情報は、スクリプト変数を使用して渡しています。  
  
 [!code-sql[HowTo#sp_AddTranPub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_1.sql)]  
  
 この例では、マージ パブリケーションを作成します。 スナップショット エージェント ジョブの作成に必要な Windows 資格情報は、スクリプト変数を使用して渡しています。  
  
 [!code-sql[HowTo#sp_AddMergePub](../../../relational-databases/replication/codesnippet/tsql/create-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってパブリケーションを作成できます。 パブリケーションの作成に使用する RMO クラスは、作成するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションを作成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのパブリケーション データベースで、設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティのインスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1、および呼び出しから、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 場合 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 返します **false**, 、データベースが存在することを確認します。  
  
3.  場合、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> プロパティは **false**, に設定 **true**します。  
  
4.  トランザクション パブリケーションの値をチェック、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentExists%2A> プロパティです。 このプロパティが **true**の場合、このデータベースに対するログ リーダー エージェント ジョブが既に存在しています。 このプロパティが **false**の場合、次の操作を実行してください。  
  
    -   設定、 <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> または <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.SecurePassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> の資格情報を提供する、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ログ リーダー エージェントを実行する Windows アカウントです。  
  
        > [!NOTE]  
        >  設定 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentProcessSecurity%2A> のメンバー、パブリケーションを作成するときは必要ありません、 **sysadmin** 固定サーバー ロールです。 この場合、エージェントは SQL Server エージェントのアカウントを借用します。 詳しくは、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能)設定、 <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.LogReaderAgentPublisherSecurity%2A> SQL Server 認証を使用してパブリッシャーに接続する場合。  
  
    -   呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.CreateLogReaderAgent%2A> メソッドは、データベースに対するログ リーダー エージェント ジョブを作成します。  
  
5.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> クラスし、このオブジェクトの次のプロパティを設定します。  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   パブリッシュされたデータベースの名前 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>します。  
  
    -   A <xref:Microsoft.SqlServer.Replication.PublicationType> いずれかの <xref:Microsoft.SqlServer.Replication.PublicationType.Transactional> または <xref:Microsoft.SqlServer.Replication.PublicationType.Snapshot>します。  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> スナップショット エージェントを実行する Windows アカウントの資格情報を入力します。 このアカウントは、Windows 認証を使用している場合に、スナップショット エージェントがローカル ディストリビューターへの接続や任意のリモート接続を行うときにも使用されます。  
  
        > [!NOTE]  
        >  設定 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> のメンバー、パブリケーションを作成するときは必要ありません、 **sysadmin** 固定サーバー ロールです。 この場合、エージェントは SQL Server エージェントのアカウントを借用します。 詳しくは、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能) <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardLogin%2A> と <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SqlStandardPassword%2A> または <xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.SecureSqlStandardPassword%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentPublisherSecurity%2A> SQL Server 認証を使用してパブリッシャーに接続する場合。  
  
    -   (省略可能)包括的論理和演算子を使用して (**|** Visual C# の場合と **または** Visual Basic で) と排他的論理和演算子 (**^** Visual C# の場合と **Xor** Visual Basic で) を設定する、 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> の値、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティです。  
  
    -   (省略可能)パブリッシャーの名前 <xref:Microsoft.SqlServer.Replication.TransPublication.PublisherName%2A> パブリッシャーが、SQL Server 以外のパブリッシャーの場合。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> パブリケーションを作成します。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのプロパティの指定された値でパブリッシャーを構成する場合を含む <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, 、ディストリビューターにプレーン テキストとして送信されます。 発行元と呼び出しの前にリモート ディストリビューター間の接続を暗号化する必要があります、 <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> メソッドです。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
7.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> 、パブリケーションのスナップショット エージェント ジョブを作成します。  
  
#### マージ パブリケーションを作成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのパブリケーション データベースで、設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティのインスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1、および呼び出しから、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 場合 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 返します **false**, 、データベースが存在することを確認します。  
  
3.  場合 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> プロパティは **false**, に設定 **true**, を呼び出すと <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>します。  
  
4.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスし、このオブジェクトの次のプロパティを設定します。  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   パブリッシュされたデータベースの名前 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>します。  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> スナップショット エージェントを実行する Windows アカウントの資格情報を入力します。 このアカウントは、Windows 認証を使用している場合に、スナップショット エージェントがローカル ディストリビューターへの接続や任意のリモート接続を行うときにも使用されます。  
  
        > [!NOTE]  
        >  設定 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> のメンバー、パブリケーションを作成するときは必要ありません、 **sysadmin** 固定サーバー ロールです。 詳しくは、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
    -   (省略可能)包括的論理和演算子を使用して (**|** Visual C# の場合と **または** Visual Basic で) と排他的論理和演算子 (**^** Visual C# の場合と **Xor** Visual Basic で) を設定する、 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> の値、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティです。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> パブリケーションを作成します。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのプロパティの指定された値でパブリッシャーを構成する場合を含む <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, 、ディストリビューターにプレーン テキストとして送信されます。 発行元と呼び出しの前にリモート ディストリビューター間の接続を暗号化する必要があります、 <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> メソッドです。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> 、パブリケーションのスナップショット エージェント ジョブを作成します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、AdventureWorks データベースでトランザクション パブリッシュを有効にして、ログ リーダー エージェント ジョブを定義し、AdvWorksProductTran パブリケーションを作成します。 このパブリケーションには、アーティクルを定義する必要があります。 ログ リーダー エージェント ジョブとスナップショット エージェント ジョブの作成に必要な Windows アカウントの資格情報は、実行時に渡されます。 RMO を使用してスナップショット アーティクルとトランザクション アーティクルを定義する方法については、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」を参照してください。  
  
 [!code-csharp[HowTo#rmo_CreateTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranpub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranpub)]  
  
 次の例では、AdventureWorks データベースでマージ パブリッシュを有効にし、AdvWorksSalesOrdersMerge パブリケーションを作成します。 このパブリケーションには、アーティクルを定義する必要があります。 スナップショット エージェント ジョブの作成に必要な Windows アカウントの資格情報は、実行時に渡されます。 RMO を使用してマージ アーティクルを定義する方法については、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」を参照してください。  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
## 参照  
 [sqlcmd でのスクリプト変数の使用](../../../relational-databases/scripting/use-sqlcmd-with-scripting-variables.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション管理オブジェクトの概念](../../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [パブリケーション プロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [ディストリビューションの構成](../../../relational-databases/replication/configure-distribution.md)   
 [ディストリビューターのセキュリティ保護](../../../relational-databases/replication/security/secure-the-distributor.md)   
 [パブリッシャーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-publisher.md)  
  
  