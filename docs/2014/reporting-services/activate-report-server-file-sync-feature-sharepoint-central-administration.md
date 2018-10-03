---
title: SharePoint サーバーの全体管理でレポート サーバー ファイル同期機能をアクティブ化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8dcdfaf16f4e279ed39c46dab7d486f517854b52
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088412"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバー ファイル同期機能では、SharePoint イベント ハンドラーを利用して、レポート サーバー カタログをドキュメント ライブラリのアイテムと同期します。 この機能は、ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合に役立ちます。 ファイル同期機能がアクティブになっていない場合、コンテンツの同期は行われますが、その頻度が下がります。  
  
 インストールした後に、ファイル同期機能を SharePoint サイトの管理でアクティブにできる、 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] SharePoint 製品用アドイン。  
  
 この機能は、サイトごとに手動でアクティブ化および非アクティブ化できますが、サイト コレクション レベルではアクティブ化および非アクティブ化することはできません。  
  
## <a name="prerequisites"></a>前提条件  
 SharePoint 用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。 アドインがインストールされていない場合は、ファイル同期機能がサイト機能の一覧に表示されません。  
  
 インストールを確認するにインストールされているアプリケーションの一覧を表示[!INCLUDE[msCoName](../includes/msconame-md.md)]Windows**コントロール パネルの **します。 場合、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]アドインがインストールされている、レポート サーバー ファイル同期機能をアクティブ化するは、このトピックの手順に従います。  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>サイトの Reporting Services ファイル同期機能をアクティブ化または非アクティブ化するには  
  
1.  サイトのメイン ページから、 **[サイトの操作]** メニューをクリックし、 **[サイトの設定]** をクリックします。  
  
2.  **[サイトの操作]** で、 **[サイト機能の管理]** をクリックします。  
  
3.  一覧で **[レポート サーバー ファイル同期]** を見つけます。  
  
4.  **[アクティブ化]** をクリックします。  
  
> [!NOTE]  
>  レポート サーバー ファイル同期機能を非アクティブ化するには、 **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
## <a name="see-also"></a>参照  
 [レポート パーツのトラブルシューティング&#40;レポート ビルダーおよび SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [レポート サーバーと SharePoint の Power View の統合機能のアクティブ化します。](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [インストールまたはアンインストール、Reporting Services アドイン、SharePoint の&#40;SharePoint 2010 および SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [インストールまたはアンインストール、Reporting Services アドイン、SharePoint の&#40;SharePoint 2010 および SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
