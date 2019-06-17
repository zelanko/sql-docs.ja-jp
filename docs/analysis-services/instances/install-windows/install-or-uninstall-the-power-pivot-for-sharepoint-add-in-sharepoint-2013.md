---
title: インストールまたは Power Pivot の SharePoint アドインのアンインストール (SharePoint 2013) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1fdc41aaaad19317db3b3795cc63d137b19600c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63055269"
---
# <a name="install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013"></a>Power Pivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2013)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)][!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ファームでの [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] データ アクセスを提供するアプリケーション サーバー コンポーネントとバックエンド サービスのコレクションです。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint アドイン (**spPowerpivot.msi**) は、アプリケーション サーバー コンポーネントのインストールに使用されるインストーラー パッケージです。  
  
-   このアドインは、SharePoint 2010 の配置に必須ではありません。  
  
-   このアドインは、SharePoint 2013 と SharePoint モードの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] が含まれるシングル サーバー配置では必須ではありません。 アドインによってインストールされたコンポーネントは、SharePoint モードで [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サーバーをインストールするときに含まれます。 アドインを使用した配置例を示す図については、「 [SQL Server BI 機能の配置トポロジ](http://msdn.microsoft.com/library/39f76bc7-94e6-4dbc-bfa5-d56f4430bb26)」を参照してください。  
  
 **注:** このトピックでは、インストールについて説明します、[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]ソリューション ファイルと[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]for SharePoint 2013 構成ツール。 インストールが完了したら、構成ツールと追加機能について「[Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)」をご覧ください。  
  
 **spPowerPivot.msi**をダウンロードする方法の詳細については、「 [Microsoft® SQL Server® 2014 PowerPivot® for Microsoft SharePoint®](http://go.microsoft.com/fwlink/?LinkID=324854)」を参照してください。  
  
##  <a name="bkmk_background"></a> 背景情報  
  
-   **アプリケーション サーバー:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能には、データ ソースとしてのブックの使用、定期データ更新、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードなどが含まれます。  
  
     [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] Analysis Services クライアント ライブラリを配置し、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インストール ファイルをコンピューターにコピーする**Windows インストーラー パッケージ (** spPowerpivot.msi [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] ) です。 インストーラーは、SharePoint での [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能の配置や構成は行いません。 既定では、次のコンポーネントがインストールされます。  
  
    -   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013.このコンポーネントには、PowerShell スクリプト (.ps1 ファイル)、SharePoint ソリューション パッケージ (.wsp)、および SharePoint 2013 ファームに [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] を配置するための [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2013 構成ツールが含まれています。  
  
    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Analysis Services (MSOLAP)。  
  
    -   ADOMD.NET データ プロバイダー。  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分析管理オブジェクト。  
  
-   **バックエンド サービス:** 使用する場合[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]分析データを含むブックを作成する Excel、Excel Services を実行して、BI サーバー構成が必要[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]サーバー環境でそのデータにアクセスする SharePoint モードでします。 SQL Server セットアップは、SharePoint Server 2013 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。 Analysis Services には、SharePoint との依存関係はありません。  
  
     バックエンド サービスのインストール、アンインストール、構成の詳細については、次のトピックを参照してください。  
  
    -   [Power Pivot モードでの Analysis Services のインストール](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
    -   [Power Pivot for SharePoint のアンインストール](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
##  <a name="bkmk_where_to_install"></a> spPowerPivot.msi をインストールする場所  
 ベスト プラクティスとして、構成の一貫性を確保するために、SharePoint ファームのすべてのサーバー (アプリケーション サーバーや Web フロントエンド サーバーなど) に **spPowerPivot.msi** をインストールすることをお勧めします。 インストーラー パッケージには、Analysis Services データ プロバイダーと [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールが含まれています。 **spPowerPivot.msi** をインストールするときに、個々のコンポーネントを除外することで、インストールをカスタマイズできます。  
  
 **データ プロバイダー:** SharePoint と SQL Server のいくつかのテクノロジは、Excel Services、PerformancePoint Services、Power View などの Analysis Services データ プロバイダーを使用します。 **spPowerPivot.msi** をすべての SharePoint サーバーにインストールすると、Analysis Services データ プロバイダーの完全なセットと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の接続をファーム全体で常に使用できるようになります。  
  
> [!NOTE]  
>  Analysis Services データ プロバイダーは、 **spPowerPivot.msi**を使用して SharePoint 2013 サーバーにインストールする必要があります。 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Feature Pack に用意されている他のインストーラー パッケージには、この環境でデータ プロバイダーが必要とする SharePoint 2013 サポート ファイルが含まれていないため、これらのパッケージはサポートされていません。  
  
 **構成ツール:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] For SharePoint 2013 構成ツールは、SharePoint サーバーの 1 つのみで必要です。 ただし、ベスト プラクティスとして、マルチサーバー ファームでは少なくとも 2 台のサーバーに構成ツールをインストールし、一方のサーバーがオフラインの場合でも構成ツールにアクセスできるようにしておくことをお勧めします。  
  
##  <a name="bkmk_prereq"></a> 要件と前提条件  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SharePoint Server 2013。  
  
-   SharePoint 製品およびテクノロジの要件に従い、**spPowerPivot.msi** は 64 ビットのみです。  
  
-   内のサーバー[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]モード。 Excel Services では、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サーバーとして SQL Server Analysis Services インスタンスを使用します。 Analysis Services は、ローカル コンピューターでもリモート コンピューターでも実行できます。  
  
-   **権限:** [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] をインストールするには、現在のユーザーがコンピューターの管理者であり、SharePoint ファーム管理者グループのメンバーである必要があります。  
  
-   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] の要件と前提条件の詳細については、「 [SharePoint モードの Analysis Service サーバーのハードウェア要件とソフトウェア要件](http://msdn.microsoft.com/library/fb86ca0a-518c-4c61-ae78-7680c57fae1f)」を参照してください。  
  
##  <a name="bkmk_install"></a> Power Pivot for SharePoint をインストールするには  
 **spPowerpivot.msi** インストーラー パッケージは、グラフィカル ユーザー インターフェイスとコマンド ライン モードの両方をサポートしています。 どちらのインストール方法でも、管理者特権で .msi を実行する必要があります。 インストールが完了したら、構成ツールと追加機能について「[Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)」をご覧ください。  
  
### <a name="user-interface-installation"></a>ユーザー インターフェイスを使用したインストール  
 グラフィカル ユーザー インターフェイスを使用して [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] をインストールするには、次の手順を実行します。  
  
1.  **SpPowerPivot.msi**を実行します。  
  
2.  ウェルカム ページで **[次へ]** をクリックします。  
  
3.  使用許諾契約書を確認して同意し、 **[次へ]** をクリックします。  
  
4.  **[機能の選択]** ページでは、すべての機能が既定で選択されています。  
  
5.  **[次へ]** をクリックします。  
  
6.  **[インストール]** をクリックしてインストールを実行し、インストールを終了します。  
  
### <a name="command-line-installation"></a>コマンド ライン インストール  
 コマンド ライン インストールでは、管理権限でコマンド プロンプトを開き、 **spPowerPivot.msi**を実行します。 以下に例を示します。  
  
 `Msiexec.exe /i SpPowerPivot.msi`」を参照してください。  
  
 インストール ログを作成するには、MsiExec の標準のログ スイッチを使用します。 次の例では、"Install_Log.txt"を"v"詳細ログ スイッチを使用して、ログ ファイルを作成します。  
  
```  
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt  
```  
  
### <a name="quiet-command-line-installation-for-scripting"></a>スクリプト作成のためのサイレント コマンド ライン インストール  
 **/q** スイッチまたは **/quiet** スイッチを使用すると、ダイアログや警告が表示されない "サイレント" インストールを実行できます。 サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。  
  
> [!IMPORTANT]  
>  サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。 インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。  
  
 **サイレント インストールを行うには、次の手順を実行します。**  
  
1.  **管理者権限を使用して**コマンド プロンプトを開きます。  
  
2.  次のコマンドを実行します。  
  
    ```  
    Msiexec.exe /i spPowerPivot.msi /q  
    ```  
  
### <a name="command-line-installation-to-include-specific-components"></a>コマンド ラインを使用した特定のコンポーネントのインストール  
 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールは、すべての SharePoint サーバーで必須というわけではありません (ただし、必要なときに使用できるように、少なくとも 2 台のサーバーにインストールすることをお勧めします)。  
  
 spPowerPivot.msi をインストールするときに、コマンド ライン オプションを使用して、 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールではなく、データ プロバイダーなどの特定の項目をインストールすることができます。 構成ツール以外のすべてのコンポーネントをインストールするコマンド ラインの例を次に示します。  
  
```  
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"  
```  
  
|オプション|説明|  
|------------|-----------------|  
|Analysis_Server_SP_addin|[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成|  
|SQL_OLAPDM|MSOLAP|  
|SQL_ADOMD|ADOMD.net プロバイダー|  
|SQL_AMO|AMO プロバイダー|  
|SQLAS_SP_Common|SharePoint 2013 の Analysis Services 共通コンポーネント|  
  
##  <a name="bkmk_deploy_solution"></a> Power Pivot for SharePoint 2013 構成ツールを使用した SharePoint ソリューション ファイルのデプロイ  
 spPowerPivot.msi によって、3 つの SharePoint ソリューション ファイルがハード ドライブにコピーされます。 ソリューション ファイルのスコープは 1 つが Web アプリケーション レベル、残り 2 つがファーム レベルです。 次のファイルがあります。  
  
-   `PowerPivotFarmSolution.wsp`  
  
-   `PowerPivotFarm14Solution.wsp`  
  
-   `PowerPivotWebApplicationSolution.wsp`  
  
 ソリューション ファイルは次のフォルダーにコピーされます。  
  
 `ssInstallPathTools\PowerPivotTools\SPAddinConfiguration\Resources`  
  
 .msi をインストールした後、 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] 構成ツールを実行して、SharePoint ファームでソリューションを構成し、配置します。  
  
 **構成ツールを起動するには、次の手順を実行します。**  
  
 Windows スタート画面から「power」と、アプリの検索結果でクリック **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 構成**します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセットアップによって SharePoint 2010 と SharePoint 2013 のそれぞれの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールがインストールされるため、検索結果には 2 つのリンクが含まれる場合があります。 必ず SharePoint 2013 構成ツールの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] を起動してください。  
  
 ![2 つの PowerPivot 構成ツール](../../../analysis-services/instances/install-windows/media/as-powerpivot-configtools-bothicons.gif "2 つの PowerPivot 構成ツール")  
  
 **Or**  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** をポイントします。  
  
2.  [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]] をクリックします。  
  
3.  **[構成ツール]** をクリックします。  
  
4.  **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013 の構成**をクリックします。  
  
 構成ツールの詳細については、「 [Power Pivot Configuration Tools](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)」を参照してください。  
  
##  <a name="bkmk_remove_addin"></a> アドインのアンインストールまたは修復  
  
> [!CAUTION]  
>  **spPowerPivot.msi** をアンインストールすると、データ プロバイダーと構成ツールがアンインストールされます。 データ プロバイダーをアンインストールすると、サーバーは [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]に接続できなくなります。  
  
 [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] をアンインストールまたは修復するには、次のいずれかの方法を使用します。  
  
1.  **Windows コントロール パネル:** 選択[!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]  **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2013**します。 **[アンインストール]** または **[修復]** をクリックします。  
  
2.  spPowerPivot.msi を実行し、 **[削除]** または **[修復]** を選択します。  
  
 **コマンドライン:** 修復またはアンインストール[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]コマンド プロンプトを開き、コマンドラインを使用して SharePoint 2013 の**管理者のアクセス許可を持つ**次のコマンドのいずれかを実行します。  
  
-   修復するには、次のコマンドを実行します。  
  
    ```  
    msiexec.exe /f spPowerPivot.msi  
    ```  
  
 スイッチまたは  
  
-   アンインストールするには、次のコマンドを実行します。  
  
    ```  
    msiexec.exe /uninstall spPowerPivot.msi  
    ```  
  
  
