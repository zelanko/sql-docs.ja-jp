---
title: "マスター データ サービスのイントールと構成 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 37
---
# マスター データ サービスのイントールと構成
  この記事では、Windows Server 2012 R2 コンピューターへの [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] のインストール方法、MDS データベースと Web サイトの設定方法、およびサンプル モデルとデータの配置方法について説明します。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) では、組織が信頼されたバージョンのデータを管理できるようにします。   
   
[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]のデータを整理する方法の概要については、 [マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md) を参照してください。     
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の新機能については、「[マスター データ サービス (MDS) の新機能](../master-data-services/what-s-new-in-master-data-services-mds.md)」を参照してください。  
 
[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]を学習するためのビデオと他のトレーニング リソースへのリンクについては、「[マスター データ サービスについて学習する](../master-data-services/learn-sql-server-master-data-services.md)」をご覧ください。 
  
> **ダウンロード**  
>-   [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]をダウンロードするには、  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**にアクセスしてください。  
>-   Azure アカウントをすでにお持ちですか?  既にお持ちの場合は、 **[こちら](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** にアクセスして、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  がインストール済みの仮想マシンをすぐにご利用いただけます。  
 
> **MDS Web サイトを作成できませんか?**
>>この問題を解決する方法については、この Microsoft サポートの記事を参照してください。
[SQL Server 2016 の低い特権のアカウントでは、MDS Web サイトを作成することはできません。](https://aka.ms/mdssupport) 
  
## <a name="installing-master-data-services-and-iis-roles-and-features"></a>マスター データ サービスのイントール、および IIS の役割と機能の構成  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップ インストール ウィザードまたはコマンド プロンプトを使用して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールします。  
  
 **Windows Server 2012 R2 コンピューター上で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップを使用して [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] をインストールするには**  
  
1.  Setup.exe をダブルクリックして、インストール ウィザードの手順を実行します。  
  
2.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [機能の選択] **ページで、** [共有機能] **の [**] を選択します。  
  
     これは [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]、アセンブリ、Windows PowerShell スナップインのほか、Web アプリケーションおよび Web サービス用のフォルダーおよびファイルがインストールされます。  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  ウィザードの指示に従って操作します。  
  
4.  [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]で、 **デスクトップ** のタスクバーにある **[サーバー マネージャー]**アイコンをクリックします。  
  
     ![Icon for the Server Manager in Windows Server 2012 taskbar](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Icon for the Server Manager in Windows Server 2012 taskbar")  
  
5.  **サーバー マネージャー**で、 **[管理]** メニューの **[役割と機能の追加]** をクリックします。  
  
     ![In Server Manage, the Add Roles and Features menu command](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "In Server Manage, the Add Roles and Features menu command")  
  
6.  **役割と機能の追加ウィザード** の **[インストールの種類]**ページで、既定値 (**役割ベースまたは機能ベースのインストール**) を承諾して、 **[次へ]**をクリックします。  
  
7.  **[サーバー プールからサーバーを選択]**をクリックして、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールしたサーバーをクリックします。  
  
     ![Server Selection page on the Add Roles and Features Wizard](../master-data-services/media/mds-servermanagerdashboard-addrolesandfeatureswizard-serverselection.png "Server Selection page on the Add Roles and Features Wizard")  
  
8.  **[役割]** ボックスで、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]に必要な役割および役割サービスをクリックして、 **[次へ]**をクリックします。 次の図は、選択済みの必須の役割と役割サービスを示しています。  
  
    > [!WARNING]  
    >  [WebDAV 発行] 役割サービスをインストールしないでください。 WebDAV 発行は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]と互換性がありません。  
  
    > [!IMPORTANT]  
    >  **動的なコンテンツ圧縮** は既定で有効になっています。 CPU 使用率は増加しますが、XML 応答サイズを大幅に縮小し、ネットワーク I/O を節約できます。  詳細については、「 **マスター データ サービス &#40;MDS&#41; の新機能** in [What's New in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)」を参照してください。  
  
    |役割と役割サービス|役割と役割サービス|  
    |-----------------------------|-----------------------------|  
    |![Common HTTP Features](../master-data-services/media/mds-servermanagerdashboard-commonhttpfeaturesroles.png "Common HTTP Features")|![Health Diagnostics Roles](../master-data-services/media/mds-servermanagerdashboard-healthdiagnosticsroles.png "Health Diagnostics Roles")|  
    |![Performance Roles](../master-data-services/media/mds-servermanagerdashboard-performanceroles.png "Performance Roles")|![Security Roles](../master-data-services/media/mds-servermanagerdashboard-securityroles.png "Security Roles")|  
    |![WebServer Application Development Roles](../master-data-services/media/mds-servermanagerdashboard-webserverapplicationdevelopmentroles.png "WebServer Application Development Roles")|![Management Tools](../master-data-services/media/mds-servermanagerdashboard-managementtoolsroles.png "Management Tools")|  
  
     他のオペレーティング システムで必須の役割と役割サービスの一覧は、「[Web アプリケーションの要件 &#40;マスター データ サービス&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)」を参照してください。  
  
9. **[機能]** ボックスで、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]に必要な機能をクリックして、 **[次へ]**をクリックします。 次の図は、選択した、必須の機能を示しています。  
  
    |[機能]|機能|  
    |--------------|--------------|  
    |![Net Framework Features](../master-data-services/media/mds-servermanagerdashboard-netframeworkfeatures.png "Net Framework Features")|![Windows Process Features](../master-data-services/media/mds-servermanagerdashboard-windowsprocessfeatures.png "Windows Process Features")|  
  
     他のオペレーティング システムで必須の機能の一覧は、「[Web アプリケーションの要件 &#40;マスター データ サービス&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)」を参照してください。  
  
 セットアップを使用した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールの詳細については、「[インストール ウィザードからの SQL Server 2016 のインストール (セットアップ)](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)」を参照してください。  
  
 コマンド プロンプトを使用した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールの詳細については、「[コマンド プロンプトから SQL Server 2016 をインストール](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。 コマンド プロンプトを使用する場合、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は機能パラメーターとして使用できるようになります。  
  
 インストール前のタスクに関する追加情報へのリンクの簡単な説明については、「 [マスター データ サービスをインストールする](../master-data-services/install-windows/install-master-data-services.md)」を参照してください。  
  
##  <a name="a-namesetupweba-setting-up-the-database-and-website"></a><a name="SetUpWeb"></a> データベースと Web サイトを設定する  
 **[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、データベースと Web サイトを設定するには**  
  
1.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]を起動して、 **[データベース構成]** をクリックします。  
  
2.  **[データベースの作成]**をクリックして、 **データベースの作成ウィザード** で **[次へ]**をクリックします。  
  
3.  **[データベース サーバー]** ページで、 **[認証の種類]** を選択して、 **[接続のテスト]** をクリックし、選択した認証の種類の資格情報を使用して、データベースに接続できることを確認します。  
  
    > [!NOTE]  
    >  認証の種類に **[現在のユーザー - 統合セキュリティ]** を選択すると、 **[ユーザー名]** ボックスは読み取り専用で、コンピューターにログオンした Windows ユーザー アカウント名が表示されます。  
  
     ![The Database server page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-serverpage.png "The Database server page in the Create Database Wizard")  
  
4.  **[データベース名]** フィールドに名前を入力します。 必要に応じて、Windows 照合順序を選択して、 **[大文字小文字を区別する]**などの利用可能なオプションを 1 つ以上指定し、 **[SQL Server の既定の照合順序]** チェック ボックスをオフにします。  
  
     ![The Database page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-databasepage.png "The Database page in the Create Database Wizard")  
  
     Windows 照合順序の詳細については、「 [Windows 照合順序名 (Transact-SQL)](https://msdn.microsoft.com/library/ms188046.aspx)」を参照してください。  
  
5.  **[ユーザー名]** フィールドで、マスター データ サービスの既定のスーパー ユーザーになるユーザーの Windows アカウントを指定します。 スーパー ユーザーには、すべての機能領域へのアクセス権があり、すべてのモデルを追加、削除、および更新できます。  
  
     ![The Administrator Account page in the Create Database Wizard.](../master-data-services/media/mds-configurationmanager-createdatabasewizard-adminpage.png "The Administrator Account page in the Create Database Wizard.")  
  
6.  **[次へ]** をクリックして、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの設定の概要を表示し、**[次へ]** をもう一度クリックしてデータベースを作成します。  
  
     **データベースの作成ウィザード**の設定の詳細については、「[データベースの作成ウィザード (マスター データ サービス構成マネージャー)](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md)」を参照してください。  
  
7.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の[データベース構成] ページで、[データベースの選択] をクリックします。  
  
8.  **[接続]**をクリックして、手順 6 で作成した [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択します。  
  
     ![Connect to Database dialog box for the Database Configuration page](../master-data-services/media/mds-configurationmanager-selectdatabasebutton-connecttodatabasedialog.png "Connect to Database dialog box for the Database Configuration page")  
  
     データベースの設定が完了しました。 **[データベース構成]** ページには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用に接続している [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]インスタンス、作成したデータベース、および現在のデータベース バージョンが表示されます。  
  
     ![Database Configuration page in the Configuration Manager shows a completed database setup.](../master-data-services/media/mds-configurationmanager-databaseconfig-completed.png "Database Configuration page in the Configuration Manager shows a completed database setup.")  
  
9. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] の左ペインで、**[Web の構成]**をクリックします。  
  
10. **[Web サイト]** リスト ボックスで、**[既定の Web サイト]****[作成]** の順にクリックして、Web アプリケーションを作成します。  
  
    > [!NOTE]  
    >  **[既定の Web サイト]** を選択した場合、Web アプリケーションを作成する必要があります。 リスト ボックスで **[新しい Web サイトの作成]** を選択した場合、アプリケーションが自動的に作成されます。  
  
     ![Web Configuration page in the Configuration Manager](../master-data-services/media/mds-configurationmanager-webconfig.png "Web Configuration page in the Configuration Manager")  
  
11. **[アプリケーション プール]** セクションで、次のいずれかを実行します。  
  
    -   **管理者アカウント**データベースに対して、手順 5 で入力したのと同じユーザー名を入力し、パスワードを入力して、 **[OK]**をクリックします。  
  
         **- または -**  
  
    -   別のユーザー名とパスワードを入力し、[OK] をクリックします。  
  
         データベースと Web アプリケーションを作成する場合、同じアカウントを使用する必要はありません。  
  
     ![Create Web Application dialog box, Web Configuration page](../master-data-services/media/mds-configurationmanager-webconfig-createwebapplication.png "Create Web Application dialog box, Web Configuration page")  
  
     **[Web アプリケーションの作成]** ダイアログ ボックスの詳細については、「[[Web アプリケーションの作成] ダイアログ ボックス (マスター データ サービス構成マネージャー)](../Topic/Create%20Web%20Application%20Dialog%20Box%20\(Master%20Data%20Services%20Configuration%20Manager\).md)」を参照してください。  
  
12. **[Web アプリケーション]** ボックスの **[Web 構成]** ページで、作成したアプリケーションをクリックして、**[アプリケーションとデータベースの関連付け]** セクションで **[選択]** をクリックします。  
  
13. **[接続]**をクリックして、Web アプリケーションと関連付けする必要がある [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択し、 **[OK]**をクリックします。  
  
     Web サイトの設定が完了しました。 **[Web の構成]** ページには、選択した Web サイト、作成した Web アプリケーション、およびアプリケーションに関連付けられた [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースが表示されます。  
  
     ![The completed Web site configuration](../master-data-services/media/mds-configurationmanager-webconfig-completed.png "The completed Web site configuration")  
  
     [Web の構成] ページの設定に関する詳細については、「[[Web の構成] ページ (マスター データ サービス構成マネージャー)](../Topic/Web%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)」を参照してください。  
  
 また、[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションとサービスのその他の設定値も指定できます。 たとえば、データの読み込み頻度や検証メールの送信頻度を指定できます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
##  <a name="a-namedeploysamplea-deploying-sample-models-and-data"></a><a name="deploySample"></a> サンプル モデルとデータを配置する  
 次の 3 つのサンプル モデル パッケージは、  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]に付属しています。   これらのサンプル モデルには、データが含まれます。 **サンプル モデル パッケージの既定の場所は、%programfiles%\Microsoft SQL Server\130\Master Data Services\Samples\Packages です。**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 このパッケージは、MDSModelDeploy ツールを使用して配置します。 MDSModelDeploy ツールの既定の場所は、 *drive*\Program Files\Microsoft SQL Server\ 130\Master Data Services\Configuration にあります。  
  
 このツールを実行するための前提条件については、「 [MDSModelDeploy を使用したモデルの配置パッケージの配置](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の新機能をサポートするためにデータに加えられた更新については、「[サンプル: モデルの配置パッケージ &#40;マスター データ サービス&#41;](../Topic/Samples:%20Model%20Deployment%20Packages%20\(Master%20Data%20Services\).md)」を参照してください。  
  
 **サンプル モデルを配置するには**  
  
1.  サンプル モデル パッケージを *drive*\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration にコピーします。  
  
2.  管理者のコマンド プロンプトを開き、次のコマンドを実行して、MDSModelDeploy.exe のある場所に移動します。  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration  
    ```  
  
3.  次の各コマンドを実行して、各サンプル モデルを [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] に配置します。  
  
    > [!IMPORTANT]  
    >  次の例では、サービスの値に `MDS1` が指定されます。 **Web サイトの設定時に、** [既定の Web サイト] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] を選択した場合、この値を使用します。  「 [データベースと Web サイトを設定する](#SetUpWeb) 」セクションを参照してください。  
    >   
    >  新しい Web サイトを作成したか、または別の既存の Web サイトを選択した場合、適切なサービス値を特定するために、まず次のコマンドを実行します。  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  戻り値のリスト内の最初のサービス値は、モデルを配置するために指定する値です。  
  
     **chartofaccounts_en.pkg サンプル モデルを配置するには**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model ChartofAccounts -service MDS1  
    ```  
  
     **customer_en.pkg サンプル モデルを配置するには**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **product_en.pkg サンプル モデルを配置するには**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Product -service MDS1  
  
    ```  
  
     モデルが正常に配置されると、" **MDSModelDeploy 操作は完了しました** " というメッセージが表示されます。  
  
     次の図は、product_en.pkg サンプル モデルを配置するためのコマンドを示します。  
  
     ![Command line for deploying the Product sample model](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Command line for deploying the Product sample model")  
  
4.  サンプル モデルを表示するには、次を実行します。  
  
    1.  設定する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サイトに移動します。 「 [データベースと Web サイトを設定する](#SetUpWeb) 」セクションを参照してください。  
  
         Web サイトのアドレスは、http://*server name*/*web application*/ です。  
  
    2.  **[モデル]** リスト ボックスからモデルを選択して、 **[エクスプローラー]**をクリックします。  
  
         ![MDS Web site, home page.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "MDS Web site, home page.")  
  
## <a name="next-step"></a>次の手順  
 自分のデータ用に新しいモデルとエンティティを作成します。 「[モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)」と「[エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)」を参照してください。  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のデータの構造を構築するモデルとエンティティを使用する方法の概要については、「[マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)」を参照してください。  
  
## <a name="did-this-article-help-you-were-listening"></a>この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services) にコメントをお送りください  
  
## <a name="see-also"></a>参照  
 [マスター データ サービス データベース](../master-data-services/master-data-services-database.md)   
 [マスター データ マネージャー Web アプリケーション](../master-data-services/master-data-manager-web-application.md)   
 [[データベース構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../Topic/Database%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)   
 [マスター データ サービス &#40;MDS&#41; の新機能](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  