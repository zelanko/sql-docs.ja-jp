---
title: "SQL Server 2016 のインストール | Microsoft Docs"
ms.custom: ""
ms.date: "04/13/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.portal.Installation.f1"
helpviewer_keywords: 
  - "SQL Server のインストール, 最初のインストール"
  - "インストール [SQL Server]"
  - "最初のインストール [SQL Server]"
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# SQL Server 2016 のインストール
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの 1 つの機能ツリーから、次のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントをインストールできます。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]  
  
-   接続コンポーネント  
  
 SQL Server 2016 以降では、SQL Server 管理ツールがメイン機能ツリーからインストールされなくなりました。詳細については、「[SSMS を使用した SQL Server 管理ツールのインストール](Install%20SQL%20Server%20Management%20Tools%20\(SSMS\).md)」を参照してください。  
  
 各コンポーネントを個別にインストールするか、上記のコンポーネントを組み合わせて選択できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最適なエディションおよびコンポーネントを選択するには、「[SQL Server 2016 のエディションとコンポーネント](../../sql-server/editions-and-components-of-sql-server-2016.md)」および「[SQL Server 2016 の各エディションでサポートされる機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」を参照してください。  
  
## このセクションの内容  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードを使用する場合でも、コマンド プロンプトから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールする場合でも、セットアップ時には以下の手順を実行する必要があります。  
  
 [SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用にコンピューターを準備する方法について説明します。  
  
-   ハードウェアとソフトウェアの要件  
  
-   システム構成チェッカーの要件とブロックの問題  
  
-   セキュリティに関する注意点  
  
 [SQL Server 2016 のインストール](../../database-engine/install-windows/install-sql-server-2016.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール オプションについて説明します。  
  
 [SQL Server セットアップのユーザー インターフェイス リファレンス](../Topic/SQL%20Server%20Setup%20User%20Interface%20Reference.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードのインストール オプションについて説明します。  
  
 [SQL Server 2016 へのアップグレード](../../database-engine/install-windows/upgrade-to-sql-server-2016.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードするためのオプションについて説明します。  
  
 [SQL Server 2016 のアンインストール](../../sql-server/install/uninstall-sql-server-2016.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のアンインストール手順について説明します。  
  
 [SQL Server フェールオーバー クラスターのインストール](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターをインストールして構成する方法について説明します。  
  
 [SQL Server 2016 のビジネス インテリジェンス機能のインストール](../../sql-server/install/install-sql-server-2016-business-intelligence-features.md)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で Microsoft BI プラットフォームに含まれる機能には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および分析データの作成または操作に使用されるいくつかのクライアント アプリケーションがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ドキュメントのこのセクションでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] および [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストール方法について説明します。  
  
## 詳細  
 [SharePoint を使用した SQL Server の BI 機能のインストール &#40;Power Pivot と Reporting Services&#41;](../Topic/Install%20SQL%20Server%20BI%20Features%20with%20SharePoint%20\(Power%20Pivot%20and%20Reporting%20Services\).md)  
 このセクションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を SharePoint 環境でインストールする方法について説明します。 ここでは、特定のバージョンとエディションの SharePoint で使用できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能を示します。 また、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint と Reporting Services を SharePoint モードでインストールする手順についても説明します。  
  
 ![ssrs_fyi_note](../../analysis-services/instances/install-windows/media/ssrs-fyi-note.png) 新しいサンプル データベース [Wide World importers](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx) をインストールします。 
  
 [その他の SQL Server サンプルとサンプル データベース](http://sqlserversamples.codeplex.com/)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のサンプルおよびサンプル データベースをインストールして構成する方法について説明します。  
  
サポートされている [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のバージョンのリンクと情報については、[SQL Server の Update Center](https://msdn.microsoft.com/library/ff803383.aspx)を参照してください。  
  
## 参照  
 [SQL Server インストールの新機能](../../sql-server/install/what-s-new-in-sql-server-installation.md)   
 [SQL Server 2016 のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
  
  