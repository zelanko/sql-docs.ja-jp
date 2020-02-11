---
title: SharePoint でレポートサーバーと Power View 統合機能をアクティブ化する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e30ae6ea0e7fa314748c4da265650273c0a7d56e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66110024"
---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]サイトコレクション機能は、通常、SharePoint 製品用[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]アドインをインストールした後で、既定でアクティブになります。 場合によっては、この機能を手動でアクティブ化する必要があります。  
  
 SharePoint 製品のインストール後に SharePoint 2010 製品用の [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールした場合、レポート サーバーの統合機能と Power View の統合機能はルート サイト コレクションでのみアクティブ化されます。 他のサイト コレクションについては、この機能を手動でアクティブ化する必要があります。 たとえば、 **http://[my server name]/sites/[site collection name]** というサイト コレクションが存在する場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のサイト コレクション機能を手動でアクティブ化する必要があります。  
  
 ルート サイト コレクションがない場合は、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインによって、次のようなメッセージがログに記録されます。  
  
 "SharePoint Web アプリケーション 80 にはルート サイト コレクションがありません"  
  
 このメッセージは、"RS_SP_ # .log" という名前のアドインインストールログに記録されます。 # はインクリメントされた数値です。 ログファイルは、現在のユーザーの Temp フォルダー (たとえば、C:\Users\\[user name] \appdata\local\temp)) にあります。アドインのログオプションの詳細については、「sharepoint [2010 および sharepoint 2013&#41;&#40;の Reporting Services アドインのインストールまたはアンインストール](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。  
  
 このトピックの内容:  
  
-   [レポートサーバーと Power View 統合サイトコレクション機能をアクティブ化するには、次のようにします。](#bkmk_features)  
  
-   [Reporting Services の中央管理サイトコレクション機能をアクティブ化または非アクティブ化するには:](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a>レポートサーバーと Power View 統合サイトコレクション機能をアクティブ化するには、次のようにします。  
  
1.  ブラウザーで、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] の機能をアクティブ化するサイトを開きます。  
  
2.  
  **[サイトの操作]** をクリックします。  
  
3.  
  **[サイトの設定]** をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの統合機能]** または **[Power View 統合機能]** を見つけます。  
  
6.  **[アクティブ化]** をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
##  <a name="bkmk_centraladmin"></a>Reporting Services の中央管理サイトコレクション機能をアクティブ化または非アクティブ化するには:  
  
1.  ブラウザーで SharePoint サーバーの全体管理を開きます。  
  
2.  
  **[サイトの操作]** をクリックします。  
  
3.  
  **[サイトの設定]** をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの全体管理機能]** を見つけます。  
  
6.  **[アクティブ化]** をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
## <a name="next-steps"></a>次の手順  
 機能をアクティブ化した後、サーバーの統合を続行できます。  
  
## <a name="see-also"></a>参照  
 [Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
