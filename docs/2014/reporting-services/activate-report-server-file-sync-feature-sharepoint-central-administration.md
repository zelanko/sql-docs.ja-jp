---
title: SharePoint サーバーの全体管理でレポート サーバー ファイル同期機能をアクティブ化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 83ffe3e16bad4fdc1c60a818dd7f07bd47e00cb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177932"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバー ファイル同期機能では、SharePoint イベント ハンドラーを利用して、レポート サーバー カタログをドキュメント ライブラリのアイテムと同期します。 この機能は、ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合に役立ちます。 ファイル同期機能がアクティブになっていない場合、コンテンツの同期は行われますが、その頻度が下がります。  
  
 インストールした後に、ファイル同期機能を SharePoint サイトの管理でアクティブ化できます、 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] SharePoint 製品用アドインです。  
  
 この機能は、サイトごとに手動でアクティブ化および非アクティブ化できますが、サイト コレクション レベルではアクティブ化および非アクティブ化することはできません。  
  
## <a name="prerequisites"></a>前提条件  
 SharePoint 用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。 アドインがインストールされていない場合は、ファイル同期機能がサイト機能の一覧に表示されません。  
  
 インストールを確認するには、インストールされたアプリケーションの一覧を表示[!INCLUDE[msCoName](../includes/msconame-md.md)]Windows**コントロール パネルの **です。 場合、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]アドインがインストールされている、レポート サーバー ファイル同期機能をアクティブ化するのには、このトピックの手順に従います。  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>サイトの Reporting Services ファイル同期機能をアクティブ化または非アクティブ化するには  
  
1.  サイトのメイン ページから、 **[サイトの操作]** メニューをクリックし、 **[サイトの設定]** をクリックします。  
  
2.  **[サイトの操作]** で、 **[サイト機能の管理]** をクリックします。  
  
3.  一覧で **[レポート サーバー ファイル同期]** を見つけます。  
  
4.  **[アクティブ化]** をクリックします。  
  
> [!NOTE]  
>  レポート サーバー ファイル同期機能を非アクティブ化するには、 **[非アクティブ化]** をクリックする点を除き、同じ手順を実行します。  
  
## <a name="see-also"></a>参照  
 [レポート パーツのトラブルシューティング&#40;レポート ビルダーおよび SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [レポート サーバーと Power View Integration Features in SharePoint のアクティブ化します。](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [インストールまたは Reporting Services アドインを SharePoint のアンインストール&#40;SharePoint 2010 および SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [インストールまたは Reporting Services アドインを SharePoint のアンインストール&#40;SharePoint 2010 および SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  