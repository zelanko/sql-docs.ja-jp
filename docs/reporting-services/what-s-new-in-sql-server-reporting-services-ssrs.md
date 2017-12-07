---
title: "Reporting Services (SSRS) の新機能 | Microsoft Docs"
ms.date: 10/10/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.custom: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Active
ms.openlocfilehash: a409c0678ca17215932cffe378bdcebbb752897d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="whats-new-in-sql-server-reporting-services-ssrs"></a>SQL Server Reporting Services (SSRS) の新機能

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../includes/ssrs-appliesto-not-pbirs.md)]

SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の新機能について説明します。 ここでは、主な機能領域を扱います。新しいアイテムがリリースされた場合は更新します。

  SQL Server の他の領域の新機能については、「[SQL Server 2017 の新機能](../sql-server/what-s-new-in-sql-server-2017.md)」、または「[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)」を参照してください。

 **ダウンロード** ![download](../analysis-services/media/download.png "download")

- SQL Server 2017 Reporting Services をダウンロードするには、「**[Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=55252)**」に移動します。

最新のリリース ノートについては、「[SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)」または「[Power BI Report Server のリリース ノート](https://powerbi.microsoft.com/documentation/reportserver-release-notes/)」を参照してください。 Power BI のレポート サーバーについては、「[Power BI Report Server の概要](https://powerbi.microsoft.com/documentation/reportserver-get-started/)」を参照してください。

## <a name="whats-new-in-sql-server-2017"></a>SQL Server 2017 の新機能

### <a name="comments-on-reports"></a>レポートのコメント

レポートでコメントが使用できるようになり、分析観点の追加や、他のユーザーとの共同作業ができるようになりました。 コメントに添付ファイルを含めることもできます。

![レポート サーバー内のコメント](media/what-s-new-in-sql-server-reporting-services-ssrs/report-server-comments.png)

詳細については、「[レポート サーバーのレポートにコメントを追加する](https://powerbi.microsoft.com/documentation/reportserver-add-comments/)」を参照してください。

### <a name="dax-queries-in-reporting-tools"></a>レポート ツールの DAX クエリ

レポート ビルダーと SQL Server Data Tools の最新リリースでは、クエリ デザイナーで必要なフィールドをドラッグ アンド ドロップすることで、サポートされている SQL Server Analysis Services 表形式データ モデルに対するネイティブの DAX クエリを作成できます。 [Reporting Services のブログ](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/)を参照してください。

### <a name="rest-api-support"></a>REST API のサポート

最新のアプリケーションとカスタマイズを開発できるようにするため、SQL Server Reporting Services は OpenAPI に完全に対応する RESTful API をサポートするようになりました。 API の完全な仕様とドキュメントは、[swaggerhub](https://app.swaggerhub.com/apis/microsoft-rs/SSRS/2.0) で入手できます。

## <a name="query-designer-support-for-dax-now-in-report-builder-and-sql-server-data-tools"></a>レポート ビルダーおよび SQL Server Data Tools での DAX に対するクエリ デザイナーのサポート

レポート ビルダーと SQL Server Data Tools (リリース候補) の最新リリースで、サポートされている SQL Server Analysis Services 表形式データ モデルに対するネイティブの DAX クエリが作成できるようになりました。 両方のツールでクエリ デザイナーを使用して、必要なフィールドをドラッグ アンド ドロップしたり、DAX クエリを自分で記述する代わりに自動生成させることができます。  
 
詳細については、[Reporting Services のブログ](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/)を参照してください。

* [Microsoft SQL Server 2016 レポート ビルダー](https://go.microsoft.com/fwlink/?LinkId=734968)のダウンロード
* [SQL Server Data Tools - リリース候補](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate)のダウンロード

> **注**: DAX のクエリ デザイナーは、SQL Server 2016+ に組み込まれた SSAS 表形式のデータ ソースでのみ使用できます。
 
## <a name="whats-new-in-sql-server-2016"></a>SQL Server 2016 の新機能
  
### <a name="reporting-services-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>Reporting Services [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]  
 新しい [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] を利用できます。 これは、KPI、モバイル レポート、ページ分割されたレポート、Excel および Power BI Desktop ファイルが組み込まれた最新のポータルです。 以前のリリースの Report Manager がこの [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] に置き換えられています。 Mobile Report Publisher と Report Builder を [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] からダウンロードすることもできます。ClickOnce テクノロジは必要ありません。
 
 モバイル レポートを作成するには、 [!INCLUDE[SS_MobileReptPub_Short](../includes/ss-mobilereptpub-short-md.md)]が必要です。  
  
 [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]の詳細については、「 [Web ポータル (SSRS ネイティブ モード)](../reporting-services/web-portal-ssrs-native-mode.md)」を参照してください。  
  
 ![ssRSPortal](../reporting-services/media/ssrsportal.png "ssRSPortal")  
 
 #### <a name="custom-branding-for-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 
  ブランド化パックを使用して、組織のロゴや色で [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] をカスタマイズできます。  
  
  カスタムブランド化の詳細については、「 [Web ポータルのブランド化](http://msdn.microsoft.com/en-us/6dac97f7-02a6-4711-81a3-e850a6b40bf1)」を参照してください。
 
 #### <a name="key-performance-indicators-kpi-in-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 

使用しているフォルダーのコンテキストに適合する KPI を [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] で直接作成できます。 KPI を作成するときは、データセットを選択し、それらの値を集約できます。 詳細をドリル スルーするための関連コンテンツを選択することもできます。
  
 ![ssrs-webportal-kpi](../reporting-services/media/ssrs-webportal-kpi.png)
 
 詳細については、「 [Reporting Services で KPI を使用する](http://msdn.microsoft.com/en-us/a28cf500-6d47-4268-a248-04837e7a09eb)」を参照してください。
  
 
 ### <a name="mobile-reports"></a>モバイル レポート
 
Reporting Services モバイル レポートは、多様なフォーム ファクター用に最適化された専用レポートであり、モバイル デバイスでレポートにアクセスするユーザーに最適なエクスペリエンスを提供します。 モバイル レポートでは、時間グラフ、カテゴリ グラフ、比較グラフ、ツリーマップ、カスタム マップなどの多種多様な視覚エフェクトを使用できます。 モバイル レポートは、オンプレミスの SQL Server Analysis Services 多次元およびテーブル データを含むさまざまなデータ ソースに接続できます。 調整可能なグリッド行とグリッド列と柔軟なモバイル レポート要素を備えたデザイン画面で、任意の画面サイズに対応するモバイル レポートをレイアウトできます。 その後、これらのモバイル レポートを Reporting Service サーバーに保存しておき、iPad、iPhone、Android フォン、および Windows 10 デバイスのブラウザーまたはPower BI モバイル アプリで表示と操作を実行できます。
  
#### <a name="mobile-report-publisher"></a>Mobile Report Publisher  
 [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)]では、SQL Server モバイル レポートを作成して [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]に公開できます。  
  
 ![SS_MRP_LayoutTabSmall](../reporting-services/media/ss-mrp-layouttabsm.png "SS_MRP_LayoutTabSmall")  
  
 詳細については、「 [SQL Server Mobile Report Publisher を使用してモバイル レポートを作成する](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)」をご覧ください。  
  
#### <a name="sql-server-mobile-reports-hosted-in-reporting-services-available-in-power-bi-mobile-app"></a>Reporting Services でホストされている SQL Server モバイル レポートを Power BI モバイル アプリで使用可能  
 iPad および iPhone の iOS 用 Power BI モバイル アプリでは、ローカル レポート サーバーでホストされている SQL Server モバイル レポートを表示できるようになりました。  
  
 ![SS_MRP_iPad_HomeSm](../reporting-services/media/ss-mrp-ipad-homesm.png "SS_MRP_iPad_HomeSm")  
  
 一部の構成を変更しないと、既定では接続できません。 Power BI モバイル アプリがレポート サーバーに接続できるようにする方法の詳細については、「 [Power BI モバイル アクセス用のレポート サーバーを有効にする](../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)」をご覧ください。
  
### <a name="support-of-sharepoint-mode-and-sharepoint-2016"></a>SharePoint モードと SharePoint 2016 のサポート  
 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、SharePoint 2013 および SharePoint 2016 との統合をサポートしています。
 
詳細については、以下をご覧ください。  
  
-   [SharePoint、Reporting Services サーバー、Reporting Services アドインのサポートされる組み合わせ &#40;SQL Server 2016&#41;](../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
-   [SharePoint 製品用 Reporting Services アドインの検索場所](../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [Reporting Services SharePoint モードのインストール](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  

### <a name="microsoft-net-framework-4-support"></a>Microsoft .NET Framework 4 のサポート  
 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] では、Microsoft .NET Framework 4 の現在のバージョンをサポートしています。 これには、バージョン 4.0 と 4.5.1 が含まれます。 .Net Framework バージョン 4.x がインストールされていない場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップの機能のインストール手順で .NET 4.0 がインストールされます。  

### <a name="report-improvements"></a>レポートの強化機能

**HTML5 レンダリング エンジン:** 新しい HTML5 レンダリング エンジンは、最新の Web の "完全" 標準モードと最新ブラウザーを対象としています。  新しいレンダリング エンジンは、一部の古いブラウザーで使用される互換モードに依存しなくなりました。
  
 ブラウザーのサポートの詳細については、「 [Reporting Services と Power View のブラウザー サポート](../reporting-services/browser-support-for-reporting-services-and-power-view.md)」を参照してください。  

**最新のページ分割されたレポート:** グラフ、ゲージ、マップ、その他のデータ ビジュアル化のための最新スタイルで改ページ調整されたレポートを美しくデザインします。
  
**ツリー マップとサンバースト グラフ:** ツリーマップ ![ssrs_treemap_icon](../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") とサンバースト グラフ ![ssrs_sunburst_icon](../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon") を使用してレポートを強化できます。これらは、階層データを表示する優れた方法です。 詳細については、「 [Reporting Services のツリー マップとサンバースト グラフ](../reporting-services/report-design/tree-map-and-sunburst-charts-in-reporting-services.md)」を参照してください。  

**レポートの埋め込み:** iframe を URL パラメーターと共に使用して、モバイル レポートやページ分割されたレポートを他の Web ページやアプリケーションに埋め込むことができるようになりました。  

**レポートアイテムの Power BI ダッシュボードへのピン留め:** [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]でレポートを表示しているときに、レポート アイテムを選択し、 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] ダッシュボードにピン留めできます。   ピン留めできるアイテムは、グラフ、ゲージ パネル、マップ、イメージです。 **(1)** ピン留めするダッシュボードを含むグループを選択し、 **(2)** アイテムをピン留するダッシュボードも選択して、 **(3)** ダッシュボードでのタイルの更新頻度を選択できます。   ![注:](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "注:") 更新は [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] サブスクリプションによって管理されます。アイテムをピン留めした後に、サブスクリプションを編集し、別の更新スケジュールを構成できます。  
  
 ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png) 
  
 詳細については、「[Power BI Report Server の統合 &#40;構成マネージャー&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)」および「[Power BI ダッシュボードへの Reporting Services のアイテムのピン留め](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)」を参照してください。  
 
 **PowerPoint のレンダリングとエクスポート:** Microsoft PowerPoint (PPTX) 形式は、 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] の新しい表示拡張機能です。 通常のアプリケーション (レポート ビルダー、レポート デザイナー (SSDT)、および [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]) から PPTX 形式のレポートをエクスポートできます。 たとえば、次の図は [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]のエクスポート メニューを示しています。 
  
 ![ssrs-export-powerpoint](../reporting-services/media/ssrs-export-powerpoint.png) 
  
 サブスクリプション出力用に PPTX 形式を選択し、レポート サーバー URL アクセスを使用してレポートをレンダリングおよびエクスポートすることもできます。 たとえば、ブラウザーで次の URL コマンドを実行すると、レポート サーバーの名前付きインスタンスからレポートがエクスポートされます。  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 詳細については、「 [URL アクセスを使用してレポートをエクスポート](../reporting-services/export-a-report-using-url-access.md)」を参照してください。  
 
 **リモート印刷での PDF による ActiveXの置き換え:** レポート ビューアー ツール バーの ActiveX 印刷エクスペリエンスが、サポートされているブラウザー (Microsoft Edge など) のマトリックス間で機能する最新の PDF ベースのエクスペリエンスに置き換えられました。 ActiveX コントロールをダウンロードする必要はなくなります。 使用するブラウザーとインストールされている PDF 表示アプリケーションおよびサービスに応じて、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] はレポートを印刷するための印刷ダイアログを表示するか、レポートの .PDF ファイルのダウンロードを促します。  管理者が [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]からクライアント側の印刷を無効にすることもできます。 詳細については、「 [Reporting Services のクライアント側印刷機能の有効化と無効化](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)」を参照してください。

![ssrs-pdf-printing](../reporting-services/media/ssrs-pdf-printing.png)

### <a name="subscription-improvements"></a>サブスクリプションの機能強化  
 
|機能|サポートされるサーバー モード|  
|-------------|---------------------------|  
|**サブスクリプションを有効または無効にする**: サブスクリプションを簡単に無効または有効にできる新しいユーザー インターフェイス オプション。 サブスクリプションを無効にしても、スケジュールなどの他の構成プロパティは維持され、簡単に有効にすることができます。<br /><br /> ![ssrs-enable-disable-subscriptions](../reporting-services/media/ssrs-enable-disable-subscriptions.png)<br /><br /> 詳細については、「 [レポートとサブスクリプションの処理を無効化または一時停止する](../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md)」を参照してください。|ネイティブ モード|  
|**サブスクリプションの説明**: 新しいサブスクリプションを作成するときに、サブスクリプションのプロパティの一部として、レポートの説明を含めることができるようになりました。 説明はサブスクリプションの概要ページに表示されます。|SharePoint モードとネイティブ モード|  
|**サブスクリプションの所有者の変更**: サブスクリプションの所有者をすばやく変更できる拡張ユーザー インターフェイス。 以前のバージョンの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、管理者はスクリプトを使用してサブスクリプションの所有者を変更できます。 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] リリース以降では、ユーザー インターフェイスまたはスクリプトを使用してサブスクリプションの所有者を変更できます。 サブスクリプションの所有者の変更は、ユーザーが組織を離れたり、組織での役割が変更されたりしたときに行う一般的な管理タスクです。|SharePoint モードとネイティブ モード|  
|**ファイル共有サブスクリプションの共有資格情報**: [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のファイル共有サブスクリプションには、現在 2 つのワークフローがあります。<br /><br /> このリリースでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 管理者が 1 つのファイル共有アカウントを構成し、そのアカウントを 1 つ以上のサブスクリプションで使用できるようになりました。 ファイル共有アカウントは、ネイティブ モードの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 構成マネージャーで **[ファイル共有アカウントの指定]**を使用して構成します。その後、サブスクリプション構成ページで、ユーザーが **[ファイル共有アカウントの使用]**を選択します。<br /><br /> 個々のサブスクリプションに、宛先のファイル共有の資格情報を具体的に構成します。<br /><br /> この 2 つの方法を組み合わせて、一部のファイル共有サブスクリプションでは管理者が構成したファイル共有アカウントを使用し、他のサブスクリプションでは特定の資格情報を使用することもできます。|ネイティブ モード|  

### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
 新しいリリースの SSDT には、 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]用のプロジェクト テンプレート (レポート サーバー プロジェクト ウィザードとレポート サーバー プロジェクト) が含まれています。 SSDT のダウンロードについては、 [SQL Server Data Tools for Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=827542)に関するページをご覧ください。  

### <a name="report-builder-improvements"></a>レポート ビルダーの機能強化

**新しいレポート ビルダーのユーザー インターフェイス:** [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] コア ユーザー インターフェイスの UI 要素が簡素化され、最新の外観になりました。  
  
|||  
|-|-|  
|新規|Previous|  
|![ssrs_rbfacelift_new](../reporting-services/media/ssrs-rbfacelift-new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../reporting-services/media/ssrs-rbfacelift-old.png "ssrs_rbfacelift_old")|  

**カスタム パラメーター ペイン:** ペインをカスタマイズできるようになりました。 レポート ビルダーのデザイン サーフェイスを使用して、パラメーター ペインの特定の列や行にパラメーターをドラッグできます。 列を追加または削除して、ペインのレイアウトを変更することもできます。   詳細については、「[レポートのパラメーター ペインをカスタマイズする &#40;レポート ビルダー&#41;](../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)」を参照してください。  
  
 ![レポート データ ペインとパラメーター ペインのパラメーター リスト](../reporting-services/media/ssrs-customizeparameter-parameterlist-reportdatapane.png "レポート データ ペインとパラメーター ペインのパラメーター リスト")  

  
**High DPI のサポート:** [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] では、高 DPI (インチあたりのドット数) スケーリングと高 DPI デバイスをサポートします。  高 DPI の詳細については、次の記事をご覧ください。  
  
-   [Windows 8.1 の DPI スケーリング拡張機能](https://blogs.windows.com/windowsexperience/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  
  
-   [高 DPI と Windows 8.1](http://technet.microsoft.com/library/dn528848.aspx)  

## <a name="next-steps"></a>次の手順

[Analysis Services の新機能](http://msdn.microsoft.com/en-us/aa69c299-b8f4-4969-86d8-b3292fe13f08)  
[SSRS での Power BI レポートの技術プレビュー - リリース ノート](../reporting-services/reporting-services-release-notes.md)  
[SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)   
[旧バージョンとの互換性](http://msdn.microsoft.com/en-us/675b0e0e-cfee-4790-9675-80fc3ea6d30f)   
[SQL Server 2016 の各エディションがサポートする Reporting Services の機能](http://msdn.microsoft.com/en-us/39f03d2d-6e48-4b34-a9d3-07f86313b937)   
[Reporting Services のアップグレードと移行](../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
[Power BI レポート サーバー](https://powerbi.microsoft.com/documentation/reportserver-get-started/)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
