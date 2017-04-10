---
title: "Reporting Services (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "レポート [Reporting Services]"
  - "SSRS"
  - "レポート [Reporting Services], レポートの概要"
  - "Reporting Services"
  - "SQL Server Reporting Services (SQL Server Reporting Services)"
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
caps.latest.revision: 70
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Reporting Services (SSRS)
  SQL Server Reporting Services (SSRS) のすぐに使えるさまざまなツールやサービスで、オンプレミスのモバイル レポートやページ分割されたレポートを作成、配置、管理します。 
  
 ![SQL Server Reporting Services all together](../reporting-services/media/ss-reporting-services-all-together.png "SQL Server Reporting Services all together")  
## <a name="what-is-sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS) とは

SQL Server Reporting Services は、レポートを作成、パブリッシュ、管理し、Web ブラウザー、モバイル デバイス、受信トレイ内のメールなどで表示できるようにさまざまな方法で適切なユーザーに提供するための、ユーザーのオンプレミスに配置されるソリューションです。

SQL Server 2016 の Reporting Services では、更新された製品スイートが提供されます。

* 更新されたツールと新しい作成機能で現代風のレポートを作成できる、新しくなった **"従来の" ページ分割されたレポート**。 
* さまざまなデバイスと持ち方に適応できる対応性の高いレイアウトの**新しいモバイル レポート**。 
* 最新のブラウザーで表示できる**新しい Web ポータル**。 新しいポータルでは、モバイル レポートやページ分割されたレポートおよび新しい KPI を整理して、表示することができます。 また、ポータルには Excel ブックや Power BI Desktop レポートを格納することもできます。 

以降ではそれぞれについて詳しく説明します。
  
### <a name="whats-new-in-reporting-services"></a>Reporting Services の新機能

これらのリソースで SQL Server 2016 Reporting Services の新機能に関する最新情報をご確認いただけます。 
* [Reporting Services の新機能](../reporting-services/sql-server-reporting-services-ssrs-の新機能.md)
* [SQL Server Reporting Services チームのブログ](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Guy in a Cube YouTube チャンネル](https://www.youtube.com/channel/UCFp1vaKzpfvoGai0vE5VJ0w)
  
## <a name="paginated-reports"></a>ページ分割されたレポート

![ssrs-paginated-reports](../reporting-services/media/ssrs-paginated-reports.png)

Reporting Services は "従来の" ページ分割されたドキュメント スタイルのレポートと関連付けられており、データ、テーブルの行、レポートのページをより多く提供できます。 PDF ファイルや Word ファイルのような印刷用に最適化された固定レイアウトで完全なピクセルのドキュメントの生成に最適です。 

その中核となる BI ワークロードは最新のものになっています。 [レポート ビルダー](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)または [SQL Server Data Tools (SSDT) のレポート デザイナー](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)を使って、更新された新しい機能で現代風のレポートを作成できます。 

* 既定のスタイルとカラー パレットはすべて更新されており、既定の設定で最新のミニマリズム スタイルのレポートを作成できます。
* 更新された [パラメーター] ウィンドウでは、必要に応じてパラメーターを調整できます。
* PowerPoint などの新しい形式にエクスポートできます。 PowerPoint での Reporting Services の視覚化は、単なるスクリーンショットではなく、ライブ表示であり編集可能です。
* Power BI と Reporting Services のハイブリッド エクスペリエンスを作成できます。オンプレミスの Reporting Services を Power BI で作成し直すのではなく、レポートのビジュアルを Power BI ダッシュボードにピン留めすることができます。 その後は、Power BI ダッシュボードだけですべての情報を監視できます。
 
## <a name="mobile-reports"></a>モバイル レポート

![ssrs-mobile-reports](../reporting-services/media/ssrs-mobile-reports.png)

モバイル コンピューティングによって使用する必要のあるデバイスが変化し、現在では異なるレポート ニーズが生まれています。 タブレットや携帯電話を導入すると、固定レイアウトのレポート エクスペリエンスではうまく機能しません。 PC のワイド画面用に設計されたレポートは、小さいだけでなく縦方向または横方向のスマートフォンの画面では最適なエクスペリエンスになりません。

このように大きく異なる画面フォーム ファクターに必要なものは固定レイアウトではなく、さまざまなデバイスと持ち方に適応する対応性の高いレイアウトです。 そのため、新しいレポートの種類であるモバイル レポートを追加しました。これは、約 1 年前に買収して製品に統合した Datazen のテクノロジが基になっています。 [SQL Server Migration Assistant for Datazen](https://www.microsoft.com/download/details.aspx?id=53128) を使って、既存の Datazen レポートを Reporting Services に移行できます。 

モバイル レポートは新しい [Mobile Report Publisher](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md) アプリで作成します。 その後、Windows 10、iOS、Android、HTML5 用のネイティブな[モバイル デバイス用 Power BI アプリ](https://powerbi.microsoft.com/documentation/powerbi-power-bi-apps-for-mobile-devices/)で、クラウドの Power BI データやオンプレミスの SQL Server 2016 Reporting Services データにアクセスできます。 視覚エフェクトを作成すると、Mobile Report Publisher によりサンプル データが自動的に生成されるので、実際のデータでの視覚エフェクトの見え方や、各視覚エフェクトに適したデータの種類を確認できます。

## <a name="web-portal"></a>Web ポータル

![ssrs-web-portal](../reporting-services/media/ssrs-web-portal.png)

ネイティブ モードの Reporting Services のエンド ユーザーの入り口は、最新のブラウザーで表示できる最新の Web ポータルです。 すべてのモバイル レポートとページ分割されたレポートには、新しいポータルに加えて新しい KPI でもアクセスできます。 お気に入りのタグを付けることができ、管理者はコンテンツを管理できます。 

独自のカスタム ブランドを Web ポータルに適用することができます。 また、Web ポータルでは KPI の権限を作成できます。 KPI を使うと、レポートを開かなくても、主要なビジネス指標をブラウザーで簡単に見ることができます。 

新しい Web サイトは、レポート マネージャーを完全に書き直したものです。 単一ページで標準ベースの HTML5 アプリであり、Edge、Internet Explorer 10 と 11、Chrome、Firefox、Safari などのすべての主要な最新ブラウザーが最適化されています。

Web ポータルでは従来のフォルダー階層が引き続き機能するので、コンテンツを整理できます。 コンテンツは、モバイル レポート、KPI、ページ分割されたレポートに加えて、レポートの構成要素として使用される Power BI Desktop レポート、Excel ブック、共有データセット、共有データ ソースなどの種類別に整理されます。 これらを安全に格納して管理できます。

また、レポート処理のスケジュール設定、オンデマンドでのレポート アクセス、新しい Web ポータルでパブリッシュされたレポートのサブスクライブも、引き続き可能です。

詳細については、「[Reporting Services Web ポータル](../reporting-services/web-portal-ssrs-native-mode.md)」をご覧ください。
  
## <a name="reporting-services-in-sharepoint-integrated-mode"></a>Reporting Services の SharePoint 統合モード  

SharePoint 統合モードで Reporting Services にレポートをパブリッシュします。 レポート処理のスケジュール設定、レポートへのオンデマンド アクセス、パブリッシュされたレポートのサブスクライブ、他のアプリケーション (Microsoft Excel など) へのレポートのエクスポートを実行できます。 SharePoint サイトにパブリッシュされたレポートに対してデータ警告を作成したり、レポートのデータが変化したときに電子メール メッセージを受信できます。  

詳しくは、「[Reporting Services Report Server (SharePoint Mode)](../reporting-services/report-server-sharepoint/reporting-services-report-server-sharepoint-mode.md)」をご覧ください。
 
## <a name="includessrsnoversiontokenssrsnoversionmdmd-programming-features"></a>[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプログラミング機能  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のプログラミング機能を活用し、API を使用してカスタム アプリケーションのデータ処理とレポート処理を統合または拡張して、レポート作成機能を拡張およびカスタマイズできます。
 
 詳しくは、「[開発者ガイド (Reporting Services)](../reporting-services/reporting-services-developer-documentation.md)」をご覧ください。 
  
## <a name="browse-content-by-area"></a>領域ごとのコンテンツの参照  
* [旧バージョンとの互換性](../reporting-services/旧バージョンとの互換性-reporting-services.md) 
* [Reporting Services Report Server](../reporting-services/report-server-sharepoint/reporting-services-report-server.md)  
* [Web ポータル](../reporting-services/web-portal-ssrs-native-mode.md)
* [Reporting Services レポート &#40;SSRS&#41;](../reporting-services/reports/reporting-services-reports-ssrs.md)  
* [レポート データ &#40;SSRS&#41;](../reporting-services/report-data/report-data-ssrs.md)  
* [SQL Server 2016 のレポート ビルダー](../reporting-services/report-builder/report-builder-in-sql-server-2016.md)  
* [SQL Server Mobile Report Publisher](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
* [Reporting Services の KPI](../reporting-services/working-with-kpis-in-reporting-services.md)
* [Reporting Services ツール](../reporting-services/tools/reporting-services-tools.md)  
  
## <a name="see-also"></a>参照  
* [Reporting Services のインストール](../reporting-services/install-windows/install-reporting-services.md)
* [レポート ビルダーをインストールする](../reporting-services/install-windows/install-report-builder.md)   
* [SQL Server Data Tools (SSDT) のダウンロード](http://go.microsoft.com/fwlink/?LinkID=616714)
  
  