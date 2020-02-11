---
title: レポートビューアー Web パーツを Web ページに追加します (SharePoint 統合モードの Reporting Services)。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 468acea55c334ffda169daff2b5da4c417348a3e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104290"
---
# <a name="add-the-report-viewer-web-part-to-a-web-page-reporting-services-in-sharepoint-integrated-mode"></a>レポート ビューアー Web パーツを Web ページに追加する (Reporting Services の SharePoint 統合モード)
  レポート ビューアー Web パーツを使用することで、SharePoint 統合モード用に構成されているレポート サーバーで実行されるレポートを表示できます。 この Web パーツでは、レポート ビルダーまたはレポート デザイナーで作成してライブラリにアップロードしたレポート定義ファイル (.rdl) を表示できます。  
  
 Web ページにレポート ビューアー Web パーツを追加することで、Web ページにレポートを埋め込むことができます。  
  
> [!NOTE]  
>  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインによってインストールされるレポート ビューアー Web パーツと、RSWebParts.cab ファイルに含まれているレポート ビューアー Web パーツは、名前は同じでも異なるものです。 このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを使用してインストールされるレポート ビューアー Web パーツを利用するための手順について説明します。  
  
 Web パーツを Web ページに追加するには、サイト レベルでの "ページの追加とカスタマイズ" 権限が必要です。 既定のセキュリティ設定を使用する場合、この権限はフル コントロール レベルの権限を持つ **所有者** グループのメンバーに与えられます。  
  
### <a name="to-embed-a-report-in-a-web-page"></a>Web ページにレポートを埋め込むには  
  
1.  Web パーツ ページまたはダッシュボードを開くか、作成します。  
  
2.  
  **[サイトの操作]** の **[ページの編集]** をクリックします。  
  
3.  [ **Web パーツの追加] を**クリックします。  
  
4.  Web パーツ カテゴリの一覧で、 **[その他]** カテゴリをクリックし、 **[SQL Server Reporting Services レポート ビューアー]** をクリックします。  
  
5.  **[追加]** をクリックします。 Web パーツが、ゾーンの一番上に追加されます。 Web パーツは、ドラッグして、領域内の別の場所に移動できます。  
  
6.  ビューアー内で、 **[ツール ペインを開くにはここをクリックします]** をクリックします。  
  
7.  参照ボタン (**[...]**) をクリックして、現在のサイト コレクションの任意のライブラリにあるレポートを選択します。 レポートの URL を入力することもできます。 レポートの URL を調べるには、レポートを右クリックし、 **[プロパティ]** をクリックします。 レポートの横にある下向きの矢印アイコンはクリックしないでください。アイテムの [プロパティの表示] ページでは、レポートの URL は表示されません。 
  **[プロパティ]** ダイアログ ボックスで URL をコピーし、貼り付ける場合には、URL 内の "%20" をスペースに置き換えてください (たとえば、"Company%20Sales" は "Company Sales" にします)。  
  
    > [!NOTE]  
    >  1 つのレポート ビューアー Web パーツには、1 つのレポートが格納されます。 URL は、現在の SharePoint サイト、または同じ Web アプリケーションやファーム内のサイト上のレポートへの完全修飾パスで指定する必要があります。 この URL は、ドキュメント ライブラリとして解決されるか、ドキュメント ライブラリ内でレポートが格納されるフォルダーとして解決される必要があります。 レポート URL には、ファイル拡張子 .rdl を含める必要があります。 レポートがモデル ファイルまたは共有データ ソース ファイルに依存している場合、URL でそのファイルを指定する必要はありません。 必要なファイルへの参照は、レポートに含まれています。  
  
8.  開いているツール ペインでプロパティを設定し、既定の外観とレイアウトを変更します。  
  
9. ツール ペインの下部で **[適用]** をクリックし、 **[OK]** をクリックしてペインを閉じます。  
  
## <a name="see-also"></a>参照  
 [SharePoint サイトのレポートビューアー Web パーツ](../report-viewer-web-part-on-a-sharepoint-site.md)   
 [レポートビューアー Web パーツのカスタマイズ](../customize-the-report-viewer-web-part.md)   
 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;](../install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
