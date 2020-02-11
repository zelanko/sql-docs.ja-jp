---
title: Reporting Services ツール | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 21c56f28a6f65b22d8fe334a1046f44f868c4453
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099909"
---
# <a name="reporting-services-tools"></a>Reporting Services ツール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]には、管理された環境での豊富なレポートの開発と使用をサポートするグラフィカルツールとスクリプトツールのセットが含まれています。 このツール セットには、開発ツール、構成と管理ツール、およびレポート表示ツールが含まれています。 ここでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の各ツール、およびツールへのアクセス方法について簡単に説明します。  
  
 ツールを簡単に見つける方法については、「[チュートリアル : Reporting Services ツールを検索および開始する方法 (SSRS)](tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md)」を参照してください。  
  
## <a name="tools-for-report-authoring"></a>レポートの作成ツール  
 次の表に、で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポートを作成するときに使用できるツールを示します。  
  
|ツール|[説明]|アクセス方法|  
|----------|-----------------|-------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 表形式モデルに基づいてレポートを作成し、対話できるようにデザインされた、対話型データの探索およびビジュアル化が可能です。<br /><br /> 注: SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]モードではが必要です。|Silverlight がインストールされているブラウザー|  
|レポート デザイナー|レポートをデザインし、ネイティブ モードまたは SharePoint モードのレポート サーバーに配置するには、このツールを使用します。<br /><br /> でホストされる [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> レポートで使用されるデータを編成するためのレポート データ ペイン<br /><br /> 対話型のレポート デザインのデザインおよびプレビューに使用するタブ付きビュー<br /><br /> データ ソースから取得するデータを指定できるクエリ デザイナー、および [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)内のデータ ソースの種類に関連付けられているクエリ デザイナー<br /><br /> レポートのコンテンツと外観をカスタマイズする [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 式を作成するための IntelliSense 対応の式エディター<br /><br /> カスタム レポート アイテムとカスタム クエリ デザイナーをサポート<br /><br /> <br /><br /> 詳細については、「[SQL Server データ ツールの Reporting Services (SSDT)](reporting-services-in-sql-server-data-tools-ssdt.md)」を参照してください。|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|レポート ビルダー|レポートをデザインし、ネイティブ モードまたは SharePoint モードのレポート サーバーに配置するには、このツールを使用します。<br /><br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)]Office と同様の作成環境<br /><br /> レポート アイテムをレポート パーツとして保存する機能<br /><br /> マップを作成するウィザード<br /><br /> 集計の集計<br /><br /> 式のサポート強化<br /><br /> 選択した組み込みのデータ ソースの種類から取得するデータを指定できるクエリ デザイナー<br /><br /> <br /><br /> 詳細については、「[レポートビルダー &#40;SSRS&#41;](report-builder-authoring-environment-ssrs.md)」を参照してください。|MSI をダウンロードするか、レポート マネージャーまたは SharePoint から開く|  
  
## <a name="tools-for-report-server-administration"></a>レポート サーバー管理用のツール  
 のレポートサーバー [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を管理するためのグラフィカルツールとスクリプトツールのセットが用意されています。 使用するツールは、レポート サーバーの配置モードによって異なります。  
  
### <a name="native-mode"></a>ネイティブ モード  
 次の表に、ネイティブ モードで配置されているレポート サーバーの管理に使用できるツールの一覧を示します。  
  
|ツール|[説明]|アクセス方法|  
|----------|-----------------|-------------------|  
|Reporting Services 構成マネージャー|Reporting Services のインストールを構成するには、このツールを使用します。 Reporting Services Configuration Manager は、レポートサーバーのコンテンツの管理、追加機能の有効化、またはサーバーへのアクセス権の付与には役立ちません。 実行できるタスクは次のとおりです。<br /><br /> ローカルとリモートの両方のレポート サーバー インスタンスの構成<br /><br /> レポート サーバー サービス アカウントの構成<br /><br /> 1 つ以上の Web サービス URL の作成および構成<br /><br /> レポート マネージャー URL の構成<br /><br /> レポート サーバー データベースの作成および構成<br /><br /> スケールアウト配置の構成<br /><br /> 保存されている接続文字列や資格情報を暗号化する対称キーのバックアップ、復元、または置き換え<br /><br /> 自動実行アカウントの構成<br /><br /> 電子メール配信用の SMTP サーバーの構成<br /><br /> <br /><br /> 詳細については、「 [Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)」を参照してください。|[スタート] メニュー|  
|SQL Server Management Studio|次のように、単一の環境で 1 つ以上のレポート サーバー インスタンスを管理するには、このツールを使用します。<br /><br /> ローカルとリモートの両方のレポート サーバー インスタンスの管理<br /><br /> レポート サーバーのプロパティの設定<br /><br /> ロールの定義の変更<br /><br /> 使用していないレポート サーバー機能の無効化<br /><br /> ジョブの管理<br /><br /> 共有スケジュールの管理|[スタート] メニュー|  
|SQL Server 構成マネージャー|このツールは次の場合に使用します。<br /><br /> Reporting Services の Windows サービスの開始と停止<br /><br /> カスタマー フィードバック レポート、ダンプ ディレクトリの場所、およびエラー報告の構成<br /><br /> <br /><br /> ** \*警告\* \* **このツールを使用してサービスアカウントを構成しないでください。 代わりに Reporting Services 構成ツールを使用します。<br /><br /> 詳細については、「 [SQL Server Configuration Manager](../../relational-databases/sql-server-configuration-manager.md)」を参照してください。|[スタート] メニュー|  
|Rsconfig ユーティリティ|レポート サーバー データベースへのレポート サーバー接続を構成および管理するには、このツールを使用します。 これを使用して、自動レポート処理に使用するユーザー アカウントを指定することもできます。<br /><br /> 詳細については、「[レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)](report-server-command-prompt-utilities-ssrs.md)」を参照してください。|コマンド プロンプト|  
|Rskeymgmt ユーティリティ|このツールは次の場合に使用します。<br /><br /> レポート サーバー データの暗号化に使用する対称キーの抽出、復元、作成、および削除<br /><br /> スケールアウト配置へのレポート サーバー インスタンスの追加<br /><br /> <br /><br /> 詳細については、「[レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)](report-server-command-prompt-utilities-ssrs.md)」を参照してください。|コマンド プロンプト|  
|Windows Management Instrumentation (WMI) クラス|グラフィカル ユーザー インターフェイスを使用せずに、Reporting Services 構成マネージャーの構成タスクを自動化するには、これらのクラスを使用します。<br /><br /> 詳細については、「 [Accessing the WMI Provider Programmatically](../accessing-the-wmi-provider-programmatically.md)」を参照してください。|Visual Basic スクリプト|  
  
### <a name="sharepoint-integrated-mode"></a>SharePoint 統合モード  
 SharePoint モードでは、Reporting Services は SharePoint アーキテクチャのサービス アプリケーションであり、SharePoint によって直接管理されます。  
  
|ツール|[説明]|アクセス方法|  
|----------|-----------------|-------------------|  
|SharePoint サーバーの全体管理|
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の共有サービス アプリケーションを作成、クエリ、および管理するには、SharePoint サーバーの全体管理を使用します。<br /><br /> 詳細については、「[レポート サーバーの構成と管理 (Reporting Services SharePoint モード)](../configure-administer-report-server-reporting-services-sharepoint-mode.md)」を参照してください。|サーバーの全体管理の SharePoint サイト URL に接続するブラウザー|  
|PowerShell コマンドレット|
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の共有サービス アプリケーションを作成、クエリ、および管理するには、PowerShell コマンドレットを使用します。<br /><br /> 詳細については、「 [Reporting Services SharePoint モード用の PowerShell コマンドレット](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md)」をご覧ください。|SharePoint 2010 管理シェル|  
  
## <a name="tools-for-report-content-management"></a>レポート コンテンツ管理用のツール  
 のコンテンツ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]を管理するためのグラフィカルツールとスクリプトツールのセットが用意されています。 使用するツールは、レポート サーバーの配置モードによって異なります。  
  
|ツール|[説明]|アクセス方法|  
|----------|-----------------|-------------------|  
|レポート サーバー Web サービスの URL|汎用アイテム ナビゲーション ページのレポート カタログのコンテンツを参照するには、このツールを使用します。<br /><br /> 詳細については、「 [Report Server Web Service](../report-server-web-service/report-server-web-service.md)」を参照してください。|Browser|  
|レポート マネージャー|**(ネイティブモードのみ)** このツールを使用すると、リモートの場所から HTTP 接続を介して1つのレポートサーバーインスタンスを管理できます。 以下の操作を行うことができます。<br /><br /> レポートの表示、検索、印刷、およびサブスクライブ。<br /><br /> サーバー上のアイテムを整理するフォルダー階層の作成、セキュリティ保護、および保守。<br /><br /> アイテムおよび操作に対するアクセスを決定するロールベースのセキュリティの構成。<br /><br /> レポート実行プロパティ、レポート履歴、およびレポート パラメーターの構成。<br /><br /> Microsoft SQL Server Analysis Services データ ソースまたは SQL Server リレーショナル データ ソースに接続してデータを取得するレポート モデルの作成。<br /><br /> モデル内の特定のエンティティへのアクセスを許可するモデル アイテム セキュリティの設定、または事前に作成した定義済みのクリックスルー レポートへのエンティティのマップ。<br /><br /> スケジュールおよびデータ ソース接続をさらに管理しやすくする共有スケジュールおよび共有データ ソースの作成。<br /><br /> 大きい受信者一覧にレポートをロール アウトするデータ ドリブン サブスクリプションの作成。<br /><br /> 既存レポートの再利用や目的変更を行うための、リンク レポートの作成。<br /><br /> レポートを作成するレポート ビルダーの起動。作成したレポートは、レポート サーバーで保存および実行できます。<br /><br /> <br /><br /> 詳細については、「[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)」を参照してください。||  
|RS ユーティリティ|このツールは、スクリプト操作の実行に使用できるスクリプト ホストです。 このツールを使用して、レポート サーバー データベース間でのデータのコピー、レポートのパブリッシュ、レポート サーバー データベースでのアイテムの作成などを行う [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] スクリプトを実行します。<br /><br /> 詳細については、「[レポート サーバーのコマンド プロンプト ユーティリティ (SSRS)](report-server-command-prompt-utilities-ssrs.md)」を参照してください。|コマンド プロンプト|  
  
## <a name="see-also"></a>参照  
 [レポートサーバーの Reporting Services](../reporting-services-report-server.md)   
 [Reporting Services の概念 &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md)   
 [Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
