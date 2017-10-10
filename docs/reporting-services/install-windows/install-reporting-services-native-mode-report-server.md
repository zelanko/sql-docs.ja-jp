---
title: "Reporting Services ネイティブ モード レポート サーバーのインストール |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
caps.latest.revision: 68
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: a8c8f93212e62b148671305354599b88e6f3d318
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="install-reporting-services-native-mode-report-server"></a>Reporting Services ネイティブ モードのレポート サーバーのインストール

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

ネイティブ モードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールする方法について説明します。 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] へのアクセスが提供されます。そこでレポートやその他のアイテムを管理できます。

> [!NOTE]
> Power BI のレポート サーバーを検索してください。 参照してください[Power BI のレポート サーバーのインストール](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/)です。

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード レポート サーバーは、既定の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバー モードで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド ラインからインストールできます。 セットアップ ウィザードで、ファイルをインストールして既定の設定でサーバーを構成するか、またはファイルのインストールのみを行うかのいずれかを選択できます。 このトピックでは *ネイティブ モードの既定の構成* について確認します。このインストールでは、セットアップでレポート サーバー インスタンスのインストールと構成の両方が行われます。 セットアップが完了したら、レポート サーバーが実行され、基本的なレポートの表示およびレポートの管理を行うために使用する準備ができます。  [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] 統合やサブスクリプションの処理を伴う電子メール配信などの追加機能は、追加の構成が必要です。  
  
##  <a name="bkmk_whatisdefaultconfiguration"></a> 既定の構成とは  
 ネイティブ モードの既定の構成オプションを選択すると、セットアップで次の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能がインストールされます。  
  
-   レポート サーバー サービス (レポートおよび権限の表示と管理のためのレポート サーバー Web サービス、バックグラウンド処理アプリケーション、および [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] を含む。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コマンド ライン ユーティリティ (rsconfig.exe、rskeymgmt.exe、rs.exe)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を個別にダウンロードできるようになりました。  
  
 ネイティブ モードのレポート サーバーのインストールの場合は、セットアップで以下が構成されます。  
  
-   レポート サーバー サービスのサービス アカウント  
  
-   レポート サーバー Web サービスの URL  
  
-   [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] URL。  
  
-   レポート サーバー データベース  
  
-   レポート サーバー データベースへのサービス アカウント アクセス  
  
-   レポート サーバー データベース用の接続情報 (データ ソース名 (DSN) とも呼ばれます)。  
  
 セットアップでは、自動実行用アカウント、レポート サーバーの電子メール、暗号化キーのバックアップ、およびスケールアウト配置が構成されません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、これらのプロパティを構成できます。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)」を参照してください。
  
##  <a name="bkmk_whentoinstalldefaultconfig"></a> ネイティブ モードの既定の構成をインストールする場合  
 既定の構成では、セットアップの完了後すぐにレポート サーバーを使用できるように、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] が操作可能な状態でインストールされます。 このモードは、他のモードであれば [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで実行すべき必須の構成タスクを省いて手順を省略する場合に指定します。  
  
 既定の構成をインストールしても、セットアップの完了後にレポート サーバーが動作するかどうかは保証されません。 サービスの起動時に既定の URL が登録されない可能性があります。 必ずインストールをテストして、サービスが予期したとおりに起動して実行されるかどうかを確認してください。  「 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)」を参照してください。
  
##  <a name="bkmk_requirements"></a> 必要条件  
 既定の構成オプションでは、レポート サーバーを稼働させるために必要な中核となる設定の構成に既定値が使用されます。 これには次の要件があります。  
  
-   「 [Hardware and Software Requirements for Installing SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md) 」を確認します。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] を、同じインスタンスに一緒にインストールする必要があります。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスは、セットアップで作成されて構成されるレポート サーバー データベースをホストします。  
  
-   セットアップの実行に使用するユーザー アカウントは、ローカルの Administrators グループのメンバーである必要があります。また、レポート サーバー データベースをホストする [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンス上のデータベースにアクセスする権限と、そのデータベースを作成する権限が必要です。  
  
-   セットアップでは、既定値を使用して、レポート サーバーと [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]にアクセスするための URL を予約できる必要があります。 これらの値には、ポート 80、強いワイルドカード、および形式の仮想ディレクトリ名**reportserver _\<***instance_name*  **>** と**reports _\<***instance_name***>**です。  
  
-   セットアップでは、既定値を使用してレポート サーバー データベースを作成できる必要があります。 ここでの既定値とは、 **ReportServer** と **ReportServerTempDB**です。 以前のインストールのデータベースが既に存在する場合は、ネイティブ モードの既定の構成のセットアップでレポート サーバーを構成できないため、セットアップはブロックされます。 セットアップのブロックを解除するには、データベースの名前を変更するか、データベースを移動または削除する必要があります。  
  
 コンピューターで、既定インストールの要件のうち満たされていないものがある場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をファイルのみのモードでインストールし、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してセットアップの完了後に構成する必要があります。
 
 > [!IMPORTANT]
 > 読み取り専用ドメイン コント ローラー (RODC) が存在する環境では、Reporting Services をインストールすることができます、Reporting Services では、正常に機能する読み取り専用ドメイン コント ローラーへのアクセスが必要です。 Reporting Services では、RODC へのアクセスのみがある、サービスを管理しようとするときにエラーが発生する可能性があります。
  
##  <a name="bkmk_defaultURLreservations"></a> 既定の URL 予約  
 URL 予約は、プレフィックス、ホスト名、ポート、および仮想ディレクトリで構成されます。  
  
|要素|説明|  
|----------|-----------------|  
|プレフィックス|既定のプレフィックスは HTTP です。 以前に SSL (Secure Sockets Layer) 証明書をインストールした場合は、HTTPS プレフィックスを使用する URL 予約がセットアップで作成されます。|  
|ホスト名|既定のホスト名は、強いワイルドカード (+) です。 レポート サーバーが、コンピューターに対して解決されるあらゆるホスト名の指定のポートに対するすべての HTTP 要求を受け付けることを指定を含む`http://<computername>/reportserver`、 `http://localhost/reportserver`、または`http://<IPAddress>/reportserver`です。|  
|ポート|既定のポートは 80 です。 80 以外のポートを使用する場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web アプリケーションをブラウザー ウィンドウで開くときに、そのポートを URL に明示的に追加する必要があるので注意してください。|  
|仮想ディレクトリ|既定では、仮想ディレクトリを作成して、reportserver _ の形式で\<*instance_name*> レポート サーバー Web サービスおよび reports _\<*instance_name*> の[!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]です。 レポート サーバー Web サービスの既定の仮想ディレクトリは、 **reportserver**です。 [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]の既定の仮想ディレクトリは、 **reports**です。|  
  
 完全な URL 文字列の例を次に示します。  
  
-   `http://+:80/reportserver`、レポート サーバーへのアクセスを提供します。  
  
-   `http://+:80/reports`、へのアクセスを提供、[!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]です。
  
##  <a name="bkmk_installwithwizard"></a> SQL Server インストール ウィザードによるネイティブ モードのインストール  
 次に示すのは、SQL Server インストール ウィザードで選択する  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 固有の手順とオプションです。 ここでは、インストール ウィザードに表示されるそれぞれのページではなく、ネイティブ モードのインストールに含まれる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 関連のページについてのみ説明します。  
  
1.  SQL Server セットアップ ウィザード (setup.exe) を実行して、次の暫定ページの手順を実行します。  
  
    -   プロダクト キー  
  
    -   ライセンス条項  
  
    -   グローバル ルール  
  
    -   Microsoft Update  
  
    -   製品の更新プログラム  
  
    -   セットアップ ファイルのインストール  
  
    -   インストール ルール  
  
2.  **[セットアップ ロール]** ページで、 **[SQL Server 機能のインストール]**を選択します。  
  
     ![セットアップ ロールの SQL Server 機能のインストール](../../reporting-services/install-windows/media/rs-setuprole.png "セットアップ ロールの SQL Server 機能のインストール")  
  
3.  **[機能の選択]** ページで、次のオプションを選択します。  
  
    -   (1) **[データベース エンジン サービス]**(データベース エンジンのインスタンスがまだインストールされていない場合)。  
  
    -   (2) **[Reporting Services - ネイティブ]**。  
  
     ![SSRS ネイティブ モードの機能の選択 を選択](../../reporting-services/install-windows/media/rs-setupfeatureselection-native-withcircles.png "機能の SSRS ネイティブ モードを選択します")  
  
4.  渡された **[機能ルール]** を確認します。  
  
5.  [インスタンスの構成] ページで **[名前付きインスタンス]**の構成を選択した場合は、レポート マネージャーとレポート サーバー自体を参照するときに、URL にインスタンス名を使用する必要があります。 インスタンス名が "THESQLINSTANCE" の場合、URL は次のようになります。  
  
    -   `http://[ServerName]/ReportServer_THESQLINSTANCE`  
  
    -   `http://[ServerName]/Reports_THESQLINSTANCE`  
  
6.  **サーバーの構成**: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサブスクリプション機能を使用する場合は、 **[サーバーの構成]** ページで、SQL Server エージェントのスタートアップの種類を **[自動]** に設定します。   既定値は手動です。  
  
7.  **[データベース エンジンの構成]** ページで SQL Server 管理者を追加します。  
  
8.  **[Reporting Services の構成]** ページで、 **[インストールと構成]**を選択します。  
  
     ![SSRS ネイティブ モード構成](../../reporting-services/install-windows/media/rs-setupconfiguration-native-with-circles.png "SSRS ネイティブ モードの構成")  
  
    > [!NOTE]  
    >  **インストールと構成** は、インストールするデータベース機能が選択されるまでは使用できません。  
  
9. 機能構成ルール: 渡されたルールを検証します。 ルールがすべて成功した場合は、セットアップ ウィザードは自動的に **[インストールの準備完了]** に進みます。  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に固有のルールでは、レポート サーバー カタログと一時カタログデータベースがまだ存在していないことを確認します。  
  
10. **[インストールの準備完了]** ページで、インストールされたコンポーネント、サービス アカウント、および管理者などのサーバーの初期の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成の概要を入手するために、後で参照できるように構成ファイルへのパスをメモします。  
  
11. SQL Server インストール ウィザードの完了後、次の基本的な手順を使用して、既定のネイティブ モードのインストールを確認します。  
  
    -   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを開いて、レポート サーバーに接続できることを確認します。  
  
    -   **管理者特権** を使用してブラウザーを開き、 [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]に接続します。たとえば、「 `http://localhost/Reports`」と入力します。  
  
    -   管理者特権を使用してブラウザーを開き、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー ページにアクセスします。 例:  `http://localhost/ReportServer`  
  
 詳細については、次の 2 つのトピックのネイティブ モードに関する説明を参照してください。  
  
 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)  
  
 [Reporting Services インストール時の問題解決](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
  
##  <a name="bkmk_additional_configuration"></a> その他の構成  
  
-   構成する[!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)]統合のため、レポートをピン留めできるアイテムを[!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)]ダッシュ ボードを参照してください[Power BI のレポート サーバーの統合](../../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)です。  
  
-   サブスクリプションの処理用の電子メールを構成するのを参照してください。[電子メールの設定 - Reporting Services のネイティブ モード](../../reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager.md)と[Reporting Services での電子メール配信](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)です。  
  
-   レポートを表示して管理レポート コンピューター上でアクセスできるように、web ポータルを構成するを参照してください。[レポート サーバー アクセスに対してファイアウォールを構成する](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)と[リモート管理のレポート サーバーを構成する](../../reporting-services/report-server/configure-a-report-server-for-remote-administration.md)です。  
  
## <a name="see-also"></a>参照

[Reporting Services インストール時の問題解決](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
[Reporting Services のインストール状態の検証](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
[レポート サーバー サービス アカウントを構成します。](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
[レポート サーバー Url を構成します。](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
[レポート サーバー データベース接続を構成します。](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
[ファイルのみのインストール &#40;Reporting Services&#41;](../../reporting-services/install-windows/files-only-installation-reporting-services.md)   
[レポート サーバーを初期化します。](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
[ネイティブ モードのレポート サーバーでの SSL 接続の構成](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)   
[Windows サービス アカウントと権限の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

