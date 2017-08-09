---
title: "レポート サーバー データベース (SSRS 構成マネージャー) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/24/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- report servers [Reporting Services], databases
- report server database
- databases [Reporting Services], creating
ms.assetid: 8a3a6ffe-4001-46be-8548-94532550f6a5
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 526abc46fe3b7fc3f923c29f4b4857b06f55a37c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="create-a-report-server-database"></a>レポート サーバー データベースの作成

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**ネイティブ モード**使って[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リレーショナル データベースを格納するレポート サーバーのメタデータとオブジェクト。 データベースの 1 つは主要な記憶域として使用され、もう 1 つは一時データの格納に使用されます。 この 2 つのデータベースは同時に作成され、データベース名によってバインドされます。 既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスでは、データベース名がそれぞれ **reportserver** と **reportservertempdb**になります。 2 つのデータベースを併せて、"レポート サーバー データベース" や "レポート サーバー カタログ" といいます。

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]**SharePoint モード**データ警告メタデータに使用する 3 番目のデータベースが含まれています。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションごとに 3 つのデータベースが作成されます。既定では、サービス アプリケーションを表す GUID がデータベース名に含まれています。 SharePoint モードの 3 つのデータベースの名前の例を次に示します。

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
  
-   手動: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用します。 リモートの [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を使用してデータベースをホストしている場合は、レポート サーバー データベースを手動で作成する必要があります。 詳細については、「[ネイティブ モード レポート サーバー データベースの作成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)」を参照してください。  
  
 **SharePoint モード:** [レポート サーバー インストール オプション] ページにある SharePoint モード用のオプションは 1 つ (**[インストールのみ]**) だけです。 このオプションを選択すると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のすべてのファイルと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスがインストールされます。 次に、次のいずれかの方法で [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを少なくとも 1 つ作成します。  
  
-   SharePoint サーバーの全体管理を使用して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを作成します。 詳細については、「 [手順 3: Reporting Services サービス アプリケーションの作成](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md#bkmk_create_serrviceapplication)」の「サービス アプリケーション」のセクションを参照してください。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] PowerShell コマンドレットを使用して、サービス アプリケーションとレポート サーバー データベースを作成します。 詳細については、「 [Reporting Services SharePoint モードの PowerShell コマンドレット](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)」トピックのサービス アプリケーションの作成のサンプルを参照してください。  
  
## <a name="database-server-version-requirements"></a>データベース サーバー バージョンの要件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レポート サーバー データベースをホストするために使用されます。 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] インスタンスは、ローカル インスタンスであってもリモート インスタンスであってもかまいません。 レポート サーバー データベースをホストするために使用できる、サポートされている [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のバージョンを次に示します。  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 リモート コンピューターにレポート サーバー データベースを作成する場合は、ネットワークにアクセスできるドメイン ユーザー アカウントまたはサービス アカウントを使用するように接続を構成する必要があります。 リモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用する場合は、レポート サーバーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用する資格情報を慎重に検討してください。 詳細については、「[レポート サーバー データベース接続の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。  
  
> [!IMPORTANT]  
>  レポート サーバーと、レポート サーバー データベースをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、同じドメインに属していなくてもかまいません。 インターネット配置では、ファイアウォール内にあるサーバーを使用するのが一般的です。 レポート サーバーをインターネット アクセス用に構成する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の資格情報を使用してファイアウォール内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続し、IPSEC を使用して接続をセキュリティで保護してください。  
  
## <a name="database-server-edition-requirements"></a>データベース サーバー エディションの要件  
 レポート サーバー データベースを作成するときは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションでデータベースをホストできるわけではないことに注意してください。 詳細については、「 [SQL Server 2016 の各エディションでサポートされる機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」の「レポート サーバー データベースのサーバー エディションの要件」を参照してください。  

## <a name="next-steps"></a>次の手順

[Reporting Services 構成マネージャー](http://msdn.microsoft.com/en-us/63519ef4-e68a-42fb-9cf7-31228ea4e434)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
