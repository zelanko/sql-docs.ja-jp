---
title: "Reporting Services レポート ビューアー web パーツでフィルターまたはドキュメント web パーツを接続 |Microsoft ドキュメント"
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 87d4b4a3f0c01804329f3a7b0688632c20ed6c9b
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="connect-filter-or-documents-web-part-with-a-reporting-services-report-viewer-web-part"></a>Reporting Services レポート ビューアー web パーツでフィルターまたはドキュメント web パーツを接続します。

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SharePoint 製品を使用している場合は、ダッシュ ボードまたは web パーツをフィルター web パーツまたはドキュメント web パーツとレポート ビューアー web パーツを含むページを作成できます。 サポートされているバージョンは [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]です。 [!INCLUDE[winSPServ3](../../includes/winspserv3-md.md)] または [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 もサポートされています。 フィルター web パーツを接続すると、フィルター web パーツのフィルターの値を選択したユーザーは、同じページにパラメーター化されたレポートに値を送信できます。 ドキュメント web パーツを接続すると、ドキュメント ライブラリでレポートをクリックするユーザーは、隣接するレポート ビューアー web パーツでレポートを表示できます。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

 フィルター web パーツはレポートの 1 つまたは複数のパラメーターに値を送信するために使用します。 フィルター web パーツを使用するのには、値、データ型、および web パーツによって送信される形式と互換性があることに定義されたパラメーターがレポートに必要です。  
  
 ドキュメント web パーツは、ホーム サイトのドキュメント ライブラリに関連付けられます。 ドキュメント ライブラリからアイテムを表示、追加、または削除するには、 **[すべてのサイト コンテンツの表示]**をクリックします。 ライブラリで、 **[ドキュメント]**をクリックします。 **[新規]**、 **[アップロード]**、および **[アクション]** メニューを使用してドキュメント ライブラリのアイテムを管理できます。  
  
## <a name="connect-a-filter-web-part"></a>フィルター web パーツを接続します。
  
1.  開くか、web パーツ ページまたはダッシュ ボードを作成します。  
  
2.  **[サイトの操作]** メニューの **[ページの編集]**をクリックします。  
  
3.  をクリックして**web パーツの追加**です。  
  
4.  **すべての web パーツ**で、 **[その他]**カテゴリで、 **SQL Server Reporting Services レポート ビューアー**です。  
  
5.  **[追加]**をクリックします。 Web パーツは、ゾーンの上部に追加されます。  
  
6.  別の領域で、同じ web パーツ ページまたはダッシュ ボードでは、をクリックして**web パーツの追加**です。  
  
7.  **すべての web パーツ**で、**フィルター**セクションで、web パーツを選択します。  
  
8.  **[追加]**をクリックします。 Web パーツは、ゾーンの上部に追加されます。  
  
9. Web パーツを含むゾーンで、web パーツをクリックして**編集**メニューのをポイント**接続**、をポイント**フィルター値の送信に**、し、**レポートビューアー** - *レポート名*です。  
  
10. 変更をチェックインし、ページを保存します。  
  
## <a name="connect-a-documents-web-part"></a>ドキュメント web パーツを接続します。  
  
1.  開くか、web パーツ ページまたはダッシュ ボードを作成します。  
  
2.  **[サイトの操作]** メニューの **[ページの編集]**をクリックします。  
  
3.  をクリックして**web パーツの追加**です。  
  
4.  **すべての web パーツ**で、**リストまたはライブラリ**セクションで、**ドキュメント。**  
  
5.  **[追加]**をクリックします。 Web パーツは、ゾーンの上部に追加されます。  
  
6.  ツール ペインの下部で **[適用]** をクリックし、 **[OK]** をクリックしてペインを閉じます。  
  
7.  別の領域で、同じ web パーツ ページまたはダッシュ ボードでは、をクリックして**web パーツの追加**です。  
  
8.  **すべての web パーツ**で、 **[その他]**カテゴリで、 **SQL Server Reporting Services レポート ビューアー。**  
  
9. **[追加]**をクリックします。 Web パーツは、ゾーンの上部に追加されます。  
  
10. Web パーツを含むゾーンで、web パーツをクリックして**編集**メニューのをポイント**接続**、をポイント**からレポート定義を取得する**、し、 **ドキュメント**です。  
  
11. 変更をチェックインし、ページを保存します。  
  
## <a name="see-also"></a>参照

 [Web ページに、レポート ビューアー web パーツを追加します。](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)   
 [ビューアー web パーツを SharePoint サイトをレポートします。](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [レポート ビューアー Web パーツのカスタマイズ](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

