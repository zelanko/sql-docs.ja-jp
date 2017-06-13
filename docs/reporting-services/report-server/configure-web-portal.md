---
title: "Web ポータルの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- the web portal [Reporting Services], configuring
ms.assetid: e918986c-af15-48f6-8178-256aed829c6a
caps.latest.revision: 28
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c0c6cc27711140e96bbf4420e8de596af53ddfcd
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="configure-the-web-portal"></a>Web ポータルを構成します。

web ポータルは、Web フロント エンド アプリケーションがレポートの表示、レポート サーバー コンテンツの管理、およびネイティブ モード レポート サーバーへのアクセスを許可するために使用します。 web ポータルは、同じレポート サーバー インスタンス内のレポート サーバー Web サービスと共にインストールされ、必要に応じて構成を選択した場合、**ネイティブ モードの既定の構成でインストール**セットアップでオプションです。 インストール後のタスクとして、web ポータルを構成することもできます。 このトピックは、次に関する情報を提供、web ポータルの構成シナリオ。

## <a name="prerequisites"></a>前提条件

Web ポータルを使用するのには、次の前提条件を満たす必要があります。

- 最小限の構成が行われているレポート サーバーが必要です。 レポート サーバーの最小限の構成の詳細については、次を参照してください。[レポート サーバーの構成](../../reporting-services/report-server/configure-a-report-server-reporting-services-native-mode.md)です。

- レポート サーバーはネイティブ モードで動作する必要があります。 SharePoint 統合モード用に構成されているレポート サーバーで web ポータルを使用できません。 SQL Server 2012 では、レポート サーバーを別のモードに切り替えることはできません。 環境で使用しているレポート サーバーの種類を変更するには、目的のモードのレポート サーバーをインストールした後、新しいレポート サーバーにレポート アイテムをコピーまたは移動する必要があります。 このプロセスは、一般的には "移行" と呼ばれます。 移行に必要な手順は、移行先のモードと移行元のバージョンによって異なります。 詳細については、「 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)」を参照してください。

- Internet Explorer 11 を持たなければなりませんまたは以降のスクリプトを有効にします。 詳細については、「 [Reporting Services と Power View のブラウザー サポート](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)」を参照してください。

## <a name="configure-the-web-portal-to-use-the-default-url"></a>既定の URL を使用する web ポータルを構成します。

Web ポータルは、ユーザーが Web ブラウザーでアクセスする Web アプリケーションです。 少なくとも、ブラウザー ウィンドウでアプリケーションを開く際に使用する URL を定義する必要があります。 URL はホスト名、ポート、および仮想ディレクトリで構成されます。 この URL の既定値には、レポート サーバー Web サービスの URL 用に定義したホスト名とポートの値に加えて、 **レポート** の仮想ディレクトリ名が含まれます。 名前付きインスタンスを使用している場合、仮想ディレクトリは **reports_instance**になります ( **instance** の箇所には、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスの名前が入ります)。

既定では、web ポータルの URL は、一意の仮想ディレクトリ名と同じインスタンスで実行されているレポート サーバー Web サービスに対して定義されているポートとホスト名で構成されます。 ほとんどの場合、ホスト名はレポート サーバー コンピューターのネットワーク名ですが、そのコンピューターを解決する IP アドレスまたはホスト ヘッダーである場合もあります。 既定の URL を使用するための web ポータルを構成するのには、使用、 **Web ポータルの URL**  ページで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]構成ツール。

> [!TIP]
> 場合は、リモート コンピューターで web ポータルにアクセスすると、ブラウザーで接続エラー メッセージを受信して、一般的な原因は、ファイアウォールの設定です。 詳細については、「 [レポート サーバー アクセスに対するファイアウォールの構成](../../reporting-services/report-server/configure-a-firewall-for-report-server-access.md)」をご覧ください。

#### <a name="to-configure-the-default-the-web-portal-url-and-virtual-directory"></a>既定の web ポータルを構成する URL と仮想ディレクトリ

1. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを起動して、レポート サーバー インスタンスに接続します。

2. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]構成ツールで、 **Web ポータルの URL** URL の構成のページを開きます。

3. Web ポータルの一意の仮想ディレクトリ名を入力します。

4. **[適用]**をクリックします。

5. 使用している場合[!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)]または Windows Server 2008 では、追加の手順があります必要な web ポータルを使用する前にします。 詳細については、「[ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」をご覧ください。

## <a name="configure-the-web-portal-to-use-a-specific-report-server-url"></a>特定のレポート サーバー URL を使用する web ポータルを構成します。

既定では、web ポータルは、同じレポート サーバー サービスで実行されているレポート サーバー Web サービスに接続します。 Web ポータルでは、レポート サーバー Web サービスの URL を使用して接続します。 レポート サーバー Web サービスに対して複数の Url を定義すると、web ポータルは、定義した最後の 1 つを使用します。 ただし、一部の展開では、常に、静的な URL を Web サービスに接続する web ポータルをする可能性があります。 このような接続が必要になる状況として、特定のポートや IP アドレスに対してパケット フィルターを構成しており、レポート サーバーへ接続するときは必ず定義したフィルター ルールを適用する場合などが例として挙げられます。

内の Url を構成するとき、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]構成ツール、web ポータル自動的に検出し、同じサーバー インスタンスで実行されているレポート サーバーのすべての新規および更新された Url を使用します。 すべてのレポート サーバー要求に 1 つの静的 URL を使用することが必要な配置では、RSReportServer.config ファイルでその URL を指定できます。

#### <a name="to-configure-a-static-report-server-url"></a>レポート サーバーの静的 URL を構成するには

1. テキスト エディターで **RSReportServer.config** ファイルを開きます。 既定では、\Program Files\Microsoft SQL Server\MSRS12 になります。\< *instancename*> \reporting です。  

2. **ReportServerURL**を探します。

3. レポート サーバー インスタンスの URL に置き換えます。

4. 変更を保存してファイルを閉じます。

構成ファイルの詳細については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更」](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)および「[RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)」を参照してください。

## <a name="customize-styles-or-application-title"></a>スタイルのカスタマイズまたはアプリケーションのタイトルのカスタマイズ

Web ポータルを使用する色を変更するカスタム ブランド パッケージを作成することができます。 詳細については、次を参照してください[web ポータルをブランド化。](../branding-the-web-portal.md)

#### <a name="to-modify-application-title"></a>アプリケーションのタイトルを変更するには

1. レポート サーバーに対する **システム管理者** 権限が割り当てられたアカウントを使用してログオンします。

2. Internet Explorer を開きます。

3. Web ポータルを入力する URL。 Http:// は既定では、\<**、サーバー名**> 名前付きインスタンス、既定の URL と Reporting Services をインストールした場合は、レポートになります http:///\<**、サーバー名**>/reports\<**_instancename**>。

4. **[サイトの設定]**を選択します。

5. **[全般]** タブの **[名前]**で、 **SQL Server Reporting Services** を別の名前に置き換えます。

6. [ **適用**] を選択します。

## <a name="next-steps"></a>次の手順

[Web ポータル](../../reporting-services/web-portal-ssrs-native-mode.md)  
[Reporting Services のブラウザー サポート](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)
[URL の構成](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[Reporting Services のインストール状態の検証](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
[Reporting Services の機能をオンまたはオフにします。](../../reporting-services/report-server/turn-reporting-services-features-on-or-off.md)   
[Reporting Services ネイティブ モードのレポート サーバーの管理](../../reporting-services/report-server/manage-a-reporting-services-native-mode-report-server.md)   
[RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[ローカル管理用のネイティブ モード レポート サーバーを構成します。](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)

 他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
