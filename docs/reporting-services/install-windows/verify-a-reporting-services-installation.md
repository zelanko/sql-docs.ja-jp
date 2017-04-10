---
title: "Reporting Services のインストール状態の検証 | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インストールされているレポート サーバーの確認"
  - "インストールされているレポート サーバーの検証"
  - "レポート デザイナー [Reporting Services], インストール状態の検証"
  - "Reporting Services のインストール, インストール状態の検証"
  - "レポート マネージャー [Reporting Services], インストール状態の検証"
  - "レポート サーバー [Reporting Services], インストール状態の検証"
  - "セットアップ [Reporting Services], インストール状態の検証"
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
caps.latest.revision: 45
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 45
---
# Reporting Services のインストール状態の検証
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーは、ネイティブまたは SharePoint の 2 つのモードのうちのいずれかのモードでインストールできます。 インストールの確認に必要な手順は、レポート サーバーのモードによって変わります。  
  
##  <a name="bkmk_sharepointmode"></a> SharePoint モードのインストールの確認  
  
### Reporting Services サービスを確認するには  
  
1.  SharePoint サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。  
  
2.  **SQL Server Reporting Services サービス** がインストールされ、 **実行中** の状態であることを確認します。  
  
     [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスが一覧に表示されない場合は、サービスがインストールされていることを確認します。 詳細については、「[SharePoint モードでの最初のレポート サーバーのインストール](http://msdn.microsoft.com/ja-jp/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538)」を参照してください。  
  
### サービス アプリケーションを確認するには  
  
1.  サーバーの全体管理から確認するには、少なくとも 1 つの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションを使用します。 **[アプリケーション構成の管理]** で **[サービス アプリケーションの管理]** をクリックします。  
  
2.  種類が **[SQL Server Reporting Services サービス アプリケーション]** のサービス アプリケーションと、対応するアプリケーション プロキシがあることを確認します。  
  
3.  サービス アプリケーションの名前の **近く** をクリックし、SharePoint ツール バーの **[プロパティ]** をクリックします。  サービス アプリケーションの名前をクリックすると、プロパティ ページではなく、サービス アプリケーションの管理ページが開きます。  
  
4.  必要な Web アプリケーションを指すように **[Web アプリケーションの関連付け]** が構成されていることを確認します。  
  
### サイト コレクション機能を確認するには  
  
1.  サイトの設定の **[サイト コレクションの管理]** で **[サイト コレクションの機能]** をクリックします。  
  
2.  **[レポート サーバーの統合機能]** がアクティブであることを確認します。  
  
### レポート サーバー コンテンツの種類を確認するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバー コンテンツの種類を確認または追加するには、「[Add Reporting Services Content Types to a SharePoint Library (SharePoint ライブラリへの Reporting Services のコンテンツの種類の追加)](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)」を参照してください。  
  
### レポート ビルダーが起動できることを確認するには  
  
1.  ドキュメント ライブラリから、SharePoint リボンの **[ドキュメント]** をクリックします。  
  
2.  **[新しいドキュメント]** をクリックし、 **[レポート ビルダー レポート]**をクリックします。 このオプションが表示されない場合は、レポート サーバー コンテンツの種類をライブラリに追加するための前の手順を確認してください。  
  
### 基本的なレポートの作成  
  
1.  SharePoint ドキュメント ライブラリ内で、タイトルなどに使用するテキスト ボックスのみを含む基本的な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを作成します。 このレポートには、データ ソースやデータセットは何も含めません。 目標は、レポート ビルダーを開いて基本的なレポートをプレビューできることの確認です。  
  
2.  レポートをドキュメント ライブラリに保存し、ライブラリからレポートを実行します。 レポート ビルダーでレポートを作成する方法の詳細については、「[レポート ビルダーの起動](http://msdn.microsoft.com/ja-jp/8c8c7d2e-b315-418d-bf65-90e7685e4259)」を参照してください。  
  
### Reporting Services のサンプル  
  
1.  Reporting Services のチュートリアルのいずれかを完了します。 詳細については、「[Reporting Services のチュートリアル &#40;SSRS&#41;](../../reporting-services/reporting-services-tutorials-ssrs.md)」を参照してください。  
  
2.  CodePlex から AdventureWorks の作業のサンプル データベースと [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サンプル レポートをダウンロードします。 詳細については、「 [AdventureWorks レポート サンプル](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home)」を参照してください。  
  
##  <a name="bkmk_nativemode"></a> ネイティブ モードのインストールの確認  
 既定の構成を使用してネイティブ モードでレポート サーバーをインストールする場合、セットアップでサーバーをインストールし、配置します。 いくつかの簡単なテストを行うことで、レポート サーバーが正常に配置されたかどうかを確認できます。 これらの手順を実行するには、ローカル管理者である必要があります。 他のユーザーがテストを実行する場合は、そのユーザーがレポート サーバーにアクセスできるように構成する必要があります。  
  
### レポート サーバーが正常にインストールされ、実行されていることを確認するには  
  
1.  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールを実行し、インストールしたレポート サーバー インスタンスに接続します。 [Web サービス URL] ページには、レポート サーバー Web サービスへのリンクが含まれています。 このリンクをクリックして、サーバーにアクセスできることを確認します。 レポート サーバー データベースが構成されていない場合は、リンクをクリックする前にレポート サーバー データベースを構成してください。  
  
2.  Services コンソール アプリケーションを開き、レポート サーバー サービスが実行されていることを確認します。 レポート サーバー サービスの状態を表示するには、**[スタート]** ボタンをクリックし、**[コントロール パネル]** をポイントして、**[管理ツール]** をダブルクリックします。次に、**[サービス]** をダブルクリックします。 サービスの一覧が表示されたら、**[Report Server (MSSQLSERVER)]** までスクロールします。 状態が **[開始]**になっていることを確認してください。  
  
3.  ブラウザーを開き、アドレス バーにレポート サーバーの URL を入力します。 アドレスは、セットアップ時にレポート サーバーに指定したサーバー名と仮想ディレクトリ名で構成されます。 既定では、レポート サーバーの仮想ディレクトリ名は **ReportServer**です。 http://*\<computer name>*/ReportServer*\<_instance name>* という URL を使用して、レポート サーバーのインストール状態を確認できます。 レポート サーバーを名前付きインスタンスとしてインストールした場合、URL は異なります。 URL 形式の詳細については、「[レポート サーバー URL の構成  &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)」を参照してください。 Windows Vista または Windows Server 2008 上のローカル管理者である場合は、「[ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。  
  
4.  レポートを実行して、レポート サーバーの動作をテストします。 この手順では、チュートリアルからサンプル レポートを作成できます。 詳細については、「[基本的なテーブル レポートの作成 &#40;SSRS チュートリアル&#41;](../../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)」を参照してください。  
  
### [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]が正常にインストールされ、実行されていることを確認するには  
  
1.  ブラウザーを開き、アドレス バーに Web ポータルの URL を入力します。 このアドレスは、セットアップ時または Reporting Services 構成ツールの [Web ポータル URL] ページで [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]に対して指定したサーバー名と仮想ディレクトリ名で構成されます。 既定では、[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]の仮想ディレクトリは **Reports** です。 次の URL を使用して、[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]のインストール状態を確認できます。  
  
     http://*\<computer name>*/Reports*\<_instance name>*.  
  
2.  レポート サーバー データベースに定義が戻されるかどうかをテストするため、[!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)]を使用して新しいフォルダーを作成するか、ファイルをアップロードします。 操作が成功した場合、接続は正しく機能しています。  
  
     詳細については、「[Web ポータル &#40;SSRS ネイティブ モード&#41;](http://msdn.microsoft.com/ja-jp/7349e626-6ed5-4d21-b05f-cf042ad9ad70)」を参照してください。  
  
### レポート デザイナーが正常にインストールされ、実行されていることを確認するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を開き、レポート サーバーのプロジェクトの種類に基づいて新しいプロジェクトを作成します。 レポート サーバー プロジェクト ウィザードの使用方法の詳細については、SQL Server オンライン ブックの「[SQL Server データ ツールの Reporting Services &#40;SSDT&#41;](../../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。  
  
2.  サンプル レポートをインストールした場合は、サンプル レポート プロジェクト ファイルを開き、レポート サーバーにレポートをパブリッシュします。  
  
## 参照  
 [Reporting Services インストール時の問題解決](../../reporting-services/install-windows/troubleshoot-a-reporting-services-installation.md)   
 [Reporting Services エラーの原因と解決方法](../../reporting-services/troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  