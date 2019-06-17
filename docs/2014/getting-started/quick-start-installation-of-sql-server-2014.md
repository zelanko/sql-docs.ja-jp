---
title: SQL Server 2014 のインストールのクイック スタート |Microsoft Docs
ms.custom: ''
ms.date: 05/25/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- quick start installation [SQL Server]
- installation [SQL Server]
- installing SQL Server, quick start installations
ms.assetid: 672afac9-364d-4946-ad5d-8a2d89cf8d81
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b06f5248152f8a11bf3e46d222df457f5442b6b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62837787"
---
# <a name="quick-start-installation-of-sql-server-2014"></a>SQL Server 2014 のクイック スタート インストール
    
## <a name="introduction"></a>概要  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インストール ウィザードは、Windows インストーラーをベースにしています。 このインストール ウィザードの 1 つの機能ツリーから次の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントをインストールできます。  
  
-   [!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  
  
-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)]  
  
-   管理ツール  
  
-   接続コンポーネント  
  
 各コンポーネントを個別にインストールするか、上記のコンポーネントを組み合わせて選択できます。 最適なエディションおよびコンポーネントで使用できるようにする[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]を参照してください[エディションと SQL Server 2014 のコンポーネントの](../sql-server/editions-and-components-of-sql-server-2016.md)します。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] には 32 ビット版と 64 ビット版があります。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップでは、次のインストール方法がサポートされています。  
  
-   **インストール ウィザードからの SQL Server&2016; のインストール (セットアップ)**  
  
     参照してください[インストール ウィザードからの SQL Server 2014 のインストール&#40;セットアップ&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)インストールの詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インストール ウィザードを使用しています。  
  
-   **コマンド プロンプト**  
  
     参照してください[コマンド プロンプトから SQL Server 2014 のインストール](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)無人セットアップを実行するためのサンプル構文とインストール パラメーターについてです。  
  
-   **構成ファイル**  
  
     参照してください[SQL Server 2014 を使用したインストール、構成ファイル](../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)構成ファイルからセットアップを実行するためのサンプル構文とインストール パラメーターについてです。  
  
-   **SysPrep**  
  
     参照してください[SQL Server 2014 を使用して SysPrep インストール](../database-engine/install-windows/install-sql-server-using-sysprep.md)インストールの詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SysPrep を使用しています。  
  
-   **Server Core インストール**  
  
     参照してください[Server Core での SQL Server 2014 のインストール](../database-engine/install-windows/install-sql-server-on-server-core.md)インストールの詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Windows Server Core でします。  
  
-   **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] BI 機能のインストール**  
  
     参照してください[SQL Server 2014 BI の機能をインストール](../sql-server/install/install-sql-server-business-intelligence-features.md)が含まれるは、Microsoft BI プラットフォームの一部である機能のインストールについては、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、および複数分析データの作成または操作に使用されるクライアント アプリケーション。  
  
-   **フェールオーバー クラスター インストール**  
  
     参照してください[SQL Server フェールオーバー クラスター インストール](../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md)インストールの詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]フェイル オーバー クラスター。  
  
 既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベースとサンプル コードはインストールされません。 Express 以外のエディションの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のサンプル データベースとサンプル コードをインストールするには、[CodePlex Web サイト](https://go.microsoft.com/fwlink/?LinkId=87843)をご覧ください。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のサンプル データベースと [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] のサンプル コードのサポートについては、「[データベースとサンプルの概要](https://go.microsoft.com/fwlink/?LinkId=110391)」をご覧ください。  
  
## <a name="includessnoversionincludesssnoversion-mdmd-installation"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インストール  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インストール ウィザードを使用する場合でも、コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をインストールする場合でも、セットアップ時には以下の 1 つ以上の手順を実行する必要があります。  
  
-   インストール要件、システム構成チェック、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールに関するセキュリティ上の考慮事項を確認します。  詳細については、「[SQL Server のインストール計画](quick-start-installation-of-sql-server-2014.md#BKMK_BeforeYouInstall)」を参照してください。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップを実行して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既存のバージョンを [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] にアップグレードします。 詳細については、次を参照してください。 [SQL Server 2014 にアップグレードする](#BKMK_Upgrading)します。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップを実行して、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の新しいインスタンスをインストールします。 詳細については、次を参照してください。 [Installing SQL Server 2014](#BKMK_Install)します。  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールが完了したら、次に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とそのコンポーネントを構成します。これは重要な手順です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を構成します。 詳細については、次を参照してください。[を構成する SQL Server 2014](#BKMK_Configure)します。  
  
 次のセクションでは、これらのタスクについて詳しく説明します。  
  
## <a name="related-tasks"></a>Related Tasks  
  
###  <a name="BKMK_BeforeYouInstall"></a> 計画、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インストール  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] をインストールする前に、ハードウェアとソフトウェアの要件、ネットワークとインターネットに関する考慮事項、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をインストールして実行するためのセキュリティ上の考慮事項を確認する必要があります。 詳細については、次を参照してください。 [SQL Server のインストール計画](../../2014/sql-server/install/planning-a-sql-server-installation.md)および次のトピックも。  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|ハードウェアとソフトウェアの要件、オペレーティング システムのサポート、ネットワークとインターネットに関する考慮事項、および必要なハード ディスク領域について確認します。|[インストールの前提条件](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)|  
|セキュリティに関する考慮事項を確認して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インストールします。|[セキュリティに関する考慮事項](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のさまざまなエディションでサポートされる機能の詳細を確認します。|[機能とエディション](features-supported-by-the-editions-of-sql-server-2014.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の最適なエディションおよびコンポーネントを決定します。|[SQL Server 2014 のエディションとコンポーネント](../sql-server/editions-and-components-of-sql-server-2016.md)|  
|ハードウェア構成を確認し、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] フェールオーバー クラスターのインストールの準備について学習します。|[フェールオーバー クラスタリングをインストールする前に](../sql-server/failover-clusters/install/before-installing-failover-clustering.md)|  
  
###  <a name="BKMK_Upgrading"></a> アップグレード [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] の既存のインスタンスを [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] にアップグレードできます。 詳細については、次を参照してください。 [SQL Server 2014 にアップグレード](../database-engine/install-windows/upgrade-sql-server.md)します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セットアップを実行して [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] にアップグレードする前に、アップグレード プロセスに関する以下のトピックを参照してください。  
  
|説明|トピック|  
|-----------------|-----------|  
|サポートされる [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] へのアップグレード パスについて説明します。|[サポートされるアップグレード](../database-engine/install-windows/supported-version-and-edition-upgrades.md)|  
|アップグレード アドバイザーについて説明します。アップグレード アドバイザーは、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] のインスタンスを分析し、アップグレードに関する既知の問題を報告するツールです。|[アップグレード アドバイザーを使用したアップグレードの準備](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)|  
|分散再生ユーティリティについて説明します。分散再生ユーティリティは、複数のコンピューターを使用してトレース データを再生し、ミッションクリティカルなワークロードをシミュレートできるツールです。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] アップグレードの前後でテスト サーバーの再生を実行することで、パフォーマンスの差を測定したり、アップグレード時にアプリケーションに非互換性が発生するかどうかを調べることができます。|[分散再生ユーティリティを使用したアップグレードの準備](../../2014/sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] へのアップグレード後にアプリケーションに影響を及ぼす可能性のある重要な変更内容を一覧表示します。|[旧バージョンとの互換性](backward-compatibility.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のスタンドアロン インスタンスを [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] にアップグレードする手順に関するトピックです。|[アップグレードする SQL Server 2014 のインストール ウィザードを使用して&#40;セットアップ&#41;](../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のエディションを別のエディションにアップグレードする手順に関するトピックです。 各エディションでサポートされるアップグレード パスについては、「 [サポートされているバージョンとエディションのアップグレード](../database-engine/install-windows/supported-version-and-edition-upgrades.md)」をご覧ください。|[SQL Server 2014 の別のエディションにアップグレードする&#40;セットアップ&#41;](../database-engine/install-windows/upgrade-to-a-different-edition-of-sql-server-setup.md)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、すべてのフェールオーバー クラスター ノードで個別に、[!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] のフェールオーバー クラスターに[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]および [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] をアップグレードすることがサポートされています。 詳細については、このトピックを参照してください。|[SQL Server フェールオーバー クラスターのアップグレード](../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)|  
  
###  <a name="BKMK_Install"></a> インストールします。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 次のトピックで、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のさまざまなインストール シナリオを確認してください。  
  
|説明|トピック|  
|-----------------|-----------|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のさまざまなコンポーネントのインストールに関するトピックと、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のインストール手順に関するトピックへのリンクが記載されています。|[SQL Server 2014 のインストール](../database-engine/install-windows/install-sql-server.md)|  
|このトピックを参照して、Windows Server Core に [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] をインストールします。|[Server Core への SQL Server 2014 のインストール](../database-engine/install-windows/install-sql-server-on-server-core.md)|  
|このトピックを参照して、既存の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンスに個々の機能を追加します。|[SQL Server 2014 のインスタンスに機能を追加&#40;セットアップ&#41;](../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md)|  
|このトピックを参照して、新しい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスを作成します。|[新しい SQL Server フェールオーバー クラスターの作成 &#40;セットアップ&#41;](../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)|  
|このトピックを参照して、既存の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスのノードを管理します。|[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;セットアップ&#41;](../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)|  
|このトピックを参照して、フェールオーバー クラスターに [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] クライアント ツールをインストールします。|[SQL Server フェールオーバー クラスターへのクライアント ツールのインストール](../sql-server/failover-clusters/install/install-client-tools-on-a-sql-server-failover-cluster.md)|  
|コンピューターにインストールされている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の機能を確認するための SQL の検出レポートの使用方法を確認します。|[SQL Server のインストールの検証](../database-engine/install-windows/validate-a-sql-server-installation.md)|  
|インストール ウィザード、コマンド プロンプト、構成ファイル、および SysPrep を使用して [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] をインストールするための手順に関するトピックへのリンクが記載されています。|[インストール方法に関するトピック](../../2014/sql-server/install/installation-how-to-topics.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
 このセクションでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の構成およびアンインストールについて説明します。  
  
###  <a name="BKMK_Configure"></a> 構成します。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストールが完了したら、グラフィカル ユーティリティやコマンド プロンプト ユーティリティを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をさらに構成できます。 初めて [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を構成する場合は、次のトピックを参照してください。  
  
|説明|トピック|  
|-----------------|-----------|  
|このトピックでは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] または PowerPivot for SharePoint へのアクセスを許可するためにファイアウォールのポートのブロックを解除する必要があるかどうかを判断するための情報を提供します。 このトピックで示す手順に従って、ポートとファイアウォールを構成できます。|[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)|  
|このトピックでは、ファイアウォール構成の概要について説明し、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理者を対象とした情報がまとめられています。|[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)|  
|このトピックでは、マルチホーム環境内の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスへのネットワーク接続用に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] とセキュリティが強化された Windows ファイアウォールを構成する方法について説明します。|[SQL Server アクセス用のマルチホーム コンピューターの構成](../../2014/sql-server/install/configure-a-multi-homed-computer-for-sql-server-access.md)|  
  
###  <a name="BKMK_Uninstalling"></a> アンインストールします。 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  
 次のトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のスタンドアロン インスタンスとフェールオーバー クラスター インスタンスを手動でアンインストールする方法について説明します。  
  
|説明|トピック|  
|-----------------|-----------|  
|このトピックでは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のスタンドアロン インスタンスを手動でアンインストールする方法について説明します。|[SQL Server 2014 のアンインストール](../sql-server/install/uninstall-sql-server.md)|  
|このトピックでは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスをアンインストールする方法について説明します。|[SQL Server のフェールオーバー クラスター インスタンスの削除 &#40;セットアップ&#41;](../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)|  
|このトピックでは、[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] または DQS サーバーのみをアンインストールした後に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (DQS) オブジェクトを手動で削除する方法について説明します。|[Data Quality Server オブジェクトの削除](../../2014/sql-server/install/remove-data-quality-server-objects.md)|  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 の製品仕様](sql-server-2014-product-specifications.md)   
 [SQL Server の製品ドキュメントの概要](../2014-toc/books-online-for-sql-server-2014.md)[旧バージョンとの互換性](backward-compatibility.md)  
  
  
