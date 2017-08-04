---
title: "マスター データ サービスのインストールと構成 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: sabotta
ms.author: carlasab
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 25e5dc869efd2417c47b72c70ede7ba19ab54b46
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="master-data-services-installation-and-configuration"></a>マスター データ サービスのイントールと構成
  この記事では、Windows Server 2012 R2 コンピューターへの [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] のインストール方法、MDS データベースと Web サイトの設定方法、およびサンプル モデルとデータの配置方法について説明します。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) では、組織が信頼されたバージョンのデータを管理できるようにします。   
  
> [!NOTE] 
> インストールすることができます[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]なった Developer edition を使用する際にコンピューターをサポートしている Windows 10 で[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]です。 
>>サポートするオペレーティング システムの詳細については異なる[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]エディションを参照してください[Hardware and Software Requirements for Installing SQL Server 2016](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)です。 

[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]のデータを整理する方法の概要については、 [マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)を参照してください。     
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の新機能については、「[マスター データ サービス (MDS) の新機能](../master-data-services/what-s-new-in-master-data-services-mds.md)」を参照してください。  
 
[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]を学習するためのビデオと他のトレーニング リソースへのリンクについては、「[マスター データ サービスについて学習する](../master-data-services/learn-sql-server-master-data-services.md)」をご覧ください。 
  
> **ダウンロード**  
>-   [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]をダウンロードするには、  **[評価センター](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2017-ctp/)**に移動してください。  
>-   Azure アカウントをすでにお持ちですか?  次いで**[ここ](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**から既にインストールされている SQL server 仮想マシンを起動します。  
 
> **MDS Web サイトを作成できませんか?**
>>この問題を解決する方法については、この Microsoft サポートの記事を参照してください。
[SQL Server 2016 の低い特権のアカウントでは、MDS Web サイトを作成することはできません。](https://aka.ms/mdssupport) 

## <a name="internet-explorer-and-silverlight"></a>Internet Explorer と Silverlight
- インストールするときに[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]Windows Server 2012 コンピューターで Internet Explorer セキュリティ強化をアプリケーションの Web サイトのスクリプティングを使用するを構成する必要があります。 それ以外の場合、サーバー コンピューター上のサイトへのアクセスは失敗します。
- Web アプリケーションで作業するには、クライアント コンピューターに Silverlight 5 をインストールする必要があります。 Silverlight の必要なバージョンがあるない場合は、必要とする Web アプリケーションの領域に移動したときにインストールする促されます。 Silverlight 5 をインストールする**[ここ](https://www.microsoft.com/silverlight/)**です。

## <a name="includessmdsshortmdincludesssmdsshort-mdmd-on-an-azure-virtual-machine"></a>[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]Azure の仮想マシン
既定を Azure 仮想マシンでを起動するときに[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]既にインストールされている、[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]もインストールされます。 

できたら [次へ] の手順ではインターネット インフォメーション サービス (IIS) をインストールします。 参照してください、[のインストールと IIS を構成する](#InstallIIS)セクションです。 

インストールを変更するのには該当するかどうかは[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]、既定の場所に、setup.exe ファイルがわかります`<drive>`: \SQLServer_13.0_Full です。
  
## <a name="InstallMDS"></a>マスター データ サービスをインストールします。  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップ インストール ウィザードまたはコマンド プロンプトを使用して、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールします。  
  
 **Windows Server 2012 R2 コンピューター上で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップを使用して [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] をインストールするには**  
  
1.  Setup.exe をダブルクリックして、インストール ウィザードの手順を実行します。  
  
2.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [機能の選択] **ページで、** [共有機能] **の [**] を選択します。  
  
     これは [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]、アセンブリ、Windows PowerShell スナップインのほか、Web アプリケーションおよび Web サービス用のフォルダーおよびファイルがインストールされます。  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  ウィザードの指示に従って操作します。  

## <a name="InstallIIS"></a>インストールして、IIS を構成します。
  
1.  [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]で、 **デスクトップ** のタスクバーにある **[サーバー マネージャー]**アイコンをクリックします。  
  
     ![サーバー マネージャーの Windows Server 2012 のタスク バーのアイコン](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "サーバー マネージャーの Windows Server 2012 のタスク バーのアイコン")  
  
5.  **サーバー マネージャー**で、 **[管理]** メニューの **[役割と機能の追加]** をクリックします。  
   
     ![サーバーの管理、追加の役割と機能 メニューのコマンドで](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "でサーバーを管理、追加の役割と機能のメニュー コマンド")  
  
6.  **役割と機能の追加ウィザード** の **[インストールの種類]**ページで、既定値 (**役割ベースまたは機能ベースのインストール**) を承諾して、 **[次へ]**をクリックします。  
  
7.  **[サーバー プールからサーバーを選択]**をクリックして、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]をインストールしたサーバーをクリックします。  
  
     ![mds_AddRolesFeaturesWizard_ServerSelectionPage](../master-data-services/media/mds-addrolesfeatureswizard-serverselectionpage.png) 
  
8. **サーバーの役割** ページで、をクリックして**Web サーバー**  をクリックし、**次**です。 

   ![mds_AddRolesFeaturesWizard_ServerRolesPage](../master-data-services/media/mds-addrolesfeatureswizard-serverrolespage.png)
   
9. **機能** ページで、次の機能が選択されていることを確認し、をクリックして**次**です。 これらの機能に必要な[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]で[!INCLUDE[winblue_server_2_md](../includes/winblue-server-2-md.md)]です。
  
    |機能のインストール|機能のインストール|  
    |--------------|--------------|  
    |![mds_AddRolesFeaturesWizard_FeaturesPage](../master-data-services/media/mds-addrolesfeatureswizard-featurespage.png)|![mds_AddRolesFeaturesWizard_FeaturesPage_WindowsProcActive](../master-data-services/media/mds-addrolesfeatureswizard-featurespage-windowsprocactive.png)|  

10. 左側のウィンドウで [ **Web サーバーの役割 (IIS)** ] をクリックし、**役割サービス**です。
11. **役割サービスの** ページで、次のサービスが選択されていることを確認し、をクリックして**次**です。 これらのサービスに必要な[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で[!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]です。

    > [!WARNING]  
    >  [WebDAV 発行] 役割サービスをインストールしないでください。 WebDAV 発行は、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]と互換性がありません。  
  
     |役割サービス|役割サービス|  
    |-----------------------------|-----------------------------|  
    |![mds_AddRolesFeaturesWizard_RoleServicesPage](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage.png)|![mds_AddRolesFeaturesWizard_RoleServicesPage_PerformSecurity](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-performsecurity.png)|  
    |![mds_AddRolesFeaturesWizard_RoleServicesPage_AppDevsection](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-appdevsection.png)|![mds_AddRolesFeaturesWizard_RoleServicesPage_ManageToolssection](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-managetoolssection.png)|  
    |||  
  
     必要な機能と他のオペレーティング システムの役割サービスの一覧は、次を参照してください。 [Web アプリケーションの要件 & #40 です。マスター データ サービス &#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md) .   
  
 セットアップを使用した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールの詳細については、「[インストール ウィザードからの SQL Server 2016 のインストール (セットアップ)](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)」を参照してください。  
  
 コマンド プロンプトを使用した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールの詳細については、「[コマンド プロンプトから SQL Server 2016 をインストール](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)」を参照してください。 コマンド プロンプトを使用する場合、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] は機能パラメーターとして使用できるようになります。  
  
 インストール前のタスクに関する追加情報へのリンクの簡単な説明については、「 [マスター データ サービスをインストールする](../master-data-services/install-windows/install-master-data-services.md)」を参照してください。  
  
##  <a name="SetUpWeb"></a> データベースと Web サイトを設定する  
 **[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、データベースと Web サイトを設定するには**  

 
> [!WARNING]  
    >  必要な[IIS をインストール](#InstallIIS)起動する前に、 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Configuration Manager です。 それ以外の場合、Configuration Manager についての情報サービス エラーが表示されます、作成することができなく、 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] web アプリケーションです。  
    
> **ブラウザー要件**
>>[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Web アプリケーションのみで Internet Explorer (IE) 9 以降の動作です。 IE 8 以前のバージョン、Microsoft Edge、Chrome はサポートされていません。    
  
1.  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]を起動して、 **[データベース構成]** をクリックします。  
  
2.  **[データベースの作成]**をクリックして、 **データベースの作成ウィザード** で **[次へ]**をクリックします。  
  
3.  **[データベース サーバー]** ページで、 **[認証の種類]** を選択して、 **[接続のテスト]** をクリックし、選択した認証の種類の資格情報を使用して、データベースに接続できることを確認します。 **[次へ]**をクリックします。
  
    > [!NOTE]  
    >  認証の種類に **[現在のユーザー - 統合セキュリティ]** を選択すると、 **[ユーザー名]** ボックスは読み取り専用で、コンピューターにログオンした Windows ユーザー アカウント名が表示されます。 実行する場合は[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]で、Azure 仮想マシン (VM) を**ユーザー名**ボックスは、VM を VM の名前と、ローカル管理者アカウントのユーザー名を表示します。 

    ![mds_2016ConfigManager_CreateDatabaseWizard_ServerPage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-serverpage.png)  
  
4.  **[データベース名]** フィールドに名前を入力します。 オプションで、Windows 照合順序を選択するには、オフ、 **SQL Server の既定の照合順序** チェック ボックスなど、使用可能なオプションの 1 つ以上のクリックと**大文字小文字を区別**です。 **[次へ]**をクリックします。

    ![mds_2016ConfigManager_CreateDatabaseWizard_DatabasePage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-databasepage.png)  
  
     Windows 照合順序の詳細については、「 [Windows 照合順序名 (Transact-SQL)](https://msdn.microsoft.com/library/ms188046.aspx)」を参照してください。  
  
5.  **[ユーザー名]** フィールドで、マスター データ サービスの既定のスーパー ユーザーになるユーザーの Windows アカウントを指定します。 スーパー ユーザーには、すべての機能領域へのアクセス権があり、すべてのモデルを追加、削除、および更新できます。  

    ![mds_2016ConfigManager_CreateDatabaseWizard_AdminPage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-adminpage.png)  
  
6.  **[次へ]** をクリックして、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの設定の概要を表示し、 **[次へ]** をもう一度クリックしてデータベースを作成します。 **進行状況し、完了日**ページが表示されます。

7. データベースが作成され、構成されているをクリックして**完了**です。  
  
     **データベースの作成ウィザード**の設定の詳細については、「[データベースの作成ウィザード (マスター データ サービス構成マネージャー)](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md)」を参照してください。  
  
7.  **データベース構成** ページで、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]、 をクリックして**データベースの選択**です。  
  
8.  をクリックして**接続**を選択、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]手順 7. で作成し、をクリックしたデータベース**OK**です。 

    ![mds_2016ConfigManager_SelectDatabaseButton_ConnectToDatabaseDialog](../master-data-services/media/mds-2016configmanager-selectdatabasebutton-connecttodatabasedialog.png)  
  
     データベースの設定が完了しました。 **[データベース構成]** ページには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用に接続している [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]インスタンス、作成したデータベース、および現在のデータベース バージョンが表示されます。  

    ![mds_2016ConfigManager_DatabaseConfig_Completed](../master-data-services/media/mds-2016configmanager-databaseconfig-completed.png)   
  
9. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の左ペインで、 **[Web の構成]** をクリックします。  
  
10. **[Web サイト]** リスト ボックスで、**[既定の Web サイト]****[作成]** の順にクリックして、Web アプリケーションを作成します。  
  
    > [!NOTE]  
    >  **[既定の Web サイト]** を選択した場合、Web アプリケーションを作成する必要があります。 リスト ボックスで **[新しい Web サイトの作成]** を選択した場合、アプリケーションが自動的に作成されます。  

     ![mds_2016ConfigManager_WebConfig](../master-data-services/media/mds-2016configmanager-webconfig.png)  
  
11. **[アプリケーション プール]** セクションで、次のいずれかを実行します。  
  
    -   **管理者アカウント**データベースに対して、手順 5 で入力したのと同じユーザー名を入力し、パスワードを入力して、 **[OK]**をクリックします。  
  
         **- または -**  
  
    -   別のユーザー名とパスワードを入力し、[OK] をクリックします。  
  
         データベースと Web アプリケーションを作成する場合、同じアカウントを使用する必要はありません。  

        ![mds_2016ConfigManager_WebConfig_CreateWebApplication](../master-data-services/media/mds-2016configmanager-webconfig-createwebapplication.png)   
  
     **[Web アプリケーションの作成]** ダイアログ ボックスの詳細については、「[[Web アプリケーションの作成] ダイアログ ボックス (マスター データ サービス構成マネージャー)](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md)」を参照してください。  
  
12. **[Web アプリケーション]** ボックスの **[Web 構成]** ページで、作成したアプリケーションをクリックして、**[アプリケーションとデータベースの関連付け]** セクションで **[選択]** をクリックします。  
  
13. **[接続]**をクリックして、Web アプリケーションと関連付けする必要がある [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースを選択し、 **[OK]**をクリックします。  
  
     Web サイトの設定が完了しました。 **[Web の構成]** ページには、選択した Web サイト、作成した Web アプリケーション、およびアプリケーションに関連付けられた [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースが表示されます。  

     ![mds_2016ConfigManager_WebConfig_Completed](../master-data-services/media/mds-2016configmanager-webconfig-completed.png)  
 
     
15. **[適用]**をクリックします。 **構成が完了しました**メッセージ ボックスが表示されます。 をクリックして**OK** web アプリケーションを起動するメッセージ ボックスにします。 Web サイトのアドレスは、http://*server name*/*web application*/ です。 


![mds_2016ConfigurationComplete_MessageBox](../master-data-services/media/mds-2016configurationcomplete-messagebox.png) 
  
     For more information about the settings on the Web Configuration page, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
 また、 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] を使って、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに関連付けられている Web アプリケーションとサービスのその他の設定値も指定できます。 たとえば、データの読み込み頻度や検証メールの送信頻度を指定できます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
##  <a name="deploySample"></a> サンプル モデルとデータを配置する  
 次の 3 つのサンプル モデル パッケージは、  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]に付属しています。   これらのサンプル モデルには、データが含まれます。 **サンプル モデル パッケージの既定の場所は、%programfiles%\Microsoft SQL Server\140\Master Data services \samples\packages です。**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 このパッケージは、MDSModelDeploy ツールを使用して配置します。 MDSModelDeploy ツールの既定の場所は*ドライブ*\Program Files\Microsoft SQL server \ 140\Master データ services \configuration にあります。  
  
 このツールを実行するための前提条件については、「 [MDSModelDeploy を使用したモデルの配置パッケージの配置](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)」を参照してください。  
  
 新機能をサポートするために、データに加えられた更新プログラムについては[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]を参照してください[SQL Server のサンプル: モデル配置パッケージ (MDS)](../master-data-services/sql-server-samples-model-deployment-packages-mds.md)です。  
  
 **サンプル モデルを配置するには**  
  
1.  サンプル モデル パッケージをコピー*ドライブ*\Program Files\Microsoft SQL Server\140\Master データ services \configuration にあります。  
  
2.  管理者のコマンド プロンプトを開き、次のコマンドを実行して、MDSModelDeploy.exe のある場所に移動します。  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\140\Master Data Services\Configuration  
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
    >
    > [!NOTE]
    > サンプル モデルのメタデータ情報に関する詳細を知りするにを参照してください"c:\Program files \microsoft SQL Server\140\Master Data services \configuration"この場所で使用可能な readme ファイル
    >
   
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
  
     ![製品サンプル モデルを配置するためのコマンド ライン](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "製品サンプル モデルを展開するためのコマンドライン")  
  
4.  サンプル モデルを表示するには、次を実行します。  
  
    1.  設定する [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サイトに移動します。 「 [データベースと Web サイトを設定する](#SetUpWeb) 」セクションを参照してください。  
  
         Web サイトのアドレスは、http://*server name*/*web application*/ です。  
  
    2.  **[モデル]** リスト ボックスからモデルを選択して、 **[エクスプローラー]**をクリックします。  
  
         ![MDS Web サイトでは、ホーム ページ。] (../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "MDS Web サイトのホーム ページです。")  
  
## <a name="next-step"></a>次の手順  
 自分のデータ用に新しいモデルとエンティティを作成します。 「[モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)」と「[エンティティを作成する (マスター データ サービス)](../master-data-services/create-an-entity-master-data-services.md)」を参照してください。  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のデータの構造を構築するモデルとエンティティを使用する方法の概要については、「[マスター データ サービスの概要 (MDS)](../master-data-services/master-data-services-overview-mds.md)」を参照してください。  
  
## <a name="did-this-article-help-you-were-listening"></a>この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services) にコメントをお送りください  
  
## <a name="see-also"></a>参照  
 [マスター データ サービス データベース](../master-data-services/master-data-services-database.md)   
 [マスター データ マネージャー Web アプリケーション](../master-data-services/master-data-manager-web-application.md)   
 [[データベース構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [マスター データ サービス &#40;MDS&#41; の新機能](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  

