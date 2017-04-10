---
title: "PowerShell scripting in Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 60bb9610-7229-42eb-a95f-a377268a8720
caps.latest.revision: 44
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 44
---
# PowerShell scripting in Analysis Services
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のサーバー、テーブル、多次元オブジェクトに移動し、管理し、クエリを実行するための PowerShell コンポーネントが含まれています。  
  
-   **SQLAS** プロバイダーは、オブジェクト階層のナビゲーションに使用され、Analysis Services のローカル インスタンスがある場合に使用できます (サーバー モードは関係ありません)。  
  
-   **SQLASCMDLETS** モジュールには、バックアップ、復元、処理など、タスク固有のコマンドレットと、XMLA または Tabular Model Scripting Language (TMSL) のクエリまたはスクリプトの入力ファイルを受け取る汎用 [Invoke-ASCmd コマンドレット](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)が含まれています。  
  
 どちらのコンポーネントも Analysis Services 管理オブジェクト ([Microsoft.AnalysisServices Namespace](http://msdn.microsoft.com/library/ms146720\(SQL.130\).aspx)) 管理インターフェイスのサブセットを実装し、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトを管理し、作成するためのコマンドレットを提供します。  どちらも SQL Server の **SQLPS** ルート モジュールの拡張です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell コンポーネントを使用するには、最初に **SQLPS** をインポートします。 すべてのコマンドレットの構文と例は「 [Analysis Services PowerShell Reference](../../analysis-services/powershell/analysis-services-powershell-reference.md)」で確認できます。  PowerShell で AMO タイプを利用して表形式データベースを作成する方法については、「 [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md)」をご覧ください。  
  
##  <a name="bkmk_prereq"></a> 手順 1: PowerShell コンポーネントのインストール  
 PowerShell コンポーネントを取得する方法としては、SQL Server Management Studio (SSMS) のインストールが推奨されます。 この方法では、SQL Serverの PowerShell モジュールと Analysis Services Management (AMO) データ プロバイダーが提供されます。 SSMS により、XMLA 入力や TMSL 入力を簡単に生成し、PowerShell スクリプトで使用するためのツールも与えられます。  
  
 Analysis Services のローカル インスタンスのインストールを検討してください。 ローカル インスタンスをインストールすれば、データベースのホストに利用しない場合でも、 **SQLAS** プロバイダー経由でオブジェクト階層を移動できます。  
  
1.  [[SQL Server Management Studio のダウンロード]](https://msdn.microsoft.com/en-us/library/mt238290.aspx) で最新版の Management Studio を入手できます。 Management Studio の最新リリース。 互換レベル 1200 で作成された表形式モデルに関して、表形式メタデータ オブジェクト定義をサポートする、更新された AMO が含まれています。  
  
2.  Management Studio をインストールしたら、PowerShell ウィンドウを開きます。 管理ウィンドウにする必要はありません。  
  
3.  **SQLPS** モジュールと **SQLASCMDLETS** モジュールが一覧に表示されていることを確認するには、`Get-Module -ListAvailable` を入力します。  
  
     Analysis Services のローカル インスタンスもインストールしない限り、**SQLAS** は表示されません (表形式または多次元モード)。  
  
4.  `Get-Command -Module sqlascmdlets` を入力すると、Analysis Services 管理に使用されるコマンドレットの一覧が作成されます。  
  
     **SQLASCMDLETS** は、 **SQLAS** プロバイダーがないときでも利用できます。  
  
    -   [Add-RoleMember コマンドレット](../../analysis-services/powershell/add-rolemember-cmdlet.md)  
  
    -   [Backup-ASDatabase コマンドレット](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)  
  
    -   [Invoke-ASCmd コマンドレット](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)**-inputfile**  
  
    -   [Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)  
  
    -   [Invoke-ProcessCube コマンドレット](../../analysis-services/powershell/invoke-processcube-cmdlet.md)  
  
    -   [Invoke-ProcessDimension コマンドレット](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)  
  
    -   [Invoke-ProcessPartition コマンドレット](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)  
  
    -   [Invoke-ProcessTable コマンドレット](../../analysis-services/powershell/invoke-processtable-cmdlet.md)  
  
    -   [Merge-Partition コマンドレット](../../analysis-services/powershell/merge-partition-cmdlet.md)  
  
    -   [New-RestoreFolder コマンドレット](../../analysis-services/powershell/new-restorefolder-cmdlet.md)  
  
    -   [New-RestoreLocation コマンドレット](../../analysis-services/powershell/new-restorelocation-cmdlet.md)  
  
    -   [Remove-RoleMember コマンドレット](../../analysis-services/powershell/remove-rolemember-cmdlet.md)  
  
    -   [Restore-ASDatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)  
  
> [!NOTE]  
>  新しいバージョンの Windows オペレーティング システムでは、既定で Windows PowerShell がインストールされます。 4.0 以降が推奨されます。  
  
## 手順 2: コンポーネントを読み込み、対話型セッションを開始する  
 コンポーネントのインストール後、コンポーネントを読み込むと、対話型セッションが開始されます。  
  
1.  `Import-Module sqlps -DisableNameChecking`を入力します。  
  
     SQL Server PowerShell コンポーネント (Analysis Services のコンポーネントを含む) を読み込み、無効な動詞名に関する警告を非表示にします。  
  
2.  次のように入力します。 `sqlserver:`  
  
     プロンプトが **PS SQLSERVER:\\>** に変わるはずです。  
  
3.  Analysis Services がローカルにインストールされている場合は、オブジェクト階層を移動できます。 `cd sqlas` を入力して、**SQLAS** プロバイダーを開きます。  
  
4.  `dir` を入力すると、Analysis Services インスタンスが一覧表示されます。 プロバイダーでは、表形式インスタンスと多次元インスタンスが区別されません。  
  
## Permissions  
 対話型 PowerShell セッションは、セッションを始めたユーザーのセキュリティ ID で実行されます。 ほとんどの作業で、セッションを始めたユーザーが Analysis Services サーバー管理者でもあることが求められます。  
  
 スケジュールされた PowerShell タスクは、無人操作と見なすべきです。 SQL Server Agent サービスなどのスケジューラーを実行するアカウントは、多くの場合、Analysis Services 管理者であることが求められます (タスクによります)。  
  
 既定のバックアップ ディレクトリやデータ ディレクトリなど、ローカルのデータ フォルダーは、ファイル システム権限により既に構成されています。この権限は、それらの場所の読み書きをローカル インスタンスに許可するものです。  
  
 リモート管理では、特に Analysis Services がインストールされていないクライアント コンピューターから実行するとき、操作を実行するリモート Analysis Services インスタンスに、復旧時にファイルを読み込み、バックアップ時にファイルを書き込むためのファイル システム権限を与える必要があります。  
  
## スクリプト入力ファイル: ASSL/XMLA または TMSL  
 **invoke-ascmd** を利用してスクリプトを実行する場合、サーバー モード、データベースの種類、互換性レベルがスクリプトの実行方法で考慮されます。  
  
-   互換性レベルが 1050-1103 の多次元データベースまたは表形式データベースは XMLA で記述されたスクリプトに応答します (Analysis Services オブジェクト定義固有の ASSL 拡張を利用)。  
  
-   SQL Server 2016 の表形式データベース (互換性レベル 1200) は TMSL スクリプトに応答します。  
  
 同じ SQL Server 2016 インスタンスでバージョン混在の表形式モデルを使用する場合、必ず適切なスクリプトをご利用ください。  
  
> [!NOTE]  
>  スクリプトは SQL Server Management Studio で生成し、必要に応じて変更できます。 互換性レベルが 1200 の表形式データベースのスクリプトは TMSL で作成されます。 その他のスクリプトは XMLA/ASSL で作成されます。 表形式モードの SQL Server 2016 インスタンスは両方のスクリプト言語に対応しています。  
  
## ローカル管理とリモート管理  
 PowerShell による Analysis Services のローカル管理が簡単な 2 つの理由:  
  
-   **SQLAS** プロバイダーを使用し、オブジェクト階層をナビゲートできます。  
  
-   バックアップ作業や復旧作業など、既定のデータ フォルダーからの読み取りを Analysis Services に許可するファイル権限が既に置かれています。これらのフォルダーをデータベースの場所として利用し、操作にローカルのサーバー インスタンスが使用されることが想定されています。  
  
 リモート インスタンスを管理するには、追加の構成が必要になります。 次の手順では、Management Studio のインストール手順を完了しているが、サービス インスタンスがリモート コンピューターにあるものと想定されています。 Analysis Services サーバーに対する管理者権限が必要です。  
  
 Analysis Services はリモートであるため、オブジェクト階層をローカルでナビゲートするための **SQLAS** プロバイダーはありません。 Analysis Services インスタンスではなく、ローカル フォルダーからファイルを復旧する場合、共有を作成し、ファイルの読み取りアクセスをサーバーに与える必要があります。  
  
1.  管理者の PowerShell ウィンドウを開きます。  
  
2.  次のように入力します。 `Set-ExecutionPolicy RemoteUnsigned`  
  
3.  ファイル エクスプローラーで、データ ファイルを保管するフォルダーが共有されていることと、コンテンツを読み取る権限が Analysis Services インスタンスに与えられていることを確認します。  
  
##  <a name="bkmk_vers"></a> サポートされている Analysis Services のバージョンとモード  
 次の表に、さまざまなコンテキストで利用可能な Analysis Services PowerShell の機能を示します。  
  
|コンテキスト|PowerShell の利用可能な機能|  
|-------------|-------------------------------------|  
|多次元のインスタンスとデータベース|ローカルおよびリモート管理でサポートされます。<br /><br /> Merge-partition にはローカル接続が必要です。|  
|表形式のインスタンスとデータベース|互換性レベルを問わず、ローカル管理とリモート管理でサポートされます。<br /><br /> XMLA ではなく、JSON の TMSL (Tabular Model Scripting Language) を利用する互換性レベル 1200 の表形式モデルの SQLAS コマンドレット。|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインスタンスとデータベース|制限付きでサポートされます。 HTTP 接続と SQLAS プロバイダーを使用して、インスタンスとデータベースの情報を表示できます。<br /><br /> ただし、コマンドレットの使用はサポートされていません。 インメモリ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースのバックアップと復元には Analysis Services PowerShell を使用できません。また、ロールの追加や削除、データの処理、任意の XMLA スクリプトの実行にも使用しないでください。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint には、構成のために個別に提供される組み込みの PowerShell サポートがあります。 詳細については、「[Power Pivot for SharePoint 用 PowerShell リファレンス](../../analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint.md)」を参照してください。|  
|ローカル キューブへのネイティブ接続<br /><br /> "Data Source=c:\backup\test.cub"|サポートされていません。|  
|SharePoint 内の BI セマンティック モデル (.bism) 接続ファイルへの HTTP 接続<br /><br /> "Data Source=http://server/shared_docs/name.bism"|サポートされていません。|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースへの埋め込み接続<br /><br /> "Data Source=$Embedded$"|サポートされていません。|  
|Analysis Services ストアド プロシージャ内のローカル サーバーのコンテキスト<br /><br /> "Data Source=*"|サポートされていません。|  
  
## PowerShell によるサーバー管理タスクの例  
 **サーバー プロパティを一覧表示する**  
  
 サーバー プロパティはいくつかの方法で公開されます。  msmdsrv. ini または Management Studio のプロパティ ページで公開されているプロパティに精通しているユーザーであれば、下の例から、プロパティが実際にはさまざまなオブジェクトから返されていることがわかるでしょう。  
  
 このスクリプトは AMO サーバー オブジェクトを読み込みます。 プロパティの完全修飾名が必要であれば、このスクリプトを実行し、一覧を返すことができます。  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$as.serverproperties  
  
```  
  
 このスクリプトは、インスタンス レベルでプロパティとメソッドを返します。 この一覧から、 **ServerMode**、 **Version**、 **ProductName**、 **ProductLevel**となどの値を確認できます。  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as | get-member  
  
```  
  
 **サーバー モードを取得する**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.ServerMode  
```  
  
 **既定の互換性レベルを取得する**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.DefaultCompatibilityLevel  
```  
  
 **データベースの一覧を取得する**  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.databases  
```  
  
 **ポート番号を変更する**  
  
 このスクリプトは名前付きインスタンスのオブジェクトを作成し、ポートを宣言し、ポートを設定し、サーバー インスタンスを更新し、オブジェクトを切断し、サービスを再起動します。 検証手順としては、新しい接続を開き、ポートを返すことができます。  
  
 msmdsrv.ini ファイルか Management Studio のサーバーの全般プロパティ ページでもポートを確認できます。  
  
```  
sqlps  
$as = New-Object Microsoft.AnalysisServices.Server  
$as.connect("server-name\instance-name")  
$port = $as.serverproperties['Port']  
$port | select *  
$port.Value = [int]55555  
$as.Update()  
$as.Disconnect()  
restart-service 'MSOLAP$TABULAR'  
$as.connect("server-name\instance-name")  
$port | select *  
  
```  
  
## 参照  
 [Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [SQL Server PowerShell のインストール](../../database-engine/install-windows/install-sql-server-powershell.md)   
 [PowerShell を使用したテーブル モデルの管理](http://go.microsoft.com/fwlink/?linkID=227685)   
 [インターネット インフォメーション サービス (IIS) 8.0 上の Analysis Services への HTTP アクセスの構成](../../analysis-services/instances/configure http access to analysis services on iis 8.0.md)  
  
  