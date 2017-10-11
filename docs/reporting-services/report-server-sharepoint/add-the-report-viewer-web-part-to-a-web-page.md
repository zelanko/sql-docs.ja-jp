---
title: "Web ページに、レポート ビューアー web パーツを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 26080938c9849d6021f30d970ab2262f405df00c
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="add-the-report-viewer-web-part-to-a-web-page"></a>Web ページに、レポート ビューアー web パーツを追加します。

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

レポート ビューアー web パーツを使用すると、統合で実行されるように構成されたレポート サーバー SharePoint で実行するのにモードのレポートを表示します。 レポート ビルダーまたはレポート デザイナーで作成し、ライブラリにアップロードしたレポート定義 (.rdl) ファイルを表示するのに web パーツを使用することができます。

そのページ上のレポートを埋め込む場合は、web ページに、レポート ビューアー web パーツを追加できます。

> [!NOTE]
> この記事では、SharePoint 製品用 Reporting Services アドインに同梱されているレポート ビューアー web パーツに固有です。 SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

Web パーツを web ページを追加するには、サイト レベルでページのカスタマイズの追加とアクセス許可があります。 既定のセキュリティ設定を使用する場合、この権限はフル コントロール レベルの権限を持つ **所有者** グループのメンバーに与えられます。

## <a name="to-embed-a-report-in-a-web-page"></a>Web ページで、レポートを埋め込むには

1.  開くか、web パーツ ページまたはダッシュ ボードを作成します。  
  
2.  **[サイトの操作]**の **[ページの編集]**をクリックします。  
  
3.  をクリックして**web パーツの追加**です。  
  
4.  Web パーツ カテゴリの一覧で、 **[その他]** カテゴリをクリックし、 **[SQL Server Reporting Services レポート ビューアー]**をクリックします。  
  
5.  **[追加]**をクリックします。 Web パーツは、ゾーンの上部に追加されます。 Web パーツは、ドラッグして、領域内の別の場所に移動できます。  
  
6.  ビューアー内で、 **[ツール ペインを開くにはここをクリックします]**をクリックします。  
  
7.  参照ボタン (**[...]**) をクリックして、現在のサイト コレクションの任意のライブラリにあるレポートを選択します。 レポートの URL を入力することもできます。 レポートの URL を調べるには、レポートを右クリックし、 **[プロパティ]**をクリックします。 レポートの横にある下向きの矢印アイコンはクリックしないでください。アイテムの [プロパティの表示] ページでは、レポートの URL は表示されません。 **[プロパティ]** ダイアログ ボックスで URL をコピーし、貼り付ける場合には、URL 内の "%20" をスペースに置き換えてください (たとえば、"Company%20Sales" は "Company Sales" にします)。  
  
    > [!NOTE]  
    >  各レポート ビューアー web パーツには、1 つのレポートが含まれています。 URL は、現在の SharePoint サイト、または同じ Web アプリケーションやファーム内のサイト上のレポートへの完全修飾パスで指定する必要があります。 この URL は、ドキュメント ライブラリとして解決されるか、ドキュメント ライブラリ内でレポートが格納されるフォルダーとして解決される必要があります。 レポート URL には、ファイル拡張子 .rdl を含める必要があります。 レポートがモデル ファイルまたは共有データ ソース ファイルに依存している場合、URL でそのファイルを指定する必要はありません。 必要なファイルへの参照は、レポートに含まれています。  
  
8.  開いているツール ペインでプロパティを設定し、既定の外観とレイアウトを変更します。  
  
9. ツール ペインの下部で **[適用]** をクリックし、 **[OK]** をクリックしてペインを閉じます。  
  
## <a name="see-also"></a>参照

 [ビューアー web パーツを SharePoint サイトをレポートします。](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [レポート ビューアー web パーツをカスタマイズします。](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)   
 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
