---
title: SQL Server 2014 のインストール |Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, preparing to install
- installation [SQL Server]
ms.assetid: 0300e777-d56b-4d10-9c33-c9ebd2489ee5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7f631209a655b11062ffd17fa9f83f3e355011cf
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356692"
---
# <a name="install-sql-server-2014"></a>SQL Server 2014 のインストール
## <a name="-download-sql-server-2014-express-httpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[ SQL Server 2014 Express をダウンロードします。 ](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **よろしくお願いする[Scott Hanselman](http://www.hanselman.com/)すべてのインストーラー パッケージ リンクを 1 か所に収集するためです。**
  
 このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の各種インストール オプションについて概説します。 詳細については、さまざまな[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストールできるコンポーネントと、インストール プロセスを参照してください。 [SQL Server 2014 のインストール](installation-for-sql-server.md)。  
> **注:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は 32 ビットおよび 64 ビット エディションで使用できます。 64 ビット版と 32 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、インストール ウィザードを使用するか、コマンド プロンプトからインストールします。 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネントを参照してください[エディションと SQL Server 2014 のコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)と[機能は、SQL Server 2014 の各エディションでサポートされている](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。  
  
 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベースとサンプル コードはインストールされません。 Express 以外のエディションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプル データベースとサンプル コードをインストールするには、[CodePlex Web サイト](https://go.microsoft.com/fwlink/?LinkId=87843)をご覧ください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプル データベースと [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] のサンプル コードのサポートについては、「[データベースとサンプルの概要](https://go.microsoft.com/fwlink/?LinkId=110391)」をご覧ください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールする前に、インストール要件、システム構成チェック、およびセキュリティ上の考慮事項を確認します。 詳細については、「[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)」を参照してください。 次のセクションのトピックで、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のさまざまなインストール シナリオを確認してください。  
  
  
## <a name="install-includesscurrentincludessscurrent-mdmd-components"></a>インストール[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]コンポーネント  
  
|トピック|説明|  
|-----------|-----------------|  
|[SQL Server データベース エンジンについて](../sql-server-database-engine-overview.md)|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をインストールして構成する方法について説明します。|  
|[SQL Server レプリケーションのインストール](install-sql-server-replication.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションをインストールして構成する方法について説明します。|  
|[分散再生のインストール](../../tools/distributed-replay/install-distributed-replay-overview.md)|分散再生の機能をインストールするためのトピックをリストします。|  
|[SQL Server 管理ツールのインストール](../../sql-server/install/install-sql-server-management-tools.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツールをインストールして構成する方法について説明します。|  
|[SQL Server PowerShell のインストール](install-sql-server-powershell.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell コンポーネントのインストールに関する考慮事項について説明します。|  
  
## <a name="how-to-install-includesscurrentincludessscurrent-mdmd"></a>インストールする方法 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
|タイトル|説明|  
|-----------|-----------------|  
|[インストール方法に関するトピック](../../sql-server/install/installation-how-to-topics.md)|インストール ウィザード、コマンド プロンプト、構成ファイル、および SysPrep を使用して [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールするための手順に関するトピックへのリンクが記載されています。|  
|[Server Core への SQL Server 2014 のインストール](install-sql-server-on-server-core.md)|このトピックを参照して、Windows Server Core に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールします。|  
|[SQL Server のインストールの検証](validate-a-sql-server-installation.md)|コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するための SQL の検出レポートの使用方法を確認します。|  
|[システム構成チェッカーの検査パラメーター](check-parameters-for-the-system-configuration-checker.md)|システム構成チェッカー (SCC) の機能について説明します。|  
  
## <a name="configuration"></a>構成  
  
|トピック|説明|  
|-----------|-----------------|  
|[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|このトピックでは、ファイアウォール構成の概要を示し、Windows ファイアウォールを構成する方法について説明します。|  
|[SQL Server アクセス用のマルチホーム コンピューターの構成](../../sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|このトピックでは、マルチホーム環境内の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスへのネットワーク接続用に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とセキュリティが強化された Windows ファイアウォールを構成する方法について説明します。|  
|[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|このトピックで示す手順に従って、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または PowerPivot for SharePoint へのアクセスを許可するためにポートとファイアウォールの両方の設定を構成できます。|  
  
## <a name="related-sections"></a>関連項目  
 [SQL Server 2014 の BI 機能をインストールします。](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] BI プラットフォームに含まれる [!INCLUDE[msCoName](../../includes/msconame-md.md)] 機能には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]、および分析データの作成または操作に使用されるいくつかのクライアント アプリケーションがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]、[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]、および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール方法について説明します。  
  
 [SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールして構成する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)   
 [SQL Server 2014 へのアップグレード](upgrade-sql-server.md)   
 [SQL Server 2014 をアンインストールします。](../../sql-server/install/uninstall-sql-server.md)   
 [高可用性ソリューション &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)  
  
  
