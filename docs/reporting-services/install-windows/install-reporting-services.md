---
title: "SQL Server Reporting Services のインストール |Microsoft ドキュメント"
ms.date: 10/10/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 52c2f8fae79884b025e067b7d628cd3154ba93f4
ms.openlocfilehash: 5ce83ff18d6908441a3eaaf05599068ec5876308
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="install-sql-server-reporting-services"></a>SQL Server Reporting Services のインストール

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

SQL Server Reporting Services のインストールには、レポート アイテムの格納、レポートの表示、およびサブスクリプションおよびその他のレポート サービスの処理中のサーバー コンポーネントが含まれます。  Power BI のレポート サーバーをインストールする方法を説明します。

SQL Server 2017 Reporting Services をダウンロードするには、 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=55252)です。

> [!NOTE]
> Power BI のレポート サーバーを検索してください。 参照してください[Power BI のレポート サーバーのインストール](https://powerbi.microsoft.com/documentation/reportserver-install-report-server/)です。

## <a name="before-you-begin"></a>アンインストールの準備

Reporting Services をインストールする前に、確認、 [SQL Server をインストールするためのハードウェアおよびソフトウェア要件](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)です。

## <a name="install-your-report-server"></a>レポート サーバーをインストールします。

レポート サーバーをインストールするは簡単です。 ファイルのインストールをいくつかの手順のみがあります。

> [!NOTE]
> SQL Server データベース エンジンのサーバーのインストール時に使用する必要はありません。 1 つのインストール後に Reporting Services を構成する必要があります。

1. SQLServerReportingServices.exe の場所を検索し、インストーラーを起動します。

2. 選択**Reporting Services のインストール**です。

    ![Reporting Services のインストール](media/install-reporting-services/report-server-install.png)

3. クリックしてインストールするエディションを選択**次**です。

    ![エディションを選択します。](media/install-reporting-services/report-server-install-edition.png)

    下へドロップから評価版または Developer のいずれかのエディションを選択できます。

    ![評価版または developer エディション](media/install-reporting-services/report-server-install-edition-select.png)

    それ以外の場合、プロダクト キーを入力することができます。

4. 読み取りと、ライセンス条項と条件に同意し、**次**です。

5. データベース エンジンがレポート サーバー データベースの格納に使用できる必要があります。 選択**次**のみ、レポート サーバーをインストールします。

    ![データベースのインストールは必要ありません。](media/install-reporting-services/report-server-install-db-engine.png)

6. レポート サーバーのインストール場所を指定します。 選択**インストール**を続行します。

    ![インストール パスを指定します。](media/install-reporting-services/report-server-install-file-path.png)

    > [!NOTE]
    > 既定のパスは、C:\Program files \microsoft SQL Server Reporting Services です。

7. 正常にセットアップした後、選択**レポート サーバーの構成**を Reporting Services 構成マネージャーを起動します。

    ![レポート サーバーを構成します。](media/install-reporting-services/report-server-install-configure.png)

## <a name="configuration-your-report-server"></a>構成、レポート サーバー

選択した後**レポート サーバーの構成**、セットアップでするが表示されます**レポート サーバーの Configuration Manager**です。 詳細については、次を参照してください。[レポート サーバーの Configuration Manager](reporting-services-configuration-manager-native-mode.md)です。

する必要があります[レポート サーバー データベースの作成](ssrs-report-server-create-a-report-server-database.md)Reporting Services の初期構成を完了します。 この手順を完了するには、SQL Server データベース サーバーが必要です。

### <a name="creating-a-database-on-a-different-server"></a>別のサーバーにデータベースを作成します。

別のコンピューター上のデータベース サーバーでレポート サーバー データベースを作成する場合は、データベース サーバーで認識されている資格情報をレポート サーバーのサービス アカウントを変更する必要があります。

既定では、レポート サーバーは、仮想サービス アカウントを使用します。 別のサーバーにデータベースを作成しようとする場合は、[接続の権利] 手順で適用する次のエラーがあります。

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

エラーを回避するには、ネットワーク サービス アカウントまたはドメイン アカウントをサービス アカウントを変更できます。 ネットワーク サービスにサービス アカウントを変更するには、レポート サーバーのマシン アカウントのコンテキストでの権限が適用されます。

詳細については、次を参照してください。 [、レポート サーバー サービス アカウントを構成する](configure-the-report-server-service-account-ssrs-configuration-manager.md)です。

## <a name="windows-service"></a>Windows サービス

Windows サービスは、インストールの一部として作成されます。 として表示される**SQL Server Reporting Services**です。 サービス名は**SQLServerReportingServices**です。

## <a name="default-url-reservations"></a>既定の URL 予約

URL 予約は、プレフィックス、ホスト名、ポート、および仮想ディレクトリで構成されます。

|要素|説明|
|----------|-----------------|
|プレフィックス|既定のプレフィックスは HTTP です。 以前に Secure Sockets Layer (SSL) 証明書をインストールした場合、セットアップは、HTTPS プレフィックスを使用して URL 予約を作成しようとします。|
|ホスト名|既定のホスト名は、強いワイルドカード (+) です。 レポート サーバーが、コンピューターに対して解決されるあらゆるホスト名の指定のポートに対するすべての HTTP 要求を受け入れることを指定を含む`http://<computername>/reportserver`、 `http://localhost/reportserver`、または`http://<IPAddress>/reportserver.`|
|ポート|既定のポートは 80 です。 ポート 80 以外の任意のポートを使用する場合は、明示的に追加したり、URL をブラウザーのウィンドウで web ポータルを開くときにする必要があります。|
|仮想ディレクトリ|既定では、仮想ディレクトリは、web ポータルのレポート サーバー Web サービスとレポートに関する ReportServer の形式で作成されます。 レポート サーバー Web サービスの既定の仮想ディレクトリは、 **reportserver**です。 Web ポータルで、既定の仮想ディレクトリは**レポート**です。|

完全な URL 文字列の例を次に示します。

- `http://+:80/reportserver`、レポート サーバーへのアクセスを提供します。

- `http://+:80/reports`、web ポータルへのアクセスを提供します。

## <a name="firewall"></a>ファイアウォール

リモート コンピューターからレポート サーバーにアクセスする、場合は、存在ファイアウォールがある場合は、すべてのファイアウォール ルールを構成したことを確認します。

Web サービス URL と Web ポータルの URL 用に構成した TCP ポートを開く必要があります。 既定では、これらは TCP ポート 80 で構成されます。

## <a name="additional-configuration"></a>その他の構成

- Power BI ダッシュ ボードにレポート アイテムをピン留めできるよう、Power BI サービスの統合を構成するを参照してください。 [Power BI サービスとの統合](power-bi-report-server-integration-configuration-manager.md)です。

- サブスクリプションの処理用の電子メールを構成するのを参照してください。[電子メール設定](e-mail-settings-reporting-services-native-mode-configuration-manager.md)と[電子メールの配信、レポート サーバーに](../subscriptions/e-mail-delivery-in-reporting-services.md)です。

- 表示およびレポートを管理するリモート コンピューター上でアクセスできるように、web ポータルを構成するを参照してください[レポート サーバー アクセスに対してファイアウォールを構成する](../report-server/configure-a-firewall-for-report-server-access.md)と[リモート管理用にレポート サーバーを構成する](../report-server/configure-a-report-server-for-remote-administration.md)。.

## <a name="related-information"></a>関連情報

SQL Server 2016 Reporting Services ネイティブ モードをインストールする方法については、次を参照してください。 [Install Reporting Services ネイティブ モード レポート サーバー](install-reporting-services-native-mode-report-server.md)です。 SharePoint 統合モードで SQL Server 2016 Reporting Services をインストールする方法については、次を参照してください。[最初のレポート サーバーを SharePoint モードでインストール](install-the-first-report-server-in-sharepoint-mode.md)です。

## <a name="next-steps"></a>次の手順

レポート サーバーのインストールされている場合とは、レポートを作成し、レポート サーバーに展開を開始します。 レポート ビルダーを開始する方法については、次を参照してください。 [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md)です。

SQL Server Data Tools を使用してレポートを作成する[SQL Server Data Tools のダウンロード](http://go.microsoft.com/fwlink/?LinkID=616714)です。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
