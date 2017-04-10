---
title: "Reporting Services と Power View のブラウザー サポート | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "レポートの表示"
  - "スクリプト [Reporting Services], 要件"
  - "レポートの表示"
  - "ブラウザー [Reporting Services]"
  - "Web ブラウザー [Reporting Services], ブラウザー サポートの概要"
  - "レポートの参照 [Reporting Services]"
  - "コンポーネント [Reporting Services], ブラウザー"
  - "Web ブラウザー [Reporting Services]"
ms.assetid: 48a75bbb-0029-4c43-891d-dc8f4fc0ebe1
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 121
---
# Reporting Services と Power View のブラウザー サポート
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、ReportViewer コントロール、Power View の管理と表示にサポートされているブラウザーのバージョンについて説明します。
  
 **適用対象:** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint モード  
  
##  <a name="bkmk_webportal"></a> ブラウザー要件:  [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]

次は、[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] でサポートされているブラウザーの現行リストです。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*
- Microsoft Edge (+)
- Microsoft Internet Explorer 10 または 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple iOS**  
*iOS 9 を内蔵した iPhone または iPad*

- Apple Safari (+)

**Google Android**  
*Android 4.4 (KitKat) 以降を内蔵したスマートフォンまたはタブレット*

- Google Chrome (+)

 **(+)** 最新公開リリース バージョン  
  
##  <a name="bkmk_reportviewer"></a> ブラウザー要件: ReportViewer Web コントロール (2015) 
 次は、ReportViewer Web コントロール (2015) でサポートされているブラウザーの現行リストです。 レポート ビューアーでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Web ポータルや SharePoint ライブラリのレポートを表示できます。  
  
**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 または 11
- Google Chrome (+)
- Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** 最新公開リリース バージョン  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]に統合されている SharePoint 製品を使用している場合は、「  [SharePoint 2016 でブラウザー サポートを計画する](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx)」を参照してください。  
  
###  <a name="bkmk_authentication"></a> 認証の要件  
 クライアント要求が正常に終了するように、ブラウザーでは、レポート サーバーで処理する必要がある特定の認証方法をサポートしています。 次の表は、Windows オペレーティング システムで実行中の各ブラウザーでサポートされる既定の認証の種類を示しています。  
  
|**ブラウザーの種類**|**サポート**|**ブラウザーの既定値**|**サーバーの既定値**|  
|----------------------|------------------|-------------------------|------------------------|  
|**Microsoft Edge** (+)|ネゴシエート、Kerberos、NTLM、基本|ネゴシエート|可能。 Edge の既定の認証設定を使用します。|  
|**[Microsoft Internet Explorer]**|ネゴシエート、Kerberos、NTLM、基本|ネゴシエート|可能。 Internet Explorer の既定の認証設定を使用します。|  
|**Google Chrome**(+)|ネゴシエート、NTLM、基本|ネゴシエート|可能。 Chrome の既定の認証設定を使用します。|  
|**Mozilla Firefox**(+)|NTLM、基本|NTLM|可能。 Firefox の既定の認証設定を使用します。|  
|**Apple Safari**(+)|NTLM、基本|基本|可能。 Safari の既定の認証設定を使用します。|  
  
 **(+)** 最新公開リリース バージョン  
  
### レポートを表示するためのスクリプトの要件  
 レポート ビューアーを使用するには、スクリプトを実行するようにブラウザーを構成する必要があります。  
  
 スクリプトが有効になっていない場合は、レポートを開くときに次のようなエラー メッセージが表示されます。  
  
-   **ブラウザーでスクリプトがサポートされていないか、スクリプトを許可するように構成されていません。ここをクリックすると、スクリプトを使用せずにこのレポートが表示されます**。  
  
 スクリプトを使用せずにレポートを表示することを選択した場合、レポート ツール バーやドキュメント マップなどのレポート ビューアー機能を使用しない HTML でレポートが表示されます。  
  
> [!NOTE]  
>  レポート ツール バーは HTML ビューアー コンポーネントの一部です。 既定では、ツール バーはブラウザー ウィンドウに表示されるすべてのレポートの上部に表示されます。 レポート ビューアーには、レポート内の情報検索、特定のページへのスクロール、および表示目的でのページ サイズの調整機能があります。 レポート ツール バーまたは HTML ビューアーの詳細については、「 [HTML Viewer and the Report Toolbar](../reporting-services/html-viewer-and-the-report-toolbar.md)」を参照してください。  
  
##  <a name="bkmk_controls"></a> Visual Studio での ReportViewer Web サーバー コントロールのブラウザー サポート  
 ReportViewer Web サーバー コントロールは、ASP.NET Web アプリケーションにレポート機能を埋め込むために使用されます。 このコントロールは Visual Studio に含まれており、このトピックで説明している他のコンポーネントとはサポートしているブラウザーおよびブラウザー バージョンが異なります。 アプリケーションの表示に使用するブラウザーの種類によって、アプリケーションに埋め込むことができる ReportViewer の機能が決まります。 レポート機能が制限されるサポート対象のブラウザーとサポートされているプラットフォームについては、このトピックの表を参照してください。  
  
 スクリプトのサポートが有効になっているブラウザーを使用します。 ブラウザーがスクリプトを実行できない場合、レポートを表示することができません。  
  
**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

- Microsoft Edge (+)
- Microsoft Internet Explorer 10 または 11
- Google Chrome (+)
- Mozilla Firefox (+)
  
 **(+)** 最新公開リリース バージョン  
  
##  <a name="bkmk_powerview"></a> Power View のブラウザー サポート  

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

- Microsoft Internet Explorer 10 または 11
- Mozilla Firefox (+)
  
**Apple OS X**  
*OS X 10.9-10.11*

- Apple Safari (+)
  
 **(+)** 最新公開リリース バージョン  
  
 SharePoint 2016 のブラウザー サポートの詳細については、「 [SharePoint 2013 でブラウザー サポートを計画する](http://technet.microsoft.com//library/cc263526\(v=office.16\).aspx)」を参照してください。  
  
## 参照  
[Web ポータルを使用したレポートの検索と表示 (レポート ビルダーおよび SSRS)](http://msdn.microsoft.com/ja-jp/8556807e-f2e2-4a7b-bb1b-ac5ea1872e51)  
[Reporting Services ツール](../reporting-services/tools/reporting-services-tools.md)  
[Web ポータル (SSRS ネイティブ モード)](http://msdn.microsoft.com/ja-jp/7349e626-6ed5-4d21-b05f-cf042ad9ad70)  
[HTML ビューアーとレポート ツール バー](../reporting-services/html-viewer-and-the-report-toolbar.md)  
[URL アクセス パラメーター リファレンス](../reporting-services/url-access-parameter-reference.md)  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]
