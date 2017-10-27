---
title: "レポート ビューアー web パーツを SharePoint サイトで |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/25/2017
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
ms.openlocfilehash: a37ed5efe7c365c601deb95d9fe761d227e7021e
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>レポート ビューアー web パーツを SharePoint サイトで

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー web パーツは、カスタム web パーツです。 Web パーツを使用して、表示、移動、印刷、および、SharePoint サイト内のレポート サーバー上のレポートをエクスポートすることができます。 レポート ビューアー web パーツは、Microsoft SQL Server Reporting Services レポート サーバーによって処理されるレポート定義 (.rdl) ファイルに関連付けられます。 

最新のレポート ビューアー web パーツは、Power BI のレポート サーバーに配置されたサービスの改ページ調整されたレポートでこともできます。 Web パーツは、Power BI レポートでは機能しません。

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>レポート ビューアー web パーツは再取得理由

レポート ビューアー web パーツが使用可能な SharePoint 製品用 Reporting Services アドインの一部として。 Web パーツは、SharePoint 統合モードでレポート サーバーを特定しました。 SharePoint 統合モードは、SQL Server 2016 より後に推奨されなくなりました。

Reporting Services のインストール モードを 1 つだけがある SQL Server 2017 から始めて、:**ネイティブ モード**です。 ページ ビューアー web パーツを使用して、使用するすべてのレポート型を埋め込むことができます、 *rs: 埋め込む = true* URL パラメーター。 SharePoint ページにレポートを埋め込むには、顧客と、更新されたレポート ビューアー web パーツによって要求された統合ストーリーの改ページ調整されたレポートには、このシナリオを有効にします。

ページ ビューアー web パーツは、SharePoint ページに改ページ調整されたレポートを埋め込むサフィックス、中に、更新されたレポート ビューアー web パーツは、追加の機能を提供します。

* 特定のツール バー ボタンの表示/非表示
* レポート パラメーターの値を上書き
* フィルター web パーツをレポート パラメーターに接続します。

## <a name="download-the-report-viewer-web-part-solution-package"></a>レポート ビューアー web パーツのソリューション パッケージをダウンロードします。

レポート ビューアー web パーツは、Microsoft ダウンロード センターで使用可能なです。

[レポート ビューアー web パーツのソリューション パッケージをダウンロードします。](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>考慮事項と制約

表示される項目は、更新されたレポート ビューアー web パーツに固有です。

* Web パーツでのみ使用できます*クラシック*SharePoint ページ。
* のみの改ページ調整された (RDL) レポートは、レポート ビューアー web パーツ内に埋め込むためサポートされています。 使用することができますを Power BI のレポートまたはモバイル レポートを埋め込むには検索する場合、 *rs: 埋め込む = true* URL パラメーター。

## <a name="next-steps"></a>次の手順

更新されたレポート ビューアー web パーツで開始するを参照してください。 [SharePoint サイト上のレポート ビューアー web パーツを展開](deploy-report-viewer-web-part.md)です。

