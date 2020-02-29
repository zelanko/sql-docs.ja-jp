---
title: Reporting Services のアップグレードと移行 | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSRS, upgrading
- Reporting Services, upgrades
- SQL Server Reporting Services, upgrading
- upgrading Reporting Services
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 42cdcb1245e5280d25a94a81617da92f755ea048
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176942"
---
# <a name="upgrade-and-migrate-reporting-services"></a>Upgrade and Migrate Reporting Services

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のアップグレードおよび移行オプションの概要を示します。 配置された [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をアップグレードするには、次の 2 つの一般的な方法があります。

-   **アップグレード:** 現在インストールさ[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]れているサーバーとインスタンスのコンポーネントをアップグレードします。 これは一般に "インプレース" アップグレードと呼ばれます。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サーバーのモード間でのインプレース アップグレードはサポートされていません。 たとえば、ネイティブ モードのレポート サーバーを SharePoint モードのレポート サーバーにアップグレードすることはできません。 レポート アイテムはモード間で移行できます。 詳細については、このドキュメントで後述する「ネイティブから SharePoint への移行」および「[レポートサーバー間でコンテンツを移行するための rs .Exe スクリプトのサンプル Reporting Services](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)」を参照してください。

-   **移行**: 新しい SharePoint 環境をインストールして構成し、レポートアイテムとリソースを新しい環境にコピーして、既存のコンテンツを使用するように新しい環境を構成します。 下位レベルの移行形式では、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データベース、構成ファイル、および SharePoint コンテンツ データベース (SharePoint モードを使用している場合) をコピーします。

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード|

##  <a name="bkmk_top"></a>このトピックの内容:

-   [アップグレードに関する既知の問題とベストプラクティス](#bkmk_known_issues)

-   [サイドバイサイドインストール](#bkmk_side_by_side)

-   [インプレース アップグレード](#bkmk_inplace_upgrade)

-   [アップグレード前のチェックリスト](#bkmk_upgrade_checklist)

-   [ネイティブモードのアップグレードと移行のシナリオ](#bkmk_native_scenarios)

-   [Reporting Services ネイティブモードのスケールアウト配置のアップグレード](#bkmk_native_scaleout)

-   [SharePoint モードのアップグレードと移行のシナリオ](#bkmk_sharePoint_scenarios)

-   [移行に関する考慮事項](#bkmk_migration_considerations)

-   [その他のリソース](#bkmk_additional_resources)

##  <a name="bkmk_known_issues"></a>アップグレードに関する既知の問題とベストプラクティス
 アップグレード可能なサポートされるエディションとバージョンの詳細な一覧については、「 [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。

> [!TIP]
>  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の問題に関する最新情報については、以下を参照してください。
> 
>  -   [SQL Server 2014 リリースノート](https://go.microsoft.com/fwlink/?LinkID=296445)。
> -   [SQL Server 2014 Reporting Services のヒント、テクニック、およびトラブルシューティング](https://go.microsoft.com/fwlink/?LinkID=391254)を行います。
> -   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アップグレード アドバイザーを使用します。 詳細については、「アップグレードの[問題 &#40;アップグレード&#41;アドバイザーの Reporting Services](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md) 」および「[方法: アップグレードアドバイザーをインストールする](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)」を参照してください。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_side_by_side"></a>サイドバイサイドインストール
 
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] ネイティブ モードは、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のネイティブ モードの配置とサイド バイ サイドでインストールできます。

 
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] SharePoint モードと以前のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードのコンポーネントのサイド バイ サイド配置はサポートされていません。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_inplace_upgrade"></a>インプレースアップグレード
 アップグレードは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップで実行されます。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を含む任意またはすべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]コンポーネントをアップグレードできます。 セットアップによって既存のインスタンスが検出され、アップグレードするように求められます。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップには、コマンド ライン引数またはセットアップ ウィザードで指定できるアップグレード オプションが用意されています。

 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行すると、次のいずれかのバージョンからアップグレードするオプションを選択するか、既存のインストールと並行して実行する [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] の新しいインスタンスをインストールすることができます。

-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]

-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]

-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]

-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]

 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の詳細については、次のトピックを参照してください。

||
|-|
|[SQL Server 2014 へのアップグレード](../../database-engine/install-windows/upgrade-sql-server.md)|
|[インストールウィザード &#40;セットアップを使用して SQL Server 2014 にアップグレード&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)|
|[コマンド プロンプトからの SQL Server 2014 のインストール](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)|

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_upgrade_checklist"></a>アップグレード前のチェックリスト
 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードする前に、次の情報を確認してください。

-   お使いのハードウェアおよびソフトウェアで [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]をサポートできるかどうかを判断する要件を確認します。 詳細については、「 [Hardware and Software Requirements for Installing SQL Server 2014](../../../2014/sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」をご参照ください。

-   システム構成チェッカー (SCC) を使用して、レポート サーバー コンピューターをスキャンし、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]の正常なインストールを妨げる可能性のある状態をチェックします。 詳細については、「 [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)」を参照してください。

-   セキュリティのベスト プラクティスと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のためのガイダンスを確認します。 詳細については、「 [SQL Server インストールのセキュリティに関する考慮事項](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)」を参照してください。

-   レポート サーバー コンピューター上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アップグレード アドバイザーを実行し、正常なアップグレードを妨げる可能性のある問題を特定します。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。

-   対称キーをバックアップします。 詳細については、「 [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)」を参照してください。

-   レポート サーバーのデータベースと構成ファイルをバックアップします。 詳細については、「 [Backup and Restore Operations for Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md)」を参照してください。

-   IIS で既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 仮想ディレクトリに任意のカスタマイズをバックアップします。

-   無効な SSL 証明書を削除します。  これには、有効期限が切れており、Reporting Services をアップグレードする前に更新する予定のない証明書が含まれます。  無効な証明書はアップグレードが失敗する原因となり、" **Microsoft.ReportingServices.WmiProvider.WMIProviderException: Web サイトで Secure Sockets Layer (SSL) 証明書が構成されていません。**" のようなエラー メッセージが Reporting Services のログ ファイルに書き込まれます。

 実稼働環境をアップグレードする前に、必ず実稼働環境と同じ構成をしている実稼動前の環境でアップグレード テストを実行してください。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

## <a name="overview-of-migration-scenarios"></a>移行シナリオの概要
 サポートされているバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にアップグレードする場合、通常は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ ウィザードを実行することで、レポート サーバーのプログラム ファイル、データベース、およびすべてのアプリケーション データをアップグレードできます。

 ただし、次の状況が生じた場合は、レポート サーバー インストールを手動で **移行** する必要があります。

-   アップグレード アドバイザーで、アップグレードの障害となる問題がもう 1 つ検出されました。 詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。

-   配置で使用されるレポート サーバーの種類を変更します。 たとえば、ネイティブ モードのレポート サーバーを SharePoint モードにアップグレードまたは変換することはできません。 詳細については、「[ネイティブ モードから SharePoint モードへの移行 &#40;SSRS&#41;](../../reporting-services/install-windows/native-to-sharepoint-migration-ssrs.md)」を参照してください。

-   アップグレード プロセス中にレポート サーバーがオフラインになる時間を最小限に抑えることが求められている。 既存のレポート サーバーのインストールの状態を変更せずに、新しいレポート サーバー インスタンスにコンテンツ データをコピーし、インストールをテストする間、現在のインストールはオンライン状態で維持されます。

-   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を配置した SharePoint 2010 を SharePoint 2013 に移行することが求められている。 SharePoint 2013 では、SharePoint 2010 からのインプレース アップグレードがサポートされていません。 詳細については、「[Reporting Services の移行 &#40;SharePoint Mode&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)」を参照してください。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_native_scenarios"></a>ネイティブモードのアップグレードと移行のシナリオ
 **アップグレード:** ネイティブモードのインプレースアップグレードは、このトピックで既に説明したサポートされている各バージョンに対して同じプロセスです。 SQL Server インストール ウィザードまたはコマンド ライン インストールを実行します。 インストールが完了すると、レポート サーバー データベースは自動的に新しいレポート サーバー データベース スキーマにアップグレードされます。 詳細については、このトピックの「[インプレースアップグレード](#bkmk_inplace_upgrade)」セクションを参照してください。

 アップグレード処理では、まずアップグレードする既存のレポート サーバー インスタンスを選択します。

1.  レポート サーバー データベースがリモート コンピューター上に存在し、そのデータベースを更新する権限がない場合は、リモートのレポート サーバー データベースを更新するための資格情報を指定するように求められます。 
  `sysadmin` 権限またはデータベース更新権限を持つ資格情報を指定してください。

2.  アップグレードの妨げになる条件または設定がないかどうかがチェックされ、構成設定が読み取られます。 たとえば、カスタム拡張機能がレポート サーバーに配置されていないかどうかがチェックされます。 アップグレードがブロックされた場合は、アップグレードがブロックされないようにインストールを変更するか、新しい [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスに移行する必要があります。 詳細については、アップグレード アドバイザーのマニュアルを参照してください。

3.  アップグレードを続行できる場合は、アップグレード処理を進めるように求められます。

4.  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] プログラム ファイルの新しいフォルダーが作成されます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インストール用のプログラムフォルダーには、MSRS12 が含まれます。\<*インスタンス名*>。

5.  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーのプログラム ファイル、構成ツール、およびレポート サーバー機能の一部であるコマンド ライン ユーティリティが追加されます。

    1.  以前のバージョンのプログラム ファイルは削除されます。

    2.  新しいバージョンにアップグレードされるレポート サーバーの構成ツールおよびユーティリティには、ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツール、コマンド ライン ユーティリティ (RS.exe など)、およびレポート ビルダーがあります。

    3.  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] やオンライン ブックなどのその他のクライアント ツールはアップグレードされません。 新しいバージョンのツールを取得する場合は、セットアップの実行時に追加できます。 以前のバージョンと [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンが共存します。 サンプルをインストールした場合は、以前のバージョンが残ります。 セットアップでは、SQL Server のサンプルのアップグレードはサポートされません。

    4.  
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は個別にダウンロードします。 詳細については、「 [Microsoft SQL Server 2014 Data Tools - Business Intelligence for Microsoft Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843)」を参照してください。

6.  
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバー サービスのサービス コントロール マネージャーにあるサービス エントリが再利用されます。 このサービスのエントリには、レポート サーバー Windows サービス アカウントが含まれます。

7.  IIS の既存の仮想ディレクトリ設定に基づいて新しい URL が予約されます。 IIS の仮想ディレクトリは削除されない場合があるので、アップグレードの完了後に手動で削除してください。

8.  レポート サーバー データベースが新しいスキーマにアップグレードされ、ロールにデータベース所有者権限を追加することによって `RSExecRole` が変更されます。 この手順は、SP1 以前のから[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アップグレードする場合にのみ実行されます。

9. 構成ファイル内の設定がマージされます。 現在のインストールの構成ファイルが基礎として使用され、新しいエントリが追加されます。 使用されなくなったエントリは削除されませんが、アップグレードの完了後はレポート サーバーによって読み取られなくなります。 アップグレードでは古いログ ファイル、使用されなくなった RSWebApplication.config ファイル、または IIS の仮想ディレクトリ設定は削除されません。 また、SQL Server 2005 のレポート デザイナーや Management Studio などのクライアント ツールは削除されません。 これらのファイルやツールが不要になった場合は、アップグレードの完了後に削除してください。

 **移行:** 以前のバージョンのネイティブモードインストールをに移行[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]する手順は、このトピックで既に説明したサポートされているすべてのバージョンで同じです。 詳細については、「[Reporting Services のインストールの移行 &#40;ネイティブ モード&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)」を参照してください。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_native_scaleout"></a>Reporting Services ネイティブモードのスケールアウト配置のアップグレード
 複数のレポート サーバーにスケールアウトされる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードの配置をアップグレードする方法の概要を次に示します。 このプロセスでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 配置のダウンタイムが発生します。

1.  レポート サーバー データベースと暗号化キーをバックアップします。 詳細については、「[Reporting Services のバックアップおよび復元操作](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md)」および「[スケールアウト配置に関する暗号化キーの追加と削除 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)」を参照してください。

2.  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、スケールアウトした配置からすべてのレポート サーバーを削除します。 詳細については、「[ネイティブ モード レポート サーバーのスケールアウト配置の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)」を参照してください。

3.  いずれかのレポート サーバーを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]にアップグレードします。

4.  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して、スケールアウト配置にレポート サーバーを再度追加します。 詳細については、「[ネイティブ モード レポート サーバーのスケールアウト配置の構成 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)」を参照してください。

     各サーバーで、アップグレードおよびスケールアウトの手順を繰り返します。

##  <a name="bkmk_sharePoint_scenarios"></a>SharePoint モードのアップグレードと移行のシナリオ
 以下のセクションでは、sharepoint モードの[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]特定のバージョンから sharepoint モードに[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]アップグレードまたは移行するために必要な問題と基本的な手順について説明します。

 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードの配置をアップグレードするためのインストール コンポーネントは 2 つあります。

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 共有サービス。

    > [!TIP]
    >  
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint コマンドレット `Get-SPRSServiceApplicationServers` を使用して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービスを現在実行しているためアップグレードが必要なサーバーを SharePoint ファームで特定します。

-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 製品用アドイン。 詳細については、「sharepoint [&#40;sharepoint 2010 および sharepoint 2013&#41;の Reporting Services アドインのインストールまたはアンインストール](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。

 SharePoint モードのインストールを移行する方法については、「[Reporting Services のインストールの移行 &#40;SharePoint Mode&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)」を参照してください。

> [!IMPORTANT]
>  次のシナリオでは、異なるテクノロジをアップグレードする必要があるため、SharePoint 環境のダウンタイムが発生する場合があります。 ダウンタイムの発生を許容できない場合は、インプレース アップグレードではなく、移行操作を実行する必要があります。

### <a name="sssql11-to-sssql14"></a>[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]宛先[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **開始環境:** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]また[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]は、SharePoint 2010。

 **終了環境:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、sharepoint 2010、または sharepoint 2013。

-   **SharePoint 2010:** の[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]インプレースアップグレードはサポートされていますが、アップグレードシナリオでは SharePoint 環境のダウンタイムが発生します。

     終了環境で SharePoint 2013 も実行する場合は、SharePoint 2010 から SharePoint 2013 へのデータベース アタッチ アップグレードを完了する必要があります。

-   **SharePoint 2013:** Sharepoint 2013 では、SharePoint 2010 からのインプレースアップグレードはサポートされていません。 ただし、**データベースアタッチアップグレード**の手順はサポートされています。 インプレース アップグレードとデータベース アタッチ アップグレードの 2 つの基本的なアップグレード方法をユーザーが選択できた SharePoint 2010 へのアップグレードとは動作が異なります。

     SharePoint 2010 と統合された [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインストールを使用している場合は、SharePoint サーバーのインプレース アップグレードを行うことはできません。 ただし、SharePoint 2010 ファームから SharePoint 2013 ファームにコンテンツ データベースとサービス アプリケーション データベースを移行することは可能です。

### <a name="sskilimanjaro-to-sssql14"></a>[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]宛先[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **開始環境:** SQL Server 2008 R2、SharePoint 2010。

 **終了環境:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、SharePoint 2010。

-   インプレース アップグレードがサポートされ、SharePoint 環境のダウンタイムは発生しません。

-   ファーム内の各 Web フロントエンドに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの SharePoint 用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールします。 アドインをインストールするには、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを使用するか、またはアドインをダウンロードします。

-   インストール[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を実行して、各 "レポートサーバー" の SharePoint モードをアップグレードします。SQL Server インストールウィザードによってサービス[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]がインストールされ、新しいサービスアプリケーションが作成されます。

     終了環境で SharePoint 2013 も実行する場合は、SharePoint 2010 から SharePoint 2013 へのデータベース アタッチ アップグレードを完了する必要があります。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

### <a name="sskatmai-sp2-to-sssql14"></a>
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2 から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **開始環境:** [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2、SharePoint 2007。

 **終了環境:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、SharePoint 2010。

-   このインプレース アップグレード シナリオでは、SharePoint テクノロジと SQL Server テクノロジの両方をアップグレードする必要があるため、SharePoint 環境のダウンタイムが発生します。 状況によっては、インプレース アップグレードではなく移行操作を実行してください。

-   最初に [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] を Service Pack 2 (SP2) にアップグレードします (この操作を実行していない場合)。

-   SharePoint 2010 にアップグレードします。 SharePoint 2010 の必須コンポーネントのインストーラーを実行すると、SharePoint 2010 製品用 Reporting Services アドインがアップグレードされます。

-   すべての SharePoint Web フロントエンドに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールします。 SharePoint の必須コンポーネントのインストーラーを使用すると SQL Server 2008 R2 バージョンのアドインがインストールされますが、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーを操作するには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンが必要です。

-   > [!WARNING]
    >  SharePoint のアップグレードの後、レポート サービス環境は SQL Server がアップグレードされるまで非動作状態になります。

-   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードします。 SQL server インストールウィザードを実行すると、[**SQL Server Reporting Services SharePoint モード認証**] ダイアログに関するダイアログが表示されます。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスがインストールされ、認証ページの資格情報を使用して新しい SharePoint アプリケーション プールが作成されます。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

### <a name="sql-server-2005-sp2-to-sssql14"></a>SQL Server 2005 SP2 から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]
 **開始環境:** SQL Server 2005 SP2、SharePoint 2007。

 **終了環境:** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、SharePoint 2010。

-   このインプレース アップグレード シナリオでは、SharePoint テクノロジと SQL Server テクノロジの両方をアップグレードする必要があるため、SharePoint 環境のダウンタイムが発生します。 状況によっては、インプレース アップグレードではなく移行操作を実行してください。

-   最初に SQL Server 2005 を Service Pack 2 (SP2) にアップグレードします (この操作を実行していない場合)。

-   SharePoint 2010 にアップグレードします。 SharePoint 2010 の必須コンポーネントのインストーラーを実行すると、SharePoint 2010 製品用 Reporting Services アドインがアップグレードされます。

-   > [!WARNING]
    >  SharePoint のアップグレードの後、レポート サービス環境は SQL Server がアップグレードされるまで非動作状態になります。

-   すべての SharePoint Web フロントエンドに [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの SharePoint 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールします。 SharePoint の必須コンポーネントのインストーラーを使用すると SQL Server 2008 R2 バージョンのアドインがインストールされますが、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーを操作するには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンが必要です。

-   
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードします。 SQL Server インストール ウィザードを実行すると、[SQL Server Reporting Services SharePoint モード認証] ダイアログに関するダイアログが表示されます。 
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスがインストールされ、認証ページの資格情報を使用して新しい SharePoint アプリケーション プールが作成されます。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_migration_considerations"></a>移行に関する考慮事項
 アプリケーション データを移動する際には、次の問題と制限事項に注意する必要があります。

-   暗号化キーの保護には、コンピューターの ID を組み込んだハッシュが含まれます。

-   レポート サーバー データベース名は固定であり、新しいコンピューターで名前を変更することはできません。

### <a name="encryption-key-considerations"></a>暗号化キーに関する考慮事項
 レポート サーバー データベースを新しいコンピューターに移動する場合は、必ず事前に暗号化キーをバックアップします。

 レポート サーバー インストールを別のコンピューターに移動すると、レポート サーバー データベースに格納されている機微なデータを保護するために使用される暗号化キーを保護するハッシュが無効になります。 データベースを使用するレポート サーバー インスタンスは、それぞれに専用の暗号化キーのコピーを保持しています。これは、現在のコンピューターで定義されたサービス アカウントの ID で暗号化されています。 コンピューターを変更すると、新しいコンピューターで同じアカウント名を使用しても、サービスはそのキーにアクセスできなくなります。

 新しいレポート サーバー コンピューターで元に戻せる暗号化を再設定するには、事前にバックアップしたキーを復元する必要があります。 レポート サーバー データベースに格納されている完全なキーのセットは、対称キーの値、およびキーを格納したレポート サーバー インスタンスのみが使用できるようにキーへのアクセスを制限するための ID 情報で構成されています。 キーを復元するときに、レポート サーバーによって、キーの既存のコピーが新しいバージョンで置き換えられます。 新しいバージョンには、現在のコンピューターで定義されたコンピューター ID とサービス ID の値が含まれています。 詳細については、次のトピックを参照してください。

-   SharePoint モード: 詳細については、「[Reporting Services SharePoint サービス アプリケーションの管理](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)」の「キー管理」のセクションを参照してください。

-   ネイティブ モード: 「 [Reporting Services の暗号化キーのバックアップと復元](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)」を参照してください。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

### <a name="fixed-database-name"></a>固定されたデータベース名
 レポート サーバー データベースの名前は変更できません。 データベースの ID は、データベース作成時にレポート サーバーのストアド プロシージャで記録されます。 レポート サーバーのプライマリ データベースまたは一時データベースの名前を変更すると、プロシージャ実行時にエラーが発生し、レポート サーバー インストールが無効になります。

 既存のインストールのデータベース名が新しいインストールに適さない場合は、適切な名前で新しいデータベースを作成し、以下の方法で既存のアプリケーション データを読み込むことを検討してください。

-   レポート サーバー Web サービスの SOAP メソッドを呼び出してデータベース間でデータをコピーする [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] スクリプトを作成します。 スクリプトの実行には RS.exe ユーティリティを使用できます。 この方法の詳細については、「 [Reporting Services を使ったスクリプトの作成と PowerShell](../tools/scripting-and-powershell-with-reporting-services.md)」を参照してください。

-   WMI プロバイダーを呼び出してデータベース間でデータをコピーするコードを記述します。 このアプローチの詳細については、「 [Reporting Service WMI プロバイダーへのアクセス](../tools/access-the-reporting-services-wmi-provider.md)」を参照してください。

-   アイテム数が少ない場合は、レポート デザイナー、モデル デザイナー、およびレポート ビルダーから新しいレポート サーバーに、レポート、レポート モデル、および共有データ ソースを再パブリッシュできます。 ロールの割り当て、サブスクリプション、共有スケジュール、レポート スナップショット スケジュール、レポートやその他のアイテムに設定したカスタム プロパティ、モデル アイテム セキュリティ、およびレポート サーバーで設定したプロパティを再作成する必要があります。 レポート履歴およびレポート実行ログ データは失われます。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

##  <a name="bkmk_additional_resources"></a>その他のリソース

> [!NOTE]
>  SharePoint データベース アタッチ アップグレードの詳細については、以下を参照してください。

-   [SharePoint 2013 へのアップグレードプロセスの概要](https://go.microsoft.com/fwlink/p/?LinkId=256688)(https://go.microsoft.com/fwlink/p/?LinkId=256688).

-   https://go.microsoft.com/fwlink/p/?LinkId=256689) [SharePoint 2013 (にアップグレードする前に準備を整える](https://go.microsoft.com/fwlink/p/?LinkId=256689)。

-   https://go.microsoft.com/fwlink/p/?LinkId=256690) [SharePoint 2010 から sharepoint 2013 (にデータベースをアップグレード](https://go.microsoft.com/fwlink/p/?LinkId=256690)します。

 [このトピックの [](#bkmk_top) ![トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン"):

## <a name="see-also"></a>参照
 [アップグレードレポート](../../reporting-services/install-windows/upgrade-reports.md)[は、インストールウィザード &#40;セットアップを使用して SQL Server 2014 にアップグレード&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)


