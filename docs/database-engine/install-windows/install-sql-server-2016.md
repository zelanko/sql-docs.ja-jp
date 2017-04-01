---
title: "SQL Server 2016 のインストール | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "AdventureWorks サンプル データベース"
  - "SQL Server のインストール, インストールの準備"
  - "インストール [SQL Server]"
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
caps.latest.revision: 59
ms.author: "mikeray"
manager: "jhubbard"
---
# SQL Server 2016 のインストール
  SQL Server 2016 は 64 ビット アプリケーションです。 SQL Server の入手およびインストールの方法に関する重要な詳細情報を次に示します。

## <a name="installation-details"></a>インストールの詳細
  
*  **オプション**: インストール ウィザード、コマンド プロンプト、または sysprep でインストールします。
 
*  **要件**: インストールする前に、「[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)」に記載されているインストール要件、システム構成チェック、セキュリティ上の考慮事項を確認してください。 

* **プロセス**: インストール プロセスの完全な手順については、「[SQL Server のインストール](../../database-engine/install-windows/installation-for-sql-server-2016.md)」を参照してください。

* **サンプル データベースとサンプル コード**: 
    * これらは、既定では SQL Server セットアップの一環としてインストールされません。 
    * SQL Server の Express 以外のエディションをインストールするには、[「CodePlex Web サイト」](http://go.microsoft.com/fwlink/?LinkId=87843) を参照してください。
    * SQL Server のサンプル データベースおよび SQL Server Express のサンプル コードに対するサポートについては、[「データベースとサンプルの概要」](http://go.microsoft.com/fwlink/?LinkId=110391) を参照してください。
    

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のダウンロード場所は、エディションによって異なります。

- **SQL Server Enterprise、Standard、Express の各エディション**は、運用環境用にライセンスされます。 Enterprise および Standard エディションのインストール メディアについては、ソフトウェア販売元に問い合わせてください。 購入に関する情報および Microsoft パートナーのディレクトリについては、[マイクロソフトの購入 Web サイト](https://www.microsoft.com/en-us/server-cloud/products/sql-server/overview.aspx)をご覧ください。 

- **無料エディション**は、次のリンクから入手できます。

| [エディション] | Description
|---------|--------
|[Developer Edition](http://myprodscussu1.app.vssubscriptions.visualstudio.com/Downloads?q=SQL%20Server%20Developer) | SQL Server 2016 Enterprise Edition ソフトウェアの無償のフル機能セットであり、運用環境以外でアプリケーションをビルド、テスト、デモンストレーションできます。 
|[Express Edition](http://www.microsoft.com/download/details.aspx?id=52679)|  エントリ レベルの無償のデータベースであり、実稼働環境での小規模なデータベースの展開に最適です。 最大 10 GB のディスク サイズの小規模サーバーによるデスクトップ向けデータ駆動アプリケーションを構築します。 
| [Evaluation Edition](http://technet.microsoft.com/evalcenter/mt130694) | 評価期間 180 日の SQL Server Enterprise Edition ソフトウェアの完全な機能セットです。
   
 
  

## <a name="how-to-install-sql-server"></a>SQL Server をインストールする方法
 
|Title|Description|  
|-----------|-----------------|  
|[Server Core への SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-on-server-core.md)|このトピックを参照して、Windows Server Core に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールします。|  
|[システム構成チェッカーの検査パラメーター](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)|システム構成チェッカー (SCC) の機能について説明します。|  
|[インストール ウィザードからの SQL Server 2016 のインストール &#40;セットアップ &#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md)|インストール ウィザードを使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一般的なインストール手順に関するトピック。|  
|[コマンド プロンプトからの SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)|自動セットアップを実行するためのサンプルの構文とインストール パラメーターを提供する手順に関するトピック。|  
|[構成ファイルを使用した SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)|構成ファイルからセットアップを実行するためのサンプルの構文とインストール パラメーターを提供する手順に関するトピック。|  
|[SysPrep を使用した SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016-using-sysprep.md)|SysPrep からセットアップを実行するためのサンプルの構文とインストール パラメーターを提供する手順に関するトピック。|  
|[SQL Server 2016 のインスタンスへの機能の追加 &#40;セットアップ&#41;](../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の既存のインスタンスのコンポーネントを更新する手順に関するトピック。|  
|[失敗した SQL Server 2016 のインストールの修復](../../database-engine/install-windows/repair-a-failed-sql-server-2016-installation.md)|壊れた [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を修復する手順に関するトピック。|  
|[SQL Server のスタンドアロン インスタンスをホストするコンピューターの名前変更](../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)|sys.servers に格納されているシステム メタデータを更新する手順に関するトピック。|  
|[SQL Server 2016 サービス更新プログラムのインストール](../../database-engine/install-windows/install-sql-server-2016-servicing-updates.md)|SQL Server 2016 の更新プログラムのインストール手順に関するトピック。|  
|[SQL Server セットアップ ログ ファイルの表示と読み取り](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)|セットアップ ログ ファイルでエラーをチェックする手順に関するトピック。|  
|[SQL Server のインストールの検証](../../database-engine/install-windows/validate-a-sql-server-installation.md)|コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するための SQL の検出レポートの使用方法を確認します。|  
  
  
## <a name="how-to-install-individual-components"></a>個々のコンポーネントをインストールする方法  
  
|トピック|Description|  
|-----------|-----------------|  
|[SQL Server データベース エンジンのインストール](../../database-engine/install-windows/install-sql-server-database-engine.md)|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をインストールして構成する方法について説明します。|  
|[SQL Server レプリケーションのインストール](../../database-engine/install-windows/install-sql-server-replication.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションをインストールして構成する方法について説明します。|  
|[分散再生のインストール - 概要](../../tools/distributed-replay/install-distributed-replay-overview.md)|分散再生の機能をインストールするためのトピックをリストします。|  
|[SSMS を使用した SQL Server 管理ツールのインストール](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツールをインストールして構成する方法について説明します。|  
|[SQL Server PowerShell のインストール](../../database-engine/install-windows/install-sql-server-powershell.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell コンポーネントのインストールに関する考慮事項について説明します。|  
  

## <a name="how-to-configure-sql-server"></a>SQL Server を構成する方法  
  
|トピック|Description|  
|-----------|-----------------|  
|[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|このトピックでは、ファイアウォール構成の概要を示し、Windows ファイアウォールを構成する方法について説明します。|  
|[SQL Server アクセス用のマルチホーム コンピューターの構成](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|このトピックでは、マルチホーム環境内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのネットワーク接続用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とセキュリティが強化された Windows ファイアウォールを構成する方法について説明します。|  
|[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|このトピックで示す手順に従って、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint へのアクセスを許可するためにポートとファイアウォールの両方の設定を構成できます。|  
  
## <a name="related-sections"></a>関連項目  
[SQL Server 2016 の各エディションでサポートされる機能](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
[SQL Server 2016 のビジネス インテリジェンス機能のインストール](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
  [SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 
  
## <a name="see-also"></a>参照  

[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [SQL Server 2016 へのアップグレード](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)   
 [SQL Server 2016 のアンインストール](../../sql-server/install/uninstall-sql-server-2016.md)   
 [高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  