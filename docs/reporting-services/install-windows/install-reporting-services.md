---
title: SQL Server Reporting Services のインストール (2017 以降) | Microsoft Docs
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
author: markingmyname
ms.author: maghan
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 620debfd008dc120e171241d0038229e9dce8a04
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50028203"
---
# <a name="install-sql-server-reporting-services-2017-and-later"></a>SQL Server Reporting Services のインストール (2017 以降)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

SQL Server Reporting Services をインストールするには、レポート アイテムの格納、レポートの表示、およびサブスクリプションや他のレポート サービスの処理を行うためのサーバー コンポーネントが必要です。 

SQL Server 2017 Reporting Services をダウンロードするには、「[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=55252)」に移動します。

> [!NOTE]
> Power BI Report Server が見つからない場合は、 「[Power BI Report Server のインストール](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/)」を参照してください。

## <a name="before-you-begin"></a>アンインストールの準備

Reporting Services をインストールする前に、「[Hardware and software requirements for installing SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」 (SQL Server のインストールに必要なハードウェアおよびソフトウェア) を確認してください。

## <a name="install-your-report-server"></a>レポート サーバーのインストール

レポート サーバーのインストールは簡単です。 わずかな手順でファイルをインストールできます。

> [!NOTE]
> インストール時に利用可能な SQL Server データベース エンジン サーバーは必要ありません。 インストール後、Reporting Services を構成するときに必要になります。

1. SQLServerReportingServices.exe の場所を検索し、インストーラーを起動します。

2. **[Reporting Services のインストール]** を選択します。

    ![Reporting Services のインストール](media/install-reporting-services/report-server-install.png)

3. インストールするエディションを選択して、**[次へ]** を選択します。

    ![エディションの選択](media/install-reporting-services/report-server-install-edition.png)

    無料版の場合、ドロップダウンから [Evaluation] または [Developer] を選択します。

    ![Evaluation エディションまたは Developer エディション](media/install-reporting-services/report-server-install-edition-select.png)

    それ以外の場合は、プロダクト キーを入力します。 [SQL Server 2017 Reporting Services のプロダクト キーを見つけます](find-reporting-services-product-key-ssrs.md)。

4. ライセンス条項および条件を読んで同意し、**[次へ]** をクリックします。

5. レポート サーバー データベースを格納するには、データベース エンジンを利用可能にする必要があります。 **[次へ]** を選択して、レポート サーバーのみをインストールします。

    ![インストールにデータベースは必要ありません](media/install-reporting-services/report-server-install-db-engine.png)

6. レポート サーバーをインストールする場所を指定します。 **[インストール]** を選択して次に進みます。

    ![インストール パスの指定](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > 既定のパスは、C:\Program Files\Microsoft SQL Server Reporting Services です。

7. 正常にセットアップした後、**[レポート サーバーの構成]** を選択して、Reporting Services Configuration Manager を起動します。

    ![レポート サーバーの構成](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>レポート サーバーの構成

セットアップで **[レポート サーバーの構成]** を選択したら、**レポート サーバー Configuration Manager** が表示されます。 詳細については、[Report Server 構成マネージャー](reporting-services-configuration-manager-native-mode.md)に関するページを参照してください。

Reporting Services の初期構成を完了するには、[レポート サーバー データベースを作成する](ssrs-report-server-create-a-report-server-database.md)必要があります。 この手順を完了するには、SQL Server データベース サーバーが必要です。

### <a name="creating-a-database-on-a-different-server"></a>別のサーバーでデータベースを作成する

別のマシン上のデータベース サーバーにレポート サーバー データベースを作成している場合は、レポート サーバーのサービス アカウントを、データベース サーバーで認識されている資格情報に変更する必要があります。

既定では、レポート サーバーは仮想サービス アカウントを使用します。 別のサーバー上でデータベースを作成しようとすると、接続権限を適用する手順で次のエラーが表示される可能性があります。

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

エラーを回避するには、サービス アカウントをネットワーク サービスまたはドメイン アカウントのいずれかに変更できます。 サービス アカウントをネットワーク サービスに変更すると、レポート サーバー用のマシン アカウントのコンテキストでの権限が適用されます。

詳細については、[レポート サーバー サービス アカウントの構成](configure-the-report-server-service-account-ssrs-configuration-manager.md)に関するページを参照してください。

## <a name="windows-service"></a>Windows サービス

Windows サービスは、インストールの一部として作成されます。 これは、**SQL Server Reporting Services** として表示されます。 サービス名は **SQLServerReportingServices** です。

## <a name="default-url-reservations"></a>既定の URL 予約

URL 予約は、プレフィックス、ホスト名、ポート、および仮想ディレクトリで構成されます。

|要素|[説明]|
|----------|-----------------|
|Prefix|既定のプレフィックスは HTTP です。 以前に SSL (Secure Sockets Layer) 証明書をインストールした場合は、HTTPS プレフィックスを使用する URL 予約がセットアップで作成されます。|
|ホスト名|既定のホスト名は、強いワイルドカード (+) です。 これにより、コンピューターに対して解決されるあらゆるホスト名 (`http://<computername>/reportserver`、`http://localhost/reportserver`、`http://<IPAddress>/reportserver.`) の指定のポートで、レポート サーバーが HTTP 要求を受け付けるように指定されます。|
|Port|既定のポートは 80 です。 ポート 80 以外のポートを使用する場合は、Web ポータルをブラウザー ウィンドウで開くときに、そのポートを URL に明示的に追加する必要があります。|
|仮想ディレクトリ|既定では、仮想ディレクトリは、レポート サーバー Web サービスの場合は ReportServer の形式で作成され、Web ポータルの場合は Reports の形式で作成されます。 レポート サーバー Web サービスの既定の仮想ディレクトリは、 **reportserver**です。 Web ポータルの既定の仮想ディレクトリは、**reports** です。|

完全な URL 文字列の例を次に示します。

- `http://+:80/reportserver` は、レポート サーバーへのアクセスを提供します。

- `http://+:80/reports` は、Web ポータルへのアクセスを提供します。

## <a name="firewall"></a>ファイアウォール

リモート マシンからレポート サーバーにアクセスしている場合、ファイアウォールが存在するのであれば、ファイアウォールの規則を構成していることを確認してください。

Web サービス URL および Web ポータル URL 用に構成されている TCP ポートを開く必要があります。 既定では、これらは TCP ポート 80 で構成されます。

## <a name="additional-configuration"></a>その他の構成

- Power BI ダッシュボードにレポート アイテムをピン留めできるように、Power BI サービスとの統合を構成するには、[Power BI サービスとの統合](power-bi-report-server-integration-configuration-manager.md)に関するページを参照してください。

- サブスクリプション処理の電子メールを構成するには、「[電子メールの設定 - Reporting Services のネイティブ モード (構成マネージャー)](e-mail-settings-reporting-services-native-mode-configuration-manager.md)」および[レポート サーバーの電子メール配信](../subscriptions/e-mail-delivery-in-reporting-services.md)に関するページを参照してください。

- レポートを表示および管理するためにレポート コンピューター上でアクセスできるように、Web ポータルを構成するには、「[Configure a firewall for report server access](../report-server/configure-a-firewall-for-report-server-access.md)」 (レポート サーバー アクセスに対するファイアウォールの構成) および「[リモート管理用のレポート サーバーの構成](../report-server/configure-a-report-server-for-remote-administration.md)」を参照してください。

## <a name="related-information"></a>関連情報

SQL Server 2016 Reporting Services ネイティブ モードをインストールする方法については、「[Reporting Services ネイティブ モードのレポート サーバーのインストール](install-reporting-services-native-mode-report-server.md)」を参照してください。 SharePoint 統合モードで SQL Server 2016 Reporting Services をインストールする方法については、「[SharePoint モードでの最初のレポート サーバーのインストール](install-the-first-report-server-in-sharepoint-mode.md)」を参照してください。

## <a name="next-steps"></a>次の手順

インストールされたレポート サーバーを使用して、レポートの作成を開始し、自分のレポート サーバーに配置します。 レポート ビルダーの使用を開始する方法については、「[レポート ビルダーをインストールする](../../reporting-services/install-windows/install-report-builder.md)」を参照してください。

SQL Server Data Tools を使用してレポートを作成するには、[SQL Server Data Tools をダウンロードします](https://go.microsoft.com/fwlink/?LinkID=616714)。

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
