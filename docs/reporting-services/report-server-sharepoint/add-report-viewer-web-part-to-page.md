---
title: "SQL Server Reporting Services レポート ビューアー web パーツを SharePoint ページに追加 |Microsoft ドキュメント"
ms.custom: Display a report, from SQL Server Reporting Services or Power BI Report Server, by adding a Report Viewer web part to a SharePoint page.
ms.date: 09/26/2017
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
ms.openlocfilehash: fbc68b6ff9f1edf5cf6ee13f6e93a3d2d1a8f834
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---

# <a name="add-sql-server-reporting-services-report-viewer-web-part-to-a-sharepoint-page"></a>SQL Server Reporting Services レポート ビューアー web パーツを SharePoint ページに追加します。

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー web パーツを SharePoint ページに追加することで、SQL Server Reporting Services または Power BI のレポート サーバーからレポートを表示します。

![ビューアー web パーツを SharePoint ページにレポートします。](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>前提条件

* レポートが正常に読み込むようにするため、Claims to Windows Token Service (C2WTS) Kerberos 用に構成する必要がありますの制約付き委任します。 C2WTS の構成方法の詳細については、次を参照してください。 [Claims to Windows Token Service (c2wts) と Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)です。

* SharePoint ファームにレポート ビューアー web パーツを展開する必要があります。 レポート ビューアー web パーツ ソリューション プロジェクトを展開する方法については、次を参照してください。 [SharePoint サイト上のレポート ビューアー web パーツを展開](deploy-report-viewer-web-part.md)です。

* Web パーツを web ページを追加するには、サイト レベルでページのカスタマイズの追加とアクセス許可があります。 既定のセキュリティ設定を使用する場合、この権限はフル コントロール レベルの権限を持つ **所有者** グループのメンバーに与えられます。

## <a name="add-web-part"></a>Web パーツを追加します。

1. SharePoint サイトで次のように選択します。、**歯車の形の**クリックし、左上にあるアイコン**ページを追加する**です。

    ![Sharepoint サイトに、歯車アイコンからページを追加します。](media/sharepoint-add-a-page.png)

2. ページの名前と選択**作成**です。

3. ページ デザイナー内でを選択、**挿入**をリボンにタブです。 選択し、 **web パーツ**内で、**パーツ**セクションです。

    ![Office のリボンから web パーツを挿入します。](media/sharepoint-insert-web-part.png)

4. **カテゴリ*** * SQL Server Reporting Services (ネイティブ モード)。 **パーツ****レポート ビューアー**です。 選択し、**追加**です。

    ![レポート ビューアー web パーツを追加します。](media/sharepoint-report-viewer-web-part.png)

    最初は、エラーで表示可能性があります。 エラーは、既定のレポート サーバーの URL 設定されているため*http://localhost*その場所で使用できない可能性があります。

## <a name="configure-the-report-viewer-web-part"></a>レポート ビューアー web パーツを構成します。

特定のレポート ポイントで次のように web パーツを構成します。

1. SharePoint ページを編集するには、web パーツの右上隅で、下矢印を選択し、選択**web パーツの編集**です。

    ![Web パーツ ドロップダウンから web ページを編集します。](media/sharepoint-edit-web-part.png)

2. 入力、**レポート サーバーの URL**レポートをホストしているレポート サーバーにします。 これは、ような*http://myrsserver/reportserver*です。

3. Web パーツ内で、表示するレポートの名前とパスを入力します。 これは、ような*AdventureWorks Sample Reports/company Sales*です。 この例では、レポートで*Company Sales*というフォルダーには、 *AdventureWorks Sample Reports*です。

4. レポートは、レポート サーバーの URL とレポートの名前を指定するパラメーターを必要とする場合は、選択**パラメーターの読み込み**内で、**パラメーター**セクションです。

5. 選択**Ok** web パーツの構成に変更を保存します。

6. 選択**保存**、SharePoint ページに変更を保存する、Office のリボン内です。

![ビューアー web パーツを SharePoint ページにレポートします。](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>考慮事項と制約

* レポート ビューアー web パーツは、SharePoint 内のページを最新では使用できません。
* Power BI レポートは、レポート ビューアー web パーツでは使用できません。
* レポート ビューアー web パーツのページに追加するが表示されない場合は、必ず確保[、レポート ビューアー web パーツを展開](deploy-report-viewer-web-part.md)です。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
