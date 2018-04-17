---
title: 更新 - SQL Server ドキュメントの Advanced Analytics |Microsoft ドキュメント
description: 更新されたコンテンツで最近変更したドキュメントについては、Microsoft SQL Server の高度な分析のためのスニペットを表示します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 058278df1ee54a6440f8225ea15f727857df76f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>新規または最近更新された: SQL Server の Advanced Analytics
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *"更新日の範囲:"* &nbsp; **2017 年 12 月 3 日**&nbsp;から&nbsp;**2018 年 2 月 3 日**
- *サブジェクト領域:* &nbsp; **for SQL Server の Advanced Analytics**です。

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [SQL Server に新しい Python パッケージをインストールする](python/install-additional-python-packages-on-sql-server.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新されたアーティクルの抜粋が

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここに表示される抜粋は、適切なセマンティック コンテキストから区切りが表示されます。 また、区切ることもあります抜粋が実際の資料の周囲にある重要なマークダウン構文からです。 したがってこれらの抜粋は、一般的なガイダンスのみです。 のみの抜粋を使用するをクリックし、実際の資料を参照してくださいに時間がかかって各自の興味を保証するかどうかを把握できます。

これらおよびその他の理由は、これらの抜粋からコードをコピーしない場合と受け取らない正確な情報源として任意のテキストの抜粋です。 代わりに、実際の資料を参照してください。





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>最近更新されたアーティクルの圧縮のリスト

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。

1. [Machine Learning のサービスの既知の問題](#TitleNum_1)
2. [データベース内の実行の R コードの変換](#TitleNum_2)
3. [SQL Server にインストールされている R パッケージを確認します。](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1.&nbsp; [Machine Learning のサービスの既知の問題](known-issues-for-sql-server-machine-learning-services.md)

*最終更新日: 2018-02-02* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 163.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c6f46adcf795c43f818120b88407a3a89304cb27 c781562605f5cd77f6c43bfe5e89810cb72ceae0  (PR=4789  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=386bfb688843bac7fa4d83dc1cfef94dd19db110) -->



追加既知の問題を R ソリューションを与える可能性がありますを参照してください、 [Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/resources-known-issues)サイトです。

**アクセスは、既定以外の場所に SQL Server で R スクリプトを実行するときに警告を拒否されました**


SQL Server のインスタンスがインストールされている場合、既定以外の場所になどの外部、`Program Files`フォルダー、ACCESS_DENIED は、パッケージをインストールするスクリプトを実行しようとしたときに発生する警告です。 以下に例を示します。

> *NormalizePath(path.expand(path)、winslash、mustWork) パス [2] ="~ExternalLibraries/R/8/1": アクセスが拒否されました。*

その理由は R 関数は、パスを読み取ろうとすると、失敗した場合、組み込みのユーザー グループ**SQLRUserGroup**は読み取りアクセスがありません。 生成される警告は、現在の R スクリプトの実行をブロックしませんが、ユーザーがその他の R スクリプトを実行するたびに、警告が繰り返し再発可能性があります。

で既定の場所に SQL Server をインストールする場合は、このエラーは発生しません、すべての Windows ユーザーのアクセス許可を読み取りがであるため、`Program Files`フォルダーです。

この問題は、次のサービス リリースで解決されます。 この問題を回避するには、提供、グループ**SQLRUserGroup**のすべての親フォルダーに対して読み取りアクセス権を持つ`ExternalLibraries`します。

**RevoScaleR の新旧のバージョン間でシリアル化エラー**


リモート SQL Server インスタンスをシリアル化された形式を使用して、モデルを渡す際にエラーが発生する可能性があります。

> *MemDecompress でエラー (データ、種類 = 圧縮解除) memDecompress(2) で内部エラー-3 です。*

シリアル化の関数の最新バージョンを使用して、モデルを保存した場合、このエラーは発生[rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)モデルの逆シリアル化する、SQL Server インスタンスが、古いバージョンの SQL からの RevoScaleR ApiServer 2017 CU2 以前のバージョン。



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-converting-r-code-for-execution-in-databaserconverting-r-code-for-use-in-sql-servermd"></a>2.&nbsp; [データベース内の実行の R コードの変換](r/converting-r-code-for-use-in-sql-server.md)

*最終更新日: 2018-01-08* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 136.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a1d156fac1af5813ef75965071686b177e2aede7 fc8beff0aa0d7ea298e493b90984875e81e9143e  (PR=4493  ,  Filename=converting-r-code-for-use-in-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=f486d12078a45c87b0fcf52270b904ca7b0c7fc8) -->



**ストアド プロシージャで R コードをパッケージ化します。**

+ コードが比較的単純な場合に埋め込んだりできます、改変の有無 T-SQL は、ユーザー定義関数でこれらのサンプル」の説明に従って。

    + [RxExec で実行されている R 関数を作成します。](r/../tutorials/deepdive-create-a-simple-simulation.md)
    + [T-SQL と R を使用して特徴エンジニア リング](r/../tutorials/sqldev-create-data-features-using-t-sql.md)

+ コードがより複雑な場合は、R パッケージを使用して**sqlrutils**コードに変換します。 経験豊富な R ユーザーの適切なストアド プロシージャのコードの記述には、このパッケージは設計されています。

    最初の手順では、明確に定義された入力と出力と 1 つの関数として、R コードを書き直してください。

    次に、使用、 **sqlrutils**正しい形式で入力と出力を生成するパッケージ。 **Sqlrutils**パッケージは、ストアド プロシージャの完全なコードを生成し、データベースでストアド プロシージャを登録することもできます。

    詳細と例については、次を参照してください。 [SqlRUtils](r/../r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)です。

**他のワークフローとの統合します。**

+ ETL プロセスの T-SQL でツールを活用できます。 特徴エンジニア リング、特徴を抽出、およびデータのワークフローの一部としてデータ クレンジングを事前に実行します。

    Visual Studio または RStudio の R ツールなど、専用の R 開発環境で作業するときする可能性がありますをコンピューターにデータをプル、繰り返し、データの分析を書き込むしたり結果を表示します。

    ただし、スタンドアロン R コードを SQL Server に移行すると、このプロセスの多くする簡略化したり、他の SQL Server のツールに委任できます。

+ セキュリティで保護された、非同期の視覚エフェクトの戦略を使用します。

    多くの場合、SQL Server のユーザーは、サーバー上のファイルにアクセスできないし、SQL クライアント ツールは通常、R のグラフィックス デバイスをサポートしています。 ソリューションの一部としてプロットやその他のグラフィックスを生成する場合は、バイナリ データとして、プロットをエクスポートして、テーブルへの保存または書き込みを検討してください。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3.&nbsp; [SQL Server にインストールされている R パッケージを確認します。](r/determine-which-packages-are-installed-on-sql-server.md)

*最終更新日: 2018-01-24* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2))

<!-- Source markdown line 78.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 9a065066398843a4bed318fa46d4982d712915a9 7a1df11f57e7bbf0abc37d3aa240dedd2b88c45f  (PR=4715  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=9e6a029456f4a8daddb396bc45d7874a43a47b45) -->




**ライブラリの場所とバージョンを取得します。**


次の例では、RevoScaleR のローカル コンピューティング コンテキストでパッケージのバージョンのライブラリの場所を取得します。

```
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

**SQL Server で使用されるライブラリのパスを確認します。**


機械学習のバインディングを使用してコンポーネントをアップグレードした場合、R ライブラリへのパスを変更する可能性があります。 この場合、R ツールを以前のショートカットは、以前のバージョンを参照場合があります。 確認するため、パスとパッケージのバージョンの SQL Server で使用される、次などのコマンドを実行できます。

```
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**結果**

```
STDOUT message(s) from external script:
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```







## <a name="similar-articles-about-new-or-updated-articles"></a>新規記事または更新記事に関する類似記事

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ある*" 対象領域


- [新規 + 更新 (1 + 3):&nbsp;**SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (12 + 1): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (6 + 2):&nbsp;**Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (15 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (2 + 9):&nbsp;**SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (1 + 0):&nbsp;**SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (1 + 1):&nbsp;**SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (1 + 1):&nbsp;**Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1):&nbsp;**SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 2):&nbsp;**SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2):&nbsp;**Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事が "*ない*" 対象領域


- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新しい + 更新 (0 0 以降): **SQL のように、ActiveX データ オブジェクト (ADO)** docs](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新しい + 更新 (0 0 以降): **SQL に対する ODBC (Open Database Connectivity)** docs](../odbc/new-updated-odbc.md)
- [新しい + 更新 (0 0 以降): **SQL 用のサンプル**docs](../samples/new-updated-samples.md)
- [新しい + 更新 (0 0 以降): **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新しい + 更新 (0 0 以降): **SQL 用の XQuery** docs](../xquery/new-updated-xquery.md)


