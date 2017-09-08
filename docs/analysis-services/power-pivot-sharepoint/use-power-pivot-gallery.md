---
title: "Power Pivot ギャラリーを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/31/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ff92d1-787a-4f34-990f-6676b61875d7
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a14deecac6f597c9f09f9659ed165345ef5faceb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="use-power-pivot-gallery"></a>Power Pivot ギャラリーを使用する
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーは、特殊な SharePoint ドキュメント ライブラリです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含むパブリッシュ済みの Excel ブックおよび Reporting Services レポートを対象とする、豊富なプレビュー機能とドキュメント管理機能を提供します。  
  
> [!NOTE]  
>  サーバーの設定によっては、特定のドキュメントのプレビュー領域に警告またはエラー メッセージが表示されることがあります。 Excel ブックが開くたびにデータを自動更新するように設定されている場合は、メッセージが表示されることがあります。 データ更新に関する警告エラー メッセージを表示するように Excel Services が構成されている場合は、データ更新警告メッセージがプレビュー画像として表示されます。 ファーム管理者またはサービス管理者は、実際のワークシートのプレビューが表示されるように構成設定を変更できます。 詳細については、「 [Create a trusted location for Power Pivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
##  <a name="bkmk_top"></a> このトピックの内容  
 [前提条件](#prereq)  
  
 [Power Pivot ギャラリーのアイコン](#icons)  
  
 [Power Pivot ギャラリーに Excel ブックを保存する](#add)  
  
 [パブリッシュ済みの Power Pivot ブックに基づいて新しいレポートまたはブックを作成する](#newdocs)  
  
 [ブックまたはレポートをページ全体モードで開く](#view)  
  
 [Power Pivot ギャラリーの Power Pivot ブックに対するデータ更新のスケジュール](#newdr)  
  
 [Power Pivot ギャラリーのブックまたはレポートを削除する](#delete)  
  
 [サムネイル画像を更新する](#image)  
  
 [既知の問題](#bkmk_known_issues)  
  
##  <a name="prereq"></a> 前提条件  
  
> [!NOTE]  
>  Power Pivot ギャラリーには、Microsoft Silverlight が必要です。  Microsoft Edge ブラウザーでは、Silverlight がサポートされていません。   
> Edge でライブラリ コンテンツを表示するには、Power Pivot ギャラリーの **[ライブラリ]** タブをクリックして、ドキュメント ライブラリ ビューを **[すべてのドキュメント]**に変更します。    
> 既定のビューを変更するには、 **[ライブラリ]** タブをクリックしてから、[ビューの変更] をクリックします。 [このビューを既定のビューにする] をクリックし、[OK] をクリックして既定のビューを保存します。  
>  Edge のサポート対象について詳しくは、Windows ブログ「 [過去からの離別、第 2 部: ActiveX、VBScript... に別れを告げる](https://blogs.windows.com/msedgedev/2015/05/06/a-break-from-the-past-part-2-saying-goodbye-to-activex-vbscript-attachevent/)」をご覧ください。  
  
 すべての前提条件の一覧については、「 [Create and Customize Power Pivot Gallery](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)」をご覧ください。  
  
##  <a name="icons"></a> Power Pivot ギャラリーのアイコン  
 アイコンは、コンテンツを使用できるかどうか、およびコンテンツの状態を視覚的に示すインジケーターです。  
  
|アイコン|Description|  
|----------|-----------------|  
|![GMNI_PowerPivotGalleryIcon_Hourglass](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-hourglass.gif "GMNI_PowerPivotGalleryIcon_Hourglass")|砂時計アイコンは、ドキュメントの各ページのサムネイル画像が生成されているときに表示されます。 ページを更新して、更新された画像を表示します。|  
|![GMNI_PowerPivotGalleryIcon_Truncated](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-truncated.gif "GMNI_PowerPivotGalleryIcon_Truncated")|ページ アイコンは、ブックまたはレポートに含まれるページ数が [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーで表示できるページ数を超えているときに表示されます。 すべてのページを表示するには、クライアント アプリケーションを使用する必要があります。|  
|![GMNI_PowerPivotGalleryIcon_Error](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-error.gif "GMNI_PowerPivotGalleryIcon_Error")|エラー アイコンは、ドキュメントのサムネイル画像をレンダリングできなかったときに表示されます。 ドキュメントはライブラリにパブリッシュされていますが、カスタム [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ビューでレンダリングできません。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel アドインなどのクライアント アプリケーションではドキュメントを表示できます。|  
|![GMNI_PowerPivotGalleryIcon_badtype](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-badtype.gif "GMNI_PowerPivotGalleryIcon_badtype")|利用できないコンテンツ アイコンは、アップロードしたドキュメントを [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーでレンダリングできないときに表示されます。 サポートされているドキュメントの種類には、SQL Server 2008 R2 Reporting Services レポート ビルダーで作成した [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックおよびレポートがあります。<br /><br /> ごみ箱からドキュメントをリサイクルする場合も、このアイコンが表示されます。<br /><br /> 以前に有効なプレビュー画像を提供したドキュメント用にこのアイコンを取得する場合は、ドキュメントのプロパティを編集して変更を保存することによって画像を更新できます。|  
|![GMNI_PowerPivotGalleryIcon_Locked](../../analysis-services/power-pivot-sharepoint/media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")|ロックされたコンテンツ アイコンは、このドキュメントでサムネイル画像が意図的に無効になっているときに表示されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含んでいない Excel ブックのサムネイル画像や、スナップショット生成要件を満たしていない [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックまたは Reporting Services レポートのサムネイル画像を生成しません。 詳細については、このトピックの「前提条件」を参照してください。|  
  
##  <a name="add"></a> Power Pivot ギャラリーに Excel ブックを保存する  
 Excel 2010 のあらゆる共有技術を使用して、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをライブラリにパブリッシュできます。 たとえば、Excel 2010 では、[名前を付けて保存] を使用してライブラリへの SharePoint パスの全体またはその一部を指定できます。  
  
1.  ファイルを保存します。  
  
2.  1.  **Excel 2010**: [ファイル] メニューの **[保存して送信]** をクリックします。  
  
    2.  **[SharePoint に保存]**をクリックします。  
  
    3.  パブリッシュする個々のシートまたはパラメーターを [Excel Services のオプション] を使用して選択する場合は、 **[発行オプション]** をクリックします。 たとえば、[Excel Services のオプション] の [パラメーター] タブでは、パブリッシュしたブックに表示するスライサーを選択できます。  
  
    1.  **Excel 2013:**  [ファイル] メニューの **[上書き保存]**をクリックします。  
  
    2.  パブリッシュする個々のシートまたはパラメーターを [Excel Services のオプション] を使用して選択する場合は、 **[ブラウザー ビュー オプション]** をクリックします。 たとえば、[Excel Services のオプション] の [パラメーター] タブでは、パブリッシュしたブックに表示するスライサーを選択できます。  
  
3.  [名前を付けて保存] ダイアログ ボックスの [ファイル名] に、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーの URL またはその一部を入力します。 サーバー名など、URL アドレスの一部を入力した場合は、サイトを参照して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを見つけることができます。 そのためには、 **[保存]** をクリックして、指定したサーバーへの接続を開きます。  
  
     ![GMNI_ExcelSaveAs](../../analysis-services/power-pivot-sharepoint/media/gmni-excelsaveas.gif "GMNI_ExcelSaveAs")  
  
1.  [名前を付けて保存] ダイアログ ボックスを使用して、サイト上の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを選択します。  
  
2.  **[開く]** をクリックしてライブラリを開きます。  
  
3.  **[保存]** をクリックしてブックをライブラリにパブリッシュします。  
  
 ブラウザー ウィンドウで、ドキュメントが [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーに表示されることを確認します。 新たにパブリッシュされたドキュメントが一覧に表示されます。 ライブラリの設定によってドキュメントの表示位置が決まります (ドキュメントは、日付の昇順や名前のアルファベット順などで並べ替えられます)。 ブラウザー ウィンドウを更新しないと、直前に追加したドキュメントが表示されない場合もあります。  
  
#### <a name="upload-a-workbook-into-power-pivot-gallery"></a>Power Pivot ギャラリーにブックをアップロードする  
 SharePoint から開始して、パブリッシュするファイルをコンピューターから選択する場合は、ブックをアップロードすることもできます。  
  
1.  SharePoint サイトで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを開きます。  
  
2.  [ライブラリ] リボンで **[ドキュメント]**をクリックします。  
  
3.  **[ドキュメントのアップロード]**で、アップロード オプションを選択し、アップロードするファイルの名前と場所を入力します。 ライブラリの設定によってドキュメントの表示位置が決まります。 ブラウザー ウィンドウを更新しないと、直前に追加したドキュメントが表示されないことがあります。  
  
##  <a name="newdocs"></a> パブリッシュ済みの Power Pivot ブックに基づいて新しいレポートまたはブックを作成する  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをパブリッシュすると、そのブックを接続先データ ソースとして使用する追加のブックまたは Reporting Services レポートを作成できます。  
  
|||  
|-|-|  
|![GMNI_btn_NewDocReportGallery](../../analysis-services/power-pivot-sharepoint/media/gmni-btn-newdocreportgallery.gif "GMNI_btn_NewDocReportGallery")|レポート ビルダーまたは Excel 2010 を開始するには、[新しいレポート] ボタンの下矢印部分をクリックします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーで [新しいレポート] ボタンを使用するには、デザイン済みのビュー (シアター、ギャラリー、またはカルーセル) のいずれかを選択する必要があります。|  
  
#### <a name="create-report-builder-report"></a>レポート ビルダー レポートの作成  
 ライブラリ内の既存の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに基づいて新しいレポートを作成するには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを含む同じサイトに対する SharePoint 統合用に Reporting Services が構成されている必要があります。 [レポート ビルダー レポートの作成] オプションを選択すると、レポート ビルダーはレポート サーバーからダウンロードされ、初回使用時にローカル ワークステーションにインストールされます。 プレースホルダー レポート ファイルが、新しいレポート用に作成され、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーに保存されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックへの接続情報が、レポートの新しいデータ ソースとして作成されます。 次の手順で、デザイン ワークスペースにデータセットおよびレポート レイアウトを構築できます。 レポート ビルダーを使用してレポートを作成すると、変更および最終結果をギャラリーのレポート ドキュメントに保存できます。 後のデータ切断を回避するには、レポートおよびブックのファイルを同じライブラリに保存します。  
  
#### <a name="open-new-excel-workbook"></a>新しい Excel ブックを開く  
 既存の Excel ブックから新しいブックを作成するには、ローカル コンピューター上に Excel および [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] がインストールされている必要があります。 [新しい Excel ブックを開く] を選択すると、Excel が起動し、空のブック (.xlsx) ファイルが開き、接続先データ ソースとして [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データがバックグラウンドで読み込まれます。 元のブックの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ウィンドウのデータのみが新しいブックに使用されます。 元のブックのピボットテーブルやピボットグラフは除外されます。 新しいブックは、元のブックのデータにリンクされます。 新しいブック自体にデータがコピーされるのではありません。  
  
##  <a name="view"></a> ブックまたはレポートをページ全体モードで開く  
 表示されているドキュメント プレビューのサムネイルをクリックすると、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーのプレビューからは独立したページ全体モードでドキュメントが開きます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックは、ブラウザーで開きます。 Reporting Services レポートは、SharePoint サーバー上の Reporting Services 配置に含まれているレポート ビューアー Web パーツで開きます。  
  
 ブックをブラウザーで表示する代わりに、クライアント ワークステーション上で Excel を使用して開く方法もあります。 ファイルを表示するには、Excel 2013 または Excel 2010 と [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] アドインが必要です。 Excel 2007 では、ファイルを開くことはできても、データをピボットすることができません。 このため、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データの表示と作成には、Excel 2013 または Excel 2010 をお勧めします。 必要なアプリケーションがない場合は、SharePoint からブラウザーでブックを表示する必要があります。  
  
##  <a name="newdr"></a> Power Pivot ギャラリーの Power Pivot ブックに対するデータ更新のスケジュール  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データは、スケジュール設定された間隔で更新できます。  
  
|||  
|-|-|  
|![GMNI_btn_NewDataRefreshReportGallery](../../analysis-services/power-pivot-sharepoint/media/gmni-btn-newdatarefreshreportgallery.gif "GMNI_btn_NewDataRefreshReportGallery")|接続されているデータ ソースから更新されたデータを取得するスケジュールを作成または表示するには、[データ更新の管理] ボタンをクリックします。 スケジュールを作成する方法については、「 [データ更新のスケジュール (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)」を参照してください。|  
  
##  <a name="delete"></a> Power Pivot ギャラリーのブックまたはレポートを削除する  
 ライブラリからドキュメントを削除するには、最初に [すべてのドキュメント] ビューに切り替えます。  
  
1.  SharePoint サイトで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを開きます。  
  
2.  リボンで、 **[ライブラリ]**をクリックします。  
  
3.  [ビューの管理] で、[現在のビュー] ボックスの一覧の下矢印をクリックし、[すべてのドキュメント] を選択します。  
  
4.  削除するブックまたはレポートを選択します。  
  
5.  [ドキュメント (ファイル)] の [管理] で、 **[ドキュメントの削除]** ボタンをクリックします。  
  
##  <a name="image"></a> サムネイル画像を更新する  
 次の手順を使用して、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーのドキュメントのサムネイル画像を再生成します。  
  
1.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを [すべてのドキュメント] ビューに切り替えます。 実行するには、リボンの **[ライブラリ]** をクリックし、 **[現在のビュー]** を **[すべてのドキュメント]**に変更します。  
  
2.  サムネイル画像を更新するブックまたはレポートを選択します。  
  
3.  右側にある下矢印をクリックし、 **[プロパティの編集]**を選択します。  
  
4.  **[保存]**をクリックします。 ドキュメントを保存すると、スナップショット サービスにより強制的にプレビュー画像が再生成されます。  
  
##  <a name="bkmk_known_issues"></a> 既知の問題  
  
### <a name="document-type-is-not-supported"></a>ドキュメントの種類がサポートされていません  
 コンテンツの種類 " **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ドキュメント** " はサポートされていません。 ドキュメント ライブラリに対してコンテンツの種類 " **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ドキュメント** " を有効にし、その種類の新しいドキュメントを作成しようとすると、次のようなエラー メッセージが表示されます。  
  
-   新しいドキュメントを作成するには、Microsoft SharePoint Foundation 互換のアプリケーションおよび Web ブラウザーが必要です このドキュメント ライブラリにドキュメントを追加するには、[ドキュメントのアップロード] ボタンをクリックします。  
  
-   インターネット アドレス 'http://[server name]/testSite/PowerPivot Gallery/ReportGallery/Forms/Template.xlsx' は無効です。ファイル 'http://[server name]/testSite/PowerPivot Gallery/ReportGallery/Forms/Template.xlsx' にアクセスできません。 さまざまな原因が考えられます。  
  
 コンテンツの種類 " **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ドキュメント** " は、ドキュメント ライブラリに自動的に追加されません。サポートされていないコンテンツの種類を手動で有効にしない限り、この問題は発生しません。  
  
## <a name="see-also"></a>参照  
 [Create a trusted location for Power Pivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)   
 [Power Pivot ギャラリーの削除](../../analysis-services/power-pivot-sharepoint/delete-power-pivot-gallery.md)   
 [作成し、Power Pivot ギャラリーのカスタマイズ](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)   
 [データ更新のスケジュール (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
  

