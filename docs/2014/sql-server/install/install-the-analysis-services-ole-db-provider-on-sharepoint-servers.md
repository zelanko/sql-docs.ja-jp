---
title: SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2c62daf9-1f2d-4508-a497-af62360ee859
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c277319377fda81e0c1f6901b2d20a22b500415c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128569"
---
# <a name="install-the-analysis-services-ole-db-provider-on-sharepoint-servers"></a>SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール
  Microsoft OLE DB Provider for Analysis Services (MSOLAP) は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データを操作するためにクライアント アプリケーションで使用されるインターフェイスです。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を含んだ SharePoint 環境では、このプロバイダーによって [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する接続要求が処理されます。  
  
 データ プロバイダーは [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インストール パッケージ (spPowerPivot.msi) に含まれていますが、手動でインストールすることが必要な場合があります。 SharePoint サーバーにクライアント ライブラリまたはデータ プロバイダーを手動でインストールしなければならない理由が 2 つあります。  
  
-   **下位互換性を確保**します。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] のブックは、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの Analysis Services OLE DB プロバイダーを接続文字列に指定します。 したがって、要求を正常に終了させるには、このプロバイダー バージョンがコンピューターに存在する必要があります。  
  
-   **専用の Excel Services インスタンスでのデータ アクセスを有効にする**します。 SharePoint ファーム内の [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] がインストールされていないサーバー上に Excel Services が存在する場合は、[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] インストール パッケージを使用して、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] バージョンのプロバイダーおよびその他のクライアント接続コンポーネントをインストールしてください。  
  
    > [!NOTE]  
    >  これらのシナリオは、共存することができます。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インスタンスを使用せずに Excel Services を実行するアプリケーション サーバーを含むファーム上で複数のブック バージョンをホストするには、各 Excel Services コンピューターに古いバージョンと新しいバージョンのデータ プロバイダーをインストールする必要があります。  
  
  
##  <a name="bkmk_vers"></a> バージョンの PowerPivot データ アクセスをサポートしている OLE DB プロバイダー  
 SharePoint ファームには、PowerPivot データ アクセスをサポートしていない旧バージョンを含め、複数のバージョンの Analysis Services OLE DB プロバイダーが含まれていることがあります。  
  
 既定では、SharePoint 2010 により [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] バージョンのプロバイダーがインストールされます。 このバージョンは、MSOLAP.4 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 用に使用されるのと同じバージョン番号) として認識されますが、PowerPivot データ アクセス用には機能しません。 正常に接続するには、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンのプロバイダーが必要です。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] バージョン以降の OLE DB プロバイダーは、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ構造に対するトランスポートおよび接続をサポートしています。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックでは、このプロバイダーの新しいバージョンを使用して、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーからクエリ処理を要求します。 更新後のバージョンを入手するには、SQL Server 機能パックのページからダウンロードしてインストールします。  
  
 次の表に、有効なバージョンを示します。  
  
|製品バージョン|ファイル バージョン|有効な対象データ|  
|---------------------|------------------|----------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|ファイル システム内の MSOLAP100.dll<br /><br /> Excel 接続文字列内の MSOLAP.4<br /><br /> ファイル バージョン詳細の 10.50.1600 以降|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの PowerPivot for Excel を使用して作成されたデータ モデルに使用します。|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|ファイル システム内の MSOLAP110.dll<br /><br /> Excel 接続文字列内の MSOLAP.5<br /><br /> ファイル バージョン詳細の 11.0.0000 以降|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel を使用して作成されたデータ モデルに使用します。|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|ファイル システム内の MSOLAP120.dll<br /><br /> ファイル バージョン詳細の 12.0.20000 以降|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] モデル以外のデータ モデルに使用します。|  
  
  
##  <a name="bkmk_why"></a> OLE DB プロバイダーのインストールに必要な理由  
 ファーム内のサーバーに OLE DB プロバイダーを手動でインストールしなければならないケースとしては、2 つのシナリオが挙げられます。  
  
 **最も一般的なシナリオ**は古いバージョンと新しいバージョンの[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]に保存されているブックは、ファーム内のライブラリを文書化します。 組織内のアナリストを使用している場合、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]版[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]Excel、および、それらのブックを保存、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]インストールでは、古いブックは機能しません。 それらの接続文字列は古いバージョンのプロバイダーを参照しますが、旧バージョンのプロバイダーは、手動でインストールしない限りサーバー上に配置されません。 両方のバージョンをインストールすると、古いバージョンと新しいバージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成された PowerPivot ブックに対してデータ アクセスが可能になります。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のセットアップでは [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンのプロバイダーはインストールされないため、以前のバージョンのブックを使用している場合には、これを手動でインストールする必要があります。  
  
 **2 番目のシナリオ**しない場合は、Excel Services を実行している SharePoint ファームにサーバーがある場合は、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]します。 このような場合には、Excel Services を実行しているアプリケーション サーバーを、新しいバージョンのプロバイダーに手動で更新する必要があります。 これは、PowerPivot for SharePoint インスタンスに接続するために必要です。 Excel Services で以前のバージョンのプロバイダーを使用している場合は、接続要求が失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートするために必要なすべてのコンポーネントが確実にインストールされるように、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] セットアップまたは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] インストール パッケージ (spPowerPivot.msi) を使用してプロバイダーをインストールする必要があることに注意してください。  
  
  
##  <a name="bkmk_sql11"></a> Excel Services サーバーに SQL Server セットアップを使用して、SQL Server 2012 OLE DB プロバイダーをインストールします。  
 OLE DB プロバイダーおよび他のクライアント接続コンポーネントがまだインストールされていない SharePoint サーバー (同じハードウェア上に PowerPivot for SharePoint がない状態で Excel Services を実行しているアプリケーション サーバーなど) に OLE DB プロバイダーおよび他のクライアント接続コンポーネントを追加するには、次の説明に従います。  
  
 これらの手順を使用して、現在の Analysis Services OLE DB プロバイダーをインストールし、追加、 **Microsoft.AnalysisServices.Xmla.dll**をグローバル アセンブリ。  
  
#### <a name="run-sql-server-setup-and-install-the-client-connectivity-tools"></a>SQL Server セットアップの実行とクライアント接続ツールのインストール  
  
1.  Excel Services をホストするアプリケーション サーバー上で、SQL Server セットアップを実行します。  
  
2.  [インストール] ページで、次のように選択します。 **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**します。  
  
3.  インストールの種類 ページで、次のように選択します。 **SQL Server 2012 の新しいインストールを実行**します。  
  
4.  セットアップ ロール ページで、次のように選択します。 **SQL Server 機能のインストール**します。  
  
5.  **機能の選択**] ページで [ **Client Tools Connectivity**します。 このオプションはインストール**Microsoft.AnalysisServices.Xmla.dll**  
  
     それ以外の機能は選択しないでください。  
  
6.  をクリックして**次**をクリックしてウィザードを終了**インストール**セットアップを実行します。  
  
7.  Excel Services を実行しているが PowerPivot for SharePoint はインストールされていないサーバーが他にある場合は、前の手順を繰り返します。  
  
#### <a name="verify-msolap5-is-a-trusted-provider"></a>MSOLAP.5 が信頼できるプロバイダーであるかどうかの確認  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックし、Excel Services サービス アプリケーションをクリックします。  
  
2.  **[信頼できるデータ プロバイダー]** をクリックします。  
  
3.  MSOLAP.5 が一覧に表示されていることを確認します。 PowerPivot for SharePoint の構成方法によっては、MSOLAP.5 が既に信頼されている場合があります。 PowerPivot 構成ツールを使用したにもかかわらず、このアクションがタスクの一覧から除外された場合、MSOLAP.5 は Excel Services によって信頼されないため、手動で追加する必要があります。  
  
4.  MSOLAP が表示されない場合は、クリックして**信頼できるデータ プロバイダーの追加**します。  
  
5.  プロバイダー id では、次のように入力します。`MSOLAP.5`します。  
  
6.  [プロバイダーの種類] では、OLE DB が選択されていることを確認します。  
  
7.  [プロバイダーの説明] に、「 **Microsoft OLE DB プロバイダー (OLAP Services 11.0 用)**」と入力します。  
  
#### <a name="verify-installation"></a>インストールの確認  
  
1.  Program files\Microsoft Analysis Services\AS OLEDB\110 に移動します。  
  
2.  msolap110.dll を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[詳細]** をクリックします。  
  
4.  ファイルのバージョン情報が表示されます。 バージョンは 11.00.< を含める必要があります。\<buildnumber >。  
  
5.  Windows\assembly フォルダーで、Microsoft.AnalysisServices.Xmla.dll、バージョン 11.0.0.0 が表示されることを確認します。  
  
  
##  <a name="bkmk_install2012_from_sppowerpivot_msi"></a> For SharePoint のインストール パッケージ (spPowerPivot.msi)、PowerPivot を使用して、SQL Server 2012 OLE DB プロバイダーをインストールするには  
 インストール、[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]へ OLE DB プロバイダーと Excel Services のサーバーを使用して、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]インストール パッケージ **(spPowerPivot.msi)** します。  
  
#### <a name="download-the-msolap5-provider-from-the-includesssql11sp1includessssql11sp1-mdmd-feature-pack"></a>[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] Feature Pack から MSOLAP.5 プロバイダーをダウンロードします。  
  
1.  参照する[Microsoft® SQL Server® 2012 SP1 Feature Pack](http://www.microsoft.com/download/details.aspx?id=35580)  
  
2.  クリックして**インストール手順**します。  
  
3.  「Microsoft Analysis Services OLE DB Provider for Microsoft SQL Server 2012 SP1」セクションを参照します。 ファイルをダウンロードし、インストールを開始します。  
  
4.  **機能の選択**] ページで、[ **Analysis Services OLE DB Provider for SQL Server**します。 他のコンポーネントの選択を解除して、インストールを完了します。 SpPowerPivot.msi の詳細については、次を参照してください。[インストールまたは PowerPivot を SharePoint アドインのアンインストール&#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)します。  
  
5.  MSOLAP.5 を信頼できるプロバイダーとして SharePoint Excel Services に登録します。 詳細については、「 [Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加](http://technet.microsoft.com/library/hh758436.aspx)」を参照してください。  
  
  
##  <a name="bkmk_kj"></a> SQL Server 2008 R2 OLE DB プロバイダーを前にホストをインストールするバージョンのブック  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの MSOLAP.4 プロバイダーをインストールして、Microsoft.AnalysisServices.ChannelTransport.dll ファイルを登録するには、次の手順に従います。 ChannelTransport は Analysis Services OLE DB プロバイダーのサブコンポーネントです。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンのプロバイダーは、ChannelTransport を使用して接続を行うときにレジストリを読み取ります。 このファイルの登録は、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] サーバー上の [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] プロバイダーによって処理される接続にのみ必要なインストール後の手順です。  
  
#### <a name="step-1-download-and-install-the-client-library"></a>手順 1: クライアント ライブラリのダウンロードとインストール  
  
1.  [SQL Server 2008 R2 Feature Pack ページ](http://go.microsoft.com/fwlink/?LinkId=159570)、Microsoft SQL Server 2008 R2 用 Microsoft Analysis Services OLE DB Provider を検索します。  
  
2.  `SQLServer2008_ASOLEDB10.msi` インストール プログラムの x64 パッケージをダウンロードします。 ファイル名には SQLServer2008 が含まれていますが、これは SQL Server 2008 R2 バージョンのプロバイダーに対応する適切なファイルです。  
  
3.  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] がインストールされているコンピューターで、.msi を実行してライブラリをインストールします。  
  
4.  Excel Services を実行しているが [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] はインストールされていないサーバーが他にファーム内にある場合は、前の手順を繰り返して 2008 R2 バージョンのプロバイダーを Excel Services コンピューターにインストールします。  
  
#### <a name="step-2-register-the-microsoftanalysisserviceschanneltransportdll-file"></a>手順 2: Microsoft.AnalysisServices.ChannelTransport.dll ファイルの登録  
  
1.  regasm.exe ユーティリティを使用してファイルを登録します。 Regasm.exe を以前を実行していない場合は、その親フォルダーで C:\Windows\Microsoft.NET\Framework64\v4.0.30319 を追加\\、システム path 変数にします。  
  
2.  管理者権限でコマンド プロンプトを開きます。  
  
3.  C:\Windows\assembly\GAC_MSIL\Microsoft.AnalysisServices.ChannelTransport\10.0.0.0__89845dcd8080cc91 フォルダーに移動します。  
  
4.  次のコマンドを入力します。`regasm microsoft.analysisservices.channeltransport.dll`  
  
5.  2008 R2 バージョンのプロバイダーを手動でインストールしたすべてのコンピューターについて前の手順を繰り返します。  
  
#### <a name="verify-installation"></a>インストールの確認  
  
1.  これで、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] のブックのスライスまたはフィルター処理を行うことができるようになります。 エラーが発生した場合は、64 ビット版の regasm.exe を使用してファイルを登録したことを確認します。  
  
2.  さらに、ファイルのバージョンを確認することができます。  
  
     移動して`C:\Program files\Microsoft Analysis Services\AS OLEDB\10`します。 右クリック**msolap100.dll**選択**プロパティ**します。 **[詳細]** をクリックします。  
  
     ファイルのバージョン情報が表示されます。 バージョンは 10.50 を含める必要があります。\<buildnumber >。  
  
  
## <a name="see-also"></a>参照  
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
