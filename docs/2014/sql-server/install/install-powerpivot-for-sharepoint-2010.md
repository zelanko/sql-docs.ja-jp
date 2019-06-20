---
title: PowerPivot for SharePoint 2010 のインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: eec38696-5e26-46fa-bc83-aa776f470ce8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8e1aa9411fbc11becf8e7b159c27ef609e38083b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094549"
---
# <a name="install-powerpivot-for-sharepoint-2010"></a>PowerPivot for SharePoint 2010 をインストールする
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] は、SharePoint 2010 ファームでの PowerPivot データ アクセスを提供する中間層のバックエンド サービスのコレクションです。 組織で分析データを格納するブックの作成にクライアント アプリケーション [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel 2010 を使用する場合、サーバー環境でそのデータにアクセスするには [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] が必要です。 このトピックでは、基本的なインストール プロセスについて説明し、PowerPivot を構成するために役立つその他のトピックに関する情報も示します。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 
  
 インストールする方法の詳細について[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]と[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、同じサーバーで、次を参照してください。[展開のチェックリスト。Reporting Services、Power View および PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)します。  
  
## <a name="prerequisites"></a>前提条件  
  
1.  SQL Server セットアップを実行するには、ローカル管理者である必要があります。  
  
2.  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 用に SharePoint Server 2010 Enterprise Edition が必要です。 評価版の Enterprise Edition を使用することもできます。  
  
3.  SharePoint Server 2010 SP2 をインストールする必要があります。 これがないと、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の機能を使用するようにファームを構成できません。  
  
4.  コンピューターがドメインに参加する必要があります。  
  
5.  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を準備するには、ドメイン ユーザー アカウントが必要です。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] のインストールでは、Analysis Services サービス アカウントは、サーバーの全体管理から管理できるように、ドメイン ユーザーである必要があります。 アカウントと資格情報を入力する、**サーバー構成**このドキュメントの手順の一部としてページ。  
  
6.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] インスタンスの名前を使用できる必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の名前付きインスタンスが既に存在するコンピューターに、PowerPivot for SharePoint をインストールすることはできません。  
  
7.  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インスタンスは、SQL Server フェールオーバー クラスターに含めることはできません。 SharePoint 製品の高可用性機能を使用します。 たとえば、Excel Services では PowerPivot for SharePoint サーバーの負荷分散が管理されます。 詳細については、次を参照してください。 [Excel Services の管理のデータ モデルの設定 (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx) (https://technet.microsoft.com/library/jj219780.aspx) します。  
  
8.  既存のファームに [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をインストールする場合は、クラシック モード認証用に構成されている SharePoint Web アプリケーションが 1 つ以上必要です。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスは、Web アプリケーションでクラシック モード認証がサポートされている場合にのみ機能します。 クラシック モードの要件の詳細については、次を参照してください。 [PowerPivot Authentication and Authorization](../../analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization.md)します。  
  
9. 次の追加トピックを確認し、システムとバージョンの要件を理解してください。  
  
    -   [SharePoint 2010 ファームで SQL Server BI 機能を使用するためのガイド](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="InstallSQL"></a> ステップ 1:PowerPivot for SharePoint インストールします。  
 この手順では、SQL Server セットアップを実行して [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をインストールします。 後続の手順では、サーバーをインストール後のタスクとして構成します。  
  
1.  インストール メディアを挿入または SQL Server のセットアップ ファイルを格納するフォルダーを開き、ダブルクリック**setup.exe**します。  
  
2.  クリックして**インストール**左側のナビゲーション ウィンドウでします。  
  
3.  **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。  
  
4.  **プロダクト キー**ページで、evaluation edition を指定するか、enterprise edition のライセンス コピーのプロダクト キーを入力します。  
  
     **[次へ]** をクリックします。  
  
5.  マイクロソフト ソフトウェア ライセンス条項に同意してください。カスタマー エクスペリエンスおよびエラー レポートもオンにしていただければさいわいです。 **[次へ]** をクリックします。  
  
6.  セットアップ ファイルの更新を求めるメッセージが表示されたら、その指示に従ってください。  
  
7.  **インストール ルール** ページで、セットアップのインストールを妨げる可能性のある問題を識別します。 リストを調べて、発生する可能性のある問題がシステムで検出されたかどうかを確認してください。  
  
    > [!NOTE]  
    >  Windows ファイアウォールが有効になっているので、ポートを開いてリモート アクセスを有効にするように求める警告が表示されます。 この警告は、通常、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のインストールには該当しません。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のサービスとデータ ファイルへの接続は、SharePoint サービス間の通信用に既に開かれている SharePoint ポートを使用して確立されます。  
  
     **[次へ]** をクリックします。 SQL Server セットアップ プログラム ファイルがサーバーにインストールされるまで待機します。  
  
8.  **[セットアップ ロール]** ページで、 **[SQL Server PowerPivot for SharePoint]** を選択します。  
  
9. オプションで、データベース エンジンのインスタンスをインストールに追加することができます。 新しいファームを設定して、データベース サーバーをファームの構成およびコンテンツ データベースを実行する必要がある場合に、これを行う場合があります。 データベース エンジンを追加した場合は、PowerPivot 名前付きインスタンスとしてインストールされます。 (たとえば、ファーム構成ウィザードでファームを構成するウィザードを使用している場合)、このインスタンスへの接続は、次の形式でデータベース名を入力するかを指定する必要がある場合: <`servername`> \PowerPivot します。  
  
     ![GMNI_SetupUI_FeatureRole](../../../2014/sql-server/install/media/gmni-setupui-featurerole.gif "GMNI_SetupUI_FeatureRole")  
  
10. **[次へ]** をクリックします。  
  
11. **機能の選択**情報提供を目的のページで、インストールされる機能の読み取り専用の一覧が表示されます。 このロールに対してあらかじめ選択されている項目を、追加または削除することはできません。 **[次へ]** をクリックします。  
  
12. **機能ルール**] ページで [**次**します。 このページはスキップされる場合があります。  
  
13. **[インスタンスの構成]** ページに、"PowerPivot" というインスタンス名が表示されます。この名前は情報として示されており、読み取り専用になっています。 このインスタンスの名前の**POWERPIVOT**は**ために必要なため、変更できません**します。 ただし、ディレクトリ名とレジストリ キーをわかりやすく示した独自のインスタンス ID を入力することができます。 **[次へ]** をクリックします。  
  
14. **サーバー構成**ページで、必要なアカウント情報を入力します。  
  
     SQL Server Analysis Services については、ドメイン ユーザー アカウントを指定する必要があります。 ビルトイン アカウントを指定しないでください。 ドメイン アカウントは、Analysis Services サービス アカウントを管理するために必要な*管理アカウント*SharePoint サーバーの全体管理でします。  
  
     ![SSAS サーバーの構成](../../../2014/sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS サーバーの構成")  
  
     SQL Server データベース エンジンと SQL Server エージェントを追加した場合は、サービスがドメイン ユーザー アカウントまたは既定の仮想アカウントで実行されるように構成できます。  
  
     サービスを提供するために、自分のドメイン ユーザー アカウントを使用しないでください。 このようなアカウントを使用すると、ネットワークのリソースに対して持っている権限と同じ権限をサーバーに付与することになります。 悪意のあるユーザーがサーバーに侵入した場合、そのユーザーは管理者のドメイン資格情報でログインし、管理者と同じデータやアプリケーションをダウンロードしたり使用したりできるようになります。  
  
15. **[次へ]** をクリックします。  
  
16. データベース エンジンをインストールする場合は、[データベース エンジンの構成] ページが表示されます。 データベース エンジンの構成] をクリックして **[現在のユーザー**ユーザー、データベース エンジン インスタンスに対するアカウント管理者のアクセス許可を付与します。 クリックして**追加**アカウントを追加します。 **[次へ]** をクリックします。  
  
17. **[Analysis Services の構成]** ページで、 **[現在のユーザーの追加]** をクリックして、ユーザー アカウントに管理権限を付与します。 セットアップの完了後にサーバーを構成するには、管理権限が必要になります。  
  
18. 同じページにも管理者権限が必要なすべての個人の Windows ユーザー アカウントを追加します。 たとえば、データベースの接続に関する問題のトラブルシューティングを行ったりバージョン情報を取得したりするために、SQL Server Management Studio で [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスに接続するユーザーには、サーバーに対するシステム管理者権限が必要です。 サーバーのトラブルシューティングや管理を担当する可能性があるユーザーのユーザー アカウントをここで追加しておきます。  
  
19. **[次へ]** をクリックします。  
  
20. をクリックして**次**to Install ページの準備完了に到達するまでの残りのページの各します。  
  
21. **[インストール]** をクリックします。  
  
> [!TIP]  
>  トラブルシューティングする必要がある場合は、SQL Server のインストールを参照してください[ビューと読み取り SQL Server セットアップ ログ ファイル](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)します。  
  
##  <a name="bkmk_config"></a> ステップ 2:サーバーを構成します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] データベース サーバーを使用する [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または SharePoint ファームを構成する前に、SharePoint 2010 SP2 をインストールする必要があります。 サービス パックをインストールしていない場合は、サーバーの構成を始める前にここでインストールしてください。  
  
 サーバーが構成されるまでは、インストールは完了しません。 このリリースでは、サーバーの構成は常に、次の方法のいずれかを使用して、インストール後のタスクとして実行します。[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]構成ツール、サーバーの全体管理、または PowerShell。 続行するには、次のいずれかのアプローチを使用します。  
  
-   [SharePoint 2010 用 PowerPivot 構成または修復&#40;PowerPivot 構成ツール&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)  
  
-   [サーバーの全体管理での PowerPivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
-   [Windows PowerShell を使用した PowerPivot の構成](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)  
  
 **データベース エンジンのインスタンスに接続します。** [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] をインストールしたときに、SQL Server セットアップで、データベース エンジンのインスタンスをインストールに追加することができました。 可能性がありますを追加した、データベース エンジンのインスタンスをインストールには新しいファームを設定して、データベース サーバーをファームの構成とコンテンツ データベースを実行する必要があります。 データベース エンジンを追加した場合は、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の名前付きインスタンスとしてインストールされています。 この形式でデータベース名を入力に注意してください (たとえば、ファーム構成ウィザードでファームを構成するウィザードを使用している場合)、このインスタンスへの接続を指定する必要がある場合: <`servername`> \PowerPivot します。  
  
##  <a name="bkmk_redist"></a> ステップ 3:Excel Services アプリケーション サーバーへの Analysis Services OLE DB プロバイダーのインストール  
 個々のアプリケーション サーバーで Excel Calculation Services と [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] を実行する場合は、追加のインストール手順が必要となります。 Excel Calculation Services を実行しているアプリケーション サーバーに、適切なバージョンの Analysis Services OLE DB (MSOLAP) プロバイダーをインストールします。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの MSOLAP は SQL Server セットアップに含まれているため、アプリケーション サーバーが PowerPivot アプリケーション サーバーではない場合にのみ、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの MSOLAP を明示的にインストールする必要があります。  
  
    > [!NOTE]  
    >  Excel Calculation Services アプリケーション サーバーは、ファイルのインスタンスも必要があります。 **Microsoft.AnalysisServices.Xmla.dll** 、グローバル アセンブリ。 アプリケーション サーバーに .dll をインストールするには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をインストールします。 「管理ツール - 完全」を選択、**機能の選択**SQL Server セットアップ ウィザードのページ。  
  
-   アプリケーション サーバーで古い [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックをサポートする必要がある場合は、SQL Server 2008 R2 バージョンの MSOLAP をインストールする必要があります。  
  
 検証の手順を含め、プロバイダーのインストールの詳細については、次を参照してください[SharePoint サーバーに、Analysis Services OLE DB プロバイダーをインストールする。](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
##  <a name="bkmk_verify"></a> 手順 4:インストールを確認します。  
 この最後の手順では、SharePoint 2010 と [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] の両方が完全に機能することを確認します。 手順については、次を参照してください。 [for SharePoint のインストール Verify a PowerPivot](../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md)します。  
  
## <a name="see-also"></a>参照  
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [配置のチェックリスト:Reporting Services、Power View および PowerPivot for SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)   
 [配置のチェックリスト:SharePoint 2010 ファームに PowerPivot サーバーの追加によるスケール アウト](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)   
 [配置のチェックリスト:PowerPivot for SharePoint 2010 のマルチ サーバー インストール](../../../2014/sql-server/install/deployment-checklist-multiserver-installation-powerpivot-sharepoint-2010.md)  
  
  
