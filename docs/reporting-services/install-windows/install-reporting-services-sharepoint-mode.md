---
title: "Install Reporting Services SharePoint Mode |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 17effa28932798a3cd35427a0a7104d4aa355b56
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="install-reporting-services-sharepoint-mode"></a>Reporting Services SharePoint モードのインストール

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services SharePoint で、有効にレポートの作成とドキュメント ライブラリでの表示[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]電子メールを使用したレポートのサブスクリプションの配信[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]のデータ アラート、およびすべての展開でのレポート管理機能に基づいて[!INCLUDE[msCoName](../../includes/msconame-md.md)]SharePoint。 SharePoint モードの機能に関する詳細についてを参照してください「機能サポートと動作の違いによってサーバー モード」で[Reporting Services レポート サーバー](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)です。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

SharePoint モードでの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、インストールする2 つの主な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンポーネントがあります。  

|インストール|説明|  
|------------------|-----------------|  
|**レポート サーバー:** SharePoint モードでインストールされる [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー|レポート サーバーは、データとレポートの処理と表示に加え、サブスクリプションとデータ警告処理も処理します。 SharePoint モードのレポート サーバーは、SharePoint 共有サービスとして設計およびインストールされています。<br /><br /> **方法:** レポート サーバーをインストールするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアを使用します。|  
|**アドイン:** SharePoint モードでインストールされる [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン ( **rssharepoint.msi**)。|アドインでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ユーザー インターフェイス (UI) ページと機能を SharePoint Web フロントエンド サーバーにインストールします。 UI 機能には、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint サーバーの全体管理の管理ページ、SharePoint ドキュメント ライブラリ内で使用される機能ページ、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ警告ページが含まれます。<br /><br /> **方法:**  アドインは、Web ダウンロードまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアからインストールできます。 詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。|  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SharePoint、Reporting Services サーバー、Reporting Services アドインのサポートされる組み合わせ &#40;SQL Server 2016&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [SharePoint モードでの最初のレポート サーバーのインストール](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [ファームへの Reporting Services Web フロントエンドの追加](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Reporting Services サービス アプリケーションの電子メールの構成 &#40;SharePoint 2013 および SharePoint 2016&#41;](http://msdn.microsoft.com/en-us/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Claims to Windows Token Service &#40;c2WTS&#41; と Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  

## <a name="next-steps"></a>次の手順

 [データ警告のアーキテクチャとワークフロー](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [警告管理者用のデータ警告マネージャー](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
