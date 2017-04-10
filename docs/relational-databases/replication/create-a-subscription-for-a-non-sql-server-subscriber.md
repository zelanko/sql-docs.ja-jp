---
title: "SQL Server 以外のサブスクライバーのサブスクリプションの作成 | Microsoft Docs"
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
  - "subscriptions [SQL Server replication], non-SQL Server Subscribers"
  - "Subscribers [SQL Server replication], non-SQL Server Subscribers"
  - "SQL Server 以外のサブスクライバー, サブスクリプション"
ms.assetid: 5020ee68-b988-4d57-8066-67d183e61237
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# SQL Server 以外のサブスクライバーのサブスクリプションの作成
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、SQL Server 以外のサブスクライバーのサブスクリプションを作成する方法について説明します。 トランザクション レプリケーションとスナップショット レプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーに対するデータのパブリッシュがサポートされています。 サポートされるサブスクライバー プラットフォームについては、次を参照してください。 [非 SQL Server サブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)します。  
  
 **このトピックの内容**  
  
-   **SQL Server 以外のサブスクライバーのサブスクリプションを作成するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーのサブスクリプションを作成するには、以下の操作を実行します。  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターに、適切なクライアント ソフトウェアおよび OLE DB プロバイダーをインストールし、これらを構成します。 詳細については、「 [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) 」および「 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)」を参照してください。  
  
2.  パブリケーションの新規作成ウィザードを使用して、パブリケーションを作成します。 パブリケーションの作成の詳細については、次を参照してください。 [パブリケーションを作成](../../relational-databases/replication/publish/create-a-publication.md) と [Oracle データベースからパブリケーションを作成](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)します。 パブリケーションの新規作成ウィザードで、以下のオプションを指定します。  
  
    -   **[パブリケーションの種類]** ページで、 **[スナップショット パブリケーション]** または **[トランザクション パブリケーション]**を選択します。  
  
    -   **[スナップショット エージェント]** ページで、 **[スナップショットをすぐに作成する]**チェック ボックスをオフにします。  
  
         [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーに対してパブリケーションが有効になったら、スナップショットを作成し、スナップショット エージェントが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーに適したスナップショットおよび初期化スクリプトを生成することを確認します。  
  
3.  パブリケーションを有効にする非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用したサブスクライバー、 **パブリケーションのプロパティ - \< PublicationName>** ] ダイアログ ボックス。 この手順の詳細については、「 [Publication Properties, Subscription Options](../../relational-databases/replication/publication-properties-subscription-options.md) 」を参照してください。  
  
4.  サブスクリプションの新規作成ウィザードを使用して、サブスクリプションを作成します。 この手順の詳細については、このトピック内で説明します。  
  
5.  (省略可能)変更、 **pre_creation_cmd** アーティクル、サブスクライバーでテーブルを保持するプロパティです。 この手順の詳細については、このトピック内で説明します。  
  
6.  パブリケーションのスナップショットを生成します。 この手順の詳細については、このトピック内で説明します。  
  
7.  サブスクリプションを同期します。 詳しくは、「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」をご覧ください。  
  
#### SQL Server 以外のサブスクライバーのパブリケーションを有効にするには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  パブリケーションを右クリックし、をクリックして **プロパティ**します。  
  
4.   **サブスクリプション オプション** の値を選択] ページで、 **True** オプション **SQL Server 以外のサブスクライバーを許可する**です。 このオプションを選択した場合、パブリケーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーとの互換性を確保するために、プロパティの数が変更されます。  
  
    > [!NOTE]  
    >  選択すると **True** の値を設定、 **pre_creation_cmd** プロパティが 'drop' のアーティクルです。 この設定では、アーティクルのテーブル名と一致するテーブルがサブスクライバーにある場合、レプリケーションによってそのテーブルが削除されます。 既存のテーブルを保持するには、使用するサブスクライバーにある場合は、 [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) ストアド プロシージャ アーティクルごとに、値を指定して 'none' を **pre_creation_cmd**: `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`です。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] パブリケーションの新しいスナップショットを作成するように要求されます。 この時点で作成しない場合は、次に示す作成手順を後で使用してください。  
  
#### SQL Server 以外のサブスクライバーのサブスクリプションを作成するには  
  
1.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
2.  適切なパブリケーションを右クリックし、をクリックし、 **新規サブスクリプション**します。  
  
3.  **[ディストリビューション エージェントの場所]** ページで、 **[ディストリビューター &lt;Distributor&gt; ですべてのエージェントを実行する]** が選択されていることを確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーは、サブスクライバーでのエージェントの実行をサポートしていません。  
  
4.   **サブスクライバー** ] ページで [ **のサブスクライバーの追加** ] をクリックし、 **非 SQL Server サブスクライバーの追加**します。  
  
5.   **非 SQL Server サブスクライバーの追加** ] ダイアログ ボックスで、サブスクライバーの種類を選択します。  
  
6.  **[データ ソース名]**に値を入力します。  
  
    -   Oracle の場合、これは構成した Transparent Network Substrate (TNS) 名です。  
  
    -   IBM の場合は、任意の名前にすることができます。 通常は、サブスクライバーのネットワーク アドレスを指定します。  
  
     この手順で入力したデータ ソース名と手順 9. で指定した資格情報は、このウィザードでは検証されません。 これらは、サブスクリプションに対してディストリビューション エージェントが実行されるまで、レプリケーションで使用されません。 すべての値はクライアント ツールを使用してサブスクライバーへの接続でテストされていることを確認 (よう **sqlplus** for Oracle)。 詳細については、「 [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) 」および「 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)」を参照してください。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  **サブスクライバー** サブスクライバーと、ウィザードのページに表示されて、 **サブスクライバー** 読み取り専用列 **(既定の出力先)** で、 **サブスクリプション データベース** 列。  
  
    -   Oracle の場合、1 つのサーバーに 1 つのデータベースしか作成できないため、データベースを指定する必要はありません。  
  
    -   IBM DB2 の場合、データベースは DB2 接続文字列の **Initial Catalog** プロパティで指定されます。DB2 接続文字列は、後述する **[追加の接続オプション]** フィールドに入力できます。  
  
8.   **ディストリビューション エージェント セキュリティ** ] ページで、[プロパティ] をクリックして (**...**) にアクセスするサブスクライバーの横にある、 **ディストリビューション エージェント セキュリティ** ] ダイアログ ボックス。  
  
9. **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、以下の操作を行います。  
  
    -   **[プロセス アカウント]**、 **[パスワード]**、および **[パスワードの確認入力]** フィールドで、ディストリビューション エージェントの実行、およびディストリビューターへのローカル接続に使用される [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントおよびパスワードを入力します。  
  
         アカウントには、最小限の権限が必要です: のメンバー、 **db_owner** スナップショットの共有で、ディストリビューション データベース内のデータベース ロール、パブリケーション アクセス リスト (PAL) のメンバー、読み取りアクセス許可を修正し、OLE DB プロバイダーのインストール ディレクトリに対するアクセス許可を読み取る。 PAL の詳細については、次を参照してください。 [パブリッシャーのセキュリティ保護](../../relational-databases/replication/security/secure-the-publisher.md)します。  
  
    -   **[サブスクライバーに接続]**の、 **[ログイン]**、 **[パスワード]**、および **[パスワードの確認入力]** フィールドで、サブスクライバーへの接続に使用するログインとパスワードを入力します。 このログインは、あらかじめ構成され、サブスクリプション データベースでオブジェクトを作成できる十分な権限を持っている必要があります。  
  
    -    **追加の接続オプション** フィールドに、(Oracle では追加のオプションは必要ありません)、接続文字列の形式で、サブスクライバーの接続オプションを指定します。 各オプションはセミコロンで区切る必要があります。 以下に、DB2 接続文字列の例を示します (読みやすいように改行しています)。  
  
        ```  
        Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
        PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
        Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
        Persist Security Info=False;Connection Pooling=True;  
        ```  
  
         文字列内のオプションの多くは、接続する DB2 サーバーに固有のものですが、 **Process Binary as Character** オプションは常に **False**に設定する必要があります。 サブスクリプション データベースを識別するため、 **Initial Catalog** オプションに値が必要です。  
  
10.  **同期スケジュール** からディストリビューション エージェントのスケジュールを選択] ページで、 **エージェント スケジュール** メニュー (スケジュールは通常 **連続的に実行**)。  
  
11. **[サブスクリプションの初期化]** ページで、サブスクリプションを初期化するかどうか、および初期化する場合はいつ行うのかを指定します。  
  
    -   すべてのオブジェクトを作成し、サブスクリプション データベースに必要なすべてのデータを追加した場合にのみ、 **[初期化]** チェック ボックスをオフにします。  
  
    -   選択 **直ちに** のドロップ ダウン リストから、 **場合に初期化** スナップショットをサブスクライバーにファイルをこのウィザードを完了した後にディストリビューション エージェントによって転送され、列です。 エージェントの次回の実行時にファイルが転送されるようにするには、 **[初回同期時]** を選択します。  
  
12. **[ウィザードのアクション]** ページで、必要に応じてサブスクリプションのスクリプトを作成します。 詳細については、「 [Scripting Replication](../../relational-databases/replication/scripting-replication.md)」を参照してください。  
  
#### サブスクライバー側のテーブルを保持するには  
  
-   既定では、用にパブリケーションを有効にする非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの値を設定する、 **pre_creation_cmd** アーティクル プロパティが 'drop' です。 この設定では、アーティクルのテーブル名と一致するテーブルがサブスクライバーにある場合、レプリケーションによってそのテーブルが削除されます。 既存のテーブルを保持するには、使用するサブスクライバーにある場合は、 [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) ストアド プロシージャ アーティクルごとに、値を指定して 'none' を **pre_creation_cmd**します。 `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`」を参照してください。  
  
#### パブリケーションのスナップショットを生成するには  
  
1.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
2.  パブリケーションを右クリックし、をクリックして **[スナップショット エージェントの状態**します。  
  
3.   **スナップショット エージェントの状態の表示 - \< パブリケーション>** ダイアログ ボックスで、をクリックして **開始**します。  
  
 スナップショット エージェントによるスナップショットの生成が完了すると、"[100%] 17 個のアーティクルのスナップショットが生成されました。" などのメッセージが表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーション ストアド プロシージャを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーに対するプッシュ サブスクリプションをプログラムから作成できます。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
#### SQL Server 以外のサブスクライバーに対する、トランザクション パブリケーションまたはスナップショット パブリケーションのプッシュ サブスクリプションを作成するには  
  
1.  パブリッシャーとディストリビューターの両方に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーの最新の OLE DB プロバイダーをインストールします。 OLE DB プロバイダーのレプリケーションの要件を参照してください。 [非 SQL Server サブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), 、[Oracle サブスクライバー](../../relational-databases/replication/non-sql/oracle-subscribers.md), 、[IBM DB2 サブスクライバー](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)します。  
  
2.  パブリッシャー側でパブリケーション データベースであることを確認、パブリケーション以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行してサブスクライバー [sp_helppublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)します。  
  
    -   場合の値 **enabled_for_het_sub** 1, 以外は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーがサポートされます。  
  
    -   場合の値 **enabled_for_het_sub** 0 では、実行 [sp_changepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), を指定して **enabled_for_het_sub** の **@property** と **true** の **@value**します。  
  
        > [!NOTE]  
        >  変更する前に **enabled_for_het_sub** に **true**, 、パブリケーションへの既存のサブスクリプションを削除する必要があります。 設定することはできません **enabled_for_het_sub** に **true** ときに、パブリケーションは、更新サブスクリプションもをサポートします。 変更する **enabled_for_het_sub** は、その他のパブリケーションのプロパティに影響します。 詳細については、次を参照してください。 [非 SQL Server サブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, の値 **(既定の出力先)** の **@destination_db**, の値 **プッシュ** の **@subscription_type**, 、および値 3 を **@subscriber_type** (OLE DB プロバイダーを指定します)。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addpushsubscription_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)します。 次の指定を行います。  
  
    -   **@subscriber**パラメーターおよび **@publication** パラメーター。  
  
    -   値 **(既定の出力先)** の **@subscriber_db**,、  
  
    -   以外のプロパティ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ ソース **@subscriber_provider**, 、**@subscriber_datasrc**, 、**@subscriber_location**, 、**@subscriber_provider_string**, 、および **@subscriber_catalog**します。  
  
    -    [!INCLUDE[msCoName](../../includes/msconame-md.md)] のディストリビューターでディストリビューション エージェントを実行する Windows 資格情報 **@job_login** と **@job_password**します。  
  
        > [!NOTE]  
        >  常に Windows 統合認証を使用して確立された接続で指定された Windows 資格情報を使用して **@job_login** と **@job_password**します。 ディストリビューション エージェントは、常に Windows 統合認証を使用してディストリビューターにローカル接続します。 既定では、エージェントは Windows 統合認証を使用してサブスクライバーに接続します。  
  
    -   値 **0** の **@subscriber_security_mode** と OLE DB プロバイダーのログイン情報の **@subscriber_login** と **@subscriber_password**します。  
  
    -   このサブスクリプションでのディストリビューション エージェント ジョブのスケジュール。 詳しくは、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値を使用するパブリッシャー側でプッシュ サブスクリプションを作成するときに含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
## 参照  
 [IBM DB2 サブスクライバー](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Oracle サブスクライバー](../../relational-databases/replication/non-sql/oracle-subscribers.md)   
 [その他の SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/other-non-sql-server-subscribers.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  