---
title: レポート サーバー データベースの作成 (SSRS 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 09/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: install-windows
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6b45d3d8ec6b7268ff1f1b9069fc9b4fa6780c87
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-report-server-database"></a>レポート サーバー データベースの作成

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **ネイティブ モード** では、レポート サーバーのメタデータとオブジェクトを格納するため、2 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベースを使用します。 データベースの 1 つは主要な記憶域として使用され、もう 1 つは一時データの格納に使用されます。 この 2 つのデータベースは同時に作成され、データベース名によってバインドされます。 既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスでは、データベース名がそれぞれ **reportserver** と **reportservertempdb**になります。 2 つのデータベースを併せて、"レポート サーバー データベース" や "レポート サーバー カタログ" といいます。

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **SharePoint モード** には、データ警告メタデータに使用する 3 つ目のデータベースが含まれています。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションごとに 3 つのデータベースが作成されます。既定では、サービス アプリケーションを表す GUID がデータベース名に含まれています。 SharePoint モードの 3 つのデータベースの名前の例を次に示します。

-   ReportingService_90a9f37075544f22953c4a62e4a9f370  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370TempDB  
  
-   ReportingService_90a9f37075544f22953c4a62e4a9f370_Alerting  
  
> [!IMPORTANT]  
>  レポート サーバー データベースに対してクエリを実行するアプリケーションは作成しないでください。 レポート サーバー データベースは、パブリック スキーマではありません。 テーブル構造は、リリースごとに変更される可能性があります。 レポート サーバー データベースにアクセスする必要のあるアプリケーションを記述する場合、常に [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] API を使用してレポート サーバー データベースにアクセスしてください。  
>   
>  例外は実行ログのビューです。 詳細については、「 [レポート サーバー実行ログと ExecutionLog3 ビュー](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md)」を参照してください。  
  
## <a name="ways-to-create-the-report-server-database"></a>レポート サーバー データベースを作成する方法  
 **ネイティブ モード:** ネイティブ モードのレポート サーバー データベースは、次の方法で作成できます:  
  
-   自動: 既定の構成をインストールするオプションを選択した場合は、SQL Server セットアップ ウィザードを使用します。 SQL Server インストール ウィザードでは、これは [レポート サーバー インストール オプション] ページの **[インストールと構成]** です。 **[インストールのみ]** オプションを選択した場合は、Reporting Services 構成マネージャーを使用してデータベースを作成する必要があります。  
  
-   手動: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用します。 リモートの [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] を使用してデータベースをホストしている場合は、レポート サーバー データベースを手動で作成する必要があります。 詳細については、「[ネイティブ モードのレポート サーバー データベースの作成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)」を参照してください。  
  
 **SharePoint モード:** [レポート サーバー インストール オプション] ページにある SharePoint モード用のオプションは 1 つ ( **[インストールのみ]**) だけです。 このオプションを選択すると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のすべてのファイルと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスがインストールされます。 次に、次のいずれかの方法で [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを少なくとも 1 つ作成します。  
  
-   SharePoint サーバーの全体管理を使用して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを作成します。 詳細については、「 [手順 3: Reporting Services サービス アプリケーションの作成](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md#bkmk_create_serrviceapplication)」の「サービス アプリケーション」のセクションを参照してください。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] PowerShell コマンドレットを使用して、サービス アプリケーションとレポート サーバー データベースを作成します。 詳細については、「 [Reporting Services SharePoint モードの PowerShell コマンドレット](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)」トピックのサービス アプリケーションの作成のサンプルを参照してください。  
  
## <a name="database-server-version-requirements"></a>データベース サーバー バージョンの要件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レポート サーバー データベースをホストするために使用されます。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] インスタンスは、ローカル インスタンスであってもリモート インスタンスであってもかまいません。 レポート サーバー データベースをホストするために使用できる、サポートされている [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のバージョンを次に示します。  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 リモート コンピューターにレポート サーバー データベースを作成する場合は、ネットワークにアクセスできるドメイン ユーザー アカウントまたはサービス アカウントを使用するように接続を構成する必要があります。 リモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用する場合は、レポート サーバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用する資格情報を慎重に検討してください。 詳細については、「 [レポート サーバー データベース接続の構成 &#40;SSRS構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」で確認します。  
  
> [!IMPORTANT]  
>  レポート サーバーと、レポート サーバー データベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、同じドメインに属していなくてもかまいません。 インターネット配置では、ファイアウォール内にあるサーバーを使用するのが一般的です。 レポート サーバーをインターネット アクセス用に構成する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の資格情報を使用してファイアウォール内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、IPSEC を使用して接続をセキュリティで保護してください。  
  
## <a name="database-server-edition-requirements"></a>データベース サーバー エディションの要件  
 レポート サーバー データベースを作成するときは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションでデータベースをホストできるわけではないことに注意してください。 詳細については、「 [SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」の「レポート サーバー データベースのサーバー エディションの要件」を参照してください。  

## <a name="next-steps"></a>次の手順

[Reporting Services 構成マネージャー](http://msdn.microsoft.com/en-us/63519ef4-e68a-42fb-9cf7-31228ea4e434)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
