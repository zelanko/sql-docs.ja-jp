---
title: "アップグレードとインストールに関してよく寄せられる質問 (SQL Server R サービス) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 001e66b9-6c3f-41b3-81b7-46541e15f9ea
caps.latest.revision: 58
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 47
---
# アップグレードとインストールに関してよく寄せられる質問 (SQL Server R サービス)
  このトピックには、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のインストールに関してよく寄せられる質問と、プレビュー リリースからのアップグレードに関してよく寄せられる質問の回答が記載されています。  
  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を初めてインストールする場合、「[SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」に記載されている指示に従い、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] と R コンポーネントを設定します。  

   
## <a name="important-changes-from-pre-releae-versions"></a>プレリリース バージョンからの重要な変更点  
 SQL Server 2016 のプレリリース版をインストールしている場合、あるいは SQL Server 2016 の一般リリースに先立って公開されたセットアップ指示を利用している場合は、セットアップ プロセスがプレリリース バージョンと RTM バージョンでまったく異なることに注意してください。 変更点には、SQL Server セットアップ ウィザードで利用できるオプションとインストール後の手順の両方が含まれます。 
   
> [!WARNING] [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のプレリリース バージョンを新しくインストールすることは現在サポートされていません。 できるだけ早くアップロードすることをお勧めします。  
+ CTP3、CTP3.1、CTP3.2、RC0、RC1 に [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールした場合、構成後のインストール スクリプトを再実行し、R コンポーネントの前のバージョンと R Services の前のバージョンをアンインストールする必要があります。 
+ 構成後のインストール スクリプトは、プレリリース バージョンのアンインストールを支援する目的のためだけに提供されます。  新しいバージョンをインストールするとき、このスクリプトは実行しないでください。

## <a name="how-to-uninstall-previous-versions-of-r-services"></a>R Services の前のバージョンをアンインストールする方法

前のバージョンの [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] とそれに関連する R コンポーネントを正しい順序でアンインストールすることが重要です。

### <a name="1-run-script-to-deregister-windows-user-group-and-components-before-uninstalling-previous-components"></a>1.前のコンポーネントをアンインストールする前に、スクリプトを実行し、Windows ユーザー グループとコンポーネントの登録を解除する
プレリリース バージョンの [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールしたら、最初にスクリプト `RegisteREext.exe` を実行する必要があります。その際、`/uninstall` 引数を指定します。

それにより、古いコンポーネントの登録が解除され、スタート パッドに関連付けられている Windows ユーザー グループが削除されます。 スクリプトを実行しないと、インストールする新しいインスタンスに必要な Windows ユーザー グループを作成できません。
  
たとえば、既定のインスタンスで R Services をインストールした場合、スクリプトがインストールされているディレクトリからこのコマンドを実行します。  
  
~~~~
    RegisterRExt.exe /UNINSTALL  
~~~~ 
  
名前付きインスタンスに R Services をインストールした場合、**INSTANCE: の後にインスタンス名を指定します。  
  
~~~~ 
RegisterRExt.exe /UNINSTALL /INSTANCE:<instancename>   
~~~~  

すべてのコンポーネントを削除するには、場合によっては、スクリプトを複数回実行する必要があります。

> [!NOTE]
> このスクリプトの既定の場所は、インストールしたプレリリース バージョンによって異なります。 間違ったバージョンのスクリプトを実行しようとすると、エラーが表示されることがあります。 
> 
>  + CTP 3.1、3.2、3.3 の場合、コンポーネントをアンインストールするには、先に [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=723194)からインストール後の構成スクリプトの更新バージョンをダウンロードする必要があります。 更新バージョンでは、古いコンポーネントの登録解除をサポートしています。 リンクをクリックし、 **[名前を付けて保存]** を選択して、スクリプトをローカル フォルダーに保存します。 既存のスクリプトの名前を変更し、スクリプトを実行するフォルダーに新しいスクリプトをコピーします。 
>  + RC0 の場合、正しいスクリプト ファイルがインストールされ、`C:\Program Files\Microsoft\MRO-for-RRE\8.0\R-3.2.2\library\RevoScaleR\rxLibs\x64` フォルダーに格納されます。  
>  + 13.0.1601.5 以降のリリース バージョンの場合、コンポーネントのインストールや構成にスクリプトは必要ありません。 このスクリプトは、古いコンポーネントの削除にのみ使用してください。 


### <a name="2-uninstall-any-older-versions-of-the-revolution-enterprise-tools-including-components-installed-with-ctp-releases"></a>2.CTP リリースでインストールされたコンポーネントを含む、Revolution Enterprise ツールの古いバージョンをアンインストールする

R コンポーネントのアンインストールは、順序がとても重要です。 常に [!INCLUDE[rsql_rre-noversion](../../includes/rsql-rre-noversion-md.md)] を最初にアンインストールしてください。 次に、[!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] をアンインストールします。  

 誤って R Open を最初にアンインストールし、Revolution R Enterprise のアンインストール時にエラーが表示された場合、1 つの回避策は、Revolution R Open または Microsoft R Open を再インストールし、それから両方のコンポーネントを正しい順序でアンインストールすることです。  

### <a name="3-uninstall-any-other-version-of-microsoft-r-open"></a>3.Microsoft R Open のその他のバージョンがあれば、アンインストールする

最後に、Microsoft R Open のその他すべてのバージョンをアンインストールします。
 
### <a name="4-upgrade-sql-server"></a>4.SQL Server をアップグレードする  
  
プレリリース コンポーネントがすべてアンインストールされたら、コンピューターを再起動します。 これは SQL Server セットアップの要件です。再起動が完了するまで、新しいインストールを続行することはできません。     

再起動後、SQL Server セットアップを実行し、「[SQL Server R サービスをセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」の指示に従い、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールします。  
  
追加コンポーネントは必要ありません。R パッケージと接続パッケージは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップでインストールされます。 


## <a name="upgrading-r-components"></a>R コンポーネントをアップグレードする

SQL Server 2016 の修正プログラムや強化機能がリリースされており、インスタンスに R Services 機能が既に含まれている場合、R コンポーネントもアップグレードまたは更新されます。 

ただし、インターネットに接続されていないサーバーをアップグレードする、あるいはパッチを適用するとき、更新を始める前に、更新されたバージョンの R コンポーネントをダウンロードする必要があります。 詳細については、「[インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)」を参照してください。

## <a name="problems-uninstalling-older-versions-of-r"></a>古いバージョンの R をアンインストールするときに発生する問題  
Revolution R Open または Revolution R Enterprise の古いバージョンはアンインストール プロセスで完全に削除されないことがあります。  
  
 古いバージョンを削除できない場合は、レジストリを編集し、関連キーを削除することもできます。  
  
 Windows レジストリを開き、`HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall` キーを見つけます。  
  
 次のエントリがあり、キーに単一値 `sEstimatedSize2` だけが含まれる場合、削除します。  
  
-   E0B2C29E-B8FC-490B-A043-2CAE75634972        (8.0.2 の場合)  
  
-   46695879-954E-4072-9D32-1CC84D4158F4        (8.0.1 の場合)  
  
-   2DF16DF8-A2DB-4EC6-808B-CB5A302DA91B        (8.0.0 の場合)  
  
-   5A2A1571-B8CD-4AAF-9303-8DF463DABE5A        (7.5.0 の場合)  


## <a name="new-license-agreement-for-r-components-required-for-unattended-installs"></a>無人インストールに必要な R コンポーネントの新しい使用許諾契約  
 コマンド ラインを使用して、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] が既にインストールされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスをアップグレードする場合、コマンド ラインを変更して、新しい使用許諾契約パラメーターである */IACCEPTROPENLICENSEAGREEMENT* を使用する必要があります。 
 
 正しい引数を使用しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップが失敗する可能性があります。  
  
## <a name="after-running-setup-includersqlproductnametokenrsqlproductnamemdmd-is-still-not-enabled"></a>セットアップの実行後、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] がまだ有効になっていない  
 外部スクリプトの実行をサポートする機能は、インストールされている場合でも、既定では無効になっています。 攻撃可能領域を減らすという目的があります。  
  
 管理者は [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で次のステートメントを実行し、R スクリプトを有効にできます。  
  
1.  R を使用する [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスで、このステートメントを実行します。  
  
    ```  
    sp_configure 'external scripts enabled',1 
    reconfigure with override  
    ```  
  
2.  インスタンスを再起動します。  
  
3.  インスタンスが再起動したら、**[SQL Server 構成マネージャー]** または **[サービス]** パネルを開き、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスが実行されていることを確認します。  

> [!TIP] 事前構成されている R Services のインスタンスをインストールするには、Enterprises Edition を含む Azure Virtual Machines を使用し、R Services を有効にします。 詳細については、「[Installing SQL Server R Services on an Azure Virtual Machine](../../advanced-analytics/r-services/installing-sql-server-r-services-on-an-azure-virtual-machine.md)」 (Azure Virtual Machine に SQL Server R Services をインストールする) を参照してください。
 

## <a name="setup-of-includersqlproductnametokenrsqlproductnamemdmd-not-available-in-a-failover-cluster"></a>[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のセットアップをフェールオーバー クラスターで利用できない  
 現在のところ、フェールオーバー クラスターに [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールすることはできません。  
    
 ただし、AlwaysOn を使用し、可用性グループに含まれるスタンドアロン コンピューターに [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールできます。 AlwaysOn 可用性グループで R Services を使用する方法については、「[Always On 可用性グループの相互運用性](../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md)」を参照してください。  

別の選択肢は、R スクリプトを実行する目的で別の SQL Server インスタンスにレプリカをセットアップすることです。 レプリカは、レプリケーションまたはログ配布で作成できます。
 
## <a name="launchpad-service-cannot-be-started"></a>スタート パッド サービスを開始できない  

スタート パッドの起動が妨げられるという問題があります。
+ **8dot3 表記が有効になっていません**。  R Services (データベース内) をインストールするには、この機能がインストールされるドライブが、**8dot3** 表記を利用した短いファイル名に対応している必要があります。  8.3 ファイル名は短いファイル名とも呼ばれ、古いバージョンの Microsoft Windows との互換性のため、または長いファイル名の代替ファイル名として使用されます。 

  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールするボリュームが短いファイル名に対応していない場合、SQL Server から R を起動するプロセスで正しい実行可能ファイルが見つからないことがあり、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] が起動しません。  
  
   回避策としては、SQL Server がインストールされ、R Services がインストールされているボリュームで 8dot3 表記を有効にします。 次に、R Services 構成ファイルに作業ディレクトリの短い名前を指定する必要があります。 

    1. 8dot3 表記を有効にするには、*8dot3name* 引数を指定して **fsutil** ユーティリティを実行します。「[fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx)」に説明があります。
    2. 8dot3 表記が有効になったら、RLauncher.config ファイルを開きます。 既定のインストールでは、RLauncher.config ファイルは C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn に置かれます。
    3. WORKING_DIRECTORY のプロパティをメモします。
    4. *file* 引数で fsutil ユーティリティを使用し、WORKING_DIRECTORY に指定されているフォルダーに短いファイル パスを指定します。
    5. 構成ファイルを編集し、WORKING_DIRECTORY の短い名前を使用します。   
     
あるいは、パスが 8dot3 表記と互換性がある別のディレクトリを WORKING_DIRECTORY に指定できます。     
   
   > [!NOTE] この制約は今後のリリースで削除される予定です。 
 
+ **スタート パッドを実行するアカウントが変更されているか、必要なアクセス許可が削除されています。** 既定では、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] は起動時にアカウント NT Service\MSSQLLaunchpad を使用します。このアカウントは [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] セットアップで構成され、必要なすべてのアクセス許可が与えられます。

  そのため、スタート パッドに別のアカウントを割り当てるか、SQL Server コンピューターのポリシーにより権限が消された場合、アカウントには必要なアクセス許可が与えられず、*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Logon failure: the user has not been granted the requested logon type at this computer* (ログオン エラー: このコンピューターで要求されるログオン タイプがユーザーに与えられていません) というエラーが表示されることがあります。

  新しいサービス アカウントに必要なアクセス許可を与えるには、**ローカル セキュリティ ポリシー** アプリケーションを使用し、アカウントのアクセス許可を更新して以下のアクセス許可を追加します。
  + プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
  + スキャン チェックを行わない (SeChangeNotifyPrivilege)
  + サービスとしてログオン (SeServiceLogonRight)
  + プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

  SQL Server サービスを実行するためのアクセス許可の詳細については、「[Windows サービス アカウントとアクセス許可の構成](https://msdn.microsoft.com/library/ms143504.aspx#Windows)」をご覧ください。
  
## <a name="side-by-side-installation-not-supported"></a>サイド バイ サイド インストールがサポートされない  
 R の別バージョンまたは Revolution Analytics からの他のリリースを利用したサイドバイサイド インストールは作成しないでください。  

## <a name="offline-installation-of-r-components-for-localized-version-of-sql-server"></a>ローカライズされた SQL Server のための R コンポーネントのオフライン インストール 
インターネット アクセスのないコンピューターに R Services をインストールする場合、さらに 2 つの手順が必要になります。SQL Server セットアップを実行する前に、ローカル フォルダーに R コンポーネント インストーラーをダウンロードする必要があります。そして、正しい言語がインストールされるように、インストーラー ファイルを編集する必要があります。 

R コンポーネントに使用される言語識別子は、インストールされる SQL Server セットアップ言語と同じにする必要があります。同じになっていない場合、**[次へ]** ボタンが無効になり、セットアップを完了できません。

詳細については、「[インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)」を参照してください。 
  
## <a name="unable-to-launch-runtime-for-r-script"></a>R スクリプトのランタイムを起動できません
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、R ジョブを実行するために [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] により使用される Windows ユーザー グループが作成されます。 このユーザー グループには、Windows 統合認証を利用しているリモート ユーザーの代わりに R を実行するために、R Services を実行しているインスタンスにログインする権限を与える必要があります。
  
 R ユーザーの Windows グループ (**SQLRUsers**) にこの権限がない環境では、次のエラーが発生します。  
  
-   R スクリプトを実行しようとしたとき:  
  
     *'R' スクリプトのランタイムを起動できません。'R' ランタイムの構成を確認してください。*  
  
     *外部スクリプト エラーが発生しました。ランタイムを起動できません。*  
  
-   [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスによって生成されるエラー:  
  
     *ランチャー RLauncher.dll を初期化できませんでした*  
  
     *ランチャー dll が登録されていません!*  
  
-   セキュリティ ログに、NT SERVICE\MSSQLLAUNCHPAD アカウントがログインできなかったことが示される。  
  
このユーザー グループに必要なアクセス許可を与える方法については、「[SQL Server R Services をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」を参照してください。 

> [!NOTE]
> 
> SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。 

  
## <a name="remote-execution-via-odbc"></a>ODBC 経由のリモート実行   
 データ サイエンス ワークステーションを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに接続し、**RevoScaleR** 関数で R コマンドを実行する場合、データをサーバーに書き込む ODBC 呼び出しを使用するときに、エラーが表示されることがあります。 
 
 これは、前のセクションで説明した理由と同じ理由によるものです。セットアップ時、R Services により、R タスクの実行に使用されるワーカー アカウントのグループが作成されます。 しかしながら、そのアカウントでサーバーに接続できない場合、ODBC 呼び出しを代理実行することができません。 
 
 SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。SQL ログインの資格情報は、R クライアントから SQL Server インスタンスに、それから ODBC に明示的に渡されるためです。
  
暗黙の認証を有効にするには、このワーカー アカウント グループに次のようにアクセス許可を与える必要があります。  
    
1. R コードを実行するインスタンスで監理者として [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開きます。 

2. 次のスクリプトを実行します。 必ずユーザー グループの名前 (初期設定を変更した場合) とコンピューターとインスタンスの名前を編集してください。
    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO  
    ```

詳細と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] UI でこれを行う手順については、「[SQL Server R Services をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」を参照してください。

    
## <a name="errors-during-setup-because-r-components-cannot-be-installed"></a>R コンポーネントをインストールできないために、セットアップ中にエラーが発生する  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを利用し、R Services (データベース内) をインストールし、Microsoft R Open ライセンス条件を含むページで **[承諾]** をクリックすると、コンポーネントの場所が特定され、他のコンポーネントがインストールされたときにインストールが開始します。 ただし、次のような場合、コンポーネントのインストールに失敗することができます。  
  
-   オフライン インストールを実行しているとき、コンポーネントをダウンロードできない。  
  
     [インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)  
  
-   更新を確認するオプションを利用しているとき、適切なバージョンのコンポーネントが見つからないため、更新サービスがエラーを返す。  
  
  これは既知の問題であり、RC3 で修正されています。  
  
 
  
## <a name="upgrade-of-r-server-standalone-to-rc3-requires-uninstallation-using-the-rc2-setup-utility"></a>R Server (スタンドアロン) を RC3 にアップグレードするには、RC2 セットアップ ユーティリティによるアンインストールが必要
 Microsoft R Server (スタンドアロン) は最初に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2 で利用可能になりました。 RC3 バージョンの Microsoft R Server にアップグレードするには、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2 セットアップを利用して最初にアンインストールし、それから [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC3 セットアップを利用して再インストールする必要があります。  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを利用し、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RC2 の Uninstall R Server (スタンドアロン) をアンインストールします。  
  
2.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を RC3 にアップグレードし、R Services (データベース内) をインストールするオプションを選択します。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のインスタンスが RC3 にアップグレードされます。追加の構成は必要ありません。  
  
3.  RC3 の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] セットアップをもう一度実行し、Microsoft R Server (スタンドアロン) をインストールします。  

RTM バージョンの Microsoft R Server にアップグレードするときは、この回避策は必要ありません。

## <a name="see-also"></a>参照  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [Microsoft R Server の概要 &#40;スタンドアロン&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  