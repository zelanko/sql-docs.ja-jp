---
title: "Microsoft Azure Virtual Machine の SQL Server データベースの配置 | Microsoft Docs"
ms.date: 07/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.deploymentwizard.deploymentsettings.f1
- sql13.swb.deploymentwizard.sourcesettings.f1
- sql13.swb.deploymentwizard.summary.f1
- sql13.swb.agdashboard.agp9virtualnw.issues.f1
- sql13.swb.deploymentwizard.f1
- sql13.swb.deploymentwizard.progress.f1
- sql13.swb.usevmdialog.f1
- sql13.swb.newvmdialog.f1
- sql13.swb.sqlvmdialog.f1
- sql13.swb.deploymentwizard.results.f1
- sql13.swb.deploymentwizard.azuresignin.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Windows Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
caps.latest.revision: "30"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cbec6e7020dce77da6fc3a78c97e676b7bb81cad
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a>Microsoft Azure Virtual Machine の SQL Server データベースの配置
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **Microsoft Azure 仮想マシンにデータベースを配置**ウィザードを使用して、データベースを [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスから Microsoft Azure Virtual Machine (VM) の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に配置します。 このウィザードはデータベースの完全バックアップ操作を活用し、SQL Server のユーザー データベースから常にデータベース スキーマ全体とデータ全体をコピーします。 また、このウィザードは Azure のすべての仮想マシンを自動的に構成するため、仮想マシンの事前構成は必要ありません。  
  
 このウィザードを使用して差分バックアップを実行することはできません。 なぜなら、同じデータベース名を持つ既存のデータベースが上書きされないからです。 仮想マシン上にある既存のデータベースを置き換えるには、まず既存のデータベースを削除するか、データベース名を変更する必要があります。 インフライト配置操作を実行しているときに、複数のデータベース名の間で名前の競合が発生し、既存のデータベースが仮想マシン上に存在している場合は、ウィザードはインフライト データベースに対して付加的なデータベース名を提示し、操作を完了できるようにします。  
  
-   [はじめに](#before_you_begin)  
  
-   [制限事項と制約事項](#limitations)  
  
-   [FILESTREAM が有効なデータベースの配置に関する注意点](#filestream)  
  
-   [資産の地理的分散に関する注意点](#geography)  
  
-   [ウィザードの構成設定](#configuration_settings)  
  
-   [必要な権限](#permissions)  
  
-   [ウィザードを起動する](#launch_wizard)  
  
-   [ウィザード ページ](#wizard_pages)  
  
> [!NOTE]  
>  このウィザードの詳細な手順については、「 [Azure VM の SQL Server への SQL Server データベースの移行](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-migrate-onpremises-database/)」をご覧ください。  
  
##  <a name="before_you_begin"></a> はじめに  
 このウィザードを完了するには、次の情報を用意し、これらの構成設定を整える必要があります。  
  
-   Windows Azure サブスクリプションに関連付けられている Microsoft アカウントの詳細。  
  
-   Windows Azure の公開プロファイル。  
  
    > [!CAUTION]  
    >  SQL Server では現在、公開プロファイルのバージョン 2.0 がサポートされています。 公開プロファイルのサポート対象バージョンをダウンロードするには、「 [公開プロファイルのバージョン 2.0 のダウンロード](http://go.microsoft.com/fwlink/?LinkId=396421)」をご覧ください。  
  
-   Microsoft Azure サブスクリプションにアップロードされた管理証明書。  Powershell のコマンドレット [New-SelfSignedCertificate](https://technet.microsoft.com/library/hh848633(v=wps.630))で管理証明書を作成します。  その後、Microsoft Azure サブスクリプションに管理証明書をアップロードします。  管理証明書のアップロードの詳細については、「 [Azure Management API Management 証明書のアップロード](https://azure.microsoft.com/en-us/documentation/articles/azure-api-management-certs/)」をご覧ください。  次に示すのは、「 [Azure Cloud Services の証明書の概要](https://azure.microsoft.com/en-us/documentation/articles/cloud-services-certs-create/)」から抜粋した管理証明書作成の構文のサンプルです。 

    ```powershell  
    $cert = New-SelfSignedCertificate -DnsName yourdomain.cloudapp.net -CertStoreLocation "cert:\LocalMachine\My"
    $password = ConvertTo-SecureString -String "your-password" -Force -AsPlainText
    Export-PfxCertificate -Cert $cert -FilePath ".\my-cert-file.pfx" -Password $password
    ```    

    > [!NOTE]  
    > MakeCert ツールを使用して管理証明書を作成することもできますが、MakeCert は推奨されなくなっています。  詳細については、「 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968)」をご覧ください。
   
  -   ウィザードを実行するコンピューターで個人証明書ストアに保存された管理証明書。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをホストするコンピューターで使用できる一時格納場所が必要です。 この一時格納場所は、このウィザードを実行するコンピューターでも使用できる必要があります。  
  
-   既存の仮想マシンにデータベースを配置する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを TCP/IP ポートでリッスンするように構成する必要があります。  
  
-   仮想マシンの作成に使用する Windows Azure VM またはギャラリーの図では、 [SQL Server 用のクラウド アダプター](http://msdn.microsoft.com/library/82ed0d0f-952d-4d49-aa36-3855a3ca9877) が構成および実行されている必要があります。  
  
-   Windows Azure ゲートウェイ上にプライベート ポート 11435 で [SQL Server 用クラウド アダプター](http://msdn.microsoft.com/library/82ed0d0f-952d-4d49-aa36-3855a3ca9877) のオープン エンドポイントを構成する必要があります。  
  
 また、データベースを既存の Windows Azure 仮想マシンに配置する計画がある場合は、次の情報も用意する必要があります。  
  
-   仮想マシンをホストするクラウド サービスの DNS 名。  
  
-   仮想マシンの管理者資格情報。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のソース インスタンスから配置を計画しているデータベースのバックアップ操作の特権資格情報。  
  
 Microsoft Azure Virtual Machines で SQL Server を実行する詳細については、「 [Azure ポータルでの SQL Server 仮想マシンのプロビジョニング](https://msdn.microsoft.com/library/dn133141.aspx) 」および「 [Azure VM の SQL Server への SQL Server データベースの移行](http://msdn.microsoft.com/library/dn133142.aspx)」をご覧ください。  
  
 Windows Server オペレーティング システムを実行しているコンピューターでは、このウィザードを実行するために、次の構成設定を使用する必要があります。  
  
-   セキュリティ強化の構成の無効化。[サーバー マネージャー] > [ローカル サーバー] を使用し、[Internet Explorer セキュリティ強化の構成]\(ESC) を **[オフ]** に設定します。  
  
-   JavaScript の有効化。Internet Explorer > [インターネット オプション] > [セキュリティ] > [レベルのカスタマイズ] > [スクリプト] > [アクティブ スクリプト] を選択し、**[有効にする]** に設定します。  
  
###  <a name="limitations"></a> 制限事項と制約事項  
この配置機能は、Service Management (クラシック) デプロイメント モデルを使って作成された Azure Storage アカウントでのみ使用できます。 Azure デプロイメント モデルに関する詳細については、「 [Azure Resource Manager とクラシック デプロイ](https://azure.microsoft.com/en-us/documentation/articles/resource-manager-deployment-model/)」を参照してください。

 この操作に対応するデータベース サイズの上限は 1 TB です。  
  
 この配置機能は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]用の SQL Server Management Studio で使用できます。  
  
 この配置機能は、ユーザー データベースを使用している場合にのみ有効です。システム データベースの配置はサポートされていません。  
  
 配置機能はアフィニティ グループに関連付けられているホストされたサービスをサポートしていません。 たとえば、アフィニティ グループに関連付けられたストレージ アカウントはこのウィザードの **配置の設定** ページで使用するためには選択できません。  
  
 このウィザードを使用して Windows Azure 仮想マシンに配置できる SQL Server データベースのバージョンは次のとおりです。  
  
-   SQL Server 2008:  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  

- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Windows Azure 仮想マシン データベースで実行されている SQL Server データベースのバージョンは以下のように配置できます。  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  

- [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 インフライト配置操作を実行しているときに、複数のデータベース名の間で名前の競合が発生し、既存のデータベースが仮想マシン上に存在している場合は、ウィザードはインフライト データベースに対して付加的なデータベース名を提示し、操作を完了できるようにします。  
  
###  <a name="filestream"></a> FILESTREAM が有効なデータベースの Azure 仮想マシンへの配置に関する注意点  
 FILESTREAM オブジェクトに格納されている BLOBS があるデータベースを配置する場合は、次のガイドラインと制限事項に注意してください:  
  
-   配置機能は FILESTREAM が有効なデータベースを新しい仮想マシンに配置することはできません。 ウィザードを実行する前に FILESTREAM が仮想マシンで有効になっていない場合は、データベースの復元操作が失敗し、ウィザードの操作が正常に完了できません。 FILESTREAM を使用するデータベースを正常に配置するには、ウィザードを起動する前にホスト仮想マシンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで FILESTREAM を有効にします。 詳細については、「 [FILESTREAM (SQL Server)](http://msdn.microsoft.com/library/gg471497.aspx)」を参照してください。  
  
-   データベースがインメモリ OLTP を使用すると、データベースを変更せずに Azure 仮想マシンにデータベースを配置できます。 詳細については、「 [インメモリ OLTP (インメモリ最適化)](http://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx)」を参照してください。  
  
###  <a name="geography"></a> 資産の地理的分散に関する注意点  
 次の資産が同じ地理的領域に存在する必要があることに注意してください:  
  
-   クラウド サービス  
  
-   仮想マシンの場所  
  
-   データ ディスク ストレージ サービス  
  
 上記の資産が同じ場所に配置されていない場合は、正常に完了できません。  
  
###  <a name="configuration_settings"></a> ウィザードの構成設定  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース配置の Azure 仮想マシンへの設定を変更するには、次の構成の詳細を使用します。  
  
-   **構成ファイルの既定のパス** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml  
  
-   **構成ファイルの構造**  
  
    -   \<DeploymentSettings>  
  
        -   <OtherSettings  
  
            -   TraceLevel="Debug" \<!-- Logging level -->  
  
            -   BackupPath="\\\\[サーバー名]\\[ボリューム]\\" \<!-- バックアップの最後に使用されたパス。 ウィザードで既定値として使用されます。 -->  
  
            -   CleanupDisabled = False /> \<! -- 中間のファイルおよび Windows Azure オブジェクト (仮想マシン、CS、SA) は削除されません。 -->  
  
        -   \<PublishProfile \<! -- 最後に使用されたパブリッシュのプロファイル情報。 -->  
  
            -   Certificate="12A34B567890123ABCD4EF567A8" \<!-- ウィザードで使用する証明書。 -->  
  
            -   Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- ウィザードで使用するサブスクリプション。 -->  
  
            -   Name="My Subscription" \<!-- サブスクリプションの名前。 -->  
  
            -   Publisher="" />  
  
    -   \</DeploymentSettings>  
  
 **構成ファイルの値**  
  
###  <a name="permissions"></a> アクセス許可  
 配置されるデータベースは標準状態でなければならず、このデータベースはウィザードを実行するユーザー アカウントからアクセスできる必要があり、ユーザー アカウントにはバックアップ操作を実行する権限が必要です。  
  
##  <a name="launch_wizard"></a> Microsoft Azure 仮想マシンへのデータベースの配置ウィザードの使用  
 **ウィザードを起動するには、次の手順を実行します。**  
  
1.  SQL Server Management Studio を使用して、配置するデータベースがある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。  
  
2.  **オブジェクト エクスプローラー**で、インスタンス名を展開してから、 **データベース** ノードを展開します。  
  
3.  配置するデータベースを右クリックして **[タスク]**を選択し、 **[Microsoft Azure 仮想マシンへのデータベースの配置]**をクリックします。  
  
##  <a name="wizard_pages"></a> ウィザード ページ  
 以下のセクションでは、この操作の配置設定と構成の詳細に関する追加情報を示しています。  
  
-   [概要](#Introduction)  
  
-   [[ソース設定]](#Source_settings)  
  
-   [[Windows Azure サインイン]](#Azure_sign-in)  
  
-   [配置の設定](#Deployment_settings)  
  
-   [概要](#Summary)  
  
-   [[結果]](#Results)  
  
##  <a name="Introduction"></a> 概要 
 このページでは、 **Microsoft Azure 仮想マシンへのデータベースの配置** ウィザードについて説明します。  
  
-   **[次回からこのページを表示しない]**  
  今後 [説明] ページを表示しないようにするには、このチェック ボックスをオンにします。  
  
-   **Next**  
**[ソースの設定]** ページに進みます。  
  
-   **キャンセル**  
  操作を取り消し、ウィザードを閉じます。  
  
-   **ヘルプ**  
ウィザードに関する MSDN ヘルプ トピックを起動します。  
  
##  <a name="Source_settings"></a> [ソース設定]  
 このページを使用して、Microsoft Azure 仮想マシンに配置するデータベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。 ローカル コンピューターからのファイルを Microsoft Azure に転送する前に、それらのファイルの一時的な保存場所も指定します。 共有のネットワークの場所を指定できます。  
 
- **SQL Server**    
**[接続]** をクリックして、配置するデータベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの接続詳細を指定します。  
  
-   **[データベースの選択]**  
このドロップダウン リストを使用して、展開するデータベースを指定します。  
  
-   **[その他の設定]**  
このフィールドで、Microsoft Azure 仮想マシン サービスがアクセスできる共有フォルダーを指定します。  
  
##  <a name="Azure_sign-in"></a> Microsoft Azure へのサインイン  
 Microsoft アカウントまたは組織アカウントを使用して Microsoft Azure にサインインします。 Microsoft アカウントまたは組織アカウントは、patc@contoso.com などの電子メール アドレスの形式になっています。Azure の資格情報の詳細については、「 [Microsoft Account for Organizations FAQ](http://technet.microsoft.com/jj592903) 」(組織向け Microsoft アカウントに関する FAQ) および「 [Troubleshooting Problems](https://technet.microsoft.com/dn197220)」(問題のトラブルシューティング) をご覧ください。  
  
##  <a name="Deployment_settings"></a> 配置の設定
 このページを使用して、配置先サーバーと、新しいデータベースの詳細を指定します。  
  
 **[Microsoft Azure Virtual Machine]**  
  
-   **[クラウド サービス名]**  
仮想マシンをホストするサービスの名前を指定します。 新しいクラウド サービスを作成するには、新しいクラウド サービスの名前を指定します。  
  
-   **[仮想マシン名]** : SQL Server データベースをホストする仮想マシンの名前を指定します。 新しい Microsoft Azure VM を作成するには、新しい仮想マシンの名前を指定します。  
  
-   **[ストレージ アカウント]**  
ドロップダウン リストからストレージ アカウントを選択します。 新しいストレージ アカウントを作成するには、新しいアカウントの名前を指定します。 アフィニティ グループに関連付けられたストレージ アカウントは、ドロップダウン リストに使用できないことに注意してください。  

-   **[設定]**  
[設定] ボタンを使用して、SQL Server データベースをホストするための新しい仮想マシンを作成します。 既存の仮想マシンを使用している場合は、指定した情報を使用して資格情報の認証が行われます。  
  
**[対象になるデータベース]**
  
-   **[SQL インスタンス名]**  
サーバーの接続詳細です。  
  
-   **データベース名**  
新しいデータベースの名前を指定または確認します。 対象の SQL Server インスタンスにデータベース名が既にある場合は、変更したデータベース名を指定することをお勧めします。  
  
##  <a name="Summary"></a> 概要
 このページを使用すると、操作について指定した設定を確認できます。 指定した設定で配置操作を実行するには、 **[完了]**をクリックします。 配置操作を取り消してウィザードを終了するには、 **[キャンセル]**をクリックします。  **[完了]** をクリックすると、 **[配置状況]** ページが表示されます。  `"%LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM"`にあるログ ファイルから進行状況を見ることもできます。
  
 データベースの詳細を Windows Azure 仮想マシンの SQL Server データベースに配置するために手動の手順が必要になる場合があります。 これらの手順については概要を詳しく説明します。  
  
##  <a name="Results"></a> [結果] 
 このページでは、配置操作の成功と失敗が報告され、各アクションの結果が示されます。 エラーが発生したアクションには、 **[結果]** 列に情報が表示されます。 そのアクションのエラーのレポートを表示するには、リンクをクリックします。  
  
 **[完了]** をクリックして、ウィザードを終了します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 用のクラウド アダプター](http://msdn.microsoft.com/library/82ed0d0f-952d-4d49-aa36-3855a3ca9877)   
 [データベースのライフサイクル管理](../../relational-databases/database-lifecycle-management.md)   
 [データ層アプリケーションのエクスポート](../../relational-databases/data-tier-applications/export-a-data-tier-application.md)   
 [BACPAC ファイルのインポートによる新しいユーザー データベースの作成](../../relational-databases/data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)   
 [Azure SQL データベースのバックアップと復元](https://msdn.microsoft.com/library/azure/jj650016.aspx)   
 [Microsoft Azure Virtual Machines 上での SQL Server の配置](http://msdn.microsoft.com/library/dn133141.aspx)   
 [Microsoft Azure Virtual Machines に SQL Server を移行するための準備](http://msdn.microsoft.com/library/dn133142.aspx)  
  
  
