---
title: SharePoint モードのインストールの Reporting Services (SharePoint 2010 および SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- default configuration [Reporting Services]
- installing Reporting Services, SharePoint integrated mode
- installation options [Reporting Services]
ms.assetid: ac6cba68-2665-4a39-8fa3-cb7d7e6723c0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef049b4ded6408e651d5ec2c3db99c10bf7c27b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108766"
---
# <a name="reporting-services-sharepoint-mode-installation-sharepoint-2010-and-sharepoint-2013"></a>Reporting Services SharePoint モードのインストール (SharePoint 2010 および SharePoint 2013)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]sharepoint モードのは、および[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] sharepoint 製品に基づいて、レポートの生成と配信を提供するサーバーコンポーネントのコレクションです。  
  
 SharePoint モードで [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を実行すると、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] とデータの警告機能が表示されます。 SharePoint モードの機能の詳細については、 [Reporting Services レポートサーバー](../reporting-services-report-server.md)の「機能のサポートと動作の違い」を参照してください。  
  
 SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に必要な基本的なインストールは 2 つあります。  
  
|インストール|説明|  
|------------------|-----------------|  
|SharePoint 製品用[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|アドインでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ユーザー インターフェイス (UI) ページと機能を SharePoint Web フロントエンド サーバーにインストールします。 UI 機能には、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]、SharePoint サーバーの全体管理の管理ページ、SharePoint ドキュメント ライブラリ内で使用される機能ページ、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ警告ページが含まれます。|  
|SharePoint [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードでインストールされたレポートサーバー|レポート サーバーは、データとレポートの処理と表示に加え、サブスクリプションとデータ警告処理も処理します。 SharePoint モードのレポート サーバーは、SharePoint 共有サービスとして構築、インストールされています。|  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をインストールするには、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール メディアを使用します。  
  
 高度な展開シナリオの手順については、「[配置のチェックリスト: Reporting Services、Power View、および PowerPivot for SharePoint](../../sql-server/install/deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)および[配置のチェックリスト: 既存の SharePoint ファームへの Reporting Services のインストール](../../sql-server/install/deployment-checklist-install-reporting-services-existing-sharepoint-farm.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [サポートされている SharePoint と Reporting Services Server およびアドイン &#40;SQL Server 2014 の組み合わせ&#41;](supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
 [SharePoint 2013 用 Reporting Services の SharePoint モードのインストール](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md)  
  
 [SharePoint 2010 用 Reporting Services SharePoint モードのインストール](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)  
  
 [Sharepoint &#40;sharepoint 2010 および SharePoint 2013 の Reporting Services アドインをインストールまたはアンインストール&#41;](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
 [SharePoint 製品用 Reporting Services アドインの検索場所](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
 [ファームへのレポート サーバーの追加 &#40;SSRS スケールアウト&#41;](add-an-additional-report-server-to-a-farm-ssrs-scale-out.md)  
  
 [ファームへの Reporting Services Web フロントエンドの追加](add-an-additional-reporting-services-web-front-end-to-a-farm.md)  
  
 [Reporting Services サービス アプリケーションの電子メールの構成 (SharePoint 2010 および SharePoint 2013)](configure-e-mail-for-a-reporting-services-service-application.md)  
  
 [SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](provision-subscriptions-and-alerts-for-ssrs-service-applications.md)  
  
 [Windows トークンサービスに対するクレーム &#40;C2WTS&#41; と Reporting Services](../../sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)  
  
## <a name="see-also"></a>参照  
 [データ警告のアーキテクチャとワークフロー](../reporting-services-data-alerts.md#AlertingWF)   
 [警告管理者用のデータ警告マネージャー](../data-alert-manager-for-alerting-administrators.md)  
  
  
