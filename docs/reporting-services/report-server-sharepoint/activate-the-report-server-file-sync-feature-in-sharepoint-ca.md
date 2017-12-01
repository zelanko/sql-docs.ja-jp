---
title: "SharePoint でレポート サーバー ファイル同期機能をアクティブにする | Microsoft Docs"
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
ms.openlocfilehash: b85d1541da8aa65bd3912310551cbc5d5ad26eea
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint"></a>SharePoint でレポート サーバー ファイル同期機能をアクティブにする

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー ファイル同期機能では、SharePoint イベント ハンドラーを利用して、レポート サーバー カタログをドキュメント ライブラリのアイテムと同期します。 この機能は、ユーザーがパブリッシュされたレポート アイテムを SharePoint ドキュメント ライブラリに頻繁に直接アップロードする場合に役立ちます。 ファイル同期機能がアクティブになっていない場合、コンテンツの同期は行われますが、その頻度が下がります。

> [!NOTE]
> SharePoint と Reporting Services の統合は、SQL Server 2016 以降では使用できません。
  
 ファイル同期機能は、SharePoint 製品用 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] アドインをインストールしてから SharePoint サイトの管理でアクティブ化できます。  
  
 この機能は、サイトごとに手動でアクティブ化および非アクティブ化できますが、サイト コレクション レベルではアクティブ化および非アクティブ化することはできません。  
  
## <a name="prerequisites"></a>前提条件

 SharePoint 用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールする必要があります。 アドインがインストールされていない場合は、ファイル同期機能がサイト機能の一覧に表示されません。  
  
 インストールを確認するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows の **コントロール パネル**でインストール済みアプリケーションの一覧を表示します。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインがインストールされている場合は、このトピックの手順に従ってレポート サーバー ファイル同期機能をアクティブ化できます。  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>サイトの Reporting Services ファイル同期機能をアクティブ化または非アクティブ化するには
  
1.  サイトのメイン ページから、 **[サイトの操作]** メニューをクリックし、 **[サイトの設定]**をクリックします。  
  
2.  **[サイトの操作]** で、 **[サイト機能の管理]**をクリックします。  
  
3.  一覧で **[レポート サーバー ファイル同期]** を見つけます。  
  
4.  **[アクティブ化]**をクリックします。  

> [!NOTE]
> レポート サーバー ファイル同期機能を非アクティブ化するには、 **[非アクティブ化]**をクリックする点を除き、同じ手順を実行します。

## <a name="see-also"></a>参照

 [レポート パーツのトラブルシューティング (レポート ビルダーおよび SSRS)](http://msdn.microsoft.com/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  

その他の質問 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
