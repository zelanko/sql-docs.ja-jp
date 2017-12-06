---
title: "SQL Server Reporting Services レポート サーバーの構成と管理 | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-server-sharepoint
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 35995be90a36fa2037d4f571b7af509afb271871
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="configuration-and-administration-of-a-sql-server-reporting-services-report-server"></a>SQL Server Reporting Services レポート サーバーの構成と管理

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services は、組織で利用するレポートの作成、配置、管理に役立つツールやサービスを豊富に備えたサーバー ベースのレポート プラットフォームです。プログラミング機能を使用して、レポート作成機能を拡張したりカスタマイズしたりすることもできます。 レポート環境を SharePoint 製品と統合すると、SharePoint サイトによって提供されるコラボレーション環境を使用するメリットを実感できます。

> [!NOTE]
> SharePoint と Reporting Services の統合は、SQL Server 2016 以降では使用できません。

次のセクションでは、Reporting Services 環境と SharePoint 製品またはテクノロジとの統合に関する概念、配置シナリオ、手順などについて説明します。  
  
-   SharePoint ドキュメント ライブラリのメニュー オプション  
  
    -   [SharePoint ユーザー用のデータ警告マネージャー](../../reporting-services/data-alert-manager-for-sharepoint-users.md)  
  
    -   [Create and Manage Subscriptions for SharePoint Mode Report Servers](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)  
  
    -   [レポート データ ソース内の資格情報を SharePoint サイトから更新する](../../reporting-services/report-data/update-credentials-in-report-data-sources-from-a-sharepoint-site.md)  
  
    -   [共有データセットを管理する](../../reporting-services/report-data/manage-shared-datasets.md)  
  
    -   [パブリッシュ済みレポートのパラメーターの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)  
  
    -   [処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
    -   [[キャッシュ更新オプション] &#40;レポート マネージャー&#41;](http://msdn.microsoft.com/library/227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6)  
  
-   [Reporting Services サイト コレクション機能](../../reporting-services/report-server-sharepoint/site-collection-features-reporting-services.md)  
  
-   [SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)  
  
-   [Reporting Services のサイト設定とサイト機能 &#40;SharePoint モード&#41;](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)  
  
-   [SharePoint サーバーの全体管理でレポート サーバーのファイル同期機能をアクティブにする](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  
  
-   [SharePoint ライブラリへの Reporting Services のコンテンツの種類の追加](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
-   [レポート ビューアーでのローカル モードと接続モードのレポート &#40;Reporting Services の SharePoint モード&#41;](../../reporting-services/report-server-sharepoint/local-mode-vs-connected-mode-reports-in-the-report-viewer.md)  
  
-   [SharePoint ライブラリへのドキュメントのアップロード &#40;Reporting Services の SharePoint モード&#41;](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)  
  
-   [処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
 Reporting Services に関する一般的な情報については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[Reporting Services](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネント、ツール、およびリソースについては、 [SQL Server オンライン ブック](../../sql-server/sql-server-technical-documentation.md)を参照してください。  

その他のご不明な点は、 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)
