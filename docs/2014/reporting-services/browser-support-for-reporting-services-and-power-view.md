---
title: Reporting Services と Power View ブラウザー サポートの計画 (Reporting Services 2014)
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 58ed105619ca5ad5eadb00271e18ddaa10c6bfe3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63266822"
---
# <a name="planning-for-reporting-services-and-power-view-browser-support-reporting-services-2014"></a>Reporting Services と Power View ブラウザー サポートの計画 (Reporting Services 2014)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] では、Web ブラウザーを使用して、レポートを表示したりレポート マネージャーを実行したりします。 すべてのブラウザーですべてのレポート機能がサポートされているわけではありません。 このトピックでは、レポート マネージャーの管理機能、レポートの表示、Visual Studio のレポート ビューアー コントロールのサポートと要件について説明します。 また、サポートされるブラウザーで使用できる機能、認証要件、およびスクリプトの要件の概要も示します。  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モード | [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モード  
  
 **このトピックの内容**  
  
- [Power View のブラウザーのシナリオ](#bkmk_powerview)  
  
- [レポート マネージャーのブラウザーの要件 (ネイティブ モード)](#bkmk_reportmanager)  
  
- [レポートを表示するためのブラウザー要件](#bkmk_reportviewer)  
  
- [認証の要件](#bkmk_authentication)  
  
- [Visual Studio での ReportViewer Web サーバー コントロールのブラウザー サポート](#bkmk_controls)  
  
##  <a name="bkmk_powerview"></a> Power View のブラウザーのシナリオ

 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] でサポートされているブラウザーとそのバージョンの一覧は、開くドキュメントの種類によって異なります。 Excel 2013 ブックと" **.rdlx**"ファイルは、さまざまなコンポーネントを利用します。  
  
|ドキュメントの種類|環境|ブラウザー サポート|  
|-------------------|-----------------|---------------------|  
|Power View レポート (.RDLX)|**SharePoint Server:** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]で[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 統合モードと Power View web アプリケーション。|参照してください[Power View を SharePoint サーバーと Reporting Services SharePoint 統合モードで](#bkmk_powerview_on_SSRS)します。|  
|Power View シートが含まれた Excel 2013 ブック|**SharePoint Server:** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] Excel Services でします。<br /><br /> **SharePoint Online (Office 365):** [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] Excel Web app です。|参照してください[ビューは Excel services または SharePoint 上の Excel Web App のオンライン電源](#bkmk_powerview_on_ExcelServices)します。|  
  
###  <a name="bkmk_powerview_on_SSRS"></a> SharePoint Server および Reporting Services SharePoint 統合モードの power View  
 次の表は、[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] サービス アプリケーションと SharePoint の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインがインストールされ、構成されている SharePoint ファームでユーザーが Power View レポート (.RDLX) を開く場合に、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] でサポートされるブラウザーをまとめたものです。  
  
- この表は、SharePoint 2010 と SharePoint 2013 に適用されます。  
  
- SharePoint 2013 のブラウザー サポートの詳細については、次を参照してください。 [SharePoint 2013 でブラウザー サポートを計画する](https://technet.microsoft.com//library/cc263526\(office.15\).aspx)(https://technet.microsoft.com/library/cc263526(office.15).aspx) します。  
  
- SharePoint 2010 のブラウザー サポートの詳細については、次を参照してください。 [(SharePoint Server 2010) のブラウザー サポートを計画する](https://technet.microsoft.com/library/cc263526\(office.14\).aspx)(https://technet.microsoft.com/library/cc263526(office.14).aspx) します。  
  
|**ブラウザー**|**Windows 8 および 8.1**|**Windows 7**|**Windows Server 2012 および 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6 10.9**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|  
|**(デスクトップ) 用の Internet Explorer 11**|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**(デスクトップ) 用の Internet Explorer 10**|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**Internet Explorer 9**|サポートされていません|32 ビット、64 ビット|サポートされていません|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|  
|**Internet Explorer 8**|サポートされていません|32 ビット、64 ビット|サポートされていません|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|  
|**Mozilla Firefox (最新公開リリース バージョン)**|32 ビット|32 ビット|32 ビット|32 ビット|32 ビット|サポートされていません|  
|**Apple Safari (最新公開リリース バージョン)**|サポートされていません|サポートされていません|サポートされていません|サポートされていません|サポートされていません|32 ビット、64 ビット|  
  
> [!NOTE]  
> "32 ビット" はブラウザーのことであり、オペレーティング システムではありません。 たとえば、32 ビット版の Internet Explorer 9 を 64 ビット版の Windows 7 で使用できます。  
  
#### <a name="inprivate-browsing-feature-in-internet-explorer"></a>Internet Explorer での InPrivate ブラウズ機能

 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] では、[!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 8 および Internet Explorer 9 の InPrivate ブラウズ機能はサポートされていません。 InPrivate ブラウズの詳細については、次を参照してください[InPrivate ブラウズとは何ですか?。](http://windows.microsoft.com/Windows7/What-is-InPrivate-Browsing) (http://windows.microsoft.com/Windows7/What-is-InPrivate-Browsing) 。  
  
###  <a name="bkmk_powerview_on_ExcelServices"></a> Excel Services または SharePoint Online の Excel Web App の power View

 次の表は、Excel Services を実行している SharePoint Server で、Power View シートが含まれた Excel 2013 ブックをユーザーが開く場合に、 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] でサポートされるブラウザーのバージョンをまとめたものです。  
  
-   SharePoint 2013 のブラウザー サポートの詳細については、次を参照してください。 [SharePoint 2013 でブラウザー サポートを計画する](https://technet.microsoft.com/library/cc263526\(office.15\).aspx)(https://technet.microsoft.com/library/cc263526(office.15).aspx) します。  
  
|**ブラウザー**|**Windows 8 および 8.1**|**Windows 7**|**Windows Server 2012 および 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6 10.9**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|  
|**(デスクトップ) 用の Internet Explorer 11**|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**(デスクトップ) 用の Internet Explorer 10**|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**Internet Explorer 9**|サポートされていません|32 ビット、64 ビット|サポートされていません|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|  
|**Internet Explorer 8**|サポートされていません|32 ビット、64 ビット|サポートされていません|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|  
|**Mozilla Firefox (最新公開リリース バージョン)**|32 ビット|32 ビット|32 ビット|32 ビット|32 ビット|32 ビット、64 ビット|  
|**Apple Safari (最新公開リリース バージョン)**|サポートされていません|サポートされていません|サポートされていません|サポートされていません|サポートされていません|32 ビット、64 ビット|  
|**Google Chrome (最新公開リリース バージョン)**|32 ビット **(\*)** 期間限定|32 ビット **(\*)** 期間限定|32 ビット **(\*)** 期間限定|32 ビット **(\*)** 期間限定|32 ビット **(\*)** 期間限定|サポートされていません|  
  
 **(\*)** Chrome は、Netscape プラグイン API (NPAPI)、Silverlight で使用されるサポートを中止します。 Power View は、Silverlight に依存します。  詳細については、 [NPAPI の最終的なカウント ダウンに関するページ](http://blog.chromium.org/2014/11/the-final-countdown-for-npapi.html)を参照してください。  
  
##  <a name="bkmk_reportmanager"></a> レポート マネージャーのブラウザーの要件 (ネイティブ モード)

 次に示しているのは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モードのレポート マネージャーを実行してレポートとレポート サーバーを管理するために使用できるブラウザーの最新の一覧です。  
  
|ブラウザー|  
|-------------|  
|Internet Explorer 7 以降 (スクリプト機能オン)|  
|Mozilla FireFox (最新公開リリース バージョン)|  
|Apple Safari (最新公開リリース バージョン)|  
|Google Chrome (最新公開リリース バージョン)|  
  
##  <a name="bkmk_reportviewer"></a> レポートを表示するためのブラウザー要件

 レポート ビューアーでサポートされているブラウザーと機能の最新の一覧を次に示します。 レポート ビューアーでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート マネージャーおよび SharePoint ライブラリからのレポートの表示がサポートされています。  
  
|**ブラウザー**|**Windows 8 および 8.1**|**Windows 7**|**Windows Server 2012 および 2012 R2**|**Windows Server 2008 R2**|**Windows Server 2008**|**Mac OS X 10.6 10.9**|**iPad の iOS 6 ~ 7**|  
|-----------------|---------------------------|-------------------|-----------------------------------------|--------------------------------|-----------------------------|------------------------------|----------------------------|  
|**(デスクトップ) 用の Internet Explorer 11**|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|サポートされていません|サポートされていません|  
|**(デスクトップ) 用の Internet Explorer 10**|32 ビット、64 ビット|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|サポートされていません|サポートされていません|  
|**Internet Explorer 9**|サポートされていません|32 ビット、64 ビット|サポートされていません|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**Internet Explorer 8**|サポートされていません|32 ビット、64 ビット|サポートされていません|32 ビット、64 ビット|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**Internet Explorer 7**|サポートされていません|サポートされていません|サポートされていません|サポートされていません|32 ビット、64 ビット|サポートされていません|サポートされていません|  
|**Mozilla Firefox (最新公開リリース バージョン)**|32 ビット|32 ビット|32 ビット|32 ビット|32 ビット|サポートされていません|サポートされていません|  
|**Apple Safari (最新公開リリース バージョン)**|サポートされていません|サポートされていません|サポートされていません|サポートされていません|サポートされていません|32 ビット、64 ビット|機能制限付きでサポートされている<sup>(1)</sup>|  
|**Google Chrome (最新公開リリース バージョン)**|32 ビット|32 ビット|32 ビット|32 ビット|32 ビット|サポートされていません|サポートされていません|  
  
 **<sup>(1)</sup>**  次の機能がサポートされます。  
  
- PDF 形式および TIFF 形式へのエクスポート  
  
- iOS デバイスの Apple Safari で対話的にレポートを表示します。 サポートされる機能には、展開/折りたたみ、パラメーター ペイン、対話的な並べ替えなどがあります。  
  
- 詳細については、次を参照してください。 [Microsoft Surface デバイスと Apple iOS デバイスでのビュー Reporting Services レポート](../../2014/reporting-services/view-reporting-services-reports-surface-ios-devices.md)します。  
  
 **注** Macintosh コンピューターからレポート サーバーにアクセスする場合は、Safari を使用することをお勧めします。 統合されている SharePoint 製品を使用しているかどうかは[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]を参照してください[ブラウザー サポート (Windows SharePoint Services) を計画する](https://go.microsoft.com/fwlink/?LinkId=183583)します。  
  
### <a name="url-access-for-viewing-reports"></a>URL アクセスを使用したレポートの表示

 レポート マネージャーを使用せずに直接レポートを表示するには、レポートおよびレポート ビューアーにリンクする URL アクセスを使用します。 URL アクセスでは、さまざまなブラウザーがサポートされます。  
  
 URL アクセスの詳細については、次のトピックを参照してください。  
  
- [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
  
###  <a name="bkmk_authentication"></a> 認証の要件

 クライアント要求が正常に終了するように、ブラウザーでは、レポート サーバーで処理する必要がある特定の認証方法をサポートしています。 次の表は、Windows オペレーティング システムで実行中の各ブラウザーでサポートされる既定の認証の種類を示しています。  
  
|**ブラウザーの種類**|**サポート**|**ブラウザーの既定値**|**サーバーの既定値**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Internet Explorer**|ネゴシエート、Kerberos、NTLM、基本|ネゴシエート|可能。 Internet Explorer の既定の認証設定を使用します。|  
|**Firefox**|NTLM、基本|NTLM|可能。 Firefox の既定の認証設定を使用します。|  
|**Safari**|Basic|Basic|可能。 Safari の既定の認証設定を使用します。|  
|**Chrome**|ネゴシエート、NTLM、基本|ネゴシエート|可能。 Chrome の既定の認証設定を使用します。|  
  
### <a name="script-requirements"></a>スクリプトの必要条件

 レポート ビューアーを使用するには、スクリプトを実行するようにブラウザーを構成する必要があります。  
  
 スクリプトが有効になっていない場合は、レポートを開くときに次のようなエラー メッセージが表示されます。  
  
- **ブラウザーでスクリプトがサポートされていないか、スクリプトを許可するように構成されていません。ここをクリックして、スクリプトを使用せずにこのレポートを表示します**。  
  
 スクリプトを使用せずにレポートを表示することを選択した場合、レポート ツール バーやドキュメント マップなどのレポート ビューアー機能を使用しない HTML でレポートが表示されます。  
  
> [!NOTE]  
> レポート ツール バーは HTML ビューアー コンポーネントの一部です。 既定では、ツール バーはブラウザー ウィンドウに表示されるすべてのレポートの上部に表示されます。 レポート ビューアーには、レポート内の情報検索、特定のページへのスクロール、および表示目的でのページ サイズの調整機能があります。 レポート ツール バーまたは HTML ビューアーの詳細については、「 [HTML Viewer and the Report Toolbar](html-viewer-and-the-report-toolbar.md)」を参照してください。  
  
##  <a name="bkmk_controls"></a> Visual Studio での ReportViewer Web サーバー コントロールのブラウザー サポート

 ReportViewer Web サーバー コントロールは、ASP.NET Web アプリケーションにレポート機能を埋め込むために使用されます。 このコントロールは Visual Studio に含まれており、このトピックで説明している他のコンポーネントとはサポートしているブラウザーおよびブラウザー バージョンが異なります。 アプリケーションの表示に使用するブラウザーの種類によって、アプリケーションに埋め込むことができる ReportViewer の機能が決まります。 レポート機能が制限されるサポート対象のブラウザーとサポートされているプラットフォームについては、このトピックの表を参照してください。  
  
 サポートされているブラウザーの描画エンジンの違いにより、一部のレポートの拡張機能の表示がブラウザー間で異なる場合があります。  たとえば、文字の回転が異なります。  
  
### <a name="scripting-requirements"></a>スクリプトの必要条件

 スクリプトのサポートが有効になっているブラウザーを使用します。 ブラウザーがスクリプトを実行できない場合、レポートを表示することができません。  
  
### <a name="browser-requirements-for-viewing-reports-with-the-reportviewer-web-server-controls"></a>ReportViewer Web サーバー コントロールを使用してレポートを表示するためのブラウザーの要件

 対話型レポート機能のサポートは、ブラウザーの種類によって異なります。 次のサポート表には、各プラットフォームでサポートされているブラウザーの種類を示しています。備考欄には、適用される制限が記載されています。  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|**ブラウザー**|**Windows 8** および **Windows 8.1**|**Windows 7**|**Windows Server 2012** および **2012 R2**|**Windows Server 2008** および **2008 R2**|**Windows Server 2003**|**Mac OS X 10.6 10.9**|**注**|  
|**(デスクトップ用 Internet Explorer 11**|はい|[はい]|はい|サポートされていません|サポートされていません|サポートされていません|Internet Explorer では、ReportViewer のすべての機能をサポートしています。|  
|**(デスクトップ) 用の Internet Explorer 10**|はい|[はい]|はい|サポートされていません|サポートされていません|サポートされていません|Internet Explorer では、ReportViewer のすべての機能をサポートしています。|  
|**Internet Explorer 9**|サポートされていません|はい|サポートされていません|はい|[はい]|はい|Internet Explorer では、ReportViewer のすべての機能をサポートしています。|  
|**Internet Explorer 8.0**|サポートされていません|はい|サポートされていません|はい|可<sup>1</sup>|サポートされていません|Internet Explorer では、ReportViewer のすべての機能をサポートしています。 <sup>1</sup>|  
|**Internet Explorer 7.0**|サポートされていません|はい|サポートされていません|はい|可<sup>1</sup>|サポートされていません|Internet Explorer では、ReportViewer のすべての機能をサポートしています。 <sup>1</sup>|  
|**Firefox (最新公開リリース バージョン)**|はい|[はい]|[はい]|[はい]|はい|サポートされていません|印刷とズームはサポートされていません。|  
|**Safari (最新公開リリース バージョン)**|サポートされていません|サポートされていません|サポートされていません|サポートされていません|サポートされていません|はい|印刷とズームはサポートされていません。<br /><br /> パラメーター化されたレポートで日付を選択するために使用するカレンダー コントロールは、このブラウザーでは無効になっています。 ユーザーは、使用する日付をパラメーター プロンプト領域に手動で入力する必要があります。|  
|**Chrome (最新公開リリース バージョン)**|はい|[はい]|[はい]|[はい]|はい|サポートされていません|印刷とズームはサポートされていません。|  
  
 <sup>1</sup>標準モード、Internet Explorer 7.0 および 8.0 は表示されませんレポートに斜線します。 レポートで斜線を使用している場合は、ASP.NET ページを Internet Explorer の Quirks モードで実行するように設定します。 これを行うには、検索、 \<!DOCTYPE > タグで、ASP.NET ページ。 また、マスター ページを使用している場合は、.master ファイルでこのタグを探します。 このタグは次のようになっています。  
  
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
```
  
 置換、 \<!DOCTYPE > タグに次のタグ。  
  
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">  
```
  
 Internet Explorer の互換モードの詳細については、次を参照してください。[ドキュメント互換性の定義](https://go.microsoft.com/fwlink/?LinkId=180380)(https://go.microsoft.com/fwlink/?LinkId=180380) します。  
  
 ReportViewer コントロールの使用の詳細については、次を参照してください。[展開レポートと ReportViewer コントロール](https://msdn.microsoft.com/library/ms251723.aspx)(https://msdn.microsoft.com/library/ms251723.aspx) します。  
  
## <a name="next-steps"></a>次の手順

 [Reporting Services ツール](tools/reporting-services-tools.md)[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) [HTML ビューアーとレポート ツールバー](html-viewer-and-the-report-toolbar.md) [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
