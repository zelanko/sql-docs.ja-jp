---
title: R 言語と Python の統合 - SQL Server Machine Learning Services の既知の問題
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 88dcbbf3a336af38b80ab8c5aa4b49dbe17d9184
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962810"
---
# <a name="known-issues-in-machine-learning-services"></a>Machine Learning サービスの既知の問題
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、既知の問題またはオプションとして提供される machine learning コンポーネントと制限事項について説明します[SQL Server 2016 R Services](install/sql-r-services-windows-install.md)と[SQL Server マシン 2017 Learning Services の R と Python](install/sql-machine-learning-services-windows-install.md)。

## <a name="setup-and-configuration-issues"></a>セットアップと構成の問題

プロセスの初期セットアップと構成に関連する一般的な質問については、次を参照してください。[アップグレードとインストールに関する FAQ](r/upgrade-and-installation-faq-sql-server-r-services.md)します。 アップグレード、サイド バイ サイドでインストール、および新しい R または Python コンポーネントのインストールに関する情報が含まれています。

### <a name="1-inconsistent-results-in-mkl-computations-due-to-missing-environment-variable"></a>1.環境変数がないため、MKL 計算で矛盾した結果

**適用対象:** 9.0、9.1、9.2 または 9.3 にバイナリを R_SERVER。

R_SERVER、Intel 数値演算ライブラリ (MKL) を使用します。 MKL を含んだ計算、矛盾した結果は、システムの環境変数がない場合に発生します。 

環境変数を設定`'MKL_CBWR'=AUTO`R_SERVER で条件付きの数値再現性を確保します。 詳細については、次を参照してください。[概要条件付き数値の再現性 (CNR) に](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr)します。

**回避策**

1. コントロール パネルで、次のようにクリックします**システムとセキュリティ** > **システム** > **システムの詳細設定** >   **。環境変数**します。

2. 新しいユーザーまたはシステム変数を作成します。 

  + 'MKL_CBWR' 変数の名前を設定します。
  + '変数値' を 'AUTO' を設定します。

3. R_SERVER を再起動します。 SQL Server で、SQL Server スタート パッド サービスを再起動することができます。

> [!NOTE]
> Linux 上の SQL Server の 2019 Preview を実行する場合は、編集または作成 *.bash_profile* 、ユーザーのホーム ディレクトリ内の行を追加する`export MKL_CBWR="AUTO"`します。 このファイルを入力して実行`source .bash_profile`bash コマンド プロンプトでします。 R_SERVER を入力して再起動`Sys.getenv()`R コマンド プロンプトでします。

### <a name="2-r-script-runtime-error-sql-server-2017-cu5-cu7-regression"></a>2.R スクリプトの実行時エラー (SQL Server 2017 CU5 CU7 回帰)

SQL Server 2017 の累積的更新プログラム 5 ~ 7 がの回帰、 **rlauncher.config**ファイルの一時ディレクトリのファイル パスにスペースが含まれています。 この回帰は CU8 で修正されます。

R スクリプトを実行するときに表示されます、エラーには、次のメッセージが含まれています。

> *'R' スクリプトのランタイムと通信できません。'R' ランタイムの要件を確認してください。*
>
> 外部スクリプトからの STDERR メッセージ: 
>
> *致命的なエラー: 'R_TempDir' を作成することはできません*

**回避策**

使用可能になったときに、CU8 を適用します。 または、再作成できます**rlauncher.config**を実行して**registerrext**管理者特権のコマンド プロンプトでのアンインストール/インストールします。 

```cmd
<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /uninstall /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>

<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExt.exe /install /sqlbinnpath:<SQLInstanceBinnPath> /userpoolsize:0 /instance:<SQLInstanceName>
```

次の例は、コマンドの既定のインスタンス"MSSQL14 します。インストールされている"MSSQLSERVER"C:\Program files \microsoft SQL Server\":

```cmd
"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /uninstall /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER

"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRext.exe" /install /sqlbinnpath:"C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\MSSQL\Binn" /userpoolsize:0 /instance:MSSQLSERVER
```

### <a name="3-unable-to-install-sql-server-machine-learning-features-on-a-domain-controller"></a>3.ドメイン コント ローラーに SQL Server machine learning の機能をインストールできません。

ドメイン コント ローラーに SQL Server 2016 R Services または SQL Server 2017 Machine Learning サービスをインストールしようとする場合セットアップが失敗し、これらのエラー。

> *機能のセットアップ プロセス中にエラーが発生しました*
> 
> *Id を持つグループを見つけることができません。*
> 
> *コンポーネントのエラー コード:0x80131509*

サービスはドメイン コント ローラーで、machine learning の実行に必要なローカル アカウントは 20 個を作成することはできませんので、障害が発生します。 一般に、ドメイン コント ローラー上の SQL Server のインストールはお勧めしません。 詳細については、次を参照してください。[サポート情報 2032911](https://support.microsoft.com/help/2032911/you-may-encounter-problems-when-installing-sql-server-on-a-domain-cont)します。

### <a name="4-install-the-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>4.Microsoft R Client との互換性を確保する最新のサービス リリースをインストールします。

Microsoft R Client の最新バージョンをインストールしてリモート コンピューティング コンテキストで SQL Server で R を実行して、次のようなエラーが発生した可能性があります。

> *Microsoft R Client のバージョン 9.x.x は、Microsoft R Server バージョン 8.x.x と互換性がないコンピューターで実行されます。互換性のあるバージョンをダウンロードしてインストールしてください。*

SQL Server 2016 では、クライアント上の R ライブラリは、サーバー上の R ライブラリを正確に一致が必要です。 制限はリリースの R Server 9.0.1 よりも後で削除されました。 ただし、このエラーが発生した場合は、クライアントとサーバーによって使用され、必要に応じて、サーバーのバージョンに一致するようにクライアントを更新するバージョンの R ライブラリを確認します。

SQL Server のサービス リリースがインストールされているときに、SQL Server R Services と共にインストールされる R のバージョンが更新されます。 常に最新バージョンの R コンポーネントがあることを確保するには、すべてのサービス パックをインストールすることを確認します。

Microsoft R Client 9.0.0 との互換性のために、これで説明されている更新プログラムのインストール[サポート記事](https://support.microsoft.com/kb/3210262)します。

R のパッケージに関する問題を回避するために、」の説明に従って、最新のライフ サイクル サポート ポリシーを使用するサービスの契約を変更することで、サーバーにインストールされている R ライブラリのバージョンをアップグレードすることも[、次のセクション](#bkmk_sqlbindr)します。 これを行うには、machine Learning Server (旧称 Microsoft R Server) の更新に使用される同じスケジュールでは SQL Server と共にインストールされる R のバージョンが更新されます。

**適用対象:** SQL Server 2016 R Services、バージョン 9.0.0 の R Server の以前のバージョン

### <a name="5-r-components-missing-from-cu3-setup"></a>5.CU3 セットアップから不足している R コンポーネント

SQL Server に付属する必要がある R のインストール ファイルがない場合、少数の Azure 仮想マシンがプロビジョニングされました。 この問題は、2018-01-05 から 2018-01-23 までの期間でプロビジョニングされた仮想マシンに適用されます。 適用した場合の SQL Server 2017 CU3 更新期間中に 2018-01-05 から 2018-01-23、この問題は、オンプレミスのインストールを影響も可能性があります。

サービス リリースは、R のインストール ファイルの正しいバージョンを含む指定されています。

+ [SQL Server 2017 KB4052987 の累積更新プログラム パッケージ 3](https://www.microsoft.com/download/details.aspx?id=56128)します。

コンポーネントをインストールし、SQL Server 2017 CU3 を修復するには、CU3 をアンインストールして、更新されたバージョンを再インストールする必要があります。

1. R のインストーラーが含まれています。 更新された CU3 インストール ファイルをダウンロードします。
2. CU3 をアンインストールします。 コントロール パネルで、検索**更新プログラムのアンインストール**、し、「SQL Server 2017 (KB4052987) (64 ビット) の 3015 修正プログラム」を選択します。 アンインストールの手順に進みます。
3. 更新プログラムをダウンロードした KB4052987 をダブルクリックして、CU3 更新プログラムを再インストール:`SQLServer2017-KB4052987-x64.exe`します。 インストール手順に従います。

### <a name="6-unable-to-install-python-components-in-offline-installations-of-sql-server-2017-ctp-20-or-later"></a>6.オフライン インストールの SQL Server 2017 CTP 2.0 以降で Python コンポーネントをインストールすることができません。

インターネットにアクセスしていないコンピューターで SQL Server 2017 のリリース前のバージョンをインストールする場合、インストーラーが失敗する、ダウンロードした Python コンポーネントの場所の入力を求めるページを表示します。 このようなインスタンスでは、Machine Learning サービスの機能が、Python コンポーネントをインストールできます。

この問題は、リリース バージョンで修正されます。 また、この制限は、R コンポーネントには適用されません。

**適用対象:** SQL Server 2017 の Python の使用

### <a name="bkmk_sqlbindr"></a> 使用して、クライアントから古いバージョンの SQL Server R Services に接続するときに、互換性のないバージョンの警告 [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

R コードを実行すると、SQL Server 2016 の計算コンテキスト、次のエラーが発生した可能性があります。

> *Microsoft R Server バージョン 8.0.3 と互換性のない、バージョン 9.0.0 の Microsoft R Client をコンピューター上で実行しています。互換性のあるバージョンをダウンロードしてインストールしてください。*

次の 2 つのステートメントのいずれかが true の場合、このメッセージが表示されます。

+ クライアント コンピューターのセットアップ ウィザードを使用して R Server (スタンドアロン) をインストールした[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]します。
+ 使用して Microsoft R Server がインストールされている、 [Windows インストーラーを区切る](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)します。

サーバーとクライアントが使用する必要があります、同じバージョンを使用することを確認する_バインド_、SQL Server 2016 のインスタンスで R コンポーネントをアップグレードするには、Microsoft R Server 9.0 とそれ以降のリリースではサポートされています。 あるかどうかを R のサービスのバージョンを参照してください、アップグレードを使用できます[SqlBindR.exe を使用して R Services のインスタンスをアップグレード](install/upgrade-r-and-python.md)します。

**適用対象:** SQL Server 2016 R Services、バージョン 9.0.0 の R Server の以前のバージョン

### <a name="7-setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>7.SQL Server 2016 サービス リリースをセットアップすると、新しいバージョンの R コンポーネントのインストールに失敗する場合がある

累積的な更新プログラムをインストールまたはインターネットに接続されていないコンピューターに SQL Server 2016 用 service pack をインストールするときに、セットアップ ウィザードが失敗することができるようにダウンロードした CAB ファイルを使用して R コンポーネントを更新するプロンプトを表示します。 このエラーは、通常、複数のコンポーネントは、データベース エンジンと共にインストールされたときに発生します。

この問題を回避するには、コマンドラインを使用し、サービス リリースをインストールすることができます、 `MRCACHEDIRECTORY` CU1 の更新プログラムをインストールするこの例で示すように、引数。

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

最新のインストーラーを取得するを参照してください。[インターネットへのアクセスなしで machine learning コンポーネントをインストール](install/sql-ml-component-install-without-internet-access.md)します。

**適用対象:** SQL Server 2016 R Services、バージョン 9.0.0 の R Server の以前のバージョン

### <a name="8-launchpad-services-fails-to-start-if-the-version-is-different-from-the-r-version"></a>8.スタート パッド サービスのバージョンが R バージョンと異なる場合の起動に失敗します。

データベース エンジンから SQL Server R Services を個別にインストールする、ビルド バージョンが異なる場合は、システム イベント ログに次のエラーを参照してください可能性があります。

> *SQL Server スタート パッド サービスは、次のエラーのため開始できませんでした。サービスは、適切なタイミングで開始または制御要求に応答しませんでした。*

たとえば、このエラー可能性がありますリリース バージョンを使用して、データベース エンジンをインストールする場合に発生する、データベース エンジンをアップグレードする修正プログラムを適用、リリース バージョンを使用して R Services の機能を追加します。

この問題を回避するのにには、バージョンの sqldk.dll などの SQL バイナリ Launchpad.exe のバージョンを比較するのにファイル マネージャーなどのユーティリティを使用します。 すべてのコンポーネントは、同じバージョン番号が必要です。 1 つのコンポーネントをアップグレードする場合は、インストールされている他のすべてのコンポーネントに必ず同じアップグレードを適用してください。

スタート パッドを探して、`Binn`インスタンスのフォルダー。 たとえば、SQL Server 2016 の既定のインストール パスは`C:\Program Files\Microsoft SQL Server\MSSQL.13.InstanceNameMSSQL\Binn`します。 

### <a name="9-remote-compute-contexts-are-blocked-by-a-firewall-in-sql-server-instances-that-are-running-on-azure-virtual-machines"></a>9.リモート計算コンテキストは、Azure の仮想マシンで実行されている SQL Server インスタンスに、ファイアウォールによってブロックされています。

インストールした場合[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Windows Azure バーチャル マシンでは、する可能性を仮想マシンのワークスペースの使用を必要とする計算コンテキストを使用します。 既定では、Azure virtual machines 上のファイアウォール ルールが含まれる、ネットワークのローカルの R ユーザー アカウントのアクセスをブロックです。

Azure VM での回避策として開く**セキュリティが強化された Windows ファイアウォール**を選択します**送信の規則**、または次のルールを無効にします。**SQL Server インスタンス MSSQLSERVER の R ローカル ユーザー アカウントのネットワーク アクセスをブロック**します。 有効な場合、ルールのままにできますが、セキュリティ プロパティを変更**許可する場合は、セキュリティで保護された**します。

### <a name="10-implied-authentication-in-sqlexpress"></a>10.SQLEXPRESS での暗黙の認証

SQL Server を使用して統合 Windows 認証を使用してリモート データ サイエンス ワークステーションから R ジョブを実行すると*暗黙の認証*スクリプトによって必要なローカル ODBC 呼び出しを生成します。 ただし、この機能は、SQL Server Express Edition の RTM ビルドでは使用できません。

この問題を解決するために、新しいサービス リリースにアップグレードすることをお勧めします。

この問題を回避するには、アップグレードを実行できない場合は、埋め込みの ODBC 呼び出しが必要となるリモート R ジョブを実行する SQL ログインを使用します。

**適用対象:** SQL Server 2016 R Services の Express Edition

### <a name="11-performance-limits-when-libraries-used-by-sql-server-are-called-from-other-tools"></a>11.SQL Server で使用されるライブラリが他のツールから呼び出されたときのパフォーマンスの制限します。

Machine learning、RGui などの外部アプリケーションから SQL Server のインストールされているライブラリを呼び出すことになります。 これにより、新しいパッケージのインストールや、非常に短いコード サンプルでのアドホック テストの実行などの特定のタスクを実行する最も簡単な方法があります。 ただし、SQL Server 以外のパフォーマンスを制限する可能性があります。 

たとえば、SQL Server の Enterprise Edition を使用している場合でも R モードで実行シングル スレッド外部ツールを使用して、R コードを実行するとします。 SQL Server のパフォーマンスの利点を取得する SQL Server の接続を開始しを使用して、 [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を外部スクリプトのランタイムを呼び出します。

一般に、machine learning の外部ツールから SQL Server で使用されるライブラリを呼び出すことを避けます。 デバッグ R または Python コードする必要がある場合は、SQL Server の外部で行う通常は簡単です。 SQL Server 内にある同じライブラリを取得するには、Microsoft R Client をインストールすることができます[SQL Server 2017 の Machine Learning Server (スタンドアロン)](install/sql-machine-learning-standalone-windows-install.md)、または[SQL Server 2016 R Server (スタンドアロン)](install/sql-r-standalone-windows-install.md)します。

### <a name="12-sql-server-data-tools-does-not-support-permissions-required-by-external-scripts"></a>12.SQL Server Data Tools が外部のスクリプトで必要なアクセス許可をサポートしていません

任意のプリンシパルは、外部スクリプトの実行に固有のアクセス許可を持っている場合、データベース プロジェクトを発行する Visual Studio または SQL Server Data Tools を使用すると、次のようなエラーが発生する可能性があります。

> *TSQL モデル:エラー時に、リバース エンジニア リングのデータベースが見つかりました。アクセス許可は認識されず、インポートされませんでした。*

現在、DACPAC モデルは、R Services または許可 ANY 外部スクリプト、または EXECUTE ANY EXTERNAL SCRIPT などの Machine Learning サービスで使用されるアクセス許可をサポートしていません。 この問題は今後のリリースで修正される予定です。

この問題を回避するには、追加の許可でステートメントを実行、配置後スクリプト。

### <a name="13-external-script-execution-is-throttled-due-to-resource-governance-default-values"></a>13.リソース ガバナンスの既定値により外部スクリプトの実行が調整されました

Enterprise Edition では、外部スクリプト プロセスを管理するためにリソース プールを使用できます。 いくつかの初期のリリース ビルドでは、R プロセスに割り当てられる最大メモリは 20% でした。 そのため、サーバーに 32 GB の RAM がある場合、R の実行可能ファイル (RTerm.exe および BxlServer.exe) は、最大 1 つの要求で 6.4 GB を使用できます。

リソースの制限事項が発生した場合は、現在の既定値を確認します。 20% が十分でない場合は、ドキュメントを参照して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]でこの値を変更する方法。

**適用対象:** SQL Server 2016 R Services の Enterprise Edition

## <a name="r-script-execution-issues"></a>R スクリプトの実行に関する問題

このセクションには、R ライブラリおよびツールが RevoScaleR を含め、Microsoft によって発行に関連するいくつかの問題と同様に、SQL Server で R を実行している固有の既知の問題が含まれています。

既知の問題に影響を与える R ソリューションを参照してください、 [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)サイト。

### <a name="1-access-denied-warning-when-executing-r-scripts-on-sql-server-in-a-non-default-location"></a>1.アクセスは、既定以外の位置での SQL Server で R スクリプトを実行するときに警告を拒否されました

SQL Server のインスタンスがインストールされている場合、既定以外の場所になどの外部、`Program Files`フォルダー、ACCESS_DENIED は、パッケージをインストールするスクリプトを実行しようとするときに発生する警告。 例 :

> *`normalizePath(path.expand(path), winslash, mustWork)` : パス [2] ="~ExternalLibraries/R/8/1"。アクセスが拒否されました*

R 関数は、パスの読み取りを試みますれ、場合に失敗したため、組み込みのユーザー グループ**SQLRUserGroup**、読み取りアクセス権はありません。 発生する警告が現在の R スクリプトの実行をブロックしませんが、ユーザーが他の任意の R スクリプトを実行するたびに、警告が繰り返し繰り返す可能性があります。

SQL Server を既定の場所をインストールした場合は、このエラーは発生しませんのすべての Windows ユーザーが読み取りアクセス許可があるため、`Program Files`フォルダー。

この問題 ia は、今後のサービス リリースで対処します。 この問題を回避するには、提供、グループ、 **SQLRUserGroup**のすべての親フォルダーに対して読み取りアクセス権を持つ`ExternalLibraries`します。

### <a name="2-serialization-error-between-old-and-new-versions-of-revoscaler"></a>2.RevoScaleR の新旧のバージョン間でシリアル化エラー

リモート SQL Server インスタンスにシリアル化された形式を使用してモデルを渡すときにエラーが発生する可能性があります。 

> *MemDecompress でエラー (データ、種類 = 圧縮解除) memDecompress(2) で内部エラー-3 です。*

シリアル化の関数の最新バージョンを使用して、モデルを保存した場合、このエラーが発生します[rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)モデルの逆シリアル化する SQL Server インスタンスが、古いバージョンの SQL から、RevoScaleR Api は、Server 2017 CU2 以前のバージョン。

この問題を回避するには、CU3 以降の SQL Server 2017 インスタンスをアップグレードすることができます。

エラーは、API バージョンが同じ場合、または保存シリアル化 API の新しいバージョンを使用するサーバーに古いシリアル化関数を使用したモデルを移動する場合に表示されません。

つまり、シリアル化および逆シリアル化の両方の操作のため、同じバージョンの RevoScaleR を使用します。

### <a name="3-real-time-scoring-does-not-correctly-handle-the-learningrate-parameter-in-tree-and-forest-models"></a>3.リアルタイム スコアリングが正しく処理しない、 _learningRate_ツリーとフォレストのモデル内のパラメーター

使用する場合は、矛盾した結果を表示可能性がありますのデシジョン ツリー、デシジョン フォレスト メソッドを使用して、モデルを作成し、学習率を指定すると、`sp_rxpredict`または SQL`PREDICT`関数を使用すると比較して`rxPredict`します。

原因は、API でエラーをシリアル化のプロセス モデルでありに制限されていますが、`learningRate`パラメーター: たとえば、 [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)、または

この問題は、今後のサービス リリースで対処されます。

### <a name="4-limitations-on-processor-affinity-for-r-jobs"></a>4.R ジョブのプロセッサ アフィニティに関する制限事項

SQL Server 2016 の初期リリース ビルドの場合は、最初の k グループ内の Cpu のみプロセッサ関係を設定できます。 たとえば、サーバーが 2 つの k グループ 2 ソケット マシンの場合は、最初の k グループからのプロセッサのみが R プロセスの使用されます。 R スクリプトのジョブのリソース管理を構成するときに、同じ制限が適用されます。

この問題は SQL Server 2016 Service Pack 1 で修正されました。 最新のサービス リリースにアップグレードすることをお勧めします。

**適用対象:** SQL Server 2016 R Services RTM バージョン

### <a name="5-changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>5.SQL Server コンピューティング コンテキストでのデータの読み取り時に列の型を変更できない

コンピューティング コンテキストが SQL Server インスタンスに設定されている場合は、 _colClasses_ 引数 (または他の同様の引数) を使用して、R コードで列のデータ型を変更できません。

たとえば、CRSDepTimeStr 列がまだ整数でない場合、次のステートメントでエラーが発生します。

```R
data <- RxSqlServerData(
  sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall", 
  connectionString = connectionString, 
  colClasses = c(CRSDepTimeStr = "integer"))
```

この問題を回避するには、キャストを使用する SQL クエリを書き直すことができます変換や、正しいデータ型を使用してデータを R に提供します。 一般に、パフォーマンスは、使用する場合のデータ、R コードでデータを変更するではなく、SQL を使用しています。

**適用対象:** SQL Server 2016 R Services

### <a name="6-limits-on-size-of-serialized-models"></a>6.シリアル化されたモデルのサイズの制限

モデルを SQL Server テーブルに保存するときに、モデルをシリアル化し、バイナリ形式で保存する必要があります。 理論的にはこの方法で格納できるモデルの最大サイズは 2 GB で、SQL Server の varbinary 列の最大サイズです。

大規模なモデルを使用する必要がある場合は、次の回避策を使用できます。

+ モデルのサイズを縮小する手順を実行します。 一部のオープン ソース R パッケージは、モデル オブジェクトに大量の情報を含めるし、この情報の多くの展開は削除できます。 
+ 機能の選択を使用すると、不要な列を削除します。
+ オープン ソースのアルゴリズムを使用している場合は、MicrosoftML または RevoScaleR で対応するアルゴリズムを使用して同様の実装を検討してください。 これらのパッケージは、展開シナリオ用に最適化されています。
+ 場合、モデルが合理化されているし、前の手順を使用してサイズを縮小を参照してください、 [memCompress](https://www.rdocumentation.org/packages/base/versions/3.4.1/topics/memCompress) SQL Server に渡す前に、モデルのサイズを小さく基本の r 関数を使用できます。 モデルが 2 GB の制限に近づいている場合は、このオプションをお勧めします。
+ 大規模なモデルは、SQL Server を使用できます[FileTable](../relational-databases/blob/filetables-sql-server.md) varbinary 列を使用するのではなく、モデルに保存する機能します。

    Filetable を使用するには、Filetable に格納されたデータは、SQL Server での Filestream のファイル システム ドライバーによって管理され、既定のファイアウォール規則は、ネットワーク ファイルへのアクセスをブロックするため、ファイアウォールの例外を追加する必要があります。 詳細については、次を参照してください。 [FileTable の前提条件を有効にする](../relational-databases/blob/enable-the-prerequisites-for-filetable.md)します。

    FileTable を有効にした後、モデルを記述する FileTable の API を使用して SQL からのパスを取得し、コードからその場所に、モデルを作成します。 モデルを読み取る必要がある場合は、SQL からパスを取得して、スクリプトからのパスを使用して、モデルを呼び出します。 詳細については、次を参照してください。[ファイル入出力 Api を使用した Filetable へのアクセス](../relational-databases/blob/access-filetables-with-file-input-output-apis.md)します。

### <a name="7-avoid-clearing-workspaces-when-you-execute-r-code-in-a-includessnoversionincludesssnoversion-mdmd-compute-context"></a>7.R コードを実行するときにワークスペースをオフにしないで、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]計算コンテキスト

R コードの実行中にオブジェクトのワークスペースをクリアする R コマンドを使用する場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]コンピューティング コンテキストでは、R スクリプトの一部としてワークスペースをクリアするかどうか、またはを使用して呼び出す[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)、このエラーが発生する可能性があります:*ワークスペース オブジェクト revoScriptConnection が見つかりませんでした*

`revoScriptConnection` は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]から呼び出される R セッションに関する情報を含む R ワークスペース内のオブジェクトです。 ただし、R コードにワークスペースをクリアするためのコマンド ( `rm(list=ls()))`など) が含まれている場合は、R ワークスペース内のセッションおよび他のオブジェクトに関するすべての情報もクリアされます。

この問題を回避するには、変数とその他のオブジェクトを無差別にクリアが回避にで R を実行しているときに[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]します。 オフにすると、ワークスペースは、R コンソールで作業する場合が一般的な意図しない結果。

* 特定の変数を削除するには、R を使用して`remove`関数: たとえば、 `remove('name1', 'name2', ...)`
* 削除する変数が複数ある場合は、リストに一時変数の名前を保存し、ガベージ コレクションを定期的に実行します。

### <a name="8-restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>8.R スクリプトの入力として提供できるデータに対する制限事項

次の種類のクエリ結果は、R スクリプトでは使用できません。

- AlwaysEncrypted 列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
- マスクされた列を参照する [!INCLUDE[tsql](../includes/tsql-md.md)] クエリのデータ。
  
     R スクリプトでマスクされたデータを使用する必要がある場合、考えられる次善策として、一時テーブルにデータのコピーを作成し、代わりにそのデータを使用します。

### <a name="9-use-of-strings-as-factors-can-lead-to-performance-degradation"></a>9.パフォーマンスが低下する可能性がありますの要因として、文字列の使用します。

文字列型の変数を使用するには、R 操作用に使用されるメモリ量を大幅に増加させる要因と。 R に関する既知の問題を一般に、これは、この主題に関する多くの記事がある. たとえばを参照してください[要因が R ブロガーで、John マウントして、R で第一級市民)](https://www.r-bloggers.com/factors-are-not-first-class-citizens-in-r/)または[stringsAsFactors:承認されていない自己紹介、Roger Peng によって](https://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/)します。 

この問題は SQL Server に固有ではありませんが、SQl Server で実行する R コードのパフォーマンスが大幅に影響ことができます。 文字列は、通常 varchar または nvarchar、として格納し、文字列データの列に多数の一意の値がある場合は、整数および文字列を R でへこれらを内部的に変換するプロセスのことができますもエラーが発生するメモリ割り当て。

絶対に必要としない文字列データ型の他の操作では、文字列値を数値 (整数) にマップする場合、データは、データ準備の一部が、パフォーマンスとスケールの観点からメリットとしてを入力します。

この問題とその他のヒントの詳細については、次を参照してください。[パフォーマンス R Services - データの最適化を](r/r-and-data-optimization-r-services.md)します。

### <a name="10-arguments-varstokeep-and-varstodrop-are-not-supported-for-sql-server-data-sources"></a>10.引数*varsToKeep*と*varsToDrop* SQL Server データ ソースはサポートされていません

使用して結果をテーブルに書き込む rxDataStep 関数を使用すると、 *varsToKeep*と*varsToDrop*または操作の一部として除外する列を指定する方法として便利です。 ただし、これらの引数は、SQL Server データ ソースはサポートされません。

### <a name="11-limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>11.Sp での SQL データ型のサポートが制限される\_実行\_外部\_スクリプト

SQL でサポートされているすべてのデータ型は R で使用できます。この問題を回避するには、sp にデータを渡す前に、サポートされているデータ型にサポートされていないデータ型をキャストを検討してください\_実行\_外部\_スクリプト。

詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)します。

### <a name="12-possible-string-corruption-using-unicode-strings-in-varchar-columns"></a>12.Varchar 列の unicode 文字列を使用可能な文字列の破損

Varchar 型の列で unicode データを渡す[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]R および Python には、文字列が破損で結果ことができます。 これは、これらの unicode 文字列のエンコーディングがあるため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] R および Python で使用される既定 utf-8 のエンコーディングでは照合順序が一致しません。 

ASCII 以外の文字列データを送信[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]R および Python に utf-8 エンコードを使用して、(で利用可能な[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]) または同じの nvarchar 型を使用します。

### <a name="13-only-one-value-of-type-raw-can-be-returned-from-spexecuteexternalscript"></a>13.型の値を 1 つだけ`raw`から返されることができます `sp_execute_external_script`

ときに、binary データ型 (R**生**データ型)、R から返される、出力データ フレームに値を送信する必要があります。

データ型以外の**生**、OUTPUT キーワードを追加することで、ストアド プロシージャの結果と共にパラメーター値を返すことができます。 詳細については、次を参照してください。[パラメーター](https://docs.microsoft.com/sql/relational-databases/stored-procedures/parameters)します。

型の値を含む複数の出力セットを使用する場合**生**1 つの考えられる回避策は、ストアド プロシージャの複数の呼び出しを行うか、結果を送信するセット[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ODBC を使用しています。

### <a name="14-loss-of-precision"></a>14.精度の損失

[!INCLUDE[tsql](../includes/tsql-md.md)]と R をサポートしてさまざまなデータ型、数値データ型の変換中に有効桁数の損失が低下することができます。

暗黙的なデータ型変換の詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)します。

### <a name="15-variable-scoping-error-when-you-use-the-transformfunc-parameter"></a>15.変数のスコープ transformFunc パラメーターを使用するときにエラーが発生

データの変換をモデル化するときに渡すことができます、 *transformFunc*などの関数の引数`rxLinmod`または`rxLogit`します。 ただし、入れ子になった関数呼び出しでは、ローカル計算コンテキストで呼び出しが正常に動作する場合でも、SQL Server 計算コンテキストではスコープ エラーにつながります。

> *分析のサンプル データ セットに変数がありません。*

たとえば、2 つの関数が定義されている`f`と`g`、ローカル グローバル環境でと`g`呼び出し`f`します。 分散またはリモート呼び出しを伴う`g`への呼び出し`g`ため、このエラーで失敗する可能性があります`f`が見つからない場合でも、両方を渡した`f`と`g`リモート呼び出し。

この問題が発生した場合は、 `f` の定義内の、通常 `g`が `g` を呼び出す場所より前の任意の場所に、 `f`の定義を組み込むことで問題を回避できます。

例 :

```R
f <- function(x) { 2*x * 3 }
g <- function(y) {
              a <- 10 * y
               f(a)
}
```

エラーを回避するには、次のように定義を書き換えます。

```R
g <- function(y){
              f <- function(x) { 2*x +3}
              a <- 10 * y
              f(a)
}
```

### <a name="16-data-import-and-manipulation-using-revoscaler"></a>16.RevoScaleR を使用したデータのインポートと操作

ときに**varchar**列が、データベースから読み取るは空白は切り捨てられます。 これを防ぐには、空白以外の文字で文字列を囲みます。

ときになどの関数`rxDataStep`を持つデータベース テーブルの作成に使用**varchar**列、列の幅とデータのサンプルに基づいて推定されます。 幅が増減する場合は、一般的な長さにすべての文字列を埋め込むために必要な場合があります。

`rxImport` または `rxTextToXdf` の繰り返しの呼び出しを使用して行のインポートと追加を実行し、複数の入力ファイルを 1 つの .xdf ファイルに結合する場合、変換を使用した変数のデータ型の変更はサポートされていません。

### <a name="17-limited-support-for-rxexec"></a>17.RxExec の制限付きサポート

SQL Server 2016 で、`rxExec`シングル スレッド モードでのみであるパッケージを使用できる、RevoScaleR で提供される関数です。

### <a name="18-increase-the-maximum-parameter-size-to-support-rxgetvarinfo"></a>18.RxGetVarInfo をサポートするためにパラメーターの最大サイズを増やす

(たとえば、40,000) 経由で変数の数が非常に多いデータ セットを使用する場合は、設定、`max-ppsize`フラグなどの関数を使用する R を起動すると`rxGetVarInfo`します。 `max-ppsize` フラグは、ポインター保護スタックの最大サイズを指定します。

値を設定することができます (RGui.exe や RTerm.exe など) は、R コンソールを使用している場合_で max-ppsize_ 」と入力して 500000 に。

```R
R --max-ppsize=500000
```

### <a name="19-issues-with-the-rxdtree-function"></a>19.RxDTree 関数に関する問題

`rxDTree` 関数では、式内変換は現在サポートされていません。 特に、係数を即座に作成するための `F()` 構文の使用はサポートされていません。 ただし、数値データは自動的にビン分割します。

順序付けされた係数は、 `rxDTree`を除くすべての RevoScaleR 分析関数の係数と同様に処理されます。

### <a name="20-datatable-as-an-outputdataset-in-r"></a>20.R で、OutputDataSet として Data.table

使用して`data.table`として、 `OutputDataSet` R では SQL Server 2017 Cumulative Update 13 (CU13) 以前のバージョンでサポートされません。 次のメッセージが表示される可能性があります。

```
Msg 39004, Level 16, State 20, Line 2
A 'R' script error occurred during execution of 
'sp_execute_external_script' with HRESULT 0x80004004.
Msg 39019, Level 16, State 2, Line 2
An external script error occurred: 
Error in alloc.col(newx) : 
  Internal error: length of names (0) is not length of dt (11)
Calls: data.frame ... as.data.frame -> as.data.frame.data.table -> copy -> alloc.col

Error in execution.  Check the output for more information.
Error in eval(expr, envir, enclos) : 
  Error in execution.  Check the output for more information.
Calls: source -> withVisible -> eval -> eval -> .Call
Execution halted
```

`data.table` として、 `OutputDataSet` R では、SQL Server 2017 Cumulative Update 14 (CU14) 以降がサポートされます。

## <a name="python-script-execution-issues"></a>Python スクリプトの実行に関する問題

このセクションには、SQL Server、および、マイクロソフトによって発行された Python パッケージに関連する問題に Python を実行している固有の既知の問題が含まれていますなど[revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)と[microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

### <a name="1-call-to-pretrained-model-fails-if-path-to-model-is-too-long"></a>1.モデルへのパスが長すぎる場合、事前トレーニング済みモデルへの呼び出しが失敗します。

SQL Server 2017 の初期のリリースで事前トレーニング済みモデルをインストールしたトレーニング済みのモデル ファイルへの完全パスを読み取る Python の長すぎる場合があります。 この制限は、今後のサービス リリースで修正されます。

これにはいくつかの潜在的な回避策があります。 

+ 事前トレーニング済みモデルをインストールする場合は、カスタムの場所を選択します。
+ 可能であれば、C:\SQL\MSSQL14 などの短いパスのカスタム インストール パスの下の SQL Server インスタンスをインストールします。MSSQLSERVER です。
+ Windows ユーティリティを使用して[Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx)モデル ファイルを短いパスにマップするハード リンクを作成します。
+ 最新のサービス リリースに更新します。

### <a name="2-error-when-saving-serialized-model-to-sql-server"></a>2.保存するときにエラーが SQL Server へのモデルをシリアル化

リモートの SQL Server インスタンスにモデルを渡すバイナリ モデルを使用して読み取るしようとしたときに、`rx_unserialize`関数[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)エラーが発生する可能性があります。 

> *Nameerror でした。 名前 'rx_unserialize_model' が定義されていません*

シリアル化の関数の最新バージョンを使用して、モデルを保存するが、モデルの逆シリアル化する SQL Server インスタンスがシリアル化 API を認識しない場合は、このエラーが発生します。

この問題を解決するには、CU3 以降の SQL Server 2017 インスタンスをアップグレードします。

### <a name="3-failure-to-initialize-a-varbinary-variable-causes-an-error-in-bxlserver"></a>3.BxlServer に varbinary 変数の初期化に失敗、エラーが発生します。

使用して SQL Server での Python コードを実行する場合`sp_execute_external_script`、varbinary (max) 型、varchar (max)、または類似した種類の変数に出力が、コードと、変数を初期化またはスクリプトの一部として設定する必要があります。 それ以外の場合、エラーと動作が停止した、データの exchange コンポーネント BxlServer を発生させます。

この制限は今後のサービス リリースで修正されます。 この問題を回避するには、Python スクリプト内で変数を初期化することを確認します。 次の例のように、有効な値を使用できます。

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

### <a name="4-telemetry-warning-on-successful-execution-of-python-code"></a>4.Python コードの実行が正常に製品利用統計情報の警告

SQL Server 2017 CU2 以降では、次のメッセージが表示される場合でも、それ以外の場合の Python コードが正常に実行します。

> *外部スクリプトからの STDERR メッセージ:* 
>  *~PYTHON_SERVICES\lib\site-packages\revoscalepy\utils\RxTelemetryLogger*
> *SyntaxWarning: telemetry_state はグローバル宣言の前に使用*

この問題は SQL Server 2017 Cumulative Update 3 (CU3) で修正されました。 

### <a name="5-numeric-decimal-and-money-data-types-not-supported"></a>5。数値、10 進数、およびコストのデータ型がサポートされていません

以降では、SQL Server 2017 Cumulative Update 12 (CU12) は、WITH RESULT SETS 内の数値、10 進数、およびコストのデータ型はサポートされていませんで Python を使用する場合`sp_execute_external_script`します。 次のメッセージが表示されます。

> *[コード。39004、SQL の状態:S1000] hresult 0x80004004 'sp_execute_external_script' の実行中に、'Python' スクリプト エラーが発生しました。*

> *[コード。39019、SQL の状態:S1000] 外部スクリプト エラーが発生しました。*
> 
> *SqlSatelliteCall エラー:出力スキーマでサポートされていない型です。サポートされている種類: bit、smallint、int 型、datetime、smallmoney、real、float です。char、varchar は部分的にサポートされています。*

これは、SQL Server 2017 Cumulative Update 14 (CU14) で修正されています。

## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise と Microsoft R Open

このセクションでは、R の接続、開発、および Revolution Analytics によって提供されるパフォーマンス ツールに固有の問題が一覧表示します。 これらのツールは、以前のプレリリース バージョンので提供されていた[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]します。

一般に、これらの以前のバージョンをアンインストールして、最新のバージョンの SQL Server または Microsoft R Server をインストールすることお勧めします。

### <a name="1-revolution-r-enterprise-is-not-supported"></a>1.Revolution R Enterprise がサポートされていません

バージョンの Revolution R Enterprise サイド バイ サイドのインストール[!INCLUDE[rsql_productname_md](../includes/rsql-productname-md.md)]はサポートされていません。

Revolution R Enterprise の既存のライセンスがあれば、両方から別のコンピューターに配置する必要があります、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンスとへの接続に使用する任意のワークステーション、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]インスタンス。

いくつかのプレリリース版の[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]Revolution Analytics によって作成された Windows に含まれている R 開発環境。 このツールは提供されなくなるはサポートされていません。

互換性のため[!INCLUDE[rsql_productname](../includes/rsql-productname-md.md)]Microsoft R Client をインストールすることをお勧めします。 [R Tools for Visual Studio](https://www.visualstudio.com/vs/rtvs/)と[Visual Studio Code](https://code.visualstudio.com/)も Microsoft R ソリューションをサポートします。

### <a name="2-compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>2.SQLite ODBC ドライバーと RevoScaleR に関する互換性の問題

SQLite ODBC ドライバーのリビジョン 0.92 は、RevoScaleR と互換性がありません。 リビジョン 0.88 ~ 0.91 と 0.93 以降は互換性が確認とします。

## <a name="see-also"></a>関連項目

[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)

[SQL Server での machine learning のトラブルシューティング](machine-learning-troubleshooting-faq.md)
