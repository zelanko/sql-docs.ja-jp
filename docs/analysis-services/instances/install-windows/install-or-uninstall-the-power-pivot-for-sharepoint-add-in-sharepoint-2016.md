---
title: "インストールまたは Power Pivot の SharePoint アドインのアンインストール (SharePoint 2016) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34dd07b8-d59d-49ce-bad0-74f40e4db0b8
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c2f754a253e2c33555712dd456002ed69b608188
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2016"></a>PowerPivot for SharePoint アドインのインストールまたはアンインストール (SharePoint 2016)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] は、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ファームでの [!INCLUDE[SPS2016](../../../includes/sps2016-md.md)] データ アクセスを提供するアプリケーション サーバー コンポーネントとバックエンド サービスのコレクションです。 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint アドイン (**spPowerpivot16.msi**) は、アプリケーション サーバー コンポーネントのインストールに使用されるインストーラー パッケージです。  
  
 **注:** このトピックでは、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ソリューション ファイルと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for SharePoint 2016 構成ツールのインストールについて説明します。 インストールが完了したら、構成ツールと追加機能について「[Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)」をご覧ください。  
  
 **spPowerPivot16.msi**をダウンロードする方法については、「 [Microsoft® SQL Server® 2016 Power Pivot® for Microsoft SharePoint®](https://www.microsoft.com/download/details.aspx?id=52675)」をご覧ください。  
  
##  <a name="bkmk_background"></a> 背景情報  
  
-   **アプリケーション サーバー:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能には、データ ソースとしてのブックの使用、定期データ更新、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理ダッシュボードなどが含まれます。  
  
     [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] は、Analysis Services クライアント ライブラリをデプロイし、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インストール ファイルをコンピューターにコピーする**Windows インストーラー パッケージ (**spPowerpivot16.msi [!INCLUDE[ssGeminiShort2017](../../../includes/ssgeminishort2017-md.md)] ) です。 インストーラーは、SharePoint での [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 機能の配置や構成は行いません。 既定では、次のコンポーネントがインストールされます。  
  
    -   [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)]」をご覧ください。 このコンポーネントには、PowerShell スクリプト (.ps1 ファイル)、SharePoint ソリューション パッケージ (.wsp)、および SharePoint 2016 ファームに [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] をデプロイするための [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールが含まれています。  
  
    -   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Analysis Services (MSOLAP)。  
  
    -   ADOMD.NET データ プロバイダー。  
  
    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分析管理オブジェクト。  
  
-   **バックエンド サービス:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] for Excel を使用して分析データが含まれたブックを作成した場合、サーバー環境でそのデータにアクセスするには、BI サーバーが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] モードで [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] を実行するように Office Online Server を構成する必要があります。 SQL Server セットアップは、SharePoint Server 2016 がインストールされているコンピューターで実行することも、SharePoint ソフトウェアがインストールされていない別のコンピューターで実行することもできます。 Analysis Services には、SharePoint との依存関係はありません。  
  
     バックエンド サービスのインストール、アンインストール、構成の詳細については、次のトピックを参照してください。  
  
    -   [Power Pivot モードでの Analysis Services のインストール](../../../analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
    -   [Power Pivot for SharePoint のアンインストール](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)  
  
##  <a name="bkmk_where_to_install"></a> spPowerPivot16.msi をインストールする場所  
 ベスト プラクティスとして、構成の一貫性を確保するために、SharePoint ファームのすべてのサーバー (アプリケーション サーバーや Web フロントエンド サーバーなど) に **spPowerPivot16.msi** をインストールすることをお勧めします。 インストーラー パッケージには、Analysis Services データ プロバイダーと [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成ツールが含まれています。 **spPowerPivot16.msi** をインストールするときに、個々のコンポーネントを除外することで、インストールをカスタマイズできます。  
  
 **データ プロバイダー:** SharePoint と SQL Server のいくつかのテクノロジで Analysis Services データ プロバイダー (PerformancePoint Services や Power View など) が使用されます。 **spPowerPivot16.msi** をすべての SharePoint サーバーにインストールすると、Analysis Services データ プロバイダーの完全なセットと [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] の接続をファーム全体で常に使用できるようになります。  
  
> [!NOTE]  
>  Analysis Services データ プロバイダーは、 **spPowerPivot16.msi**を使用して SharePoint 2016 サーバーにインストールする必要があります。 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Feature Pack に用意されている他のインストーラー パッケージには、この環境でデータ プロバイダーが必要とする SharePoint 2016 サポート ファイルが含まれていないため、これらのパッケージはサポートされていません。  
  
 **構成ツール:** [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成ツールが必須となる SharePoint サーバーは 1 台だけです。 ただし、ベスト プラクティスとして、マルチサーバー ファームでは少なくとも 2 台のサーバーに構成ツールをインストールし、一方のサーバーがオフラインの場合でも構成ツールにアクセスできるようにしておくことをお勧めします。  
  
##  <a name="bkmk_prereq"></a> 要件と前提条件  
  
-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SharePoint Server 2016。  
  
-   SharePoint 製品およびテクノロジの要件に従うと、**spPowerPivot16.msi** は 64 ビットのみです。  
  
-   内のサーバー[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]モード。 Office Online Server では、 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] サーバーとして SQL Server Analysis Services インスタンスを使用します。 Analysis Services は、ローカルの SharePoint サーバーでもリモート コンピューターでも実行できます。 Office Online Server にインストールすることはできません。  
  
-   **権限:** [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)]をインストールするには、現在のユーザーがコンピューターの管理者であり、SharePoint ファーム管理者グループのメンバーである必要があります。  
  
-   [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] の要件と前提条件の詳細については、「 [SharePoint モードの Analysis Service サーバーのハードウェア要件とソフトウェア要件](http://msdn.microsoft.com/library/fb86ca0a-518c-4c61-ae78-7680c57fae1f)」をご覧ください。  
  
##  <a name="bkmk_install"></a> Power Pivot for SharePoint をインストールするには  
 **spPowerpivot16.msi** インストーラー パッケージは、グラフィカル ユーザー インターフェイスとコマンド ライン モードの両方をサポートしています。 どちらのインストール方法でも、管理者特権で .msi を実行する必要があります。 インストールが完了したら、構成ツールと追加機能について「[Power Pivot の構成とソリューションの配置 &#40;SharePoint 2013&#41;](../../../analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013.md)」をご覧ください。  
  
### <a name="user-interface-installation"></a>ユーザー インターフェイスを使用したインストール  
 グラフィカル ユーザー インターフェイスを使用して [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] をインストールするには、次の手順を実行します。  
  
1.  **spPowerPivot16.msi**を実行します。  
  
2.  ウェルカム ページで **[次へ]** を選択します。  
  
3.  使用許諾契約書を確認して同意し、 **[次へ]**を選択します。  
  
4.  **[機能の選択]** ページでは、すべての機能が既定で選択されています。  
  
5.  **[次へ]** を選択します。  
  
6.  **[インストール]** を選択してインストールし、インストールを終了します。  
  
### <a name="command-line-installation"></a>コマンド ライン インストール  
 コマンド ライン インストールでは、管理権限でコマンド プロンプトを開き、 **spPowerPivot16.msi**を実行します。 例:  
  
 `Msiexec.exe /i spPowerPivot16.msi`」をご覧ください。  
  
 インストール ログを作成するには、MsiExec の標準のログ スイッチを使用します。 次の例では、"v" 詳細ログ スイッチを使用して、ログ ファイル "Install_Log.txt" を作成します。  
  
```  
Msiexec.exe /i spPowerPivot16.msi /L v c:\test\Install_Log.txt  
```  
  
### <a name="quiet-command-line-installation-for-scripting"></a>スクリプト作成のためのサイレント コマンド ライン インストール  
 **/q** スイッチまたは **/quiet** スイッチを使用すると、ダイアログや警告が表示されないサイレント インストールを実行できます。 サイレント インストールは、アドインのインストールのスクリプトを作成する場合に役立ちます。  
  
> [!IMPORTANT]  
>  サイレント コマンド ライン インストールで **/q** スイッチを使用する場合、使用許諾契約書は表示されません。 インストール方法にかかわらず、このソフトウェアの使用は、使用許諾契約に基づいています。ユーザーは使用許諾契約に準拠する責任があります。  
  
 **サイレント インストールを行うには、次の手順を実行します。**  
  
1.  **管理者権限を使用して**コマンド プロンプトを開きます。  
  
2.  次のコマンドを実行します。  
  
    ```  
    Msiexec.exe /i spPowerPivot16.msi /q  
    ```  
  
### <a name="command-line-installation-to-include-specific-components"></a>コマンド ラインを使用した特定のコンポーネントのインストール  
 [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成ツールは、すべての SharePoint サーバーで必須というわけではありません (ただし、必要なときに使用できるように、少なくとも 2 台のサーバーにインストールすることをお勧めします)。  
  
 spPowerPivot16.msi をインストールするときに、コマンド ライン オプションを使用して、 [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成ツールではなく、データ プロバイダーなどの特定の項目をインストールすることができます。 構成ツール以外のすべてのコンポーネントをインストールするコマンド ラインの例を次に示します。  
  
```  
Msiexec /i spPowerPivot16.msi AGREETOLICENSE="yes" ADDLOCAL=” SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common”  
```  
  
|オプション|Description|  
|------------|-----------------|  
|Analysis_Server_SP_addin16|[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成|  
|SQL_OLAPDM|SQL Server 2016 の Analysis Services OLE DB プロバイダー|  
|SQL_ADOMD|ADOMD.NET プロバイダー|  
|SQL_AMO|SQL Server 2016 の Analysis Management Objects (AMO) プロバイダー|  
|SQLAS_SP16_Common|SharePoint 2016 の Analysis Services 共通コンポーネント|  
  
##  <a name="bkmk_deploy_solution"></a> PowerPivot for SharePoint 2016 構成ツールを使用した SharePoint ソリューション ファイルのデプロイ  
 spPowerPivot16.msi によって、3 つの SharePoint ソリューション ファイルがハード ドライブにコピーされます。 ソリューション ファイルのスコープは 1 つが Web アプリケーション レベル、残り 2 つがファーム レベルです。 次のファイルがあります。  
  
-   `PowerPivot16FarmSolution.wsp`  

-   `PowerPivot16WebApplicationSolution.wsp`  
  
 ソリューション ファイルは次のフォルダーにコピーされます。  
  
 `ssInstallPathTools\PowerPivotTools\SPAddinConfiguration\Resources`  
  
 .msi をインストールした後、 [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成ツールを実行して、SharePoint ファームでソリューションを構成し、配置します。  
  
 **構成ツールを起動するには、次の手順を実行します。**  
  
 Windows のスタート画面から「power」と入力し、[アプリ] の検索結果で **[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] の構成**を選択します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のセットアップによって SharePoint 2013 と SharePoint 2016 のそれぞれの [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 構成ツールがインストールされるため、検索結果には 2 つのリンクが含まれる場合があることに注意してください。 必ず [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] 構成ツールを起動してください。  
  
 ![PowerPivot for SharePoint 2016 構成](../../../analysis-services/instances/install-windows/media/powerpivot-for-sharepoint-2016-configuration.png "PowerPivot for SharePoint 2016 構成")  
  
 **Or**  
  
1.  **[スタート]**ボタンをクリックし、 **[すべてのプログラム]**をポイントします。  
  
2.  [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]] を選択します。  
  
3.  **[構成ツール]**を選択します。  
  
4.  **[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] の構成**を選択します。  
  
 構成ツールの詳細については、「 [Power Pivot Configuration Tools](../../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools.md)」をご覧ください。  
  
##  <a name="bkmk_remove_addin"></a> アドインのアンインストールまたは修復  
  
> [!CAUTION]  
>  **spPowerPivot16.msi** をアンインストールすると、データ プロバイダーと構成ツールがアンインストールされます。 データ プロバイダーをアンインストールすると、サーバーは [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]に接続できなくなります。  
  
 [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] をアンインストールまたは修復するには、次のいずれかの方法を使用します。  
  
1.  **Windows コントロール パネル:** [ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]**[!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)]**] を選択します。 **[アンインストール]** または **[修復]**を選択します。  
  
2.  spPowerPivot16.msi を実行し、 **[削除]** オプションまたは **[修復]** オプションを選択します。  
  
 **コマンド ライン:** コマンド ラインを使用して [!INCLUDE[ssGeminiShort2016](../../../includes/ssgeminishort2016-md.md)] を修復またはアンインストールするには、 **管理者権限で** コマンド プロンプトを開き、次のいずれかのコマンドを実行します。  
  
-   修復するには、次のコマンドを実行します。  
  
    ```  
    msiexec.exe /f spPowerPivot16.msi  
    ```  
  
 スイッチまたは  
  
-   アンインストールするには、次のコマンドを実行します。  
  
    ```  
    msiexec.exe /uninstall spPowerPivot16.msi  
    ```  
  
  
