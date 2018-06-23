---
title: '配置のチェックリスト: 既存の SharePoint ファームに Reporting Services のインストール |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 436b4c3d-3f2f-464a-be7e-5c051d9ffb8f
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d13c0329073781f54ac02b653b15ead4959bd96e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084926"
---
# <a name="deployment-checklist-install-reporting-services-into-an-existing-sharepoint-farm"></a>配置のチェック リスト: 既存の SharePoint ファームへの Reporting Services のインストール
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint レポート サーバーは、新しい SharePoint ファーム、または既存の SharePoint ファームにインストールできます。 このトピックは、可能なシナリオおよびインストールするためのベスト プラクティスについて説明します。[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]にし、既存の SharePoint ファーム。  
  
## <a name="prerequisites"></a>前提条件  
 セットアップを実行する前に、次の情報を確認します。  
  
|手順|リンク|  
|----------|----------|  
|レポート サーバーを配置する際に使用するアカウントを作成または識別します。 レポート サーバー サービスのサービス アカウントと、レポート サーバー データベースに接続するための資格情報が必要になります。||  
|インスタンスを決定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レポート サーバー データベースをホストします。 ローカルまたはリモート インスタンスを使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 レポートに見合う記憶域容量があるコンピューターのインスタンスを選択してください。||  
|(省略可能) サブスクリプションにレポート サーバーの電子メールを使用する場合は、組織の電子メール サービスを行う SMTP サーバーまたはゲートウェイの名前を調べます。|[レポート サーバー電子メール配信用に構成&#40;SSRS 構成マネージャー&#41;](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)|  
|注: 以前の CTP リリースからコンピューターをアップグレードするかどうかは[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]と構成ファイルに独自の変更を加えて、次へのアップグレード、構成ファイルに同じ変更を加える必要がある[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 影響を受けるファイルが**web.config**と**client.config**です。||  
  
## <a name="installation-scenarios"></a>インストールのシナリオ  
 次の表をインストールするときに、考えられるシナリオを示して[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]にし、既存の SharePoint ファーム。 ローカル モードでレポートと統合することがなく、SharePoint ドキュメント ライブラリからローカルに表示するのには、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポート サーバー。 SharePoint 製品では [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインは必須ですが、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーは必須ではありません。 ローカル モードの詳細については、「[レポート ビューアーでのローカル モードと接続モードのレポート、レポート ビューアーで&#40;Reporting Services SharePoint モードの&#41;](../../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)と[SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)です。  
  
|構成の開始|ワークフロー|構成の終了|コメント|  
|----------------------------|--------------|--------------------------|--------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ローカル モードで|インストール|接続モードの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]||  
|接続モード[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|インプレース アップグレード|接続モードの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]||  
|接続モード[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|移行|接続モードの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]||  
  
## <a name="installation-and-in-place-upgrade-checklist"></a>インストールとインプレース アップグレードのチェック リスト  
 次の表は、インストール時に確認および使用する必要がある手順、ツール、および情報をまとめたものです。  
  
|手順|リンク|  
|----------|----------|  
|**インストールと初期構成**||  
|すべての Web フロントエンド (WFE) コンピューターに SharePoint アドインをインストールします。|[ファームへの Reporting Services Web フロントエンドの追加](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|SQL Server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services とデータベース エンジンをインストールします。|[SharePoint 2010 用 Reporting Services の SharePoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|少なくとも 1 つの SSRS サービス アプリケーションを作成し、サービス アプリケーションの関連付けを構成します。|「サービス アプリケーション」セクションを参照して[Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|**追加の構成**||  
|ドキュメント ライブラリに SSRS のコンテンツの種類を追加します。|[レポート サーバー コンテンツ タイプをライブラリに追加&#40;Reporting Services の SharePoint 統合モード&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)|  
|SQL Server エージェントを準備します。|[SSRS サービス アプリケーションを使用するためのサブスクリプションと警告の準備](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)|  
|サービス アプリケーションの電子メール設定を構成します。|[サービス アプリケーション、Reporting Services の電子メールを構成する&#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|Claims to Windows Token Service (C2WTS) を構成します。|[Claims to Windows Token Service &#40;C2WTS&#41;と Reporting Services](../../../2014/sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)|  
  
## <a name="migration-checklist"></a>移行のチェック リスト  
 次に、既存のインストールから新規インストールに移行する場合の基本的な手順の一覧を示します。  
  
|手順|リンク|  
|----------|----------|  
|新規サーバーをインストールおよび構成します。 これには、次の内容が含まれます。<br /><br /> SharePoint 製品準備ツール<br /><br /> SharePoint 2010 製品<br /><br /> SharePoint 2010 SP1<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード<br /><br /> SharePoint 2010 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドイン|[SharePoint 2010 用 Reporting Services の SharePoint モードのインストール](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|少なくとも 1 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを作成します。||  
|バックアップ[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]データベース||  
|バックアップ[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]暗号化キー||  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベースと暗号化キーを復元します。||  
|すべての web アプリケーションを新規にマップ[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]サービス アプリケーション|これで新しいインストールが **機能**します。|  
|古いサーバーの統合 URL を削除します。|SharePoint サーバーの全体管理の **[アプリケーションの全般設定]** ページで、 **[Reporting Services 統合]** をクリックします。|  
|必要に応じて、古いインストールから [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアンインストールします。||  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>参照  
 [Reporting Services の SharePoint モードのインストール&#40;SharePoint 2010 および SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [SharePoint 2010 ファームで SQL Server BI 機能の使用に関するガイダンス](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)   
 [SharePoint、Reporting Services サーバー、アドインのサポートされる組み合わせ&#40;SQL Server 2014&#41;](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
  