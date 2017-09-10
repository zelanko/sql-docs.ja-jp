---
title: "Machine Learning のサービスに関する既知の問題 |Microsoft ドキュメント"
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
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b7b9d53a87490e83f888b47b1cff87191b9693a8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="known-issues-for-machine-learning-services"></a>Machine Learning のサービスの既知の問題

このトピックでは、機械学習の SQL Server 2016 および SQL Server 2017 のオプションとして提供されるコンポーネントで既知の問題または制限事項について説明します。

具体的に指示がない限り、以下のすべてに適用されます。

+ SQL Server 2016

  - R Services (In-Database)
  - Microsoft R Server (スタンドアロン)

+ SQL Server 2017

  - Machine Learning の R (In-database) 用サービス
  - Machine Learning Python (In-database) 用サービス
  - Machine Learning Server (スタンドアロン)

## <a name="setup-and-configuration-issues"></a>セットアップおよび構成の問題

初期セットアップと構成に関連する処理で一般的な質問の説明がここに一覧表示されます:[アップグレードとインストールに関する FAQ](r/upgrade-and-installation-faq-sql-server-r-services.md)です。

アップグレード、サイド バイ サイド インストール、および新しい R または Python コンポーネントのインストール方法については、この記事も参照してください。

### <a name="unable-to-install-python-components-in-in-offline-installs-of-sql-server-2017"></a>SQL Server 2017 のオフライン インストールでの Python コンポーネントをインストールできません。

インストーラーがダウンロードされた Python コンポーネント以外の場所の入力を求めるページが表示できないことがありますをインターネットにアクセスできないコンピューターを SQL Server 2017 をインストールする場合したがって、Python のコンポーネントではないは Machine Learning サービス機能をインストールすることができます。

この問題は、今後のリリースで修正されます。 この問題を回避するには、一時的にセットアップの実行中にインターネットへのアクセスを有効にできます。 R. にこの制限は適用されません。

**適用されます:** Python の SQL Server 2017

### <a name="install-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>最新のサービス リリースをインストールして Microsoft R Client との互換性を維持する

Microsoft R クライアントの最新バージョンをインストールしてで R を実行することを使用する計算コンテキストを使用して、リモート SQL Server は、次のようなエラーが発生する可能性があります。

*Microsoft R Server バージョン 8.x.x と互換性がないコンピューターに Microsoft R クライアントのバージョン 9.x.x を実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 により、クライアント上の R ライブラリは、サーバー上の R ライブラリを正確に一致が必要です。 R Server 9.0.1 より後のリリースの制限が削除されています。 ただし、このエラーが発生した場合は、R ライブラリのバージョンが、クライアントで使用され、サーバーでは、必要に応じて、%1%n サーバー バージョンと一致するクライアントの更新を確認します。

SQL Server サービスのリリースがインストールされているときに、SQL Server R Services と共にインストールされている R のバージョンが更新されます。 したがってを常に最新バージョンの R コンポーネントがあることを確認して、すべてのサービス パックをインストールする必要があります。

Microsoft R Client 9.0.0 との互換性を維持するには、この [サポート記事](https://support.microsoft.com/kb/3210262)で説明されている更新プログラムをインストールする必要があります。

R パッケージに問題を避けるためには、R ライブラリ」の説明に従って、最新のライフ サイクル ポリシーに変更することで、サーバーにインストールされているのバージョンをアップグレードすることも[ここ](#bkmk_sqlbindr)です。 SQL Server と共にインストールされている R のバージョンがサーバーとクライアントの両方は、常に、Microsoft R. の最新リリースを持つことができるようにする、Microsoft R Server の更新プログラムが発行されたこと、同じスケジュールで更新これを行うときに

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="bkmk_sqlbindr"></a>使用してクライアントからの古いバージョンの SQL Server R Services に接続するときに、互換性のないバージョンの警告[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] のセットアップ ウィザードまたは [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)の新しいスタンドアロン インストーラーを使用してクライアント コンピューターに Microsoft R Server をインストールしている状態で、以前のバージョンの SQL Server R Services を使用するコンピューティング コンテキストで R コードを実行すると、次のようなエラーが表示される場合があります。

*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

**SqlBindR.exe** ツールは、互換性のある 9.0 バージョンへの SQL Server インスタンスのアップグレードをサポートするために Microsoft R Server 9.0 リリースで提供されています。 9.0 への R Services インスタンスのアップグレードのサポートは、今後のサービス リリースの一部として SQL Server に追加されます。 将来のアップグレードの候補となるバージョンには、SQL Server 2016 RTM CU3 + と SP1 以降、および SQL Server 2017 CTP 1.1 が含まれます。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>SQL Server 2016 サービス リリースをセットアップすると、新しいバージョンの R コンポーネントのインストールに失敗する場合がある

累積的な更新プログラムをインストールした場合や、インターネットに接続されていないコンピューターに SQL Server 2016 のサービス パックをインストールした場合は、セットアップ ウィザードに、ダウンロードした CAB ファイルを使用して R コンポーネントを更新するためのプロンプトが表示されないことがあります。 通常、これはデータベース エンジンと共に複数のコンポーネントがインストールされている場合に発生します。

この問題を回避するには、コマンドラインを使用し、サービス リリースをインストールすることができます、 */MRCACHEDIRECTORY*引数のこの例では、CU1 更新プログラムをインストールします。

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

最新のインストーラーを取得するには、次を参照してください。 [Machine Learning Components without Internet Access をインストールする](r/installing-ml-components-without-internet-access.md)です。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="launchpad-services-fails-to-start-if-version-is-different-than-r-version"></a>スタート パッド サービスのバージョンが R のバージョンと異なる場合は開始できない

データベース エンジンから R Services を個別にインストールするし、ビルドのバージョンが異なる場合、システム イベント ログでこのエラーを参照してください可能性があります: _SQL Server スタート パッド サービスは、次のエラーにより開始できませんでしたサービスがしませんでした。適切なタイミングで開始または制御要求に応答します。_

たとえば、このエラーは、リリース バージョンを使用してデータベース エンジンをインストールする場合に、パッチを適用してデータベース エンジンをアップグレードしてからリリース バージョンを使用して R Services を追加した場合に発生することがあります。

この問題を回避するには、すべてのコンポーネントのバージョン番号が同じであることを確認します。 1 つのコンポーネントをアップグレードする場合は、インストールされている他のすべてのコンポーネントに必ず同じアップグレードを適用してください。

SQL Server 2016 の各リリースに必要な R バージョン番号のリストを表示する場合は、「 [インターネットへのアクセスなしで R コンポーネントをインストールする](r/installing-ml-components-without-internet-access.md)」を参照してください。

### <a name="remote-compute-contexts-blocked-by-firewall-in-sql-server-instances-running-on-azure-virtual-machines"></a>Azure 仮想マシンで実行されている SQL Server インスタンスのファイアウォールでブロックされるリモート計算コンテキスト

[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] が Windows Azure 仮想マシンにインストールされている場合、仮想マシンのワークスペースを使用する必要がある計算コンテキストを使用できません。 これは、Azure VM のファイアウォールに、R ローカル ユーザー アカウントのネットワーク アクセスをブロックするルールが既定で含まれるためです。

回避策として、Azure VM で **[セキュリティが強化された Windows ファイアウォール]**を開き、 **[送信の規則]**を選択して、"SQL Server インスタンス MSSQLSERVER の R ローカル ユーザー アカウントのネットワーク アクセスをブロック" ルールを無効にします。

### <a name="implied-authentication-in-sqlexpress"></a>SQLEXPRESS での暗黙の認証

Windows 統合認証を使用してリモート データ サイエンス ワークステーションから R ジョブを実行する際に、SQL Server は *暗黙の認証* を使用して、スクリプトで必要になる可能性のあるローカル ODBC 呼び出しを生成します。 ただし、この機能は、SQL Server Express Edition の RTM ビルドでは使用できません。

この問題を解決するために、新しいサービス リリースにアップグレードすることをお勧めします。

アップグレードできない場合は、SQL ログインを使用して、埋め込みの ODBC 呼び出しを必要とする可能性のあるリモート R ジョブを実行できます。

**適用されます:** Services Express Edition の SQL Server 2016 R

### <a name="performance-limits-when-r-libraries-are-called-from-standalone-r-tools"></a>R ライブラリがスタンドアロン R ツールから呼び出された場合にパフォーマンスが制限します。

R のツールと RGui などの外部 R アプリケーションから SQL Server R Services のインストールされているライブラリを呼び出すことができます。 新しいパッケージのインストールまたは非常に短いコード サンプルでアドホック テストを実行するときに、便利な可能性があります。

ただし、SQL Server の外部でパフォーマンスが制限されることに注意してください。 たとえば、SQL Server の Enterprise Edition を購入した場合でも R が実行シングル スレッド モードで外部ツールを使用して R コードを実行するとします。 パフォーマンスが優れているは、SQL Server の接続を開始しを使用して、R コードを実行する場合にする[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)の R ライブラリを呼び出しがされます。

+ 外部 R ツールから SQL Server で使用される R ライブラリは呼び出さないでください。
+ SQL server を使用せず、SQL Server コンピューターで広範な R コードを実行する必要がある場合は、Microsoft R クライアントなどの R の別のインスタンスをインストールし、R 開発ツールは、新しいライブラリを指していることを確認します。

詳細については、「 [スタンドアロン R Server の作成](r/create-a-standalone-r-server.md)」を参照してください。

### <a name="r-script-throttled-due-to-resource-governance-default-values"></a>R スクリプトのリソース ガバナンスの既定値が原因で抑制

Enterprise Edition では、外部スクリプト プロセスを管理するためにリソース プールを使用できます。 いくつかの初期のリリース ビルドでは、R プロセスに割り当てられる最大メモリは、20% をでした。 したがって、サーバーに 32 GB の RAM がある場合、R の実行可能ファイル (RTerm.exe および BxlServer.exe) では 1 つの要求で最大 6.4 GB を使用できました。

リソースに制限がある場合は、現在の既定値を確認し、20% では十分でない場合は、この値の変更方法について、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のドキュメントを参照してください。

**適用されます:** SQL Server 2016 の R Services, Enterprise Edition

## <a name="r-code-execution-and-package-or-function-issues"></a>R コードの実行とパッケージまたは関数の問題

このセクションには、SQL Server で R を実行している固有の既知の問題だけでなく、R ライブラリと RevoScaleR をなど、マイクロソフトによって発行されたツールに関連するいくつかの問題が含まれています。

R ソリューションに影響する可能性がその他の既知の問題は、Microsoft R Server のサイトを参照してください: [Microsoft R Server の既知の問題](https://msdn.microsoft.com/microsoft-r/rserver-known-issues)

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>R ジョブのプロセッサ アフィニティに関する制限事項

SQL Server 2016 の最初のリリース ビルドでは、最初の k グループ内の Cpu のみのプロセッサ アフィニティを設定できます。 たとえば、サーバーが 2 k グループの 2 ソケット マシンである場合、最初の k グループのプロセッサのみが R プロセスで使用されます。 R スクリプト ジョブのリソース管理を構成するときに、同じ制限が適用されます。

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

回避策として、SQL クエリを書き直し、CAST または CONVERT を使用して、正しいデータ型を用いて R でデータを表示できます。 一般的には、R コードでデータを変更するのではなく、SQL を使用してデータを操作することをお勧めします。

**適用されます:** SQL Server 2016 の R Services

### <a name="avoid-clearing-workspaces-when-executing-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンピューティング コンテキストでの R コードの実行時にワークスペースをクリアできない

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンピューティング コンテキストで R コードを実行中に R コマンドを使用してオブジェクトのワークスペースをクリアする場合や、 [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して呼び出した R スクリプトの一部としてワークスペースをクリアする場合、" *ワークスペース オブジェクト 'revoScriptConnection' が見つかりません*" のようなエラーが発生することがあります。

`revoScriptConnection` は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]から呼び出される R セッションに関する情報を含む R ワークスペース内のオブジェクトです。 ただし、R コードにワークスペースをクリアするためのコマンド ( `rm(list=ls()))`など) が含まれている場合は、R ワークスペース内のセッションおよび他のオブジェクトに関するすべての情報もクリアされます。

回避策として、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]での R の実行時に変数および他のオブジェクトを無差別にクリアしないようにします。 R コンソールでの操作時にワークスペースをクリアすることはよくありますが、意図しない結果になる場合があります。

+ 特定の変数を削除するには、R の *remove* 関数の `remove('name1', 'name2', ...)`を使用します。
+ 削除する変数が複数ある場合は、リストに一時変数の名前を保存し、ガベージ コレクションを定期的に実行します。

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>R スクリプトの入力として提供できるデータに対する制限事項

次の種類のクエリ結果は、R スクリプトでは使用できません。

- AlwaysEncrypted 列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
- マスクされた列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
     R スクリプトでマスクされたデータを使用する必要がある場合、考えられる次善策として、一時テーブルにデータのコピーを作成し、代わりにそのデータを使用します。

### <a name="arguments-varstokeep-and-varstodrop-not-supported-for-sql-server-data-sources"></a>引数*varsToKeep*と*varsToDrop* SQL Server データ ソースはサポートされていません

使用してテーブルに結果を書き込む rxDataStep 関数を使用する場合、 *varsToKeep*と*varsToDrop*または操作の一部として除外する列を指定する便利な方法は、します。 現時点では、これらの引数は、SQL Server データ ソースに対してはサポートされません。

この制限は、今後のリリースで削除されます。

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>SQL データ型の制限付きサポート`sp_execute_external_script`

SQL でサポートされているデータ型の一部を R で使用できません。回避策として、サポートされていないデータ型をサポートされているデータ型にキャストしてから、sp_execute_external_script にデータを渡すことを検討してください。

詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

### <a name="possible-string-corruption"></a>文字列が破損する可能性がある

文字列データが [!INCLUDE[tsql](../includes/tsql-md.md)] から R に送信された後、再び [!INCLUDE[tsql](../includes/tsql-md.md)] に返されるラウンドトリップで、文字列が破損する可能性があります。 これは、R と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]で異なるエンコードが使用されていることと、R と [!INCLUDE[tsql](../includes/tsql-md.md)]でサポートされる照合順序と言語が異なることに起因します。 非 ASCII エンコードの文字列は正しく処理されない可能性があります。

文字列データを R に送信するときに、可能であれば、ASCII 形式に変換します。

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>型の値を 1 つだけ`raw`から返されることができます`sp_execute_external_script`

R から binary データ型 (R の **raw** データ型) を返す場合、この値は出力データ フレーム内の値である必要があります。

今後のリリースで、 **raw** の複数の出力のサポートが追加される予定です。

複数の出力セットが必要な場合の考えられる次善策の 1 つとして、ストアド プロシージャの複数の呼び出しを実行し、ODBC を使用して結果セットを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に送信します。

OUTPUT キーワードを追加するだけで、ストアド プロシージャの結果と共にパラメーター値を返すことができます。 詳細については、「 [OUTPUT パラメーターを使用してデータを返す処理](https://technet.microsoft.com/library/ms187004.aspx)」を参照してください。

### <a name="loss-of-precision"></a>精度の損失

[!INCLUDE[tsql](../includes/tsql-md.md)] と R はサポートするデータ型が異なるため、変換時に数値データ型の精度が損なわれる可能性があります。

暗黙的なデータ型変換の詳細については、「 [Working with R Data Types](r/r-libraries-and-data-types.md)」を参照してください。

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

### <a name="data-import-and-manipulation-using-revoscaler"></a>RevoScaleR を使用したデータのインポートと操作

データベースから **varchar** 列を読み取るときに、空白が削除されます。 これを防ぐには、空白以外の文字で文字列を囲みます。

`rxDataStep` などの関数を使用して **varchar** 列を含むデータベース テーブルを作成するときには、データのサンプルに基づいて列幅が推定されます。 幅が増減する可能性がある場合、すべての文字列を共通の長さにして空白を埋めることが必要な場合があります。

`rxImport` または `rxTextToXdf` の繰り返しの呼び出しを使用して行のインポートと追加を実行し、複数の入力ファイルを 1 つの .xdf ファイルに結合する場合、変換を使用した変数のデータ型の変更はサポートされていません。

### <a name="limited-support-for-rxexec"></a>RxExec の制限付きサポート

SQL Server 2016 では、`rxExec`が RevoScaleR パッケージで提供される関数は、シングル スレッド モードでのみ使用できます。

複数のプロセスでの `rxExec` の並列処理は、今後のリリースで追加される予定です。

### <a name="increase-maximum-parameter-size-to-support-rxgetvarinfo"></a>RxGetVarInfo をサポートするためにパラメーターの最大サイズを増やす

非常に多くの変数 (40,000 個以上など) が含まれたデータ セットを使用する場合、 `max-ppsize` などの関数を使用するために、R の起動時に `rxGetVarInfo`フラグを設定する必要があります。  `max-ppsize` フラグは、ポインター保護スタックの最大サイズを指定します。

(rgui.exe や rterm.exe などで) R コンソールを使用している場合、次のように入力することで max-ppsize の値を 500000 に設定できます。

```  
R --max-ppsize=500000  
```  
  
[!INCLUDE[rsql_developr](../includes/rsql-developr-md.md)] 環境を使用している場合は、次のように RevoIDE 実行可能ファイルを呼び出すことで、 `max-ppsize` フラグを設定できます。

```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  

### <a name="issues-with-the-rxdtree-function"></a>RxDTree 関数に関する問題

`rxDTree` 関数では、式内変換は現在サポートされていません。 特に、係数を即座に作成するための `F()` 構文の使用はサポートされていません。 ただし、数値は自動的にビン分割されます。

順序付けされた係数は、 `rxDTree`を除くすべての RevoScaleR 分析関数の係数と同様に処理されます。

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise と Microsoft R Open

このセクションでは、Revolution Analytics によって提供される R の接続、開発、およびパフォーマンス ツールに固有の問題を示します。 これらのツールは、以前のプレリリース版の  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]で提供されていました。 

一般に、これらの以前のバージョンをアンインストールして、SQL Server または Microsoft R Server の最新バージョンをインストールすることをお勧めします。

### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Revolution R Enterprise の複数のバージョンの共存

Revolution R Enterprise をインストールして任意のバージョンの [!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)] と共存させることはできません。

別のバージョンの Revolution R Enterprise を使用するためのライセンスがある場合は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスおよび [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスへの接続に使用するワークステーションとは別のコンピューターにライセンスを配置する必要があります。

### <a name="use-of-r-productivity-environment-not-supported"></a>サポートされていません R Productivity Environment の使用

一部のプレリリース版の [!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)] には、Revolution Analytics によって作成された Windows 用の R 開発環境が含まれていました。 このツールになったことはできませんし、サポートされていません。

互換性のため[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]、Revolution Analytics ツールではなく Microsoft R Client または Microsoft R Server をインストールすることを強くお勧めします。 Microsoft R ソリューションをサポートするクライアントとして[R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/) もお勧めします。

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>SQLite ODBC ドライバーと RevoScaleR に関する互換性の問題

SQLite ODBC ドライバーのリビジョン 0.92 は RevoScaleR と互換性がありません。リビジョン 0.88 ～ 0.91 と 0.93 以降は互換性があることがわかっています。

## <a name="see-also"></a>参照

[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)


