---
title: "SQL Server R Services (In-Database) をセットアップする | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "SQL Server R Services のインストール"
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 30
---
# SQL Server R Services (In-Database) をセットアップする
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 以降では、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] に関連するすべてのコンポーネントを、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ウィザードを使ってインストールできます。  
 
 
 セットアップが完了した後は、R Services を有効にし、アカウントを構成して、特定のデータベースへのアクセス許可をユーザーに与えるために、若干の追加手順が必要になる場合があります。   
  
セットアップ完了後にデータベースへのアクセスで問題が発生する場合、または以前のバージョンをアンインストールする必要がある場合は、「[アップグレードとインストールに関してよく寄せられる質問 &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)」をご覧ください。  

> [!NOTE]
> R Services (データベース内) をインストールするには、この機能がインストールされるドライブが、8dot3 表記を利用した短いファイル名に対応している必要があります。 サポートしていない場合、SQL Server から R を起動するプロセスが開始しない可能性があります。 R Services をインストールする前に、ボリュームで 8dot3 表記を必ず有効にしてください。 この制約は今後のリリースで削除される予定です。

  
##  <a name="a-namebkmkinstallrservicesindatabasea-step-1-install-r-services-in-database-on-sql-server-2016-or-later"></a><a name="bkmk_installRServicesInDatabase"></a> 手順 1: SQL Server 2016 以降に R Services (データベース内) をインストールする  
   
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行します。  
  
    無人インストールを行う方法については、「 [Unattended Installs of SQL Server R Services](../../advanced-analytics/r-services/unattended-installs-of-sql-server-r-services.md)」を参照してください。  
  
2.  **[インストール]** タブで、 **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]**をクリックします。  
  
    > [!NOTE]  
    >  フェールオーバー クラスターには [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールできません。 ただし、AlwaysOn を使用し、可用性グループに含まれるスタンドアロン コンピューターに [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールできます。 AlwaysOn 可用性グループで R Services を使用する方法については、「[Always On 可用性グループの相互運用性](../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)」を参照してください。  
  
3.  **[機能の選択]** ページで、次のオプションを選択します。  
  
    -   **データベース エンジン サービス**  
  
         [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]を使用するには、データベース エンジンのインスタンスが少なくとも 1 つ必要です。 既定のインスタンスまたは名前付きインスタンスを使用できます。  
  
    -   **R Services (データベース内)**  
  
         このオプションは、R ジョブによって使用されるデータベース サービスを構成し、外部のスクリプトとプロセスをサポートする拡張機能をインストールします。  
    > [!NOTE]
    > 
    > R コードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行する必要がある場合は、必ず **[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]** をインストールしてください。 
    > 
    > これに対し、Microsoft R サーバー (スタンドアロン) は、SQL Server を実行していない Windows コンピューターで Scale R ライブラリを使用できるようにするオプションです。 R の開発に使うラップトップまたは他のコンピューターに Microsoft R サーバー (スタンドアロン) をインストールして R ソリューションを作成し、R Services (データベース内) を実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに展開することをお勧めします。
 
  
4.  **[Microsoft R オープンのインストールに同意する]** ページで、**[同意する]** をクリックします。  
  
     Microsoft R Open をダウンロードするには、このライセンス条項に同意する必要があります。これには、オープン ソース R 基本パッケージとツール、Revolution Analytics から提供された R パッケージおよび接続プロバイダーの配布に関する条件が含まれています。  
  
    > [!NOTE]  
    >  使用しているコンピューターがインターネットにアクセスできない場合は、ここでいったんセットアップを停止し、「[インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)」に説明されているように、個別にインストーラーをダウンロードできます。  
  
     **[同意する]** をクリックし、**[次へ]** ボタンがアクティブになるまで待ってから、**[次へ]** をクリックします。  
  
5.  **[インストールの準備完了]** ページで、以下が選択されていることを確認した後、**[インストール]** をクリックします。  
  
     **機能**  
  
     データベース エンジン サービス  
  
     R Services (In-Database)  
  
6.  インストールが完了した後、コンピューターを再起動します。   
  
  
##  <a name="a-namebkmkenablefeaturea-step-2-enable-r-services-and-verify-that-local-r-script-execution-works"></a><a name="bkmk_enableFeature"></a> 手順 2: R Services を有効にして、R スクリプトのローカル実行が動作することを確認します  
  
  
1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開きます。 まだインストールされていない場合は、SQL Server セットアップ ウィザードを再実行してダウンロード リンクを開き、インストールすることができます。  
  
2. R Services (データベース内) をインストールしたインスタンスに接続し、次のコマンドを実行して、R Services の機能を明示的に有効にします。有効にしないと、セットアップで機能をインストールしてあっても、R スクリプトを呼び出すことはできません。  
  
   ```    
   Exec sp_configure  'external scripts enabled', 1  
   Reconfigure  with override    
   ```  
  
10. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの SQL Server サービスを再起動します。 関連する [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスも自動的に再起動されます。 サービスの再起動は、コントロール パネルの [サービス] パネルまたは SQL Server 構成マネージャーを使って行うことができます。  
  
9. SQL Server サービスが使用できるようになった後、次のコマンドを実行し、*run_value* が 1 に設定されていることを調べて、R の機能が有効になっていることを確認します。  
  
    ```    
    Exec sp_configure  'external scripts enabled'    
    ```  
   必要に応じて、**[サービス]** パネルを開き、インスタンスのスタート パッド サービスが動作していることを確認します。 各インスタンスには専用のスタート パッド サービスがあります。
   
10. 以上が済むと、次のような簡単な R スクリプトを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で実行できるようになります。  
  
    ```  
    exec sp_execute_external_script  @language =N'R',  
    @script=N'OutputDataSet<-InputDataSet',    
    @input_data_1 =N'select 1 as hello'  
    with result sets (([hello] int not null));  
    go  
    ```  
  
    **結果**  
  
    *hello*  
    *1*   
  
> [!IMPORTANT]  SQL Server のデータにアクセスする必要がある場合、またはリモート データ サイエンス クライアントから R コマンドを実行する必要がある場合は、追加の手順が必要です。 次の手順では、これらの追加要件の詳細について説明します。
 
  
##  <a name="a-namebkmkconfigureaccountsa-step-3-enable-implied-authentication-for-launchpad-accounts"></a><a name="bkmk_configureAccounts"></a> 手順 3: スタート パッド アカウントの暗黙の認証を有効にする  
   
  
セットアップの間に、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスのセキュリティ トークンの下でタスクを実行するために、新しい Windows ユーザー アカウントが 20 個作成されます。 ユーザーが外部クライアントから R スクリプトを送信すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は利用可能なワーカー アカウントをアクティブ化し、呼び出し元ユーザーの ID にそれをマップして、ユーザーの代わりに R スクリプトを実行します。 これは、外部スクリプトの安全な実行をサポートする、データベース エンジンの*暗黙の認証*と呼ばれる新しいサービスです。 

これらのアカウントは、Windows ユーザー グループ **SQLRUserGroup** で見ることができます。  リモート データ サイエンス クライアントから R スクリプトを実行する必要があり、Windows 認証を使っている場合は、これらのワーカー アカウントに、ユーザーに代わって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログインするためのアクセス許可を与える必要があります。  
  
1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、**[セキュリティ]** を展開し、**[ログイン]** を右クリックして、**[新しいログイン]** を選択します。  
2. **[ログイン - 新規作成]** ダイアログ ボックスで、**[検索]** をクリックします。  
3. **[オブジェクトの種類]** をクリックし、**[グループ]** を選択します。 他のすべての選択を解除します。  
4. [選択するオブジェクト名を入力します] に「*SQLRUserGroup*」と入力し、**[名前の確認]** をクリックします。  
5. インスタンスのスタート パッド サービスに関連付けられているローカル グループの名前が、"*インスタンス名\SQLRUserGroup*" などに解決されます。 **[OK]**をクリックします。  
6. 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。 
7. **[OK]**をクリックします。  
  
> [!NOTE] SQL Server Compute Context で R スクリプトを実行するために SQL ログインを使う場合は、この追加手順は必要ありません。
  
  
## <a name="step-4-give-non-admin-users-r-script-permissions"></a>手順 4: 管理者以外のユーザーに R スクリプトのアクセス許可を付与する  
  
自分で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールし、独自のインスタンスで R スクリプトを実行する場合は、通常、管理者としてスクリプトを実行するので、データベースのさまざまな操作とすべてのデータに対する暗黙的なアクセス許可、および必要に応じて新しい R パッケージをインストールするための暗黙的なアクセス許可を持っています。  
  
しかし、エンタープライズのシナリオでは、SQL ログインを使ってデータベースにアクセスするユーザーを含むほとんどのユーザーは、そのような昇格されたアクセス許可を持っていません。 そのため、外部スクリプトを実行するユーザーごとに、R が使われる各データベースで R スクリプトを実行するためのユーザー アクセス許可を付与する必要があります。   
  
  
```  
USE <database_name>  
GO  
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]  
```  

> [!TIP] セットアップのヘルプが必要ですか。 すべての手順を実行したかわかりませんか。
>
> カスタム レポートを使って、R Services のインストール状態を確認できます。 詳しくは、「[Management Studio でカスタム レポートを使用して R Services を監視する](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md)」をご覧ください。    
  
##  <a name="a-namebkmkadditionala-optional-modifications"></a><a name="bkmk_Additional"></a>省略可能な変更  
  
このセクションでは、R スクリプトの実行をサポートするために、インスタンスまたはデータ サイエンス クライアントの構成でさらに行うことができる変更について説明します。
  
### <a name="modify-the-number-of-worker-accounts-used-by-includersqllaunchpadtokenrsqllaunchpadmdmd"></a>[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] によって使われるワーカー アカウントの数を変更する
  
R を多く使う場合、または多くのユーザーが同時にスクリプトを実行する場合は、スタート パッド サービスに割り当てられるワーカー アカウントの数を増やすことができます。 詳しくは、「[SQL Server R サービスのユーザー アカウント プールを変更する](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)」をご覧ください。  
  
  
### <a name="give-your-r-users-or-logins-read-write-or-ddl-permissions-as-needed-in-additional-databases"></a>追加データベースで必要な場合に、R ユーザーまたはログインに読み取り、書き込み、または DDL のアクセス許可を与える  
  
R スクリプトを実行していると、他のデータベースからのデータの読み取り、結果を格納するための新しいテーブルの作成、テーブルへのデータの書き込みが必要になることがあります。 
     
その場合は、R スクリプトを実行する各ユーザーのユーザー アカウントに、特定のデータベースに対する **db_datareader**、**db_datawriter**、または **db_ddladmin** アクセス許可を付与する必要があります。   
       
たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、SQL ログイン *MySQLLogin* に、*RSamples* データベースで T-SQL クエリを実行する権限を与えています。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。  
  
```  
USE RSamples  
GO  
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'  
```  
  
各ロールに含まれるアクセス許可の詳細については、「[データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)」をご覧ください。  
  
  
### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>データ サイエンス クライアント上のインスタンス用の ODBC データ ソースを作成する  
  
データ サイエンス クライアント コンピューター上に R ソリューションを作成し、Compute Context として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに接続する必要がある場合は、SQL ログインまたは統合 Windows 認証を使うことができます。  
  
SQL ログインを使う場合は、読み取るデータが存在するデータベースに対する適切なアクセス許可をログインが持っていることを確認します。 そのためには、Connect to** および SELECT **アクセス許可を追加するか、ログインを **db_datareader** ロールに追加します。 オブジェクトを作成する必要がある場合は、**DDL_admin** 権限が必要です。  テーブルにデータを保存するには、ログインを **db_datawriter** ロールに追加します。  
  
Windows 認証を使用する場合は、インスタンス名と他の接続情報を指定する ODBC データ ソースをデータ サイエンス クライアントで構成する必要があります。  
  
詳しくは、「[ODBC データ ソース アドミニストレーターの使用](http://windows.microsoft.com/windows/using-odbc-data-source-administrator)」をご覧ください。  
  
### <a name="optimize-the-server-for-r"></a>R 用にサーバーを最適化する  

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップの既定の設定では、データベース エンジンによってサポートされているさまざまなサービス (ETL プロセス、レポート、監査など) と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを使うアプリケーションのバランスを最適化するようになっています。 そのため、既定の設定では、R 操作用のリソースが制限または調整されることがあります (特に、メモリを大量に使用する操作の場合)。  
  
 R のタスクが適切に優先順位を設定されて、リソースを提供されるようにするため、リソース ガバナーを使って R 操作専用の外部リソース プールを構成することをお勧めします。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース エンジンに割り当てられるメモリの量を変更したり、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスで実行するアカウントの数を増やしたりすることもできます。  
  
-   外部リソースの管理用にリソース プールを構成します  
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)  
  
-   データベース エンジン用に予約されるメモリの量を変更します  
  
     [サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
-   [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]で開始できる R アカウントの数を変更します  
  
     [SQL Server R サービスのユーザー アカウント プールを変更する](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  
  
### <a name="get-the-r-source-code-optional"></a>R のソース コードを取得する (省略可能)  

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] には、オープン ソースの R 基本パッケージの配布が含まれます。  
  
必要に応じて、変更された GPL/LGPL ソース コードのダウンロードをすぐに始めるには、以下のリンクをクリックしてください。 このソース コードは GNU General Public License に従って使用できますが、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールまたは使う必要はありません。  
  
-   RC2 と互換性あり: アーカイブ [rre-gpl-src.8.0.2.tar.gz](http://go.microsoft.com/fwlink/?LinkId=786770) をダウンロードします 
  
-   RC3 と互換性あり: アーカイブ [rre-gpl-src.8.0.3.tar.gz](http://go.microsoft.com/fwlink/?LinkId=786771) をダウンロードします 

-   RTM と互換性あり: アーカイブ [rre-gpl-src.8.0.3.tar.gz](http://go.microsoft.com/fwlink/?LinkID=786771) をダウンロードします
  
## <a name="troubleshooting"></a>トラブルシューティング  
 問題が発生した場合は、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のプレリリース版をインストールするときの一般的な問題の一覧を参照してください。  
  
 [アップグレードとインストールに関してよく寄せられる質問 &#40;SQL Server R サービス&#41;](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)  
  
## <a name="see-also"></a>参照  
 [データ サイエンス クライアントをセットアップする](../../advanced-analytics/r-services/set-up-a-data-science-client.md)   
 [スタンドアロン R Server の作成](../../advanced-analytics/r-services/create-a-standalone-r-server.md)  
  
  