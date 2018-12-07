---
title: SharePoint Web パーツを使用したネイティブ モードのレポートの表示と探索 (SSRS) | Microsoft Docs
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.topic: conceptual
ms.assetid: dee8ee42-156b-43b6-b202-02dfb9404284
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c78f6e02a2aef893aa3e8702158a5f3c63cea76a
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52417283"
---
# <a name="view-and-explore-native-mode-reports-using-sharepoint-web-parts-ssrs"></a>View and Explore Native Mode Reports Using SharePoint Web Parts (SSRS)

> [!IMPORTANT]  
>  SQL Server Reporting Services では、ネイティブ モードの (RSWebParts.cab) Web パーツを使用した、ネイティブ モードのレポート サーバーから SharePoint サイト上のレポート サーバー コンテンツへのアクセスがサポートされなくなりました。 代わりに、 [SharePoint サイトのレポート ビューアー Web パーツ](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md) を使用してください。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、特定のバージョンのレポート サーバーにおいて、特定の配置モードで動作する Web パーツがいくつかあります。  
  
-   **ネイティブ モード:** ネイティブ モードのレポート サーバーから SharePoint サイト上のレポート サーバー コンテンツにアクセスするには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に同梱されている SharePoint 2.0 Web パーツの、レポート エクスプローラーとレポート ビューアーを使用します。 このトピックでは、2.0 Web パーツのインストールと使用の方法について説明します。  
  
-   **SharePoint モード:** SharePoint モードで実行されているレポート サーバーにアクセスするには、SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインによってインストールされる Web パーツを使用します。 アドインの詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」をご覧ください。  
  
> [!NOTE]  
>  ネイティブ モード用のレポート ビューアー Web パーツ (SPViewer.dwp) は、SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインによってインストールされる Web パーツ (ReportViewer.dwp) とは異なる Web パーツです。 これらの Web パーツのスキーマと実装は異なりますが、両方を同じ SharePoint ファームにインストールできます。 この 2 つの Web パーツは外観によって区別できます。アドインと共にインストールされるレポート ビューアー Web パーツには、ツール バーに **[アクション]** メニューがあります。  
  
 レポート サーバー モードの詳細については、「 [Reporting Services レポート サーバー](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)」をご覧ください。  
  
 このトピックの内容  
  
-   [レポート エクスプローラーとレポート ビューアーについて](#bkmk_aboutwebparts)  
  
-   [Web パーツを使用するための要件](#bkmk_requirements)  
  
-   [Web パーツのインストール](#bkmk_installingwebparts)  
  
-   [Web パーツの追加と構成](#bkmk_configurewebparts)  
  
##  <a name="bkmk_aboutwebparts"></a> レポート エクスプローラーとレポート ビューアーについて  
 レポート エクスプローラーとレポート ビューアーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Service Pack 2 (SP2) から導入された SharePoint 2.0 Web パーツであり、現在のリリースでも引き続き提供されています。  
  
 この Web パーツを利用することで、レポートを表示したり、SharePoint サイトからレポート サーバーのフォルダー階層を参照することができます。  
  
 Web パーツのカスタマイズがサポートされないことに注意してください。 Web パーツはそのまま使用することが想定されています。拡張したり変更したりしないでください。  
  
-   **レポート エクスプローラー** (SPExplorer.dwp) はレポート サーバー コンピューター上のレポート マネージャーに接続します。 レポート サーバーで使用可能なレポートを表示し、個々のレポートにサブスクライブできます。 レポート ビルダーが有効であり、十分な権限がある場合には、レポート エクスプローラー Web パーツからレポート ビルダーを起動することができます。  
  
     レポート エクスプローラーでは、レポート マネージャーのページを使用してフォルダーの内容を表示できます。 レポート サーバーのフォルダー階層に含まれる個別のアイテムおよびフォルダーへのアクセスは、レポート サーバーにおけるロール割り当てによって制御されます。 レポートを選択すると、新しいブラウザー ウィンドウでレポートが開きます。 レポート サーバーの HTML ビューアーにレポートが表示され、レポート ツール バーが表示されますが、レポート ビューアー Web パーツは表示されません。 ツール バーの設定をカスタマイズする場合には、レポート サーバーに URL アクセス パラメーターを指定してください。 手順については、「 [URL アクセス パラメーター リファレンス](../../reporting-services/url-access-parameter-reference.md)」をご覧ください。  
  
-   **レポート ビューアー** (SPViewer.dwp) には、レポートが表示されるだけでなく、ページの移動、コンテンツの検索、レポートのエクスポートなどに使用できるツール バーも表示されます。 Web パーツ ページにレポート ビューアー Web パーツを追加することで、ページに特定のレポートが常に表示されるようにできます。また、 **これをレポート エクスプローラーに接続** して、レポート ビューアー Web パーツで開いているレポートをレポート エクスプローラーで表示することができます。  
  
##  <a name="bkmk_requirements"></a> Web パーツを使用するための要件  
 レポート ビューアー Web パーツとレポート エクスプローラー Web パーツの使用には、次の要件があります。  
  
-   次のバージョンの SharePoint 製品およびテクノロジがサポートされています。  
  
    -   [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 および [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007。  
  
    -   [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] と [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]の両方で使用できます。  
  
-   ネイティブ モードのレポート サーバーのバージョンは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以降である必要があります。  
  
-   レポート サーバーはネイティブ モードで動作する必要があります。 レポート エクスプローラー Web パーツまたはレポート ビューアー Web パーツを使用して、SharePoint モードで動作するレポート サーバー上のレポートに接続したり表示することは **できません** 。  
  
-   レポート マネージャーをインストールする必要があります。  
  
 レポート エクスプローラー Web パーツとレポート ビューアー Web パーツは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に含まれているキャビネット (.cab) ファイルを使用して配布されます。 以降のセクションでは、この Web パーツのインストール、構成、および使用の方法について説明します。  
  
##  <a name="bkmk_installingwebparts"></a> Web パーツのインストール  
 Web パーツは、SharePoint サーバーに対してキャビネット (.cab) ファイルとして配布されます。 Web パーツをインストールするには、コマンド ラインで SharePoint Stsadm.exe ツールを .cab ファイルに対して実行します。 このツールの詳細と Web パーツの配置の詳細については、SharePoint のマニュアルを参照してください。  
  
#### <a name="install-web-parts-using-powershell"></a>PowerShell を使用した Web パーツのインストール  
  
1.  SharePoint サーバー上のフォルダーに **RSWebParts.cab** をコピーします。 これを SharePoint サーバー上の任意のフォルダーにコピーしておき、Web パーツのインストールが終わった後で削除できます。 SQL Server 2014 Reporting Services 以前のバージョンでは、RSWebParts.cab ファイルが既定で次のフォルダーにインストールされます。  
  
    ```  
    C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Reporting Services\SharePoint  
    ```  
  
2.  SharePoint 製品がインストールされているコンピューターで、 **SharePoint 2010 管理シェル** を **管理者権限**で開きます。  
  
3.  次の PowerShell コマンドを実行します。  
  
    ```  
    Install-SPWebPartPack -LiteralPath "C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Reporting Services\SharePoint\RSWebParts.cab" -GlobalInstall  
    ```  
  
4.  Web パーツが配置されたことを示す次のようなメッセージが表示されます。  
  
    > Name               SolutionId                                             Deployed  
  
    > ----                    ----------                                              -------\-  
  
    > rswebparts.cab    00000000-0000-0000-0000-000000000000     True  
  
     PowerShell の使用方法の詳細については、[Install-SPWebPartPack (https://technet.microsoft.com/library/ff607840.aspx)](https://technet.microsoft.com/library/ff607840.aspx) を参照してください。  
  
#### <a name="install-web-parts-using-stsadmexe"></a>STSADM.exe を使用した Web パーツのインストール  
  
1.  このドキュメントの PowerShell に関するセクションの説明と同じ SharePoint サーバーの場所に、 **RSWebParts.cab** ファイルをコピーします。  
  
2.  SharePoint 製品がインストールされているコンピューターで、コマンド プロンプト ウィンドウを開き、 **Stsadm.exe** ツールのあるフォルダーに移動します。 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] の既定のパスを次に示します。  
  
    > C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\BIN  
  
3.  次の構文を使用して、.cab に対して Stsadm.exe を実行します。  
  
    ```  
    STSADM.EXE -o addwppack -filename "C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Reporting Services\SharePoint\RSWebParts.cab" -globalinstall  
    ```  
  
4.  "操作が正常に完了しました" というメッセージが表示されます。  
  
     `-globalinstall` を指定すると、Web パーツがグローバル アセンブリ キャッシュ (GAC) に追加されます。 Web パーツを接続する場合には、この手順を必ず実行してください。  
  
##  <a name="bkmk_configurewebparts"></a> Web パーツの追加と構成  
 Web パーツをインストールした後で、SharePoint サイトの 1 つ以上の Web ページに Web パーツを追加できます。 Web サイトを作成してコンテンツを追加する権限が必要です。  
  
 両方の Web パーツをページに追加し、レポート エクスプローラーとレポート ビューアーを接続する手順を次に示します。これによって、レポート エクスプローラーでクリックしたレポートがレポート エクスプローラー内に表示されるようになります。  
  
#### <a name="add-report-viewer"></a>レポート ビューアーの追加  
  
1.  [サイトの操作] の **[ページの編集]** をクリックします。  
  
2.  ページのゾーンで、 **[Web パーツの追加]** をクリックします。  
  
3.  **[Web パーツの追加]** ダイアログ ボックスを下にスクロールして **[その他]** カテゴリを表示します。  
  
4.  **[レポート ビューアー]** を選択します。  
  
    > [!WARNING]  
    >  **[SQL Server Reporting Services レポート ビューアー]** は選択しないでください。この Web パーツは SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールすると登録され、レポート サーバーを SharePoint モードで実行する場合に使用します。 これを使用してネイティブ モードのレポート サーバーのレポートを表示することはできません。  
  
5.  **[追加]** をクリックします。  
  
6.  ページが編集モードのときに、レポート ビューアー Web パーツで **[Web パーツの編集]** をクリックします。  
  
7.  **[レポート マネージャー URL]** に、アクセス対象のネイティブ モードのレポート サーバーに関連付けられているレポート マネージャー インスタンスの URL を入力します。 レポート マネージャー URL の既定の構文は、**https://\<サーバー名>/reports** です。  
  
8.  **[レポート パス]** で、スラッシュ、フォルダーのパス、レポート名の順に指定します。 サーバー名やレポート マネージャーの仮想ディレクトリは **含めないでください** 。 たとえば、Adventure Works フォルダーにある 'Company Sales' レポートを開くには、「**/Adventure Works/Company Sales**」と指定します。 'Products' レポートがレポート サーバーのルート フォルダーの **/Products** にある別の例を次に示します。  
  
9. **[OK]** をクリックします。  
  
#### <a name="add-report-explorer-and-connect-to-report-viewer"></a>レポート エクスプローラーの追加とレポート ビューアーへの接続  
  
1.  ベージの別の領域で **[Web パーツの追加]** をクリックし、"その他" フォルダーで **[レポート エクスプローラー]** をクリックして、 **[追加]** をクリックします。  
  
2.  レポート エクスプローラー Web パーツのショートカット メニューで、 **[Web パーツの編集]** をクリックします。  
  
3.  **[レポート マネージャー URL]** に、アクセス対象のネイティブ モードのレポート サーバーに関連付けられているレポート マネージャー インスタンスの URL を入力します。  
  
4.  必要に応じて、 **[開始パス]** を設定します。 開始パスは、レポート サーバーのフォルダー階層内のフォルダーです。 既定のページをフォルダー階層の下層のフォルダーに置く場合、開始パスを指定できます。 パスは必ずスラッシュから開始します。 レポート サーバーのフォルダー階層のルート ノードを起点とし、サーバー名やレポート マネージャー仮想ディレクトリを含まない、完全なパスを指定する必要があります。 たとえば、ルート ノードの直下にある Adventure Works という名前のフォルダーを開くには、[開始パス] に「 **/Adventure Works** 」と指定します。  
  
5.  **[OK]** をクリックします。  
  
6.  レポート エクスプローラーに、レポート サーバー内のレポート アイテムの一覧が表示されます。 既定では、レポートの名前をクリックすると、レポートが新しいウィンドウに表示されます。 レポート エクスプローラーとレポート ビューアーを接続し、レポート エクスプローラーでクリックしたレポートがレポート ビューアーに表示されるようにするには、以下の手順を完了します。  
  
    1.  レポート エクスプローラーのショートカット メニューで **[接続]** をクリックします。  
  
    2.  **[レポートの表示先]** をクリックします。  
  
    3.  **[レポート ビューアー]** をクリックします。  

その他の質問 [Reporting Services のフォーラムに質問してみてください](https://go.microsoft.com/fwlink/?LinkId=620231)
