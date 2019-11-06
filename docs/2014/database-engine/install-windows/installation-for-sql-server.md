---
title: SQL Server 2014 のインストール |Microsoft Docs
ms.custom: ''
ms.date: 09/09/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
f1_keywords:
- sql12.portal.Installation.f1
helpviewer_keywords:
- installing SQL Server, initial installation
- installation [SQL Server]
- initial installation [SQL Server]
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5a7e72b429789477a9ae1245be30b18965560ee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62775365"
---
# <a name="installation-for-sql-server-2014"></a>SQL Server 2014 のインストール
 ## <a name="download-sql-server-2014-expresshttpwwwhanselmancomblogdownloadsqlserverexpressaspx"></a>[SQL Server 2014 Express をダウンロードします。](http://www.hanselman.com/blog/DownloadSQLServerExpress.aspx)
  **よろしくお願いする[Scott Hanselman](http://www.hanselman.com/)すべてのインストーラー パッケージ リンクを 1 か所に収集するためです。**
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの 1 つの機能ツリーから、次のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをインストールできます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   管理ツール  
  
-   接続コンポーネント  
  
 各コンポーネントを個別にインストールするか、上記のコンポーネントを組み合わせて選択できます。 最適なエディションおよびコンポーネントで使用できるようにする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[エディションと SQL Server 2014 のコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)と[機能は、SQL Server 2014 の各エディションでサポートされている](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には 32 ビット版と 64 ビット版があります。
 
 **お試しください:**  
  
-   Azure アカウントをすでにお持ちですか?  やがて **[ここ](https://ms.portal.azure.com/?flight=1#create/Microsoft.SQLServer2016RTMEnterpriseWindowsServer2012R2)** 既にインストールされている SQL Server 2014 Service Pack 1 (SP1) の仮想マシンを作成します。 SQL Server 2014 (SP1) の詳細については、次を参照してください。 [SQL Server 2014 Service Pack 1 リリース情報](https://support.microsoft.com/en-us/kb/3058865)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードを使用する場合でも、コマンド プロンプトから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールする場合でも、セットアップ時には以下の手順を実行する必要があります。  
  
 [SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用にコンピューターを準備する方法について説明します。  
  
-   ハードウェアとソフトウェアの要件  
  
-   システム構成チェッカーの要件とブロックの問題  
  
-   セキュリティに関する注意点  
  
 [SQL Server 2014 のインストール](install-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインストール オプションについて説明します。  
  
 [SQL Server 2014 へのアップグレード](upgrade-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードするためのオプションについて説明します。  
  
 [SQL Server 2014 のアンインストール](../../sql-server/install/uninstall-sql-server.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]のアンインストール手順について説明します。  
  
 [SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールして構成する方法について説明します。  
  
 [SQL Server 2014 の BI 機能をインストールします。](../../sql-server/install/install-sql-server-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で Microsoft BI プラットフォームに含まれる機能には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および分析データの作成または操作に使用されるいくつかのクライアント アプリケーションがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインストール方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [インストール方法に関するトピック](../../sql-server/install/installation-how-to-topics.md)  
 インストール ウィザード、コマンド プロンプト、構成ファイル、および SysPrep を使用して [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールするための手順に関するトピックへのリンクが記載されています。  
  
 [SharePoint と SQL Server BI 機能をインストール&#40;PowerPivot と Reporting Services&#41;](../../sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)  
 このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を SharePoint 環境でインストールする方法について説明します。 ここでは、特定のバージョンとエディションの SharePoint で使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を示します。 また、PowerPivot for SharePoint と Reporting Services を SharePoint モードでインストールする手順についても説明します。  
  
 [SQL Server のサンプルとサンプル データベースのインストール](http://sqlserversamples.codeplex.com/)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプルおよびサンプル データベースをインストールして構成する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [SQL Server インストールの新機能](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
