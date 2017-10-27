---
title: "SQL Server Reporting Services レポート サーバーの構成と管理 |Microsoft ドキュメント"
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
ms.openlocfilehash: b521a0a2198d74c8766f18fb8d7a199b25005efe
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="configuration-and-administration-of-a-sql-server-reporting-services-report-server"></a>SQL Server Reporting Services レポート サーバーの構成と管理

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

SQL Server Reporting Services は、組織で利用するレポートの作成、配置、管理に役立つツールやサービスを豊富に備えたサーバー ベースのレポート プラットフォームです。プログラミング機能を使用して、レポート作成機能を拡張したりカスタマイズしたりすることもできます。 レポート環境を SharePoint 製品と統合すると、SharePoint サイトによって提供されるコラボレーション環境を使用するメリットを実感できます。

> [!NOTE]
> SQL Server 2016 より後に、SharePoint と reporting Services の統合を使用できなくします。

次のセクションを使用して、概念、配置シナリオ、手順、および Reporting Services 環境を SharePoint 製品またはテクノロジと統合するための詳細を理解するのに役立ちます。  
  
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
  
 Reporting Services の概要については、次を参照してください。 [Reporting Services](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブック。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネント、ツール、およびリソースについては、 [SQL Server オンライン ブック](../../sql-server/sql-server-technical-documentation.md)を参照してください。  

その他のご不明な点は、 [Reporting Services のフォーラムに質問してみてください](http://go.microsoft.com/fwlink/?LinkId=620231)

