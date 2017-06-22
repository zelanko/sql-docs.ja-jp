---
title: "レポート ビューアー Web パーツのプログラミングに SharePoint 統合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6e176aafa062c1184ff120cc1e886b9f5e244712
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>SharePoint 統合でのレポート ビューアー Web パーツのプログラミング
  レポート ビューアー Web パーツは、サーバー コントロールは、開発者はカスタムの SharePoint アプリケーションを作成するパブリック アプリケーション プログラミング インターフェイス (API) のセットを含むです。 レポートのパスと Web パーツ接続を使用してレポート ビューアー Web パーツのパラメーターを指定するカスタム Web パーツを作成することができます。 Web パーツをカスタム SharePoint Web パーツ ページに埋め込み、パブリック API を使用してカスタマイズすることもできます。  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>レポート ビューアー Web パーツとカスタム Web パーツとの接続  
 レポート ビューアー Web パーツは、実装する SharePoint Web パーツに接続するコンシューマー<xref:System.Web.UI.WebControls.WebParts.IWebPartRow>または T:Microsoft.SharePoint.WebPartPages.IFilterValues です。 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> Web パーツなど、**ドキュメント**Web パーツはレポート ビューアー Web パーツと同じ Web パーツ ページに配置されたレポート ビューアー Web パーツにレポート パスを指定できます。 同様に、T:Microsoft.SharePoint.WebPartPages.IFilterValues Web パーツなど、**テキスト フィルター**または**フィルターの選択**、レポート ビューアー Web パーツと同じ Web パーツ ページに配置されたレポート ビューアー Web パーツにレポート パラメーターを指定できます。  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>レポート パス プロバイダーと IWebPartRow の実装  
 Web パーツ接続を通じてレポート ビューアー Web パーツにレポートのパスを指定するには、次の手順に従います。  
  
1.  <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> インターフェイスを実装する Web パーツを作成します。  
  
2.  Web パーツを同じ Web パーツ ページにレポート ビューアー Web パーツとして追加します。  
  
3.  Web ベースの Web パーツ デザイン ユーザー インターフェイスで Web パーツをレポート ビューアー Web パーツに接続します。  
  
    > [!NOTE]  
    >  いずれかを接続することができますのみ<xref:System.Web.UI.WebControls.WebParts.IWebPartRow>一度に、するには、レポート ビューアー Web パーツを Web パーツ接続できません。 どちらも、<xref:System.Web.UI.WebControls.WebParts.IWebPartRow>を同時にレポート ビューアー Web パーツの T:Microsoft.SharePoint.WebPartPages.IFilterValues Web パーツと Web パーツ。  
  
 <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> 、T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart で正しく動作する Web パーツ、次を実行する必要があります、<xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A>メソッド。  
  
-   <xref:System.Data.DataRowView> オブジェクトを入力パラメーターとして使用してコールバック メソッドを呼び出します。  
  
-   <xref:System.Data.DataRowView> オブジェクトに、レポート パスを含む "DocUrl" という列が含まれるようにします。  
  
    > [!NOTE]  
    >  [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 用アドインのレポート ビューアー Web パーツでは、"FileRef" 列を使用するレポート パスを受信することもできます。  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>レポート パラメーター プロバイダーと IFilterValues の実装  
 T:Microsoft.SharePoint.WebPartPages.IFilterValues を実装する Web パーツは、レポート ビューアー Web パーツに 1 つのパラメーター値を指定できます。 レポート ビューアー Web パーツに送信されるパラメーター値には、レポート定義で指定された、レポート パラメーターに対する制限と同じ制限 (データ型、有効な値など) が課されます。  
  
 レポート ビューアー Web パーツにレポート パラメーターを指定するには、次の手順に従います。  
  
1.  T:Microsoft.SharePoint.WebPartPages.IFilterValues インターフェイスを実装する Web パーツを作成します。  
  
2.  Web パーツを T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart と同じページに追加します。  
  
3.  Web ベースの Web パーツ デザイン ユーザー インターフェイスでは、レポート ビューアー Web パーツに T:Microsoft.SharePoint.WebPartPages.IFilterValues Web パーツを接続します。  
  
    > [!NOTE]  
    >  複数の T:Microsoft.SharePoint.WebPartPages.IFilterValues Web パーツは、一度にレポート ビューアー Web パーツに接続できます。 ただし、両方が接続できない、<xref:System.Web.UI.WebControls.WebParts.IWebPartRow>を同時にレポート ビューアー Web パーツの T:Microsoft.SharePoint.WebPartPages.IFilterValues Web パーツと Web パーツ。  
  
  
