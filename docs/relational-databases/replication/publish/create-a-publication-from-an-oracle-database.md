---
title: "Oracle データベースからのパブリケーションの作成 | Microsoft Docs"
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
  - "publications [SQL Server replication], Oracle databases"
  - "Oracle パブリッシュ [SQL Server レプリケーション], 構成"
ms.assetid: b3812746-14b0-4b22-809e-b4a95e1c8083
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Oracle データベースからのパブリケーションの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、Oracle データベースからパブリケーションを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
-   **Oracle データベースからパブリケーションを作成するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   パブリケーションを作成する前に、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターに Oracle ソフトウェアをインストールし、Oracle データベースを構成する必要があります。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードを使用して、Oracle データベースからスナップショット パブリケーションまたはトランザクション パブリケーションを作成します。  
  
 Oracle データベースからパブリケーションを最初に作成するときは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで Oracle パブリッシャーを識別する必要があります (以降同じデータベースからパブリケーションを作成するときは、この作業は不要です)。 Oracle パブリッシャーを識別するは、パブリケーションの新規作成ウィザードから行うことができますか **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックス。 このトピックを示しています、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックス。  
  
#### SQL Server ディストリビューターで Oracle パブリッシャーを識別するには  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で、Oracle パブリッシャーがディストリビューターとして使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続し、サーバー ノードを展開します。  
  
2.  右クリックし、 **レプリケーション** フォルダー、およびクリック **ディストリビューターのプロパティ**します。  
  
3.   **パブリッシャー** のページ、 **ディストリビューターのプロパティ - \< ディストリビューター>** ダイアログ ボックスで、をクリックして **追加**, 、順にクリック **[Oracle パブリッシャーの追加**します。  
  
4.  **[サーバーへの接続]** ダイアログ ボックスで、 **[オプション]** ボタンをクリックします。  
  
5.  **[ログイン]** タブで、次の操作を実行します。  
  
    1.  Oracle データベースのインスタンス名を入力するか、または **[サーバー インスタンス]** コンボ ボックスで **[参照]** を選択します。  
  
    2.  選択 **Oracle 標準認証** (推奨) または **Windows 認証**します。  
  
         選択した場合 **Windows 認証**: Oracle サーバーは、Windows 資格情報を使用して接続を許可するように構成する必要があります (詳細については、Oracle のマニュアルを参照してください。) で同じ現在ログインする必要がありますが、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] レプリケーション管理ユーザー スキーマ用に指定した Windows アカウントです。  
  
    3.  **[Oracle 標準認証]**を選択する場合は、構成時に Oracle パブリッシャーで作成したレプリケーション管理ユーザー スキーマのログインおよびパスワードを入力します。  
  
6.  **[接続プロパティ]** タブで、パブリッシャーの種類として **[ゲートウェイ]** または **[完全]**を選択します。  
  
     **[完全]** オプションを選択した場合は、Oracle パブリッシング用にサポートされる完全な機能セットがスナップショットおよびトランザクション パブリケーションに提供されます。 **[ゲートウェイ]** オプションを選択した場合は、レプリケーションがシステム間のゲートウェイとして動作する場合のパフォーマンスを向上させるために、特定のデザインが最適化されます。 複数のトランザクション パブリケーションに同じテーブルをパブリッシュする場合は、 **[ゲートウェイ]** オプションは使用できません。 **[ゲートウェイ]**オプションを選択した場合、1 つのテーブルは、最大で 1 つのトランザクション パブリケーションおよび任意の数のスナップショット パブリケーションに含めることができます。  
  
7.  **[接続]**をクリックします。これにより、Oracle パブリッシャーへの接続が作成され、レプリケーション用に構成されます。  **サーバーへの接続** ] ダイアログ ボックスが閉じに返される、 **ディストリビューターのプロパティ - \< ディストリビューター>** ] ダイアログ ボックス。  
  
    > [!NOTE]  
    >  ネットワーク構成に問題がある場合は、この時点でエラーが返されます。 Oracle データベースへの接続中に問題が発生した場合は、「 [Troubleshooting Oracle Publishers](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md)」の「SQL Server ディストリビューターが Oracle データベース インスタンスに接続できない」を参照してください。  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Oracle データベースからパブリケーションを作成するには  
  
1.  Oracle パブリッシャーがディストリビューターとして使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開します。  
  
3.  右クリックし、 **ローカル パブリケーション** フォルダー、およびクリック **新しい Oracle パブリケーション**します。  
  
4.  パブリケーションの新規作成ウィザードの **[Oracle パブリッシャー]** ページで、Oracle パブリッシャーを選択します。 Oracle パブリッシャーが表示されていない場合は、 **[Oracle パブリッシャーの追加]**をクリックし、前の手順から操作を行います。  
  
5.  **[パブリケーションの種類]** ページで、 **[スナップショット パブリケーション]** または **[トランザクション パブリケーション]**を選択します。  
  
6.  **[アーティクル]** ページで、パブリッシュするデータベース オブジェクトを選択します。  
  
     必要に応じて、テーブルを展開してから 1 つ以上の列のチェック ボックスをオフにし、テーブルの列をフィルター選択します。 **[アーティクルのプロパティ]** をクリックしてアーティクルのプロパティを表示および変更し、必要に応じて代替データ型マッピングを指定します。 データ型のマッピングの詳細については、次を参照してください。 [Oracle パブリッシャーのデータ型マッピングを指定](../../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)します。  
  
7.  **[テーブル行のフィルター選択]** ページで、必要に応じてフィルターを適用し、1 つ以上のテーブルからデータのサブセットをパブリッシュします。  
  
8.  サブスクリプション データベースですべてのオブジェクトを作成し、必要なデータをすべて追加している場合に限り、 **[スナップショット エージェント]** ページで **[スナップショットをすぐに作成する]** をオフにします。  
  
9.  **エージェントのセキュリティ** ] ページで、(すべてのパブリケーション) 用のスナップショット エージェントおよびログ リーダー エージェント (トランザクション パブリケーション) 用の資格情報を指定します。 エージェントが実行され、指定した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows アカウントのコンテキストを使用して [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ディストリビューターへの接続が確立されます。 レプリケーション管理ユーザー スキーマとして指定したアカウントのコンテキストを使用して、エージェントから Oracle データベースへの接続が確立されます。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
     各エージェントで必要な権限の詳細については、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)」を参照してください。  
  
10. **[ウィザードのアクション]** ページで、必要に応じてパブリケーションのスクリプトを作成できます。 詳細については、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」をご参照ください。  
  
11. **[ウィザードの完了]** ページで、パブリケーションの名前を指定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 Oracle データベースをパブリッシャーとして構成した後で、システム ストアド プロシージャを使用して、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーから行う場合と同じ方法でトランザクション パブリケーションまたはスナップショット パブリケーションを作成できます。  
  
#### Oracle パブリケーションを作成するには  
  
1.  Oracle データベースをパブリッシャーとして構成します。 詳細については、次を参照してください。 [Oracle パブリッシャーを構成する](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)です。  
  
2.  リモート ディストリビューターが存在しない場合は、リモート ディストリビューターを構成します。 詳細については、「 [Configure Publishing and Distribution](../../../relational-databases/replication/configure-publishing-and-distribution.md)」をご参照ください。  
  
3.  Oracle パブリッシャーを使用して、リモート ディストリビューターで実行 [sp_adddistpublisher & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)します。 Oracle データベース インスタンスの透過的なネットワーク Substrate (TNS) 名を指定 **@publisher** の **ORACLE** または **ORACLE GATEWAY** の **@publisher_type**します。 `Specify` 次のいずれかの方法で、Oracle パブリッシャーからリモート [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターに接続するときに使用されるセキュリティ モードを指定します。  
  
    -   既定の Oracle 標準認証を使用するには、値を指定 **0** の **@security_mode**, の構成時に Oracle パブリッシャーで作成したレプリケーション管理ユーザー スキーマのログイン **@login**, とパスワードを **@password**します。  
  
        > [!IMPORTANT]  
        >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する場合は、不正アクセスを防ぐために、そのファイルをセキュリティで保護する必要があります。  
  
    -   Windows 認証を使用するには、値を指定 **1** の **@security_mode**します。  
  
        > [!NOTE]  
        >  Windows 認証を使用する場合は、Windows 資格情報を使用した接続を許可するように Oracle サーバーが構成されている必要があります (詳細については、Oracle のマニュアルを参照してください)。また、レプリケーション管理ユーザー スキーマに指定した Microsoft Windows アカウントと同じアカウントを使用して現在ログインしている必要があります。  
  
4.  パブリケーション データベースのログ リーダー エージェント ジョブを作成します。  
  
    -   パブリッシュされたデータベースに対するログ リーダー エージェント ジョブが存在するかどうかが不明な場合は実行 [sp_helplogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) ディストリビューターのディストリビューション データベースの Oracle パブリッシャーによって使用されます。 **@publisher**に Oracle パブリッシャーの名前を指定します。 結果セットが空の場合、ログ リーダー エージェント ジョブを作成する必要があります。  
  
    -   パブリケーション データベース用のログ リーダー エージェント ジョブが既に存在する場合、手順 5. に進みます。  
  
    -   Oracle パブリッシャーのディストリビューション データベースが使用するディストリビューターで実行 [sp_addlogreader_agent & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)します。 エージェントを実行する Windows 資格情報を指定 **@job_login** と **@job_password**します。  
  
        > [!NOTE]  
        >   **@Job_login** パラメーターは手順 3. で指定したログインと一致する必要があります。 パブリッシャーのセキュリティ情報を指定しないでください。 ログ リーダー エージェントは、手順 3. で指定されたセキュリティ情報を使用してパブリッシャーに接続します。  
  
5.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_addpublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) パブリケーションを作成します。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
6.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 4 で使用するパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@job_name** と **@password**します。 Oracle 標準認証を使用するパブリッシャーに接続するときの値を指定する必要がありますも **0** の **@publisher_security_mode** Oracle ログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。  
  
## 参照  
 [Oracle パブリッシャーの構成](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [#40; (&)、Oracle パブリッシャーのトランザクション セット ジョブを構成します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/administration/configure the transaction set job for an oracle publisher.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)   
 [Oracle の権限を許可するためのスクリプト](../../../relational-databases/replication/non-sql/script-to-grant-oracle-permissions.md)  
  
  