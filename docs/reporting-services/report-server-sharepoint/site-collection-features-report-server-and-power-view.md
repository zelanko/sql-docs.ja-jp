---
title: "レポート サーバーと Power View Integration Features in SharePoint のアクティブ化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bca4115307f7bf9dab5ffc9d2ab02ababb209d65
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="site-collection-features---report-server-and-power-view"></a>サイト コレクション機能のレポート サーバーと Power View
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサイト コレクション機能は、通常、SharePoint 製品用の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] アドインをインストールすると、既定でアクティブ化されます。 場合によっては、この機能を手動でアクティブ化する必要があります。  
  
 SharePoint 製品のインストール後に SharePoint 2010 製品用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールした場合、レポート サーバーの統合機能と Power View の統合機能はルート サイト コレクションでのみアクティブ化されます。 他のサイト コレクションについては、この機能を手動でアクティブ化する必要があります。 たとえば、 **http://[my server name]/sites/[site collection name]** というサイト コレクションが存在する場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサイト コレクション機能を手動でアクティブ化する必要があります。  
  
 ルート サイト コレクションがない場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインによって、次のようなメッセージがログに記録されます。  
  
 "SharePoint Web アプリケーション 80 にはルート サイト コレクションがありません"  
  
 メッセージは、"RS_SP_#.log" (# は増加する値) という名前のアドイン インストール ログに記録されます。 ログ ファイルは、現在のユーザーの Temp フォルダー (例: C:\Users\\[user name]\AppData\Local\Temp) にあります。 アドインのインストール方法の詳細については、「 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。  
  
 このトピックの内容:  
  
-   [レポート サーバーと Power View の統合サイト コレクション機能をアクティブ化するには](#bkmk_features)  
  
-   [Reporting Services の全体管理のサイト コレクション機能をアクティブ化または非アクティブ化するには](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> レポート サーバーと Power View の統合サイト コレクション機能をアクティブ化するには  
  
1.  ブラウザーで、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の機能をアクティブ化するサイトを開きます。  
  
2.  **[サイトの操作]**をクリックします。  
  
3.  **[サイトの設定]**をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの統合機能]** または **[Power View 統合機能]** を見つけます。  
  
6.  **[アクティブ化]**をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]**をクリックする点を除き、同じ手順を実行します。  
  
##  <a name="bkmk_centraladmin"></a> Reporting Services の全体管理のサイト コレクション機能をアクティブ化または非アクティブ化するには  
  
1.  ブラウザーで SharePoint サーバーの全体管理を開きます。  
  
2.  **[サイトの操作]**をクリックします。  
  
3.  **[サイトの設定]**をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの全体管理機能]** を見つけます。  
  
6.  **[アクティブ化]**をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]**をクリックする点を除き、同じ手順を実行します。  
  
## <a name="next-steps"></a>次の手順  
 機能をアクティブ化した後、サーバーの統合を続行できます。  
  
## <a name="see-also"></a>参照  
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
