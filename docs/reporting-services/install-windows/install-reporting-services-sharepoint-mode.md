---
title: "Reporting Services SharePoint モードのインストール | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "既定の構成 [Reporting Services]"
  - "Reporting Services のインストール, SharePoint 統合モード"
  - "インストール オプション [Reporting Services]"
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
caps.latest.revision: 35
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 35
---
# Reporting Services SharePoint モードのインストール
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポートの作成とドキュメント ライブラリでの表示、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サブスクリプションの電子メールを使用したレポートの配信、  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、データ アラート、レポート管理機能をすべて、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SharePoint ベースの配置で使用できます。 SharePoint モードの機能の詳細については、「[Reporting Services レポート サーバー](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)」の「サーバー モードごとの機能サポートと動作の違い」を参照してください。  
  
 SharePoint モードでの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、インストールする2 つの主な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコンポーネントがあります。  
  
|インストール|説明|  
|------------------|-----------------|  
|**レポート サーバー:** SharePoint モードでインストールされる [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー|レポート サーバーは、データとレポートの処理と表示に加え、サブスクリプションとデータ警告処理も処理します。 SharePoint モードのレポート サーバーは、SharePoint 共有サービスとして設計およびインストールされています。<br /><br /> **方法:** レポート サーバーをインストールするには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアを使用します。|  
|**アドイン:** SharePoint 製品用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン (**rssharepoint.msi**)。|アドインでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ユーザー インターフェイス (UI) ページと機能を SharePoint Web フロントエンド サーバーにインストールします。 UI 機能には、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint サーバーの全体管理の管理ページ、SharePoint ドキュメント ライブラリ内で使用される機能ページ、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ警告ページが含まれます。<br /><br /> **方法:** アドインは、Web ダウンロードまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアからインストールできます。 詳細については、「[SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。|  
  
## このセクションの内容  
 [SharePoint、Reporting Services サーバー、Reporting Services アドインのサポートされる組み合わせ &#40;SQL Server 2016&#41;](../../reporting-services/install-windows/supported combinations of sharepoint and reporting services server.md)  
  
 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [SharePoint モードでの最初のレポート サーバーのインストール](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md)  
  
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;](../../reporting-services/install-windows/add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [ファームへの Reporting Services Web フロントエンドの追加](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Reporting Services サービス アプリケーションの電子メールの構成 &#40;SharePoint 2013 および SharePoint 2016&#41;](http://msdn.microsoft.com/ja-jp/38fc34a6-aae7-4dde-9ad2-f1eee0c42a9f)  
  
 [SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Claims to Windows Token Service &#40;c2WTS&#41; と Reporting Services](../../reporting-services/install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## 参照  
 [データ警告のアーキテクチャとワークフロー](../../reporting-services/reporting-services-data-alerts.md#AlertingWF)   
 [警告管理者用のデータ警告マネージャー](../../reporting-services/data-alert-manager-for-alerting-administrators.md)  
  
  