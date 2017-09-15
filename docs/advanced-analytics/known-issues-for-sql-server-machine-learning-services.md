---
title: "Machine Learning のサービスの既知の問題 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: 53
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 754242a86367b07b98caa9f70f457b70d0840075
ms.openlocfilehash: d5d36a57d73bd0f37d9e8aee6a4d154fb096f375
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="known-issues-in-machine-learning-services"></a>Machine Learning のサービスの既知の問題

この記事では、既知の問題または SQL Server 2016 および SQL Server 2017 のオプションとして用意されている機械学習コンポーネントと制限事項について説明します。

具体的に指示がない限り、ここにある情報が、次のすべてに適用されます。

* SQL Server 2016

  - R Services (In-Database)
  - Microsoft R Server (スタンドアロン)

* SQL Server 2017

  - Machine Learning の R (In-database) 用サービス
  - Machine Learning Python (In-database) 用サービス
  - Machine Learning Server (スタンドアロン)

## <a name="setup-and-configuration-issues"></a>セットアップおよび構成の問題

プロセスとの初期セットアップと構成に関連する一般的な質問については、次を参照してください。[アップグレードとインストールに関する FAQ](r/upgrade-and-installation-faq-sql-server-r-services.md)です。 アップグレード、サイド バイ サイド インストール、および新しい R または Python コンポーネントのインストールに関する情報が含まれています。

### <a name="unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>オフライン インストールでは SQL Server 2017 CTP 2.0 またはそれ以降に Python コンポーネントをインストールすることができません。

インターネットにアクセスできないコンピューターに SQL Server 2017 のプレリリース版をインストールする場合は、ダウンロードされた Python コンポーネントの場所の入力を求めるページを表示するインストーラーが失敗します。 このようなインスタンスでは、Machine Learning サービス機能は、Python コンポーネントではないをインストールできます。

リリース バージョンでは、この問題が解決します。 この問題を回避するには、この問題が発生した場合は、セットアップ中に一時的にインターネットへのアクセスを有効にできます。 R. にこの制限は適用されません。

**適用されます:** Python の SQL Server 2017

### <a name="install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Microsoft R クライアントとの互換性を確保するのには、最新のサービス リリースをインストールします。

Microsoft R クライアントの最新バージョンをインストール、使用して、SQL Server でリモート計算コンテキストで R を実行する場合、次のようなエラーが発生した可能性があります。

>*Microsoft R Server バージョン 8.x.x と互換性がないコンピューターに Microsoft R Client のバージョン 9.x.x を実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 では、クライアント上の R ライブラリは、サーバー上の R ライブラリを正確に一致が必要です。 制限は R Server 9.0.1 より後のリリースで削除されました。 ただし、このエラーが発生した場合は、クライアントとサーバーによって使用され、必要に応じて、サーバー バージョンと一致するクライアントを更新する R ライブラリのバージョンを確認します。

SQL Server サービスのリリースがインストールされているときに、SQL Server R Services と共にインストールされている R のバージョンが更新されます。 常に最新バージョンの R コンポーネントがあることを確認してください、するすべてのサービス パックをインストールすることを確認します。

Microsoft R クライアント 9.0.0 との互換性のために、これに説明されている更新プログラムのインストール[サポートの記事](https://support.microsoft.com/kb/3210262)です。

R パッケージに問題を避けるためにはに記載されている最新のライフ サイクル ポリシーに変更することで、サーバーにインストールされている R ライブラリのバージョンをアップグレードすることも[、次のセクション](#bkmk_sqlbindr)です。 これを行うときに SQL Server と共にインストールされている R のバージョンが更新、同じスケジュールで Microsoft R Server は、により、サーバーとクライアントの両方常に、Microsoft R. の最新リリースの更新プログラムが発行されたこと

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="bkmk_sqlbindr"></a>使用して、クライアントから、古いバージョンの SQL Server R Services に接続するときに、互換性のないバージョンの警告[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

SQL Server 2016 のコンピューティング コンテキストで R コードを実行して、次の 2 つのステートメントのいずれかが true の場合、次のようなエラーが表示される場合。
* セットアップ ウィザードを使用してクライアント コンピューターで R Server (スタンドアロン) をインストールした[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]です。
* 使用して Microsoft R Server をインストールする、 [Windows インストーラーを区切る](https://docs.microsoft.com/r-server/install/r-server-install-windows)です。

>*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SqlBindR.exe ツールは、互換性のある 9.0 バージョンの SQL Server インスタンスのアップグレードをサポートする 9.0 に Microsoft R Server で提供されます。 9.0 に R services のインスタンスをアップグレードするためのサポートは、次のサービス リリースの一環として SQL Server に追加されます。 将来のアップグレードの候補となるバージョンには、SQL Server 2016 RTM CU3 および SP1 以降、および SQL Server 2017 CTP 1.1 が含まれます。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>SQL Server 2016 サービス リリースをセットアップすると、新しいバージョンの R コンポーネントのインストールに失敗する場合がある

累積的な更新プログラムのインストールまたはインターネットに接続されていないコンピューターに SQL Server 2016 の service pack をインストールするときに、ダウンロードした CAB ファイルを使用して、R コンポーネントを更新できるプロンプトを表示するセットアップ ウィザードが失敗します。 このエラーは、複数のコンポーネントが、データベース エンジンと共にインストールされている場合に通常発生します。

この問題を回避するには、コマンドラインを使用し、サービス リリースをインストールすることができます、 */MRCACHEDIRECTORY*引数のこの例では、CU1 更新プログラムをインストールします。

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

最新のインストーラーを取得するには、次を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストール](r/installing-ml-components-without-internet-access.md)です。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>スタート パッド サービスのバージョンが R のバージョンと異なる場合の開始に失敗します。

データベース エンジンから R services を個別にインストールするし、ビルドのバージョンが異なる場合は、システム イベント ログに次のエラーを参照してください可能性があります。 

>_SQL Server スタート パッド サービスは、次のエラーのため開始できませんでした。 サービスは適時に開始または制御要求に応答しませんでした。_

たとえば、このエラー可能性があります、リリース バージョンを使用して、データベース エンジンをインストールする場合に発生する、データベース エンジンのアップグレード修正プログラムを適用およびリリース バージョンを使用して R services を追加します。

この問題を回避するには、すべてのコンポーネントのバージョン番号が同じであることを確認します。 1 つのコンポーネントをアップグレードする場合は、インストールされている他のすべてのコンポーネントに必ず同じアップグレードを適用してください。

SQL Server 2016 の各リリースに必要な R のバージョン番号の一覧を表示するには、次を参照してください。[インターネットにアクセスできないインストールの R コンポーネント](r/installing-ml-components-without-internet-access.md)です。

### <a name="remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>Azure の仮想マシンで実行されている SQL Server インスタンス内のファイアウォールでリモート計算コンテキストがブロックされています。

インストールした場合[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Windows Azure バーチャル マシンでは、するできないことがありますを仮想マシンのワークスペースの使用を必要とする計算コンテキストを使用します。 これは、Azure VM のファイアウォールに、R ローカル ユーザー アカウントのネットワーク アクセスをブロックするルールが既定で含まれるためです。

Azure vm での回避策として開きます**セキュリティが強化された Windows ファイアウォール****送信の規則**、し、次のルールを無効にする:**で R ローカル ユーザー アカウントのネットワーク アクセスをブロックSQL Server インスタンス MSSQLSERVER**です。

### <a name="implied-authentication-in-sqlexpress"></a>SQLEXPRESS での暗黙の認証

SQL Server を使用して Windows 統合認証を使用してリモート データ サイエンス ワークステーションから R ジョブを実行するときに*黙示的な認証*をスクリプトで必要なローカルの ODBC 呼び出しを生成します。 ただし、この機能は、SQL Server Express Edition の RTM ビルドでは使用できません。

この問題を解決するために、新しいサービス リリースにアップグレードすることをお勧めします。

アップグレードできない場合は、SQL ログインを使用して、埋め込みの ODBC 呼び出しを必要とする可能性のあるリモート R ジョブを実行できます。

**適用されます:** Services Express Edition の SQL Server 2016 R

### <a name="performance-limits-when-r-libraries-are-called-from-standalone-r-tools"></a>R ライブラリがスタンドアロン R ツールから呼び出されると、パフォーマンスの制限

R のツールと RGui などの外部 R アプリケーションから SQL Server R Services のインストールされているライブラリを呼び出すことができます。 この呼び出しは、非常に短いコード サンプルのアドホック テストを実行するときや、新しいパッケージをインストールするときに役立ちます。

ただし、SQL Server の外部でパフォーマンスが制限されることに注意してください。 たとえば、SQL Server の Enterprise Edition を購入した場合でも R が実行シングル スレッド モードで外部ツールを使用して、R コードを実行するとします。 パフォーマンスが優れているは、SQL Server の接続を開始しを使用して、R コードを実行する場合にする[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)の R ライブラリを呼び出しがされます。

* 外部の R ツールから SQL Server で使用される R ライブラリを呼び出すことを回避します。
* SQL Server を使用せず、SQL Server コンピューターで広範な R コードを実行する必要がある場合は、Microsoft R クライアントなどの R の別のインスタンスをインストールし、R 開発ツールは、新しいライブラリを指していることを確認します。

詳細については、「 [スタンドアロン R Server の作成](r/create-a-standalone-r-server.md)」を参照してください。

### <a name="the-r-script-is-throttled-due-to-resource-governance-default-values"></a>リソース統制の既定値のため、R スクリプトを調整します。

Enterprise Edition では、外部スクリプト プロセスを管理するためにリソース プールを使用できます。 いくつかの初期のリリース ビルドでは、R プロセスに割り当てられる最大メモリは、20% をでした。 そのため、サーバーに 32 GB の RAM がある場合、R の実行可能ファイル (RTerm.exe と BxlServer.exe) は、最大 1 つの要求で 6.4 GB を使用できます。

リソースの制限により、発生した場合は、現在の既定値を確認します。 20% が十分でない場合は、ドキュメントを参照して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でこの値を変更する方法です。

**適用されます:** SQL Server 2016 の R Services, Enterprise Edition

## <a name="r-code-execution-and-package-or-function-issues"></a>R コードの実行とパッケージまたは関数の問題

このセクションでは、SQL Server で R を実行している固有の既知の問題だけでなく、R ライブラリと RevoScaleR をなど、マイクロソフトによって発行されたツールに関連する問題のいくつか含まれています。

追加既知の問題を R ソリューションを与える可能性がありますを参照してください、 [Microsoft R Server サイト](https://msdn.microsoft.com/microsoft-r/rserver-known-issues)です。

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>R ジョブのプロセッサ アフィニティに関する制限事項

SQL Server 2016 の最初のリリース ビルドでは、最初の k グループ内の Cpu のみのプロセッサ アフィニティを設定できます。 たとえば、2 ソケットのマシンが 2 つの k グループをサーバーには場合、は、最初の k グループからのみのプロセッサが R プロセスに使用されます。 R スクリプトのジョブのリソース管理を構成するときに、同じ制限が適用されます。

この問題は SQL Server 2016 Service Pack 1 で修正されました。

**適用されます:**バージョンの SQL Server 2016 R Services RTM

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>SQL Server コンピューティング コンテキストでのデータの読み取り時に列の型を変更できない

コンピューティング コンテキストが SQL Server インスタンスに設定されている場合は、 _colClasses_ 引数 (または他の同様の引数) を使用して、R コードで列のデータ型を変更できません。

たとえば、CRSDepTimeStr 列がまだ整数でない場合、次のステートメントでエラーが発生します。

~~~~
data <- RxSqlServerData(sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall",
                                connectionString = connectionString,
                                colClasses = c(CRSDepTimeStr = "integer"))
~~~~

この問題は今後のリリースで修正される予定です。

この問題を回避するには、キャストを使用する SQL クエリを書き直すことができます、または変換して正しいデータ型を使用してデータを R に提供します。 一般に、パフォーマンスは、操作する際にデータを R コードでデータを変更することによってではなく、SQL を使用しています。

**適用されます:** SQL Server 2016 の R Services

### <a name="avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>R コードを実行するときに、ワークスペースをオフにしないで、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]計算コンテキスト

R コマンドを使用して R コードの実行中にオブジェクトのワークスペースを削除する場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]コンピューティング コンテキストを使用して R スクリプトの一部としてワークスペースをクリアするかどうか、または呼び出す[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、これをする可能性がありますエラー: 

>*ワークスペース オブジェクト 'revoScriptConnection' が見つかりません。*

`revoScriptConnection` は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]から呼び出される R セッションに関する情報を含む R ワークスペース内のオブジェクトです。 ただし、R コードにワークスペースをクリアするためのコマンド ( `rm(list=ls()))`など) が含まれている場合は、R ワークスペース内のセッションおよび他のオブジェクトに関するすべての情報もクリアされます。

この問題を回避するには、変数およびその他のオブジェクトの区別しないで消去中にされないようにで R を実行している[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 R コンソールでの操作時にワークスペースをクリアすることはよくありますが、意図しない結果になる場合があります。

* 特定の変数を削除するには、R を使用*削除*関数:`remove('name1', 'name2', ...)`です。
* 削除する変数が複数ある場合は、リストに一時変数の名前を保存し、ガベージ コレクションを定期的に実行します。

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>R スクリプトの入力として提供できるデータに対する制限事項

次の種類のクエリ結果は、R スクリプトでは使用できません。

- AlwaysEncrypted 列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
- マスクされた列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
     R スクリプトでマスクされたデータを使用する必要がある場合、考えられる次善策として、一時テーブルにデータのコピーを作成し、代わりにそのデータを使用します。

### <a name="arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>引数*varsToKeep*と*varsToDrop* SQL Server データ ソースはサポートされていません

使用してテーブルに結果を書き込む rxDataStep 関数を使用する場合、 *varsToKeep*と*varsToDrop*または操作の一部として除外する列を指定する便利な方法は、します。 現時点では、これらの引数は、SQL Server データ ソースに対してはサポートされません。

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>SQL データ型の制限付きサポート`sp_execute_external_script`

SQL でサポートされているデータ型の一部を R で使用できません。回避策として、サポートされていないデータ型をサポートされているデータ型にキャストしてから、sp_execute_external_script にデータを渡すことを検討してください。

詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

### <a name="possible-string-corruption"></a>文字列が破損する可能性がある

文字列からのデータのラウンド トリップ[!INCLUDE[tsql](../includes/tsql-md.md)]、R に[!INCLUDE[tsql](../includes/tsql-md.md)]破損再度を招くことができます。 これは、R で使用されるさまざまなエンコードにより[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、さまざまな照合順序と R でサポートされている言語だけでなくと[!INCLUDE[tsql](../includes/tsql-md.md)]です。 非 ASCII エンコードの文字列は正しく処理されない可能性があります。

文字列データを R に送信するときに可能であれば、ASCII 形式に変換します。

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>型の値を 1 つだけ`raw`から返されることができます`sp_execute_external_script`

R から binary データ型 (R の **raw** データ型) を返す場合、この値は出力データ フレーム内の値である必要があります。

今後のリリースで、 **raw** の複数の出力のサポートが追加される予定です。

複数の出力セットを使用する場合は、いずれかの可能な回避策は、ストアド プロシージャの複数の呼び出しを行い、結果を送信するセット[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ODBC を使用しています。

OUTPUT キーワードを追加するだけでは、ストアド プロシージャの結果と共にパラメーター値を返すことができます。 詳細については、次を参照してください。[出力パラメーターを使用してデータを返す](https://technet.microsoft.com/library/ms187004.aspx)です。

### <a name="loss-of-precision"></a>精度の損失

[!INCLUDE[tsql](../includes/tsql-md.md)]と R をサポートしてさまざまなデータ型、数値データ型は変換中に有効桁数の損失を低下することができます。

暗黙のデータ型変換の詳細については、次を参照してください。 [R データ型を扱う](r/r-libraries-and-data-types.md)です。

### <a name="variable-scoping-error-when-you-use-the-transformfunc-parameter-the-sample-data-set-for-the-analysis-has-no-variables"></a>変数のスコープ transformFunc パラメーターを使用するときのエラー:*分析のサンプル データ セットに変数がありません*

渡すことができますをモデル化するときに、データを変換する、 *transformFunc*などの関数の引数`rxLinmod`または`rxLogit`です。 ただし、入れ子になった関数呼び出しは、ローカル コンピューティング コンテキストでの呼び出しが正しく動作させる場合でも、SQL Server のコンピューティング コンテキストではスコープ エラーに可能性があります。

たとえば、2 つの関数が定義されている`f`と`g`をローカル グローバル環境でと`g`呼び出し`f`です。 `g`を含む分散またはリモート呼び出しでは、リモート呼び出しに `g` と `f` の両方を渡した場合でも、 `f` が見つからないために `g` の呼び出しが失敗します。

この問題が発生した場合は、 `f` の定義内の、通常 `g`が `g` を呼び出す場所より前の任意の場所に、 `f`の定義を組み込むことで問題を回避できます。

例:

```  
f <- function(x) { 2*x * 3 }  
g <- function(y) {   
              a <- 10 * y  
               f(a)  
}  
  
```  


エラーを回避するには、定義を次のように書き換えます。

```  
g <- function(y){  
              f <- function(x) { 2*x +3}  
              a <- 10 * y  
              f(a)  
}  
  
```  

### <a name="data-import-and-manipulation-using-revoscaler"></a>RevoScaleR を使用したデータのインポートと操作

ときに**varchar**列は読み取りをデータベースからの空白は切り捨てられます。 これを防ぐには、空白以外の文字で文字列を囲みます。

ときになどの関数`rxDataStep`を持つデータベース テーブルの作成に使用する**varchar**列、列の幅とデータのサンプルに基づいて推定されます。 幅が増減する場合は、共通の長さにすべての文字列の余白を埋めるために必要な場合があります。

`rxImport` または `rxTextToXdf` の繰り返しの呼び出しを使用して行のインポートと追加を実行し、複数の入力ファイルを 1 つの .xdf ファイルに結合する場合、変換を使用した変数のデータ型の変更はサポートされていません。

### <a name="limited-support-for-rxexec"></a>RxExec の制限付きサポート

SQL Server 2016 では、`rxExec`関数がシングル スレッド モードでのみで、RevoScaleR パッケージを使用できる指定します。

複数のプロセスでの `rxExec` の並列処理は、今後のリリースで追加される予定です。

### <a name="increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>RxGetVarInfo をサポートするためにパラメーターの最大サイズを増やす

非常に多数の変数 (たとえば、40,000) 経由でデータ セットを使用する場合は、設定、`max-ppsize`始めると R 関数を使用するようにフラグを設定`rxGetVarInfo`です。 `max-ppsize` フラグは、ポインター保護スタックの最大サイズを指定します。

(rgui.exe や rterm.exe などで) R コンソールを使用している場合、次のように入力することで max-ppsize の値を 500000 に設定できます。

```  
R --max-ppsize=500000  
```  
  
使用している場合、[!INCLUDE[rsql_developr](../includes/rsql-developr-md.md)]環境を設定できます、 `max-ppsize` RevoIDE 実行可能ファイルに次の呼び出しを行ってフラグ。

```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  

### <a name="issues-with-the-rxdtree-function"></a>RxDTree 関数に関する問題

`rxDTree` 関数では、式内変換は現在サポートされていません。 特に、係数を即座に作成するための `F()` 構文の使用はサポートされていません。 ただし、数値データが自動的にビン分割されます。

順序付けされた係数は、 `rxDTree`を除くすべての RevoScaleR 分析関数の係数と同様に処理されます。

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise と Microsoft R Open

このセクションでは、R の接続、開発、および Revolution Analytics によって提供されるパフォーマンス ツールに固有の問題を一覧表示します。 これらのツールは、以前のプレリリース バージョンので提供されていた[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]です。 

一般に、これらの以前のバージョンをアンインストールして、SQL Server または Microsoft R Server の最新バージョンをインストールすることをお勧めします。

### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>サイド バイ サイドのバージョンの Revolution R Enterprise を実行しています。

バージョンの Revolution R Enterprise サイド バイ サイドのインストール[!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)]はサポートされていません。

別のバージョンの Revolution R Enterprise を使用するためのライセンスがある場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスへの接続に使用するワークステーションとは別のコンピューターにライセンスを配置する必要があります。

### <a name="the-use-of-an-r-productivity-environment-is-not-supported"></a>生産性の R 環境の使用はサポートされていません

プレリリース バージョンによって[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]Revolution Analytics によって作成された Windows の R 開発環境を含まれています。 このツールが提供されなくなるはサポートされていません。

互換性のため[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]、Revolution Analytics ツールではなく Microsoft R Client または Microsoft R Server をインストールすることを強くお勧めします。 Microsoft R ソリューションをサポートするクライアントとして[R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/) もお勧めします。

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>SQLite ODBC ドライバーと RevoScaleR に関する互換性の問題

SQLite ODBC ドライバーのリビジョン 0.92 は RevoScaleR と互換性がありません。 リビジョン 0.88 ~ 0.91 と 0.93 以降、互換性があることが判明しています。

## <a name="see-also"></a>参照

[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)


