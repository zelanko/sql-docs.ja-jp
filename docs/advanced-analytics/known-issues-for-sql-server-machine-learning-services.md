---
title: "Machine Learning のサービスの既知の問題 |Microsoft ドキュメント"
ms.date: 01/19/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: "53"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 197bfc48d000246b59b983fbf890e998cc2b5beb
ms.sourcegitcommit: d7dcbcebbf416298f838a39dd5de6a46ca9f77aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2018
---
# <a name="known-issues-in-machine-learning-services"></a>Machine Learning のサービスの既知の問題

この記事では、機械学習の SQL Server 2016 および SQL Server 2017 のオプションとして提供されるコンポーネントで既知の問題または制限事項について説明します。

特に指示しない限り、ここにある情報が、次のすべてに適用されます。

* SQL Server 2016

  - R Services (データベース内)
  - Microsoft R Server (スタンドアロン)

* SQL Server 2017

  - Machine Learning の R (In-database) 用サービス
  - Machine Learning Python (In-database) 用サービス
  - Machine Learning Server (スタンドアロン)

## <a name="setup-and-configuration-issues"></a>セットアップおよび構成の問題

プロセスとの初期セットアップと構成に関連する一般的な質問については、次を参照してください。[アップグレードとインストールに関する FAQ](r/upgrade-and-installation-faq-sql-server-r-services.md)です。 アップグレード、サイド バイ サイド インストール、および新しい R または Python コンポーネントのインストールに関する情報が含まれています。

### <a name="unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>ドメイン コント ローラーに SQL Server マシン学習機能をインストールできません。

SQL Server 2016 の R Services または SQL Server 2017 Machine Learning サービスをドメイン コント ローラーにインストールしようとすると、セットアップが失敗がこれらのエラー。

>*「エラーは、機能のセットアップ プロセス中に発生しました。」*
> 
>*「... Id を持つグループを見つけることができません」*
> 
>*"コンポーネントのエラー コード: 0x80131509"*

、ドメイン コント ローラーで、サービス アカウントを作成できない、20 ローカル機械学習の実行に必要なために、障害が発生します。 一般に、ドメイン コント ローラー上の SQL Server のインストールはお勧めしません。 詳細については、次を参照してください。[サポート情報 2032911](https://support.microsoft.com/en-us/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont)です。

### <a name="install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Microsoft R クライアントとの互換性を確保するのには、最新のサービス リリースをインストールします。

Microsoft R クライアントの最新バージョンをインストール、使用して、SQL Server でリモート計算コンテキストで R を実行する場合、次のようなエラーが発生した可能性があります。

>*Microsoft R Server バージョン 8.x.x と互換性がないコンピューターに Microsoft R Client のバージョン 9.x.x を実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 では、クライアント上の R ライブラリは、サーバー上の R ライブラリを正確に一致が必要です。 制限は R Server 9.0.1 より後のリリースで削除されました。 ただし、このエラーが発生した場合は、クライアントとサーバーによって使用され、必要に応じて、サーバー バージョンと一致するクライアントを更新する R ライブラリのバージョンを確認します。

SQL Server サービスのリリースがインストールされているときに、SQL Server R Services と共にインストールされている R のバージョンが更新されます。 常に最新バージョンの R コンポーネントがあることを確認してください、するすべてのサービス パックをインストールすることを確認します。

Microsoft R クライアント 9.0.0 との互換性のために、これに説明されている更新プログラムのインストール[サポートの記事](https://support.microsoft.com/kb/3210262)です。

R パッケージに問題を避けるためには、R ライブラリ」の説明に従って、最新のライフ サイクルのサポート ポリシーを使用して、サービス契約を変更することで、サーバーにインストールされているのバージョンをアップグレードすることも[、次のセクション](#bkmk_sqlbindr)です。 これを行うときに SQL Server と共にインストールされている R のバージョンは、machine Learning サーバー (旧称 Microsoft R Server) の更新に使用される同じスケジュールで更新されます。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>オフライン インストールでは SQL Server 2017 CTP 2.0 またはそれ以降に Python コンポーネントをインストールすることができません。

インターネットにアクセスできないコンピューターに SQL Server 2017 のプレリリース版をインストールする場合は、ダウンロードされた Python コンポーネントの場所の入力を求めるページを表示するインストーラーが失敗します。 このようなインスタンスでは、Machine Learning サービス機能は、Python コンポーネントではないをインストールできます。

リリース バージョンでは、この問題が解決します。 この問題を回避するには、この問題が発生した場合は、セットアップ中に一時的にインターネットへのアクセスを有効にできます。 R. にこの制限は適用されません。

**適用されます:** Python の SQL Server 2017

### <a name="bkmk_sqlbindr"></a>使用して、クライアントから、古いバージョンの SQL Server R Services に接続するときに、互換性のないバージョンの警告[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

SQL Server 2016 のコンピューティング コンテキストで R コードを実行するときは、次のようなエラーを参照してください可能性があります。

*Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

次の 2 つのステートメントのいずれかが true の場合、このメッセージが表示されます。

+ セットアップ ウィザードを使用してクライアント コンピューターで R Server (スタンドアロン) をインストールした[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]です。
+ 使用して Microsoft R Server をインストールする、 [Windows インストーラーを区切る](https://docs.microsoft.com/r-server/install/r-server-install-windows)です。

使用する必要があります、同じバージョンを使用すると、サーバーとクライアント_バインディング_、SQL Server 2016 インスタンスに R コンポーネントをアップグレードするには、Microsoft R Server 9.0 と以降のリリースでサポートされています。 かどうかをする R サービスのバージョンを参照して、アップグレードを使用できます[SqlBindR.exe を使用して R Services のインスタンスをアップグレード](/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>SQL Server 2016 サービス リリースをセットアップすると、新しいバージョンの R コンポーネントのインストールに失敗する場合がある

累積的な更新プログラムのインストールまたはインターネットに接続されていないコンピューターに SQL Server 2016 の service pack をインストールするときに、ダウンロードした CAB ファイルを使用して、R コンポーネントを更新できるプロンプトを表示するセットアップ ウィザードが失敗します。 このエラーは、複数のコンポーネントは、データベース エンジンと共にインストールされたときに通常発生します。

この問題を回避するには、コマンドラインを使用し、サービス リリースをインストールすることができます、`MRCACHEDIRECTORY`引数のこの例では、CU1 更新プログラムをインストールします。

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

最新のインストーラーを取得するには、次を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストール](r/installing-ml-components-without-internet-access.md)です。

**適用されます:** SQL Server 2016 R Services、R Server バージョン 9.0.0 の以前のバージョン

### <a name="launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>スタート パッド サービスのバージョンが R のバージョンと異なる場合の開始に失敗します。

データベース エンジンから SQL Server R Services を個別にインストールするし、ビルドのバージョンが異なる場合は、システム イベント ログに次のエラーを参照してください可能性があります。

>_SQL Server スタート パッド サービスは、次のエラーのため開始できませんでした。 サービスは適時に開始または制御要求に応答しませんでした。_

たとえば、このエラー可能性があります、リリース バージョンを使用して、データベース エンジンをインストールする場合に発生する、データベース エンジンのアップグレード修正プログラムを適用およびリリース バージョンを使用して、R Services の機能を追加します。

この問題を回避するには、ファイル マネージャーなどのユーティリティを使用して Launchpad.exe のバージョンの sqldk.dll などの SQL バイナリのバージョンと比較します。 すべてのコンポーネントは、同じバージョン番号が必要です。 1 つのコンポーネントをアップグレードする場合は、インストールされている他のすべてのコンポーネントに必ず同じアップグレードを適用してください。

スタート パッドを探して、`Binn`インスタンスのフォルダーです。 たとえば、SQL Server 2016 の既定のインストールで、パスがあります"C:\Program files \microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn"。 

### <a name="remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>Azure の仮想マシンで実行されている SQL Server インスタンス内のファイアウォールでリモート計算コンテキストがブロックされています。

インストールした場合[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Windows Azure バーチャル マシンでは、するできないことがありますを仮想マシンのワークスペースの使用を必要とする計算コンテキストを使用します。 既定では、Azure の仮想マシン上のファイアウォール ルールが含まれる、ネットワークのローカルの R ユーザー アカウントのアクセスをブロックです。

Azure vm での回避策として開きます**セキュリティが強化された Windows ファイアウォール****送信の規則**、し、次のルールを無効にする:**で R ローカル ユーザー アカウントのネットワーク アクセスをブロックSQL Server インスタンス MSSQLSERVER**です。 有効な場合、ルールのままには、セキュリティ プロパティを変更することができますも**許可する場合は、セキュリティで保護された**です。

### <a name="implied-authentication-in-sqlexpress"></a>SQLEXPRESS での暗黙の認証

統合 Windows 認証を使用してリモート データ サイエンス ワークステーションから R ジョブを実行した場合に、SQL Server が使用*黙示的な認証*をスクリプトで必要なローカルの ODBC 呼び出しを生成します。 ただし、この機能は、SQL Server Express Edition の RTM ビルドでは使用できません。

この問題を解決するために、新しいサービス リリースにアップグレードすることをお勧めします。

アップグレードできない場合は、SQL ログインを使用して、埋め込みの ODBC 呼び出しを必要とする可能性のあるリモート R ジョブを実行できます。

**適用されます:** Services Express Edition の SQL Server 2016 R

### <a name="performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>SQL Server で使用されるライブラリが他のツールから呼び出されると、パフォーマンスの制限

これは、機械学習 RGui など、外部アプリケーションから SQL Server のインストールされているライブラリを呼び出すことです。 これにより、新しいパッケージのインストールや、非常に短いコード サンプルでのアドホック テストの実行などの特定のタスクを実行する最も便利な方法があります。 ただし、SQL Server の外部パフォーマンスを制限する可能性があります。 

たとえば、SQL Server の Enterprise Edition を使用している場合でも R モードで実行シングル スレッド外部ツールを使用して、R コードを実行するとします。 SQL Server のパフォーマンスの利点を取得する SQL Server の接続を開始して[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を外部スクリプトの実行時を呼び出します。

+ 一般に、機械学習の外部ツールから SQL Server で使用されるライブラリを呼び出すことを回避します。 デバッグ R または Python コードをする必要がある場合は、そのためには SQL Server の外部通常簡単です。 Microsoft R クライアントをインストールする SQL Server 内にある同じライブラリを取得するにまたは[Machine Learning サーバー](r/create-a-standalone-r-server.md)です。

### <a name="sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>SQL Server Data Tools は外部スクリプトで必要なアクセス許可をサポートしていません

使用すると Visual Studio または SQL Server Data Tools データベース プロジェクトを発行する任意のプリンシパルは、外部スクリプトの実行に固有のアクセス許可を持っている場合、次のようなエラーが発生した可能性があります。

"TSQL モデル: エラーとリバース エンジニア リング、データベースが検出されました。 アクセス許可は認識されず、インポートされませんでした。"

現在、DACPAC モデルは R Services または GRANT ANY 外部スクリプト、または EXECUTE ANY EXTERNAL SCRIPT などの Machine Learning サービスによって使用されるアクセス許可をサポートしていません。 この問題は今後のリリースで修正される予定です。

この問題を回避するには、追加の許可でステートメントを実行、配置後スクリプトです。

### <a name="external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>リソース統制の既定値が原因で抑制は外部スクリプトの実行

Enterprise Edition では、外部スクリプト プロセスを管理するためにリソース プールを使用できます。 いくつかの初期のリリース ビルドでは、R プロセスに割り当てられる最大メモリは、20% をでした。 そのため、サーバーに 32 GB の RAM がある場合、R の実行可能ファイル (RTerm.exe と BxlServer.exe) は、最大 1 つの要求で 6.4 GB を使用できます。

リソースの制限により、発生した場合は、現在の既定値を確認します。 20% が十分でない場合は、ドキュメントを参照して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でこの値を変更する方法です。

**適用されます:** SQL Server 2016 の R Services, Enterprise Edition

## <a name="r-issues"></a>R の問題

このセクションでは、SQL Server で R を実行している固有の既知の問題だけでなく、R ライブラリと RevoScaleR をなど、マイクロソフトによって発行されたツールに関連する問題のいくつか含まれています。

追加既知の問題を R ソリューションを与える可能性がありますを参照してください、 [Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/resources-known-issues)サイトです。

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>R ジョブのプロセッサ アフィニティに関する制限事項

SQL Server 2016 の最初のリリース ビルドでは、最初の k グループ内の Cpu のみのプロセッサ アフィニティを設定できます。 たとえば、2 ソケットのマシンが 2 つの k グループをサーバーには場合、は、最初の k グループからのみのプロセッサが R プロセスに使用されます。 R スクリプトのジョブのリソース管理を構成するときに、同じ制限が適用されます。

この問題は SQL Server 2016 Service Pack 1 で修正されました。 最新のサービス リリースにアップグレードすることをお勧めします。

**適用されます:**バージョンの SQL Server 2016 R Services RTM

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>SQL Server コンピューティング コンテキストでのデータの読み取り時に列の型を変更できない

コンピューティング コンテキストが SQL Server インスタンスに設定されている場合は、 _colClasses_ 引数 (または他の同様の引数) を使用して、R コードで列のデータ型を変更できません。

たとえば、CRSDepTimeStr 列がまだ整数でない場合、次のステートメントでエラーが発生します。

```r
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

この問題を回避するには、キャストを使用する SQL クエリを書き直すことができます、または変換して正しいデータ型を使用してデータを R に提供します。 一般に、パフォーマンスは、操作する際にデータを R コードでデータを変更することによってではなく、SQL を使用しています。

**適用されます:** SQL Server 2016 の R Services

### <a name="limits-on-size-of-serialized-models"></a>シリアル化されたモデルのサイズの制限

モデルを SQL Server テーブルに保存すると、モデルをシリアル化およびバイナリ形式で保存する必要があります。 理論上はこのメソッドを使用して格納できるモデルの最大サイズは、2 GB は、SQL Server の varbinary 列の最大サイズです。

大規模なモデルを使用する必要がある場合は、次の回避策を使用できます。

+ モデルのサイズを縮小する手順を実行します。 一部のオープン ソース R パッケージは、モデル オブジェクトに多くの情報を含めるし、展開の情報の大部分を削除することができます。 
+ 機能の選択を使用すると、不要な列を削除します。
+ オープン ソースのアルゴリズムを使用している場合は、MicrosoftML または RevoScaleR で対応するアルゴリズムを使用して同様の実装を検討します。 これらのパッケージは、展開シナリオ用に最適化されています。
+ 場合、モデルが合理化されたされているし、上記の手順を使用して、サイズの縮小を参照してください、 [memCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress)を SQL Server に渡す前に、モデルのサイズを減らすために基本の r 関数を使用できます。 モデルが 2 GB の制限に近い場合は、このオプションをお勧めします。
+ 大規模なモデルでは、SQL Server を使用することができます[FileTable](..\relational-databases\blob\filetables-sql-server.md) varbinary 列を使用するのではなく、モデルを格納する機能します。

    Filetable を使用するには、Filetable に格納されたデータは、Filestream ファイル システム ドライバーで SQL Server で管理され、既定のファイアウォール規則は、ネットワーク ファイルへのアクセスをブロックするため、ファイアウォールの例外を追加する必要があります。 詳細については、次を参照してください。 [FileTable の前提条件を有効にする](../relational-databases/blob/enable-the-prerequisites-for-filetable.md)です。 

    FileTable を有効にした後、モデルの書き込み先、FileTable の API を使用して SQL からのパスを取得してその場所に、コードからモデルを作成します。 モデルの読み取りに必要なときは、SQL からパスを取得して、スクリプトからのパスを使用して、モデルを呼び出します。 詳細については、次を参照してください。[ファイル入出力 Api を使用した Filetable へのアクセス](../relational-databases/blob/access-filetables-with-file-input-output-apis.md)です。

### <a name="avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>R コードを実行するときに、ワークスペースをオフにしないで、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]計算コンテキスト

R コマンドを使用して R コードの実行中にオブジェクトのワークスペースを削除する場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]コンピューティング コンテキストを使用して R スクリプトの一部としてワークスペースをクリアするかどうか、または呼び出す[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、このエラーが発生する可能性があります:*ワークスペース オブジェクト revoScriptConnection が見つかりませんでした*

`revoScriptConnection` は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]から呼び出される R セッションに関する情報を含む R ワークスペース内のオブジェクトです。 ただし、R コードにワークスペースをクリアするためのコマンド ( `rm(list=ls()))`など) が含まれている場合は、R ワークスペース内のセッションおよび他のオブジェクトに関するすべての情報もクリアされます。

この問題を回避するには、変数およびその他のオブジェクトの区別しないで消去中にされないようにで R を実行している[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 それが持つことができますが、ワークスペースをクリアする一般的な R コンソールで作業するとき、予想外の結果。

* 特定の変数を削除するには、R を使用`remove`関数: たとえば、`remove('name1', 'name2', ...)`
* 削除する変数が複数ある場合は、リストに一時変数の名前を保存し、ガベージ コレクションを定期的に実行します。

### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>R スクリプトの入力として提供できるデータに対する制限事項

次の種類のクエリ結果は、R スクリプトでは使用できません。

- AlwaysEncrypted 列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
- マスクされた列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
     R スクリプトでマスクされたデータを使用する必要がある場合、考えられる次善策として、一時テーブルにデータのコピーを作成し、代わりにそのデータを使用します。

### <a name="use-of-strings-as-factors-can-lead-to-performance-degradation"></a>パフォーマンスの低下につながる可能性が要素として文字列の使用します。

R 演算に使用されるメモリの量を大幅に増加させる要因とは、文字列型の変数を使用します。 R の既知の問題を一般に、これは、多数の記事にあるサブジェクトに。 たとえばを参照してください[要因が捉える r-bloggers で、John マウントして、R ではない)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/)または[stringsAsFactors: Roger Peng によって、承認されていない人物詳細](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/)です。 

問題は SQL Server に固有ではありませんが、SQl Server で実行される R コードのパフォーマンス大きく変化します。 文字列は通常、varchar、nvarchar、として格納され、内部的にこれらの整数にし、R での文字列に変換するプロセスがメモリ割り当てエラーにつながることができますも文字列データの列に多数の一意の値がある場合は、します。

絶対に必要としない文字列データ型の他の操作では、文字列値を数値 (整数) にマップする場合、データは、データの準備の一部のパフォーマンスと拡張性の観点からと役に立つようを入力します。

この問題とその他のヒントの詳細については、次を参照してください。 [R Services - データの最適化のパフォーマンス](r/r-and-data-optimization-r-services.md)です。

### <a name="arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>引数*varsToKeep*と*varsToDrop* SQL Server データ ソースはサポートされていません

使用してテーブルに結果を書き込む rxDataStep 関数を使用する場合、 *varsToKeep*と*varsToDrop*または操作の一部として除外する列を指定する便利な方法は、します。 ただし、これらの引数は、SQL Server データ ソースに対してはサポートされません。

### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>SQL データ型の制限付きサポート`sp_execute_external_script`

SQL でサポートされているデータ型の一部を R で使用できません。回避策として、サポートされていないデータ型をサポートされているデータ型にキャストしてから、sp_execute_external_script にデータを渡すことを検討してください。

詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

### <a name="possible-string-corruption"></a>文字列が破損する可能性がある

文字列からのデータのラウンド トリップ[!INCLUDE[tsql](../includes/tsql-md.md)]、R に[!INCLUDE[tsql](../includes/tsql-md.md)]破損再度を招くことができます。 これは、R で使用されるさまざまなエンコードにより[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、さまざまな照合順序と R でサポートされている言語だけでなくと[!INCLUDE[tsql](../includes/tsql-md.md)]です。 非 ASCII エンコードの文字列は正しく処理されない可能性があります。

文字列データを R に送信するときに可能であれば、ASCII 形式に変換します。

この制限は、同様の SQL Server および Python の間で渡されるデータに適用されます。 マルチバイト文字の utf-8 として渡され、Unicode として格納されている必要があります。

### <a name="only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>型の値を 1 つだけ`raw`から返されることができます`sp_execute_external_script`

ときに、バイナリ データ型 (R**生**データ型) が返されます、R から、値が出力データ フレームに送信する必要があります。

データ型以外の**生**、OUTPUT キーワードを追加することで、ストアド プロシージャの結果と共にパラメーター値を返すことができます。 詳細については、次を参照してください。[パラメーター](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters)です。

型の値を含む複数の出力セットを使用する場合**生**戻す設定可能な回避策は、ストアド プロシージャの複数の呼び出しを実行するか、または結果を送信する 1 つ[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ODBC を使用しています。

### <a name="loss-of-precision"></a>精度の損失

[!INCLUDE[tsql](../includes/tsql-md.md)]と R をサポートしてさまざまなデータ型、数値データ型は変換中に有効桁数の損失を低下することができます。

暗黙のデータ型変換の詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

### <a name="variable-scoping-error-when-you-use-the-transformfunc-parameter-the-sample-data-set-for-the-analysis-has-no-variables"></a>変数のスコープ transformFunc パラメーターを使用するときのエラー:*分析のサンプル データ セットに変数がありません*

渡すことができますをモデル化するときにデータを変換する、 *transformFunc*などの関数の引数`rxLinmod`または`rxLogit`です。 ただし、入れ子になった関数呼び出しは、ローカル コンピューティング コンテキストでの呼び出しが正しく動作させる場合でも、SQL Server のコンピューティング コンテキストではスコープ エラーに可能性があります。

たとえば、2 つの関数が定義されている`f`と`g`をローカル グローバル環境でと`g`呼び出し`f`です。 `g`を含む分散またはリモート呼び出しでは、リモート呼び出しに `g` と `f` の両方を渡した場合でも、 `f` が見つからないために `g` の呼び出しが失敗します。

この問題が発生した場合は、 `f` の定義内の、通常 `g`が `g` を呼び出す場所より前の任意の場所に、 `f`の定義を組み込むことで問題を回避できます。

例:

```r
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

エラーを回避するには、定義を次のように書き換えます。

```r
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

並列処理次数`rxExec`複数のプロセスでは、今後のリリースで計画的なです。

### <a name="increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>RxGetVarInfo をサポートするためにパラメーターの最大サイズを増やす

非常に多数の変数 (たとえば、40,000) 経由でデータ セットを使用する場合は、設定、`max-ppsize`始めると R 関数を使用するようにフラグを設定`rxGetVarInfo`です。 `max-ppsize` フラグは、ポインター保護スタックの最大サイズを指定します。

(RGui.exe や RTerm.exe など) は、R コンソールを使用している場合は、値を設定することができます_max ppsize_ 」と入力して 500000 に。

```R
R --max-ppsize=500000
```

### <a name="issues-with-the-rxdtree-function"></a>RxDTree 関数に関する問題

`rxDTree` 関数では、式内変換は現在サポートされていません。 特に、係数を即座に作成するための `F()` 構文の使用はサポートされていません。 ただし、数値データが自動的にビン分割されます。

順序付けされた係数は、 `rxDTree`を除くすべての RevoScaleR 分析関数の係数と同様に処理されます。

## <a name="python-code-execution-or-python-package-issues"></a>Python コードの実行、または Python パッケージの問題

このセクションでは、マイクロソフトによって発行された Python パッケージに関連する問題をできるだけでなく、SQL Server で Python を実行しているに固有の既知の問題の説明を含む[revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)と[microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>モデルへのパスが長すぎる場合、事前トレーニング済みモデルへの呼び出しが失敗しました。

SQL Server 2017 の早期のリリースでは、事前トレーニング済みモデルがインストールされている場合、トレーニング済みモデル ファイルへの完全パスが Python を読み取るには長すぎます場合があります。 この制限は、以降のサービス リリースで修正します。

これにはいくつかの潜在的な回避策があります。 

+ 事前トレーニング済みモデルをインストールする場合は、カスタムの場所を選択します。
+ 可能であれば、C:\SQL\MSSQL14 などの短いパスを持つカスタムのインストール パスで SQL Server インスタンスをインストールします。MSSQLSERVER です。
+ Windows ユーティリティを使用して[Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx)短いパスをモデル ファイルにマップするハード リンクを作成します。 
+ 最新のサービス リリースを更新します。

### <a name="failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>Varbinary 変数の初期化の失敗である BxlServer でエラーが発生します。

SQL Server を使用して Python コードを実行すると`sp_execute_external_script`、varbinary (max) 型、varchar (max)、または類似した種類の変数に出力が、コードと、変数を初期化またはスクリプトの一部として設定する必要があります。 それ以外の場合、エラーと動作が停止した、データの exchange コンポーネントである BxlServer を発生させます。

この制限は、次のサービス リリースで修正される予定です。 この問題を回避するには、Python スクリプト内で、変数が初期化されることを確認します。 次の例のように、任意の有効な値を使用できます。

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N'b = 0x0'
  , @params = N'@b varbinary(max) OUTPUT'
  , @b = @b OUTPUT;
go
```

```sql
declare @b varchar(30);
exec sp_execute_external_script
  @language = N'Python'
  , @script = N' b = ""  '
  , @params = N'@b varchar(30) OUTPUT'
  , @b = @b OUTPUT;
go
```

### <a name="telemetry-warning-on-successful-execution-of-python-code"></a>Python コードの実行完了後に製品利用統計情報の警告

SQL Server 2017 CU2 以降では、次のメッセージが表示される場合でも、それ以外の場合の Python コードが正常に実行されます。

```text
STDERR message(s) from external script:  ~PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger
SyntaxWarning: telemetry_state is used prior to global declaration
```

SQL Server 2017 累積更新プログラム 3 (CU3) で、この問題は修正されました。 

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise と Microsoft R Open

このセクションでは、R の接続、開発、および Revolution Analytics によって提供されるパフォーマンス ツールに固有の問題を一覧表示します。 これらのツールは、以前のプレリリース バージョンので提供されていた[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]です。

一般に、これらの以前のバージョンをアンインストールして、SQL Server または Microsoft R Server の最新バージョンをインストールすることをお勧めします。

### <a name="revolution-r-enterprise-is-not-supported"></a>Revolution R Enterprise はサポートされていません

バージョンの Revolution R Enterprise サイド バイ サイドのインストール[!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)]はサポートされていません。

Revolution R Enterprise の既存のライセンスを取得する場合は、両方から別のコンピューターに配置する必要があります、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスと、ワークステーションへの接続に使用する、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンス。

プレリリース バージョンによって[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]Revolution Analytics によって作成された Windows の R 開発環境を含まれています。 このツールは提供されなくなるはサポートされていません。

互換性のため[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]Microsoft R クライアントをインストールすることをお勧めします。 [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)と[Visual Studio Code](https://code.visualstudio.com/)も Microsoft R ソリューションをサポートします。

### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>SQLite ODBC ドライバーと RevoScaleR に関する互換性の問題

SQLite ODBC ドライバーのリビジョン 0.92 は RevoScaleR と互換性がありません。 リビジョン 0.88 ~ 0.91 と 0.93 以降、互換性があることが判明しています。

## <a name="see-also"></a>参照

[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)

[機械学習で SQL Server のトラブルシューティング](machine-learning-troubleshooting-faq.md)
