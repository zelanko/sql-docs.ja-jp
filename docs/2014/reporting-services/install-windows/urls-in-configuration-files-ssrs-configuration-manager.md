---
title: 構成ファイル内の URL (SSRS 構成マネージャー)
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- URL configuration [Reporting Services]
ms.assetid: 4f5e7fe0-b5b1-4665-93d4-80dce12d6b14
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fc1acb83b6147d7767c87a04515239a0672e0e5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160093"
---
# <a name="urls-in-configuration-files--ssrs-configuration-manager"></a>構成ファイル内の URL (SSRS 構成マネージャー)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、RSReportServer.config ファイルにアプリケーション設定を格納します。 このファイルには、URL と URL 予約の両方の構成設定が含まれています。 これらの構成設定は、変更の目的とルールが大きく異なります。 構成ファイルの変更による配置のチューニングに慣れている場合、各 URL 設定の使用方法の理解にこのトピックが役立ちます。  
  
## <a name="url-settings-in-rsreportserverconfig-file"></a>RSReportServer.config ファイルの URL 設定  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、アプリケーションやレポートにアクセスするための URL、および Web フロントエンド コンポーネントをバックエンド レポート サーバーに接続するための URL が格納されます。  
  
#### <a name="urls-for-application-access"></a>アプリケーションにアクセスするための URL  
 レポート サーバー Web サービスとレポート マネージャーへのアクセスに URL が使用されます。 URL を構成するには、Reporting Services 構成ツールを使用する必要があります。 このツールでは、HTTP.SYS に各アプリケーションの URL 予約が作成され、RSReportServer.config の `URLReservations` セクションに URL のエントリが追加されます。  
  
-   内の各要素の説明を表示、`URLReservations`セクションを参照してください[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
-   構文について`UrlString`要素を参照してください[URL 予約の構文&#40;SSRS 構成マネージャー&#41;](url-reservation-syntax-ssrs-configuration-manager.md)します。  
  
-   アプリケーションへのアクセスに Url を構成する方法については、次を参照してください。 [URL の構成&#40;SSRS 構成マネージャー&#41;](configure-a-url-ssrs-configuration-manager.md)します。  
  
#### <a name="urls-for-report-access"></a>レポートにアクセスするための URL  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、レポート リンクまたは添付ファイルの送信に使用できるレポート サーバーの電子メール配信拡張機能が用意されています。 レポート リンクは、レポートが配信されるときに構築されます。 レポート サーバーの電子メール配信拡張機能の使用、`UrlRoot`リンクを作成、構成ファイルで設定します。 `UrlRoot` 自動実行レポート処理によって生成される表示レポート内のリンクを解決するのにも使用されます。  
  
 `UrlRoot` 指定されて自動的に RSReportServer.config ファイルにアプリケーションへのアクセスの Url を構成する場合。 構成ファイルでこの値を変更する場合は、配信するレポートが格納されているレポート サーバー データベースに接続しているレポート サーバー Web サービスの有効な URL アドレスを指定する必要があります。 `UrlRoot` は、各レポート サーバー インスタンスにつき 1 つしか指定できません。RSReportServer.config ファイルに存在できる `UrlRoot` エントリは、レポート サーバー インスタンスごとに 1 つだけです。 複数の Url をレポート サーバー Web サービス用に予約した場合に使用できる値のいずれかを選択する必要があります`UrlRoot`します。  
  
 ほとんどの場合は変更する必要はありません`UrlRoot`します。 ただし、完全修飾 URL では、使用、レポート サーバーにアクセスする、完全修飾サイト名にホスト ヘッダーを使用する URL を構成していない場合は、設定を手動で RSReportServer.config を編集する必要があります、`UrlRoot`完全修飾するレポート、レポートを表示するために使用されるサーバーの URL (たとえば、https://www.adventure-works.com/mywebapp/reportserver)します。  
  
#### <a name="urls-connecting-report-manager-and-web-parts-to-the-report-server-web-service"></a>レポート マネージャーおよび Web パーツをレポート サーバー Web サービスに接続するための URL  
 Reporting Services のレポート マネージャーおよび SharePoint 2.0 Web パーツは、レポート サーバーに接続する Web フロントエンド コンポーネントです。 バックエンド レポート サーバーへの接続に使用される URL は次のとおりです。  
  
-   `ReportServerUrl` (レポート マネージャーで使用)  
  
-   `ReportServerExternalUrl` (Web パーツで使用)  
  
> [!NOTE]  
>  以前のバージョンの Reporting Services が含まれている、`ReportServerVirtualDirectory`要素。 この値は [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは使用しません。 既存のインストールをアップグレードした場合にこの設定を含む構成ファイルを使用しても、レポート サーバーはこの値を読み取りません。  
  
 次の表は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ファイルで指定可能なすべての URL の概要を示しています。  
  
|設定|使用方法|説明|  
|-------------|-----------|-----------------|  
|`ReportServerUrl`|任意。 この要素は、手動で追加しない限り RSReportServer.config ファイルには含まれません。 この要素は、次のいずれかのシナリオを構成する場合にのみ設定します。<br /><br /> 別のコンピューターまたは同じコンピューター上の別のインスタンスで実行されるレポート サーバー Web サービスへの Web フロントエンド アクセスを、レポート マネージャーが提供する場合<br /><br /> レポート サーバーの URL が複数存在し、レポート マネージャーで特定の URL を使用する場合<br /><br /> レポート マネージャーのすべての接続に特定のレポート サーバーの URL を使用する場合<br /><br /> たとえば、ネットワーク上のすべてのコンピューターにレポート マネージャーへのアクセスを許可しても、ローカル接続を使用してレポート サーバーに接続するようにレポート マネージャーに求める場合があります。 この場合、構成する場合があります`ReportServerUrl`に"http://localhost/reportserver"。<br /><br /> <br /><br /> これらのシナリオを実装する方法については、次を参照してください。[レポート マネージャーの構成&#40;ネイティブ モード&#41;](../report-server/configure-web-portal.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。|この値には、レポート サーバー Web サービスの URL を指定します。 この値は、起動時にレポート マネージャー アプリケーションによって読み取られます。 この値を設定すると、レポート マネージャーは、URL で指定されたレポート サーバーに接続します。<br /><br /> 既定では、レポート マネージャーは、レポート マネージャーと同じレポート サーバー インスタンス内で実行されるレポート サーバー Web サービスへの Web フロントエンド アクセスを提供します。 ただし、別のインスタンスまたは別のコンピューター上のインスタンス内で実行されるレポート サーバー Web サービスでレポート マネージャーを使用する場合は、外部のレポート サーバー Web サービスに接続するようにレポート マネージャーに指示するようにこの URL を設定することができます。<br /><br /> これには、次の接続は、レポート サーバーで Secure Sockets Layer (SSL) 証明書がインストールされている場合、`ReportServerUrl`値は、その証明書の登録されているサーバーの名前を指定する必要があります。 "基になる接続が閉じられました: SSL/TLS セキュリティ チャネルに対する信頼関係を確立できませんでした" というエラーが表示される場合は、`ReportServerUrl` を、SSL 証明書が発行されたサーバーの完全修飾ドメイン名に設定してください。 たとえば、証明書が **https://adventure-works.com.onlinesales** に登録されている場合、レポート サーバーの URL は **https://adventure-works.com.onlinesales/reportserver** になります。|  
|`ReportServerExternalUrl`|任意。 この要素は、手動で追加しない限り RSReportServer.config ファイルには含まれません。<br /><br /> SharePoint 2.0 Web パーツを使用しており、ユーザーがレポートを取得して新しいブラウザー ウィンドウで開くことができるようにする場合にのみ、この要素を設定します。<br /><br /> <`ReportServerUrl`> 要素の下に <`ReportServerExternalUrl`> を追加し、別のブラウザー ウィンドウでアクセスされたときにレポート サーバー インスタンスに解決されるレポート サーバーの完全修飾名に設定します。 <`ReportServerUrl`> は削除しないでください。<br /><br /> 構文例を次に示します。<br /><br /> `<ReportServerExternalUrl>http://myserver/reportserver</ReportServerExternalUrl>`|この値は SharePoint 2.0 Web パーツで使用されます。<br /><br /> 以前のリリースでは、この値を設定してインターネットに接続されたレポート サーバーにレポート ビルダーを配置することが推奨されていました。 この配置シナリオはテストされていません。 以前に、レポート ビルダーへのインターネット アクセスをサポートするためにこの設定を使用していた場合は、他の方法を検討してください。|  
  
## <a name="see-also"></a>参照  
 [レポート サーバー Url の構成&#40;SSRS 構成マネージャー&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [URL の構成&#40;SSRS 構成マネージャー&#41;](configure-a-url-ssrs-configuration-manager.md)  
  
  
