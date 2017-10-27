---
title: "レポート サーバーと SharePoint の Power View 統合機能のアクティブ化 |Microsoft ドキュメント"
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
ms.openlocfilehash: e97378914a59fab938fc3e4c7926847effcffc94
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="activate-the-report-server-and-power-view-integration-features-in-sharepoint"></a>レポート サーバーと SharePoint の Power View 統合機能のアクティブ化します。

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  インストールした後、Reporting Services サイト コレクションの機能は既定でアクティブ化、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] SharePoint 製品用アドインです。 一部の状況では、機能を手動でアクティブ化する必要があります。  

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

 SharePoint 製品のインストール後に SharePoint 2010 製品用 Reporting Services アドインをインストールする場合、レポート サーバーの統合機能と Power View の統合機能はでのみアクティブ化ルート サイト コレクション。 他のサイト コレクション機能を手動でアクティブ化する必要があります。 サイト コレクションがある場合など、 **http://[my サーバー名] [サイト コレクション name]/sites/** Reporting Services サイト コレクションの機能を手動でアクティブ化する必要があります。  
  
 ルート サイト コレクションがない場合は、Reporting Services アドインがログには、次のようなメッセージ。  
  
 "SharePoint Web アプリケーション 80 にはルート サイト コレクションがありません"  
  
 メッセージはアドインのインストール ログで、"RS_SP # .log"# には、増分する番号が見つかりました。 ログ ファイルが見つかると、現在のユーザーの Temp フォルダーに、たとえば C:\Users\\[ユーザー名] \AppData\Local\Temp です。アドインのインストール方法の詳細については、「 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。  

## <a name="activate-the-report-server-and-power-view-integration-site-collection-features"></a>レポート サーバーと Power View の統合サイト コレクション機能をアクティブ化します。
  
1.  Reporting Services の機能アクティブなサイトにブラウザーを開きます。  
  
2.  **[サイトの操作]**をクリックします。  
  
3.  **[サイトの設定]**をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの統合機能]** または **[Power View 統合機能]** を見つけます。  
  
6.  **[アクティブ化]**をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]**をクリックする点を除き、同じ手順を実行します。  
  
## <a name="activate-or-deactivate-reporting-services-central-administration-site-collection-feature"></a>アクティブ化または Reporting Services の非アクティブ化サーバーの全体管理サイト コレクション機能
  
1.  ブラウザーで SharePoint サーバーの全体管理を開きます。  
  
2.  **[サイトの操作]**をクリックします。  
  
3.  **[サイトの設定]**をクリックします。  
  
4.  [サイト コレクションの管理] グループで **[サイト コレクションの機能]** をクリックします。  
  
5.  一覧で **[レポート サーバーの全体管理機能]** を見つけます。  
  
6.  **[アクティブ化]**をクリックします。  
  
 機能を非アクティブ化するには、 **[アクティブ化]** ではなく **[非アクティブ化]**をクリックする点を除き、同じ手順を実行します。  
  
## <a name="next-steps"></a>次の手順

機能をアクティブ化した後、サーバーの統合を続行できます。

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

