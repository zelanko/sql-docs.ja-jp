---
title: "SQL Server R Services の既知の問題 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: 52
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 49
---
# SQL Server R Services の既知の問題
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] および [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] での [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] とその関連コンポーネントの制限事項と問題について説明します。  
  
> [!NOTE]
> 初期のセットアップや構成に関連するその他の問題は、「[アップグレードとインストールに関してよく寄せられる質問](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)」に記載されています。  
  
## <a name="r-services-in-database"></a>R Services (In-Database)  
 このセクションでは、R 統合をサポートするデータベース エンジンの機能に固有の問題を示します。  

### <a name="install-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>最新のサービス リリースをインストールして Microsoft R Client との互換性を維持する

インストールした最新バージョンの Microsoft R Client を使用し、SQL Server でリモート コンピューティング コンテキストを用いて R を実行すると、以下のようなエラーが発生する場合があります。

*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

通常、サービス リリースの公開時に、SQL Server R Services と共にインストールされる R のバージョンが更新されます。 常に最新バージョンの R コンポーネントを使用するためには、サービス パックをすべてインストールします。 Microsoft R Client 9.0.0 との互換性を維持するには、この[サポート記事](https://support.microsoft.com/kb/3210262)で説明されている更新プログラムをインストールする必要があります。 
  
### <a name="new-license-agreement-for-r-components-required-for-unattended-installs"></a>無人インストールに必要な R コンポーネントの新しい使用許諾契約  
 コマンド ラインを使用して、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] がインストールされている SQL Server のインスタンスをインストールする場合、コマンド ラインを編集して、新しい使用許諾契約パラメーターである */IACCEPTROPENLICENSEAGREEMENT* を使用する必要があります。 正しい引数を使用しないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップが失敗する可能性があります。  
  
### <a name="warning-of-incompatible-version-when-connecting-to-older-version-of-sql-server--r-services-from-a-client-using-includesssqlv14mdtokensqlv14sssqlv14mdmd"></a>[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] を使用してクライアントから古いバージョンの SQL Server R Services に接続すると、互換性のないバージョンであることが警告される 

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] のセットアップ ウィザードまたは [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) の新しいスタンドアロン インストーラーを使用してクライアント コンピューターに Microsoft R Server をインストールしている状態で、以前のバージョンの SQL Server R Services を使用するコンピューティング コンテキストで R コードを実行すると、次のようなエラーが表示される場合があります。

*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

**SqlBindR.exe** ツールは、互換性のある 9.0 バージョンへの SQL Server インスタンスのアップグレードをサポートするために Microsoft R Server 9.0 リリースで提供されています。 9.0 への R Services インスタンスのアップグレードのサポートは、今後のサービス リリースの一部として SQL Server に追加されます。 今後のアップグレードの候補となるバージョンには、SQL Server 2016 RTM CU3+ と SP1+、および SQL Server vNext CTP 1.1 が含まれます。 

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>SQL Server 2016 サービス リリースをセットアップすると、新しいバージョンの R コンポーネントのインストールに失敗する場合がある

累積的な更新プログラムをインストールした場合や、インターネットに接続されていないコンピューターに SQL Server 2016 のサービス パックをインストールした場合は、セットアップ ウィザードに、ダウンロードした CAB ファイルを使用して R コンポーネントを更新するためのプロンプトが表示されないことがあります。 通常、これはデータベース エンジンと共に複数のコンポーネントがインストールされている場合に発生します。
 
回避策として、コマンドラインを使用し、CU1 の以下の例に示されている /MRCACHEDIRECTORY 引数を指定して、サービス リリースをインストールすることができます。 

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

最新の CAB ファイルを取得する場合は、「[インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)」を参照してください。

### <a name="windows-group-created-for-launchpad-must-have-an-account-in-the-sql-server-instance"></a>スタート パッドに作成される Windows グループでは SQL Server インスタンスのアカウントが必要
 SQL Server R Services のインストール時に、R ジョブを実行するために Trusted Launchpad で使用される、既定の名前の **SQLRUsers** で Windows ユーザー グループが作成されます。 Windows 統合認証を使用してリモート クライアントから R ジョブを実行する必要がある場合に、R が有効になっている SQL Server インスタンスにログインするにはこの Windows ユーザー グループ権限を付与する必要があります。

グループ **SQLRUsers** にこの権限がない環境では、次のエラーが表示される場合があります。  
  
-   R スクリプトを実行しようとしたとき:  
  
     *'R' スクリプトのランタイムを起動できません。'R' ランタイムの構成を確認してください。*  
  
     *外部スクリプト エラーが発生しました。ランタイムを起動できません。*  
  
-   [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスによって生成されるエラー:  
  
     *ランチャー RLauncher.dll を初期化できませんでした*  
  
     *ランチャー dll が登録されていません!*  
  
-   セキュリティ ログに、NT SERVICE\MSSQLLAUNCHPAD アカウントがログインできなかったことが示される。  
 
> [!NOTE]
> 共有メモリを使用して SQL Server Management Studio で R ジョブを実行すると、R ジョブで埋め込みの ODBC 呼び出しが使用されるまで、この制限が適用されない場合があります。 
> 
> リモート ワークステーションから SQL ログインを使用する場合、この回避策は必要ありません。

### <a name="launchpad-services-fails-to-start-if-version-is-different-than-r-version"></a>スタート パッド サービスのバージョンが R のバージョンと異なる場合は開始できない
データベース エンジンとは別に R Services をインストールし、バージョンが異なる場合、システム イベント ログに "_SQL Server のスタート パッド サービスは次のエラーのため開始できませんでした: サービスは適切な時間内に開始要求または制御要求に応答しませんでした_" のようなエラーが表示されることがあります。

たとえば、このエラーは、リリース バージョンを使用してデータベース エンジンをインストールする場合に、パッチを適用してデータベース エンジンをアップグレードしてからリリース バージョンを使用して R Services を追加した場合に発生することがあります。

この問題を回避するには、すべてのコンポーネントのバージョン番号が同じであることを確認します。 1 つのコンポーネントをアップグレードする場合は、インストールされている他のすべてのコンポーネントに必ず同じアップグレードを適用してください。

SQL Server 2016 の各リリースに必要な R バージョン番号のリストを表示する場合は、「[インターネットへのアクセスなしで R コンポーネントをインストールする](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)」を参照してください。


### <a name="service-account-for-launchpad-requires-permission-replace-process-level-token"></a>スタート パッドのサービス アカウントにはプロセス レベル トークンの置換の権限が必要
 SQL Server R Services のインストール時に、Trusted Launchpad は、既定で必要な権限でプロビジョニングされる NT Service\MSSQLLaunchpad アカウントを使用して起動します。 ただし、別のアカウントを使用する場合や、このアカウントに関連付けられている特権を変更する場合は、スタート パッドの起動に失敗することがあります。
 
 スタート パッド サービス アカウントで確実にログインできるようにするには、アカウントに `Replace Process Level Token` の特権を与えます。 詳細については、「[Replace a process level token](https://technet.microsoft.com/itpro/windows/keep-secure/replace-a-process-level-token)」 (アカウント レベル トークンを置き換える) を参照してください。

### <a name="remote-compute-contexts-blocked-by-firewall-in-sql-server-instances-running-on-azure-virtual-machines"></a>Azure 仮想マシンで実行されている SQL Server インスタンスのファイアウォールでブロックされるリモート計算コンテキスト  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] が Windows Azure 仮想マシンにインストールされている場合、仮想マシンのワークスペースを使用する必要がある計算コンテキストを使用できません。 これは、Azure VM のファイアウォールに、R ローカル ユーザー アカウントのネットワーク アクセスをブロックするルールが既定で含まれるためです。  
  
 回避策として、Azure VM で **[セキュリティが強化された Windows ファイアウォール]**を開き、 **[送信の規則]**を選択して、"SQL Server インスタンス MSSQLSERVER の R ローカル ユーザー アカウントのネットワーク アクセスをブロック" ルールを無効にします。  
  
### <a name="implied-authentication-in-sqlexpress"></a>SQLEXPRESS での暗黙の認証
Windows 統合認証を使用してリモート データ サイエンス ワークステーションから R ジョブを実行する際に、SQL Server は*暗黙の認証*を使用して、スクリプトで必要になる可能性のあるローカル ODBC 呼び出しを生成します。 ただし、この機能は、SQL Server Express Edition の RTM ビルドでは使用できません。 

この問題を解決するために、新しいサービス リリースにアップグレードすることをお勧めします。

アップグレードできない場合は、SQL ログインを使用して、埋め込みの ODBC 呼び出しを必要とする可能性のあるリモート R ジョブを実行できます。 

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>R ジョブのプロセッサ アフィニティに関する制限事項 
 
SQL Server 2016 の RTM ビルドでは、最初の k グループ内の CPU にのみプロセッサ関係を設定できます。 たとえば、サーバーが 2 k グループの 2 ソケット マシンである場合、最初の k グループのプロセッサのみが R プロセスで使用されます。 R スクリプト ジョブのリソース管理を構成するときに、同じ制限が適用されます。

この問題は SQL Server 2016 Service Pack 1 で修正されました。

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>SQL Server コンピューティング コンテキストでのデータの読み取り時に列の型を変更できない

コンピューティング コンテキストが SQL Server インスタンスに設定されている場合は、_colClasses_ 引数 (または他の同様の引数) を使用して、R コードで列のデータ型を変更できません。 

たとえば、CRSDepTimeStr 列がまだ整数でない場合、次のステートメントでエラーが発生します。

~~~~
data <- RxSqlServerData(sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall",
                                connectionString = connectionString,
                                colClasses = c(CRSDepTimeStr = "integer"))
~~~~

この問題は今後のリリースで修正される予定です。 

回避策として、SQL クエリを書き直し、CAST または CONVERT を使用して、正しいデータ型を用いて R でデータを表示できます。 一般的には、R コードでデータを変更するのではなく、SQL を使用してデータを操作することをお勧めします。
  
### <a name="resource-governance-default-values"></a>リソース ガバナンスの既定値  
Enterprise Edition では、外部スクリプト プロセスを管理するためにリソース プールを使用できます。 一部のビルドでは、R プロセスに割り当てられる最大メモリは 20% でした。 したがって、サーバーに 32 GB の RAM がある場合、R の実行可能ファイル (RTerm.exe および BxlServer.exe) では 1 つの要求で最大 6.4 GB を使用できました。 

リソースに制限がある場合は、現在の既定値を確認し、20% では十分でない場合は、この値の変更方法について、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のドキュメントを参照してください。  

### <a name="avoid-clearing-workspaces-when-executing-r-code-in-a-includessnoversiontokenssnoversionmdmd-compute-context"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューティング コンテキストでの R コードの実行時にワークスペースをクリアできない  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューティング コンテキストで R コードを実行中に R コマンドを使用してオブジェクトのワークスペースをクリアする場合や、[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) を使用して呼び出した R スクリプトの一部としてワークスペースをクリアする場合、"*ワークスペース オブジェクト 'revoScriptConnection' が見つかりません*" のようなエラーが発生することがあります。

`revoScriptConnection` は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から呼び出される R セッションに関する情報を含む R ワークスペース内のオブジェクトです。 ただし、R コードにワークスペースをクリアするためのコマンド (`rm(list=ls()))` など) が含まれている場合は、R ワークスペース内のセッションおよび他のオブジェクトに関するすべての情報もクリアされます。

回避策として、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での R の実行時に変数および他のオブジェクトを無差別にクリアしないようにします。 R コンソールでの操作時にワークスペースをクリアすることはよくありますが、意図しない結果になる場合があります。 

+ 特定の変数を削除するには、R の *remove* 関数の `remove('name1', 'name2', ...)` を使用します。 
+ 削除する変数が複数ある場合は、リストに一時変数の名前を保存し、ガベージ コレクションを定期的に実行します。 
   
### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>R スクリプトの入力として提供できるデータに対する制限事項  
 次の種類のクエリ結果は、R スクリプトでは使用できません。  
  
-   AlwaysEncrypted 列を参照する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリのデータ。  
  
-   マスクされた列を参照する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリのデータ。  
  
     R スクリプトでマスクされたデータを使用する必要がある場合、考えられる次善策として、一時テーブルにデータのコピーを作成し、代わりにそのデータを使用します。  
   
  
## <a name="microsoft-r-server-standalone"></a>Microsoft R Server (スタンドアロン)  
 このセクションでは、スタンドアロン バージョンの Microsoft R Server に固有の問題を示します。 
  
### <a name="multiple-r-libraries-and-executables-are-installed-if-you-install-both-standalone-and-in-database"></a>スタンドアロンとデータベース内の両方のバージョンをインストールすると、複数の R ライブラリおよび実行可能ファイルがインストールされる  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップには、Microsoft R Server (スタンドアロン) をインストールするためのオプションが含まれています。 Microsoft R Server (スタンドアロン) オプションを Enterprise Edition で使用することで、R をサポートするが、SQL Server との対話を必要としないスタンドアロンの Windows Server をインストールできます。    

> [!TIP] R を [!INCLUDE[tsql](../../includes/tsql-md.md)] で使用する場合、このスタンドアロン オプションは必要**ありません**。
> 
> [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] または Microsoft R Server (スタンドアロン) に接続できるデータ サイエンス クライアント コンピューターをセットアップする必要がある場合は、[Microsoft R Client](http://go.microsoft.com/fwlink/?LinkId=799768) をお勧めします。  

R Services (データベース内) と Microsoft R Server (スタンドアロン) の両方を同じコンピューターにインストールする場合は、R が有効な SQL Server のインスタンスごとに別の R インスタンスと、Microsoft R Server (スタンドアロン) の R の別のインスタンスが作成されることに注意してください。  たとえば、既定のインスタンスと名前付きインスタンス、および R Server (スタンドアロン) をインストールした場合、同じコンピューター上に次の R の 3 つのインスタンスが存在する可能性があります。  
  
-   **スタンドアロン:** C:\Program Files\Microsoft SQL Server\130\R_SERVER  
  
-   **既定のインスタンス:** C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES  
  
-   **名前付きインスタンス:** C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES  
  
> [!NOTE] 
> 
> [!INCLUDE[tsql](../../includes/tsql-md.md)] のコンテキストからのみデータベース インスタンスに関連付けられている R ライブラリとツールを使用してください。 その他の R ツールを使用して R を実行する必要がある場合は、C:\Program Files\Microsoft SQL Server\130\R_SERVER に既定でインストールされる、R Server (スタンドアロン) で使用される R ライブラリを必ず参照してください。  

### <a name="performance-limits-when-r-services-libraries-are-called-from-standalone-r-tools"></a>R Services ライブラリがスタンドアロン R ツールから呼び出される場合のパフォーマンスの制限

SQL Server R Services で使用される R ライブラリは、C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES に既定でインストールされます。 RGui などの外部 R アプリケーションから SQL Server R Services に対してインストールされる R ツールとライブラリを呼び出すことが*できます*。 

ただし、これを行う場合は、パフォーマンスが制限されます。 たとえば、SQL Server Enterprise Edition を購入した場合でも、外部ツールを使用して R コードを実行すると、R はシングル スレッド モードで実行されます。 SQL Server 接続を開始し、[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) (自動的に R Services ライブラリを呼び出す) を使用して、R コードを実行すると、パフォーマンスが高まります。

+ 外部 R ツールから SQL Server で使用される R ライブラリは呼び出さないでください。 
+ 外部ツールを使用して SQL Server コンピューターで R を実行する必要がある場合は、R の別のインスタンスをインストールしてから、R ツールが新しいライブラリをポイントしていることを確認する必要があります。 
+ Enterprise Edition を使用している場合は、SQL Server コンピューターに Microsoft R Server (スタンドアロン) をインストールすることをお勧めします。 その後、R コードを実行するために使用する外部ツールから、C:\Program Files\Microsoft SQL Server\<バージョン番号>\R_SERVER に既定でインストールされる、R Server のライブラリを参照します。 

詳細については、「[スタンドアロン R Server の作成](../../advanced-analytics/r-services/create-a-standalone-r-server.md)」を参照してください。  
  
  
## <a name="general-r-issues"></a>R の一般的な問題  

 このセクションでは、R の接続およびパフォーマンス ツールに固有の問題を示します。  
  
### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>sp_execute_external_script では SQL データ型のサポートが制限されている  

 SQL でサポートされているデータ型の一部を R で使用できません。回避策として、サポートされていないデータ型をサポートされているデータ型にキャストしてから、sp_execute_external_script にデータを渡すことを検討してください。  
  
 詳細については、「[R データ型の処理](../../advanced-analytics/r-services/working-with-r-data-types.md)」を参照してください。  
  
### <a name="possible-string-corruption"></a>文字列が破損する可能性がある  

 文字列データが [!INCLUDE[tsql](../../includes/tsql-md.md)] から R に送信された後、再び [!INCLUDE[tsql](../../includes/tsql-md.md)] に返されるラウンドトリップで、文字列が破損する可能性があります。 これは、R と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で異なるエンコードが使用されていることと、R と [!INCLUDE[tsql](../../includes/tsql-md.md)]でサポートされる照合順序と言語が異なることに起因します。 非 ASCII エンコードの文字列は正しく処理されない可能性があります。  
  
 文字列データを R に送信するときに、可能であれば、ASCII 形式に変換します。  
  
### <a name="only-one-raw-value-can-be-returned-from-spexecuteexternalscript"></a>sp_execute_external_script から返すことができる raw 値は 1 つに限られる  

 R から binary データ型 (R の **raw** データ型) を返す場合、この値は出力データ フレーム内の値である必要があります。  
  
 今後のリリースで、 **raw** の複数の出力のサポートが追加される予定です。  
  
 複数の出力セットが必要な場合の考えられる次善策の 1 つとして、ストアド プロシージャの複数の呼び出しを実行し、ODBC を使用して結果セットを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信します。  
  
 OUTPUT キーワードを追加するだけで、ストアド プロシージャの結果と共にパラメーター値を返すことができます。 詳細については、「[OUTPUT パラメーターを使用してデータを返す処理](https://technet.microsoft.com/library/ms187004.aspx)」を参照してください。
  
### <a name="loss-of-precision"></a>精度の損失  

 [!INCLUDE[tsql](../../includes/tsql-md.md)] と R はサポートするデータ型が異なるため、変換時に数値データ型の精度が損なわれる可能性があります。  
  
 暗黙的なデータ型変換の詳細については、「 [Working with R Data Types](../../advanced-analytics/r-services/working-with-r-data-types.md)」を参照してください。  
  
### <a name="variable-scoping-error-the-sample-data-set-for-the-analysis-has-no-variables-when-using-the-transformfunc-parameter"></a>transformFunc パラメーターの使用時に、"分析用のサンプル データ セットに変数が含まれていません" という変数のスコープ エラーが発生する  

 モデリング時に、 *transfやmFunc* 引数を `rxLinmod` や `rxLogit` to transfやm the data while modelling. ただし、入れ子になった関数呼び出しでは、呼び出しがローカルの計算コンテキストで正しく機能していても、SQL Server の計算コンテキストではスコープ エラーが発生する可能性があります。  
  
 たとえば、ローカル グローバル環境で定義した `f` と `g` の 2 つの関数があり、 `g` で `f`を呼び出すとします。 `g`を含む分散またはリモート呼び出しでは、リモート呼び出しに `g` と `f` の両方を渡した場合でも、 `f` が見つからないために `g` の呼び出しが失敗します。  
  
 この問題が発生した場合は、 `f` の定義内の、通常 `g`が `g` を呼び出す場所より前の任意の場所に、 `f`の定義を組み込むことで問題を回避できます。  
  
 例:  
  
```  
f <- function(x) { 2*x + 3 }  
g <- function(y) {   
              a <- 10 * y  
               f(a)  
}  
  
```  
  
 エラーを回避するには、次のように書き換えます。  
  
```  
g <- function(y){  
              f <- function(x) { 2*x +3}  
              a <- 10 * y  
              f(a)  
}  
  
```  

  
## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise と Microsoft R Open 
 
 このセクションでは、Revolution Analytics によって提供される R の接続、開発、およびパフォーマンス ツールに固有の問題を示します。 これらのツールは、以前のプレリリース版の [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で提供されていました。 

一般的には、これらの以前のバージョンをアンインストールして、最新バージョンの SQL Server R Services、Microsoft R Server、または Microsoft R Client をインストールすることをお勧めします。
  
### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Revolution R Enterprise の複数のバージョンの共存  

 Revolution R Enterprise をインストールして任意のバージョンの [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] と共存させることはできません。  
  
 別のバージョンの Revolution R Enterprise を使用するためのライセンスがある場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスへの接続に使用するワークステーションとは別のコンピューターにライセンスを配置する必要があります。  
  
### <a name="limited-support-for-revoscaler-rxexec"></a>RevoScaleR rxExec の制限付きサポート  

 RC0 以降では、 `rxExec` で提供される [!INCLUDE[rsql_rre-short](../../includes/rsql-rre-short-md.md)] 関数はシングルスレッド モードでのみ使用できます。  
  
 複数のプロセスでの `rxExec` の並列処理は、今後のリリースで追加される予定です。  
  
### <a name="data-import-and-manipulation-using-revoscaler"></a>RevoScaleR を使用したデータのインポートと操作  

 データベースから **varchar** 列を読み取るときに、空白が削除されます。 これを防ぐには、空白以外の文字で文字列を囲みます。  
  
  `rxDataStep` などの関数を使用して **varchar** 列を含むデータベース テーブルを作成するときには、データのサンプルに基づいて列幅が推定されます。 幅が増減する可能性がある場合、すべての文字列を共通の長さにして空白を埋めることが必要な場合があります。  
  
 `rxImport` または `rxTextToXdf` の繰り返しの呼び出しを使用して行のインポートと追加を実行し、複数の入力ファイルを 1 つの .xdf ファイルに結合する場合、変換を使用した変数のデータ型の変更はサポートされていません。  
  
### <a name="increase-maximum-parameter-size-to-support-rxgetvarinfo"></a>RxGetVarInfo をサポートするためにパラメーターの最大サイズを増やす  

 非常に多くの変数 (40,000 個以上など) が含まれたデータ セットを使用する場合、 `max-ppsize` などの関数を使用するために、R の起動時に `rxGetVarInfo`フラグを設定する必要があります。  `max-ppsize` フラグは、ポインター保護スタックの最大サイズを指定します。  
  
 (rgui.exe や rterm.exe などで) R コンソールを使用している場合、次のように入力することで max-ppsize の値を 500000 に設定できます。  
  
```  
R --max-ppsize=500000  
```  
  
 [!INCLUDE[rsql_developr](../../includes/rsql-developr-md.md)] 環境を使用している場合は、次のように RevoIDE 実行可能ファイルを呼び出すことで、 `max-ppsize` フラグを設定できます。  
  
```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  
  
### <a name="issues-with-rxdtree-function"></a>rxDTree 関数に関する問題  

 `rxDTree` 関数では、式内変換は現在サポートされていません。 特に、係数を即座に作成するための `F()` 構文の使用はサポートされていません。 ただし、数値は自動的にビン分割されます。  
  
 順序付けされた係数は、 `rxDTree`を除くすべての RevoScaleR 分析関数の係数と同様に処理されます。  
  
### <a name="using-the-r-productivity-environment"></a>R Productivity Environment の使用  

一部のプレリリース版の [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] には、Revolution Analytics によって作成された Windows 用の R 開発環境が含まれていました。 

ただし、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] との互換性を維持するために、Revolution Analytics ツールではなく、Microsoft R Client または Microsoft R Server をインストールすることを強くお勧めします。 Microsoft R ソリューションをサポートするクライアントとして [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/) もお勧めします。
  
### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>SQLite ODBC ドライバーと RevoScaleR に関する互換性の問題  
 SQLite ODBC ドライバーのリビジョン 0.92 は RevoScaleR と互換性がありません。リビジョン 0.88 ～ 0.91 と 0.93 以降は互換性があることがわかっています。  
  
## <a name="see-also"></a>参照  
[SQL Server 2016 の新機能](../../sql-server/what-s-new-in-sql-server-2016.md)
  