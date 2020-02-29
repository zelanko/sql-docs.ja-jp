---
title: ネイティブモードのレポートサーバーをインストール Reporting Services |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- report servers [Reporting Services], default configurations
- installation options [Reporting Services]
ms.assetid: 8f25e6dc-b753-400e-9e9a-50f4f35bf6c4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ba2744f759a59ae4360bcd0d7c09dc45c7a4bdbf
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173481"
---
# <a name="install-reporting-services-native-mode-report-server"></a>Reporting Services ネイティブ モードのレポート サーバーのインストール
  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード レポート サーバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド ラインからインストールできます。 セットアップ ウィザードで、1) ファイルをインストールして既定の設定でサーバーを構成する、または 1) ファイルのインストールのみを行いインストール ウィザードではサーバーを構成しない、のいずれかを選択できます。 このトピックでは *ネイティブ モードの既定の構成* について確認します。このインストールでは、セットアップでレポート サーバー インスタンスのインストールと構成の両方が行われます。 セットアップが完了すると、レポート サーバーが実行され、使用できる状態になります。 ネイティブ モードのレポート サーバーは、スタンドアロンのアプリケーション サーバーとして実行されます。 ネイティブ モードは既定のサーバー モードです。

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード|

##  <a name="bkmk_top"></a>このトピックの内容

-   [既定の構成とは](#bkmk_whatisdefaultconfiguration)

-   [ネイティブモードの既定の構成をインストールする場合](#bkmk_whentoinstalldefaultconfig)

-   [必要条件](#bkmk_requirements)

-   [既定の URL 予約](#bkmk_defaultURLreservations)

-   [SQL Server インストールウィザードを使用してネイティブモードをインストールする](#bkmk_installwithwizard)

-   [コマンド ラインによるネイティブ モードのインストール](#bkmk_commandline)

##  <a name="bkmk_whatisdefaultconfiguration"></a>既定の構成とは
 ネイティブ モードの既定の構成オプションを選択すると、セットアップで次の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能がインストールされます。

-   レポート サーバー サービス (レポート サーバー Web サービス、バックグラウンド処理アプリケーション、およびレポート マネージャーを含む)

-   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャー

-   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コマンド ライン ユーティリティ (rsconfig.exe、rskeymgmt.exe、rs.exe)

 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]やなどの共有機能には[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]適用されません。これらの機能をインストールする場合は、個別の項目として指定する必要があります。

 ネイティブ モードのレポート サーバーのインストールの場合は、セットアップで以下が構成されます。

-   レポート サーバー サービスのサービス アカウント

-   レポート サーバー Web サービスの URL

-   レポート マネージャーの URL

-   レポート サーバー データベース

-   レポート サーバー データベースへのサービス アカウント アクセス

-   レポート サーバー データベース用の DSN 接続

 セットアップでは、自動実行用アカウント、レポート サーバーの電子メール、暗号化キーのバックアップ、およびスケールアウト配置が構成されません。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、これらのプロパティを構成できます。 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。

##  <a name="bkmk_whentoinstalldefaultconfig"></a>ネイティブモードの既定の構成をインストールする場合
 既定の構成では、セットアップの完了後すぐにレポート サーバーを使用できるように、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] が操作可能な状態でインストールされます。 このモードは、他のモードであれば [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールで実行すべき必須の構成タスクを省いて手順を省略する場合に指定します。

 既定の構成をインストールしても、セットアップの完了後にレポート サーバーが動作するかどうかは保証されません。 サービスの起動時に既定の URL が登録されない可能性があります。 必ずインストールをテストして、サービスが予期したとおりに起動して実行されるかどうかを確認してください。

##  <a name="bkmk_requirements"></a>必要性
 既定の構成オプションでは、レポート サーバーを稼働させるために必要な中核となる設定の構成に既定値が使用されます。 これには次の要件があります。

-   Microsoft SQL Server を実行するには、最低限のハードウェア要件とソフトウェア要件をハードウェアが満たしている必要があります。 詳細については、「 [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」をご参照ください。

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]は、同じインスタンスに一緒にインストールする必要があります。 
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスは、セットアップで作成されて構成されるレポート サーバー データベースをホストします。

-   セットアップの実行に使用するユーザー アカウントは、ローカルの Administrators グループのメンバーである必要があります。また、レポート サーバー データベースをホストする [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンス上のデータベースにアクセスする権限と、そのデータベースを作成する権限が必要です。

-   セットアップでは、既定値を使用して、レポート サーバーとレポート マネージャーにアクセスするための URL を予約できる必要があります。 ここでの既定値とは、ポート 80、強いワイルドカード、および **ReportServer_\<***instance_name***>** と **Reports_\<***instance_name***>** の形式の仮想ディレクトリ名です。

-   セットアップでは、既定値を使用してレポート サーバー データベースを作成できる必要があります。 ここでの既定値とは、 **ReportServer** と **ReportServerTempDB**です。 以前のインストールのデータベースが既に存在する場合は、ネイティブ モードの既定の構成のセットアップでレポート サーバーを構成できないため、セットアップはブロックされます。 セットアップのブロックを解除するには、データベースの名前を変更するか、データベースを移動または削除する必要があります。

 コンピューターで、既定インストールの要件のうち満たされていないものがある場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をファイルのみのモードでインストールし、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用してセットアップの完了後に構成する必要があります。

 既定のインストールを続行できるようにするためだけにコンピューターを再構成しないでください。 再構成の作業には数時間かかる可能性があり、時間を節約できるというこのインストール オプションの利点が実質的に失われます。 このような場合は、ファイルのみのモードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールし、特定の値を使用するようにレポート サーバーを構成することをお勧めします。

##  <a name="bkmk_defaultURLreservations"></a>既定の URL 予約
 URL 予約は、プレフィックス、ホスト名、ポート、および仮想ディレクトリで構成されます。

|要素|説明|
|----------|-----------------|
|Prefix|既定のプレフィックスは HTTP です。 以前に SSL (Secure Sockets Layer) 証明書をインストールした場合は、HTTPS プレフィックスを使用する URL 予約がセットアップで作成されます。|
|ホスト名|既定のホスト名は、強いワイルドカード (+) です。 これにより、レポートサーバーは、コンピューターに解決される任意のホスト名 (http://\<computername>/reportserver、 http://localhost/reportserver、http://\<IPAddress>/reportserverなど) に対して、指定されたポートでの HTTP 要求を受け入れることを指定します。|
|Port|既定のポートは 80 です。 80 以外のポートを使用する場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web アプリケーションをブラウザー ウィンドウで開くときに、そのポートを URL に明示的に追加する必要があるので注意してください。|
|仮想ディレクトリ|既定では、仮想ディレクトリは、レポートサーバー Web サービス\<の ReportServer_*instance_name*> の形式で作成され\<、instance_name に対して Reports_*>* レポートマネージャーます。 レポート サーバー Web サービスの既定の仮想ディレクトリは、 **reportserver**です。 レポート マネージャーの既定の仮想ディレクトリは、 **reports**です。|

 完全な URL 文字列の例を次に示します。

-   http://+:80/reportserver は、レポート サーバーへのアクセスを提供します。

-   http://+:80/reportsは、レポートマネージャーへのアクセスを提供します。

##  <a name="bkmk_installwithwizard"></a>SQL Server インストールウィザードを使用してネイティブモードをインストールする
 次に示すのは、SQL Server インストール ウィザードで選択する  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 固有の手順とオプションです。 ここでは、インストール ウィザードに表示されるそれぞれのページではなく、ネイティブ モードのインストールに含まれる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 関連のページについてのみ説明します。

1.  [**セットアップロール**] ページで、[ **SQL Server 機能のインストール**] を選択します。

     ![[セットアップ ロール] の [SQL Server 機能のインストール]](../../../2014/sql-server/install/media/rs-setuprole.gif "[セットアップ ロール] の [SQL Server 機能のインストール]")

2.  
  **[機能の選択]** ページで、次のオプションを選択します。

    -   **データベースエンジンサービス**(データベースエンジンのインスタンスが既にインストールされている場合を除く)。

    -   **Reporting Services-ネイティブ**です。

    -   **管理ツール-基本**。 管理ツールは必須ではありませんが、その他の管理ツールがインストールされていない場合に推奨されています。 既定の構成オプションを使用すると、レポートサーバーが機能しますが、後で構成オプションを変更することもできます。 ' 個人用レポート ' などの一部のオプションは、を使用して管理されます。[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]

     ![機能の選択での SSRS ネイティブ モード選択](../../../2014/sql-server/install/media/rs-setupfeatureselection-native-withcircles.gif "機能の選択での SSRS ネイティブ モード選択")

3.  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサブスクリプション機能を使用する場合は、 **[サーバーの構成]** ページで、SQL Server エージェントのスタートアップの種類が **[自動]** に構成されていることを確認する必要があります。

4.  
  **[Reporting Services の構成]** ページで、 **[インストールと構成]** を選択します。

     ![SSRS ネイティブ モードの構成](../../../2014/sql-server/install/media/rs-setupconfiguration-native-with-circles.gif "SSRS ネイティブ モードの構成")

5.  SQL Server インストール ウィザードの完了後、次の基本的な手順を使用して、既定のネイティブ モードのインストールを確認します。

    -   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを開いて、レポート サーバーに接続できることを確認します。

    -   管理者特権を使用してブラウザーを開き、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート マネージャーに接続します。たとえば、「 `http://loclahost/Reports`」と入力します。

    -   管理者特権を使用してブラウザーを開き、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー ページにアクセスします。 たとえば、`http://loclahost/ReportServer` のように入力します。

 詳細については、次の 2 つのトピックのネイティブ モードに関する説明を参照してください。

 [Verify a Reporting Services Installation](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)

 [Reporting Services インストール時の問題解決](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)

##  <a name="bkmk_commandline"></a>コマンドラインを使用してネイティブモードをインストールする
 次の例には、既定の構成に必要な [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスが示されています。

```
setup /q /ACTION=install /FEATURES=SQL,RS,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" 
/RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK 
SERVICE" /RSSVCSTARTUPTYPE="Manual" /RSINSTALLMODE="DefaultNativeMode"
```

 詳細と例については、「 [Reporting Services SharePoint モードとネイティブモードのコマンドプロンプトインストール](../../reporting-services/install-windows/install-reporting-services-at-the-command-prompt.md)」と「[コマンドプロンプトから SQL Server 2014 をインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)する」を参照してください。

## <a name="see-also"></a>参照
 [Reporting Services のインストールのトラブルシューティング](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md) [Reporting Services のインストールの確認](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)[レポートサーバーサービスアカウントの構成 ssrs Configuration Manager&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)レポート[サーバーの url](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)の構成 &#40;ssrs Configuration Manager&#41;[ファイルのみのインストール](../../reporting-services/install-windows/files-only-installation-reporting-services.md)&#40;Configuration Manager&#41;レポートサーバー[の](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)[構成 &#40;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md) ssrs Reporting Services&#41;&#40;[SSL の構成 &#40;ネイティブモードのレポートサーバーでの接続](../security/configure-ssl-connections-on-a-native-mode-report-server.md)[レポートサーバーの URL &#40;SSRS Configuration Manager 構成&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md) [Windows サービスアカウントとアクセス許可の構成](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) [SQL Server 2014 のクイックスタートインストール](../../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)


