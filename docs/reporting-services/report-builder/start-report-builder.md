---
title: "レポート ビルダーの起動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レポート ビルダー, 起動"
  - "レポート ビルダーの起動"
  - "SharePoint 統合 [Reporting Services], レポート ビルダーの起動"
  - "レポート ビルダーの起動"
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 56
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 56
---
# レポート ビルダーの起動
  Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] は、スタンドアロンのレポート作成環境です。 この環境を使用すると、ページ分割されたレポートを作成して、ネイティブ モードまたは SharePoint 統合モードでインストールされた [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] にパブリッシュできます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web ポータルまたは SharePoint 統合モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] から [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] を初めて起動する場合は、Microsoft ダウンロード センターからダウンロードするように求められます。 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 ユーザー自身、または管理者が [Microsoft ダウンロード センターからユーザーのコンピューターにレポート ビルダーをインストールする](http://go.microsoft.com/fwlink/?LinkID=219138)こともできます。 詳細については、「[レポート ビルダーをインストールする](../../reporting-services/install-windows/install-report-builder.md)」の「Systems Manager Server を使用したレポート ビルダーのインストール」を参照してください。
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインストール時にインストールされません。別途ダウンロードして、インストールする必要があります。  
  
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] を Web ポータルまたは SharePoint サイトから起動したときに [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] の以前のバージョンが開く場合は、Web ポータルまたは SharePoint サイト上のバージョンを更新できる管理者に相談してください。  
  
## [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] を [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Web ポータルから起動するには  
  
1.  Web ブラウザーで、アドレス バーにレポート サーバーの URL を入力します。 既定の URL は http://\<*servername*>/reports です。  
  
2.  Web ポータルの上部のバーで、**[新規]** > **[ページ分割されたレポート]** の順に選択します。  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     初回の実行時は、[レポート ビルダーをインストール](../../reporting-services/install-windows/install-report-builder.md)するよう求められます。 
  
     次回からは、[!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] が開いて、ページ分割されたレポートを作成したり、レポート サーバー上のレポートを開いたりできます。  
  
## [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] を SharePoint 統合モードで起動するには  
  
1.  目的のライブラリがある SharePoint サイトに移動します。  
  
2.  ライブラリを開きます。  
  
3.  **[ドキュメント]**をクリックします。  
  
4.  **[新しいドキュメント]** メニューの **[レポート ビルダー レポート]**をクリックします。  
  
     初めてこの項目を選択すると、SQL Server [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] ウィザードが起動します。 詳細については、「 [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) 」を参照してください。  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] が開き、改ページ調整されたレポートを作成したり、レポート サーバー上のレポートを開いたりできます。  
  
     **注**   **[新しいドキュメント]** メニューに **[レポート ビルダー レポート]**、 **[レポート ビルダーのモデル]**、または **[レポート データ ソース]**が表示されない場合は、それらのコンテンツの種類を SharePoint ライブラリに追加する必要があります。 詳細については、「[SharePoint ライブラリへの Reporting Services のコンテンツの種類の追加](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)」を参照してください。  
  
## 参照  
 [SQL Server 2016 のレポート ビルダー](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [レポート ビルダーの既定のオプションを設定する](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  
  
  