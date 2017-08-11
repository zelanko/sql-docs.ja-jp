---
title: "Verify a Reporting Services のインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/03/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- checking report server installations
- verifying report server installations
- Report Designer [Reporting Services], verifying installations
- installing Reporting Services, verifying installations
- Report Manager [Reporting Services], verifying installations
- report servers [Reporting Services], verifying installations
- Setup [Reporting Services], verifying installations
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
caps.latest.revision: 45
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a5849b6240557cd1682d08210f256e0edabfa70b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="verify-a-reporting-services-installation"></a>Reporting Services のインストール状態の検証
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーは、ネイティブまたは SharePoint の 2 つのモードのうちのいずれかのモードでインストールできます。 インストールの確認に必要な手順は、レポート サーバーのモードによって変わります。  
  
##  <a name="bkmk_sharepointmode"></a> SharePoint モードのインストールの確認  
  
### <a name="to-verify-the-reporting-services-service"></a>Reporting Services サービスを確認するには  
  
1.  SharePoint サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。  
  
2.  **SQL Server Reporting Services サービス** がインストールされ、 **実行中** の状態であることを確認します。  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスが一覧に表示されない場合は、サービスがインストールされていることを確認します。 詳細については、「 [SharePoint モードでの最初のレポート サーバーのインストール](http://msdn.microsoft.com/en-us/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538)」を参照してください。  
  
### <a name="to-verify-the-service-application"></a>サービス アプリケーションを確認するには  
  
1.  サーバーの全体管理から確認するには、少なくとも 1 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを使用します。 **[アプリケーション構成の管理]** で **[サービス アプリケーションの管理]** をクリックします。  
  
2.  種類が **[SQL Server Reporting Services サービス アプリケーション]** のサービス アプリケーションと、対応するアプリケーション プロキシがあることを確認します。  
  
3.  サービス アプリケーションの名前の **近く** をクリックし、SharePoint ツール バーの **[プロパティ]** をクリックします。  サービス アプリケーションの名前をクリックすると、プロパティ ページではなく、サービス アプリケーションの管理ページが開きます。  
  
4.  必要な Web アプリケーションを指すように **[Web アプリケーションの関連付け]** が構成されていることを確認します。  
  
### <a name="to-verify-the-site-collection-feature"></a>サイト コレクション機能を確認するには  
  
1.  サイトの設定の **[サイト コレクションの管理]** で **[サイト コレクションの機能]** をクリックします。  
  
2.  **[レポート サーバーの統合機能]** がアクティブであることを確認します。  
  
### <a name="to-verify-reporting-server-content-types"></a>レポート サーバー コンテンツの種類を確認するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー コンテンツの種類を確認または追加するには、「 [Add Reporting Services Content Types to a SharePoint Library (SharePoint ライブラリへの Reporting Services のコンテンツの種類の追加)](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)」を参照してください。  
  
### <a name="to-verify-you-can-launch-report-builder"></a>レポート ビルダーが起動できることを確認するには  
  
1.  ドキュメント ライブラリから、SharePoint リボンの **[ドキュメント]** をクリックします。  
  
2.  **[新しいドキュメント]** をクリックし、 **[レポート ビルダー レポート]**をクリックします。 このオプションが表示されない場合は、レポート サーバー コンテンツの種類をライブラリに追加するための前の手順を確認してください。  
  
### <a name="create-a-basic-report"></a>基本的なレポートの作成  
  
1.  SharePoint ドキュメント ライブラリ内で、タイトルなどに使用するテキスト ボックスのみを含む基本的な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを作成します。 このレポートには、データ ソースやデータセットは何も含めません。 目標は、レポート ビルダーを開いて基本的なレポートをプレビューできることの確認です。  
  
2.  レポートをドキュメント ライブラリに保存し、ライブラリからレポートを実行します。 レポート ビルダーでレポートを作成する方法の詳細については、「 [レポート ビルダーの起動](http://msdn.microsoft.com/en-us/8c8c7d2e-b315-418d-bf65-90e7685e4259)」を参照してください。  
  
### <a name="reporting-services-samples"></a>Reporting Services のサンプル  
  
1.  Reporting Services のチュートリアルのいずれかを完了します。 詳細については、次を参照してください。 [Reporting Services のチュートリアル & #40 です。SSRS &#41;](../../reporting-services/reporting-services-tutorials-ssrs.md).  
  
2.  CodePlex から AdventureWorks の作業のサンプル データベースと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サンプル レポートをダウンロードします。 詳細については、「 [AdventureWorks レポート サンプル](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home)」を参照してください。  
  
##  <a name="bkmk_nativemode"></a> ネイティブ モードのインストールの確認  
 既定の構成を使用してネイティブ モードでレポート サーバーをインストールする場合、セットアップでサーバーをインストールし、配置します。 いくつかの簡単なテストを行うことで、レポート サーバーが正常に配置されたかどうかを確認できます。 これらの手順を実行するには、ローカル管理者である必要があります。 他のユーザーがテストを実行する場合は、そのユーザーがレポート サーバーにアクセスできるように構成する必要があります。  
  
### <a name="to-verify-that-the-report-server-is-installed-and-running"></a>レポート サーバーが正常にインストールされ、実行されていることを確認するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを実行し、インストールしたレポート サーバー インスタンスに接続します。 [Web サービス URL] ページには、レポート サーバー Web サービスへのリンクが含まれています。 このリンクをクリックして、サーバーにアクセスできることを確認します。 レポート サーバー データベースが構成されていない場合は、リンクをクリックする前にレポート サーバー データベースを構成してください。  
  
2.  Services コンソール アプリケーションを開き、レポート サーバー サービスが実行されていることを確認します。 レポート サーバー サービスの状態を表示するには、 **[スタート]**ボタンをクリックし、 **[コントロール パネル]**をポイントして、 **[管理ツール]**をダブルクリックします。次に、 **[サービス]**をダブルクリックします。 サービスの一覧が表示されたら、 **[Report Server (MSSQLSERVER)]**までスクロールします。 状態が **[開始]**になっていることを確認してください。  
  
3.  ブラウザーを開き、アドレス バーにレポート サーバーの URL を入力します。 アドレスは、セットアップ時にレポート サーバーに指定したサーバー名と仮想ディレクトリ名で構成されます。 既定では、レポート サーバーの仮想ディレクトリ名は **ReportServer**です。 次の URL を使用するをレポート サーバーのインストールの確認: http://*\<コンピューター名 >*/ReportServer*\<_instance name >*です。 レポート サーバーを名前付きインスタンスとしてインストールした場合、URL は異なります。 URL の形式の詳細については、次を参照してください。[レポート サーバー Url の構成 & #40 です。SSRS 構成マネージャー &#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md). Windows Vista または Windows Server 2008 上のローカル管理者の場合を参照してください[のローカルの管理 &#40; ネイティブ モードのレポート サーバーを構成する。SSRS &#41;](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
4.  レポートを実行して、レポート サーバーの動作をテストします。 この手順では、チュートリアルからサンプル レポートを作成できます。 詳細については、次を参照してください[基本的なテーブル レポート &#40; を作成する。SSRS チュートリアル &#41;](../../reporting-services/create-a-basic-table-report-ssrs-tutorial.md).  
  
### <a name="to-verify-that-the-includessrswebportalincludesssrswebportalmd-is-installed-and-running"></a>[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] が正常にインストールされ、実行されていることを確認するには  
  
1.  ブラウザーを開き、アドレス バーに Web ポータルの URL を入力します。 このアドレスは、セットアップ時または Reporting Services 構成ツールの [Web ポータル URL] ページで [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] に対して指定したサーバー名と仮想ディレクトリ名で構成されます。 既定では、 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] の仮想ディレクトリは **Reports**です。 次の URL を使用して、 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] のインストール状態を確認できます。  
  
     http://*\<コンピューター名 >*/reports*\<_instance name >*です。  
  
2.  レポート サーバー データベースに定義が戻されるかどうかをテストするため、 [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] を使用して新しいフォルダーを作成するか、ファイルをアップロードします。 操作が成功した場合、接続は正しく機能しています。  
  
     詳細については、次を参照してください。 [Web ポータル & #40 です。SSRS ネイティブ モード &#41;](http://msdn.microsoft.com/en-us/7349e626-6ed5-4d21-b05f-cf042ad9ad70).  
  
### <a name="to-verify-that-report-designer-is-installed-and-running"></a>レポート デザイナーが正常にインストールされ、実行されていることを確認するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を開き、レポート サーバーのプロジェクトの種類に基づいて新しいプロジェクトを作成します。 レポート サーバー プロジェクト ウィザードを使用する方法については、次を参照してください。 [Reporting Services の SQL Server Data Tools & #40 です。SSDT &#41;](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md) SQL Server オンライン ブック。  
  
2.  サンプル レポートをインストールした場合は、サンプル レポート プロジェクト ファイルを開き、レポート サーバーにレポートをパブリッシュします。  
  
## <a name="see-also"></a>参照  
 [Reporting Services インストール時の問題解決](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [原因と Reporting Services エラーの解決方法](../../reporting-services/troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  

