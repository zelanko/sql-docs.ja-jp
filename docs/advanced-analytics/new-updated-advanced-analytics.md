---
title: "更新 - SQL Server ドキュメントの Advanced Analytics |Microsoft ドキュメント"
description: "更新されたコンテンツで最近変更したドキュメントについては、Microsoft SQL Server の高度な分析のためのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/02/2017
ms.author: genemi
ms.workload: 
ms.openlocfilehash: 65bdb7f8f8547644d6c8b32606e17c18983aa717
ms.sourcegitcommit: 06131936f725a49c1364bfcc2fccac844d20ee4d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>新規または最近更新された: SQL Server の Advanced Analytics



ほとんど毎日 Microsoft への更新プログラムの既存のアーティクルのいくつかの[Docs.Microsoft.com](http://docs.microsoft.com/)ドキュメント web サイトです。 この記事では、最近更新された文書からの抜粋を表示します。 新しい情報の記事へのリンクも表示される可能性があります。

この記事は、定期的に再実行しているプログラムによって生成されます。 場合によっては抜粋を付けること不完全な書式設定、マークダウンとしてソース アーティクルからです。 イメージはここでは表示されません。

最新の更新プログラムは、次の日付範囲とサブジェクトの報告されます。



- *更新日の範囲:* &nbsp; **2017 年 9 月 28 日**&nbsp;から &nbsp; **2017 年 12 月 2 日**
- *サブジェクト領域:* &nbsp; **for SQL Server の Advanced Analytics**です。

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>最近作成された新しい情報の記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [データベース ユーザーとしての SQLRUserGroup の追加](r/add-sqlrusergroup-to-database.md)
2. [RevoScaleR 関数を使用して、見つからないか、SQL Server で R パッケージをインストールする方法](r/use-revoscaler-to-manage-r-packages.md)
3. [Azure SQL データベースでの R の使用](r/using-r-in-azure-sql-database.md)



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
2. [miniCRAN を使用してローカル パッケージ リポジトリを作成する](#TitleNum_2)
3. [SQL Server にインストールされている R パッケージを確認します。](#TitleNum_3)
4. [SQL Server に追加の R パッケージをインストールします。](#TitleNum_4)
5. [Azure の仮想マシンの機能を学習する SQL Server マシンにインストール](#TitleNum_5)
6. [事前トレーニング済みの機械学習の SQL Server 上のモデルをインストールします。](#TitleNum_6)
7. [ユーザーのライブラリでインストールされている R パッケージのエラーを回避します。](#TitleNum_7)
8. [Azure での機械学習の仮想マシンのプロビジョニングします。](#TitleNum_8)
9. [RevoScaleR](#TitleNum_9)
10. [有効にするにまたは SQL Server の R パッケージの管理を無効にします。](#TitleNum_10)
11. [SQL Server で使用するためのデータ サイエンス クライアントのセットアップします。](#TitleNum_11)
12. [SQL Server Machine Learning サービス (データベース内) のセットアップ](#TitleNum_12)
13. [Machine Learning Services (In-database) の無人インストール](#TitleNum_13)
14. [手順 3: データの探索と視覚化](#TitleNum_14)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1.&nbsp;[Machine Learning のサービスの既知の問題](known-issues-for-sql-server-machine-learning-services.md)

*最終更新日: 2017 年-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([次](#TitleNum_2))

<!-- Source markdown line 321.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00121c648c21576d5c86494137de1d4d81e2e265 c65973f6ae9253af5ecc621916ef36d7c0398789  (PR=3980  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



**Python コードの実行、または Python パッケージの問題**


このセクションでは、マイクロソフトによって発行された Python パッケージに関連する問題をできるだけでなく、SQL Server で Python を実行しているに固有の既知の問題の説明を含む[revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)と[microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

**モデルへのパスが長すぎる場合、事前トレーニング済みモデルへの呼び出しが失敗しました。**


コンピューター名とインスタンス名によって、既定のインストールで、事前トレーニング済みモデルをインストールする場合、トレーニング済みモデル ファイルに結果の完全なパスが Python を読み取るには長すぎます場合があります。 この制限は、次のサービス リリースで修正される予定です。

これにはいくつかの潜在的な回避策があります。

+ 事前トレーニング済みモデルをインストールする場合は、カスタムの場所を選択します。
+ 可能であれば、C:\SQL\MSSQL14 などのカスタム インストール パスの下、SQL Server インスタンスをインストールします。MSSQLSERVER です。
+ Windows ユーティリティを使用して[Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx)短いパスをモデル ファイルにマップするハード リンクを作成します。

**Varbinary 変数の初期化の失敗である BxlServer でエラーが発生します。**


SQL Server を使用して Python コードを実行すると`sp_execute_external_script`、varbinary (max) 型、varchar (max)、または類似した種類の変数に出力が、コードと、変数を初期化またはスクリプトの一部として設定する必要があります。 それ以外の場合、エラーと動作が停止した、データの exchange コンポーネントである BxlServer を発生させます。

この制限は、次のサービス リリースで修正される予定です。 この問題を回避するには、Python スクリプト内で、変数が初期化されることを確認します。 次の例のように、任意の有効な値を使用できます。

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-create-a-local-package-repository-using-minicranrcreate-a-local-package-repository-using-minicranmd"></a>2.&nbsp;[MiniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。](r/create-a-local-package-repository-using-minicran.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 43.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 44b77cb127e9ffab1777216a66f0e5be9c82f3d2 65e30f10fc36acb3ce95f60f51f3501fbc98ad08  (PR=4150  ,  Filename=create-a-local-package-repository-using-minicran.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



-   **オフライン インストールを簡単に**: パッケージをインストールするサーバーがオフラインにする必要がありますダウンロードすることもすべてのパッケージの依存関係を使用する miniCRAN 簡単に正しい形式ですべての依存関係を取得します。

-   **バージョン管理の改善**: マルチ ユーザー環境では、サーバー上の複数のパッケージ バージョンの無制限のインストールを回避する理由。

リポジトリを作成した後に、新しいパッケージを追加または既存のパッケージのバージョンのアップグレードによって変更できます。

**手順 1 です。MiniCRAN パッケージをインストールします。**


まず、ソースとして使用する miniCRAN リポジトリを作成します。 インターネットにアクセスできるコンピューターでこのリポジトリを作成する必要があります。

1.  MiniCRAN パッケージと、必要なインストール**igraph**パッケージです。

```
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
```

**手順 2 です。パッケージ ソースの定義: CRAN ミラー、または MRAN スナップショット**


1. パッケージの取得中に使用するミラー サイトを指定します。

```
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
```

2.  収集されたパッケージを格納するローカル フォルダーを指定します。 フォルダー miniCRAN; 名前を付ける必要はありません。"GeneticsPackages"または"ClientRPackages1.0.2"のようなわかりやすい名前がある可能性があります。

    フォルダーを事前に作成することを確認するだけです。 場合、エラーが発生、`local_repo`フォルダーでは、後で、R コードを実行するときに存在しません。



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3.&nbsp;[SQL Server にインストールされている R パッケージを確認](r/determine-which-packages-are-installed-on-sql-server.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2) | [次](#TitleNum_4))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 13d93acedc6e6b4615f1a244a2a1542910feb69e 9a065066398843a4bed318fa46d4982d712915a9  (PR=4150  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



+ パッケージが見つかった場合、返されたメッセージがありますのような"コマンド正常に完了します"

+ 次のようなエラーが発生した場合は、パッケージの配置または読み込まれることはできません、:"外部スクリプト エラーが発生しました: library("RevoScaleR") でエラー: RevoScaleR と呼ばれるパッケージはありません"

**R を使用するインストール済みのパッケージの一覧を取得します。**


R ツールと R 関数を使用すると、複数の方法でインストールまたは読み込み済みのパッケージの一覧を取得できます。 多くの R 開発ツールでは、オブジェクト ブラウザーや、インストール済みパッケージまたは現在の R ワークスペースに読み込まれているパッケージの一覧が提供されます。

+ ローカルの R ユーティリティでは、ベースの R 関数をなど使用`installed.packages()`に含まれている、`utils`パッケージです。 インスタンスの正確な一覧を取得するには、ライブラリ パスを明示的に指定かインスタンス ライブラリに関連付けられた R のツールを使用する必要があります。

+ 特定のコンピューティング コンテキストでパッケージを確認するには、RevoScaleR パッケージから、次の機能を使用できます。 これらの関数を使用して、指定された計算コンテキストでパッケージを識別できます。

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)

たとえば、指定した SQL Server のコンピューティング コンテキストで使用可能なパッケージの一覧を取得する次の R コードを実行します。

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```
**参照**




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-install-additional-r-packages-on-sql-serverrinstall-additional-r-packages-on-sql-servermd"></a>4.&nbsp;[SQL Server に追加の R パッケージをインストール](r/install-additional-r-packages-on-sql-server.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_3) | [次](#TitleNum_5))

<!-- Source markdown line 266.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ba48f1838857d90d6692aafc48f393777ac602fa 37de2586a344a99969bcd9a20723c021db2604a4  (PR=4150  ,  Filename=install-additional-r-packages-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



このセクションでは、さまざまなヒントと SQL Server で R パッケージのインストールに関連するサンプル コードを提供します。

**<a name="packageVersion"></a>適切なパッケージのバージョンと形式を取得します。**


R パッケージの供給元は複数あります。その中でもよく知られているのは CRAN と Bioconductor です。 R 言語の公式サイト (<https://www.r-project.org/>) には、これらのリソースが多数掲載されています。 多くのパッケージは、GitHub のソース コードを取得する場所に発行されます。 ただしが提供された社内の誰かによって開発された R パッケージです。

元に関係なくをインストールするパッケージが、Windows プラットフォームのバイナリ形式を持つことを確認する必要があります。 それ以外の場合、ダウンロードしたパッケージは、SQL Server 環境で実行できません。

をダウンロードする前に、また、パッケージが SQL Server で実行されている R のバージョンと互換性があるかどうかを確認する必要があります。

**<a name="bkmk_zipPreparation"></a>Zip 形式のファイルとしてパッケージをダウンロードします。**


サーバーのインストールに、インターネットにアクセスせず、オフライン インストールの zip ファイルの形式でパッケージのコピーをダウンロードします。 パッケージを解凍できません。

たとえば、次の手順は、の正しいバージョンを取得するようになりましたについて説明します。、 [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html)パッケージを Bioconductor、コンピューターがインターネットにアクセスしていると仮定してからです。

1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。

2.  リンクを右クリックします。ZIP ファイル、および選択**として保存ターゲット**です。

3.  Zip 形式のパッケージが格納されているをクリックして、ローカル フォルダーに移動**保存**です。

このプロセスにより、パッケージのローカル コピーが作成されます。 パッケージをインストールしたり、zip 形式のパッケージをインターネット アクセスが許可されていないサーバーにコピーできます。

Zip ファイル形式と、R パッケージを作成する方法の詳細については、内容、ことをお勧めこのチュートリアルでは、R プロジェクト サイトから PDF 形式でダウンロードできます: [R パッケージを作成する](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf)です。



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-installing-sql-server-machine-learning-features-on-an-azure-virtual-machinerinstalling-sql-server-r-services-on-an-azure-virtual-machinemd"></a>5.&nbsp;[SQL サーバーをインストールするマシンが Azure の仮想マシンの機能の学習](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_4) | [次](#TitleNum_6))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f4d287044b8bfda2dbe77fbf65b0d9cdd8f2ff42 2a8e33de6383f5d3af52256c5dfcb60184659eb8  (PR=4150  ,  Filename=installing-sql-server-r-services-on-an-azure-virtual-machine.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



6. リモート データ サイエンス クライアントからのインスタンスに接続する場合は、完了 [追加の手順-ステップ #additional) 必要に応じて、します。

**SQL Server VM で、マシン学習機能を無効にします。**


有効にするも、いつでも既存の SQL Server 仮想マシンでこの機能を無効にすることができます。

1. 仮想マシンのブレードを開きます。
2. **[設定]** をクリックし、**[SQL Server の構成]** を選択します。
3. 機能を変更して適用します。

**<a name="existing"></a>R Services、SQL Server 2016 Enterprise の既存の VM を追加します。**


機械学習なしの SQL Server を含む Azure の仮想マシンを作成する場合は、次の手順で機能を追加することができます。

1. 再実行. です。テキストの NotShown--ssNoVersion--./../includes/ssnoversion-md.md)] の設定し、の機能を追加、**サーバー構成**ウィザードのページです。
2. 外部スクリプトの実行を有効にし、再起動、. です。テキストの NotShown--ssNoVersion--./../includes/ssnoversion-md.md)] のインスタンス。 詳細については、次を参照してください [設定を SQL Server R Services--。/../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)。
3. (省略可能) R ワーカー アカウントのデータベースへのアクセスを構成します (リモート スクリプトの実行に必要な場合)。
   詳細についてを参照してください [設定を SQL Server R Services--./../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)。
3. (省略可能) Azure 仮想マシンでファイアウォール規則を変更します (リモートのデータ サイエンス クライアントから R スクリプトを実行できるようにする場合)。 詳細についてを参照してください [ブロック解除ファイアウォール--#firewall)。
4. 必要なネットワーク ライブラリをインストールまたは有効化します。 詳細についてを参照してください [追加ネットワーク プロトコル--#network)。



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-install-pretrained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>6.&nbsp;[インストールは、SQL Server 上の機械学習モデルを事前トレーニング済み](r/install-pretrained-models-sql-server.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_5) | [次](#TitleNum_7))

<!-- Source markdown line 96.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07b51584a90568cccceea382c44155e40e09c967 db083f8536fbb2ea5886fed787872867b5de5750  (PR=4150  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    For example, to enable use of the latest version of the pretrained models for Python, in a default instance of SQL Server 2017, you would run this statement:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    On a named instance, the command would be something like this:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Python を使用するには、Machine Learning Server (スタンドアロン) を持つモデルに事前トレーニング済み。

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    たとえば、2017 年 1 SQL Server セットアップを使用してマシン ラーニング Server (スタンドアロン) の既定のインストールと仮定した場合、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. バージョン パラメーターは、次の値がサポートされています。



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-avoiding-errors-on-r-packages-installed-in-user-librariesrpackages-installed-in-user-librariesmd"></a>7.&nbsp;[ユーザー ライブラリでインストールされている R パッケージのエラーを回避します。](r/packages-installed-in-user-libraries.md)

*最終更新日: 2017 年 1-10-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_6) | [次](#TitleNum_8))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 52cb9a53d7d9c31ee9bc6977464ebd2a18081ff3 3537aa6755c66f12c19bb3448dc9b5c8abb9cc28  (PR=3619  ,  Filename=packages-installed-in-user-libraries.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=aecf422ca2289b2a417147eb402921bb8530d969) -->



ただし、このことができますは機能しません、SQL Server で R ソリューションを実行する場合、インスタンスに関連付けられている特定の既定のライブラリに R パッケージをインストールする必要があるためです。

パッケージが既定のライブラリにインストールされていない場合は、パッケージを呼び出したときに次のエラーが送信されることがあります。

*Library(xxx) でエラー: 'パッケージ名' と呼ばれるパッケージはありません*

不適切な開発ことも、カスタム ユーザー ライブラリに必要な R パッケージをインストールする可能性があるため発生したエラーをソリューションがライブラリの場所にアクセスできない他のユーザーによって実行される場合。

**アクセス可能なライブラリに R パッケージをインストールする方法**


**SQL Server 2016 用**

インスタンスに関連付けられているパッケージ ライブラリを使用します。 詳細については、[SQL Server--installing-and-managing-r-packages.md にインストールされている R パッケージ) を参照してください。

**SQL server 2017**

SQL Server では、複数のパッケージ バージョンを管理し、ファイル システムへのアクセスをユーザーがあることを必要とせず、個々 のパッケージにユーザーのアクセス許可を付与するための機能を提供します。

パッケージの共有ライブラリを設定し、ユーザー ロールを割り当てる方法の詳細については、[R パッケージの管理 SQL Server--r-package-management-for-sql-server-r-services.md) を参照してください。




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-provision-a-virtual-machine-for-machine-learning-on-azurerprovision-the-r-server-only-sql-server-2016-enterprise-vm-on-azuremd"></a>8.&nbsp;[Azure 機械学習の仮想マシンのプロビジョニング](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

*最終更新日: 2017 年 1-10-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_7) | [次](#TitleNum_9))

<!-- Source markdown line 132.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 16439b4a8f5f4218edfcd746ed20ccbc8263dabc 1b3a8a7d1ceceaa459b3fd5640da26859df8d80b  (PR=3748  ,  Filename=provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=262e3cf5df2448bb6b532c0549c3d72daefe5a96) -->



|名前| コメント|
|----|----|----|
| **SQL Server 2016**| ***  |
|Windows 上の SQL Server 2016 SP1 Enterprise|R Services の統合の高度な分析します。|
|Windows Server 上の BYOL SQL Server 2016 SP1 Enterprise |R Services の統合の高度な分析します。 |
|Windows Server 2016 での無料のライセンス: SQL Server 2016 SP1 Developer |R Services の統合の高度な分析します。 |
| データ サイエンス仮想マシン - Windows 2012|Microsoft R Server Developer Edition、SQL Server 2016 Developer edition、Anaconda Python 配布、ジュリア Pro developer edition、および Jupyter ノートブックを R. 用など、データ サイエンス用の一般的なツールが含まれています|
| データ サイエンス仮想マシン - Windows 2016|データベース内 R 分析のサポートは、SQL Server 2016 Developer Edition が含まれています。|
|**SQL Server 2017**| ***   |
|SQL Server 2017 Enterprise Windows Server 2016| Python と R 言語のサポートを備えた machine Learning サービス。|
|BYOL SQL Server 2017 Enterprise Windows Server 2016|Python と R 言語のサポートを備えた machine Learning サービス。|
| Windows Server での無料の SQL Server のライセンス: SQL Server 2017 Developer|Python と R 言語のサポートを備えた machine Learning サービス。|
| **その他**| *** |
| 機械学習のサーバーのみ SQL Server 2017 Enterprise|同様に、SQL Server 2016 Enterprise イメージが Machine Learning のサーバーのスタンドアロン バージョンを含むコア ScaleR と操作運用の機能が Windows の環境を最適化します。|
| Machine Learning Server for Windows|Windows 環境用に最適化された操作運用の機能とは、Machine Learning のサーバーのスタンドアロン バージョンが含まれています。|



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-revoscalerrrevoscaler-overviewmd"></a>9.&nbsp;[RevoScaleR](r/revoscaler-overview.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_8) | [次](#TitleNum_10))

<!-- Source markdown line 18.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 92f2dfa2e75037a932415881c55d2fd37fc6847a c6e9f17f2df82447b18beff41769ae3ebfbed562  (PR=4150  ,  Filename=revoscaler-overview.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->




RevoScaleR は、規模でデータ サイエンスをサポートするには、Microsoft によって提供される、machine learning 関数のパッケージです。

+ 関数は、データのインポート、データ変換、要約、ビジュアル化、および分析をサポートします。

+ _一度に_ファイル システムの操作の並列の非常に大規模なデータセットに対して実行され配布のことを意味します。 アルゴリズムは、チャンクを使用して、操作が完了した場合、戻した結果によって、メモリに収まり切らないデータセットを操作できます。

+ RevoScaleR は、オープン ソースの R 関数より多くの機能強化を提供します。 最も人気のある基本 R 関数の多くに対応する RevoScaleR 関数があります。 RevoScaleR 関数が示されて、 **rx**または**Rx**プレフィックスを識別しやすいようにします。

+ RevoScaleR は、分散データ サイエンス用のプラットフォームとして機能します。 最新のアルゴリズムでな RevoScaleR 計算コンテキストと変換を使用するなど、 [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)です。 使用することも[rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec)ベースの R 関数を並列に実行します。

アクションで RevoScaleR の例は、これらのブログを参照してください。

+ [ビルドおよび R と SQL Server を使用して、予測モデルの配置](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Machine Learning のサーバーで 1 秒あたりの 100万予測](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [MicrosoftML を使用してタクシー ヒントを予測します。](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [RxExec によるパフォーマンスの最適化](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

**RevoScaleR を取得する方法**




&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-enable-or-disable-r-package-management-for-sql-serverrr-package-how-to-enable-or-disablemd"></a>10.&nbsp;[を有効にするか、SQL Server の R パッケージの管理を無効にします。](r/r-package-how-to-enable-or-disable.md)

*最終更新日: 2017 年-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_9) | [次](#TitleNum_11))

<!-- Source markdown line 60.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f846cd7d601459a95e694ada41e9fc5285f3de9 83a4a84adf47670c7fd4599f889f27ec3c219708  (PR=4150  ,  Filename=r-package-how-to-enable-or-disable.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    If you do not specify a user, the current security context is used.

3. パッケージをインストールする必要がありますデータベースごとに、コマンドを繰り返します。

4.  新しいロールが正常に作成されたことを確認するには、SQL Server Management Studio でデータベースをクリックして、展開**セキュリティ**、展開と**データベース ロール**です。

    Sys.database_principals、次のようにクエリを実行することもできます。

```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,
        pr.authentication_type_desc, pe.state_desc,
        pe.permission_name, s.name + '.' + o.name AS ObjectName
    FROM sys.database_principals AS pr
    JOIN sys.database_permissions AS pe
        ON pe.grantee_principal_id = pr.principal_id
    JOIN sys.objects AS o
        ON pe.major_id = o.object_id
    JOIN sys.schemas AS s
        ON o.schema_id = s.schema_id;
```

4.  適切なアクセス許可を持つユーザーを使用できる機能が有効にすると、[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)パッケージに追加するには、t-sql ステートメントです。 このしくみの例は、次を参照してください。 [SQL Server のその他のパッケージをインストール](r/install-additional-r-packages-on-sql-server.md)です。

**<a name="bkmk_disable"></a>パッケージの管理を無効にします。**




&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-set-up-a-data-science-client-for-use-with-sql-serverrset-up-a-data-science-clientmd"></a>11.&nbsp;[SQL Server で使用するためのデータ サイエンス クライアントのセットアップ](r/set-up-a-data-science-client.md)

*最終更新日: 2017 年-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_10) | [次](#TitleNum_12))

<!-- Source markdown line 52.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f674f5d329211e4c7d8dc464bd70f1cdef633350 8c65fc96c04f32d1e4777870774a11f9fd2ee219  (PR=3765  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



    For setup information, see [How to install R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

    To configure RTVS to use your Microsoft R client libraries, see [About Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

    無料の Community Edition でもには、R、Python、および f# のプロジェクト テンプレートがインストールされるデータ サイエンス ワークロードが含まれています。

    Visual Studio からのダウンロード[このサイト](https://www.visualstudio.com/vs/)です。

+ RStudio

    RStudio を使用する場合は、RevoScaleR ライブラリを使用するために追加の手順が必要です。

    - 必要なパッケージとライブラリを取得する Microsoft R クライアントをインストールします。
    - Microsoft R ランタイムを使用する R パスを更新します。

    詳細については、次を参照してください。 [R クライアントの構成、IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide)です。

**IDE を構成します。**


+ R Tools for Visual Studio

    参照してください[このサイト](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r)ビルドし、R をデバッグする方法の例をいくつかのプロジェクト R Tools for Visual Studio を使用します。

+ Visual Studio 2017

    Microsoft R クライアントまたは R サーバーをインストールする場合**する前に**Visual Studio をインストールして、R サーバー ライブラリを自動的に検出され、ライブラリ パスに使用します。 RevoScaleR ライブラリをインストールしていないかどうか、 **R ツール**メニューの  **R クライアントのインストール**です。

**SQL Server で R を実行します。**


この例では、インストールされている、データ サイエンスのワークロードで Visual Studio の 2017 Community Edition を使用します。

1. **ファイル**メニューの **新規**し、**プロジェクト**です。

2. 手の形は、ウィンドウには、プレインストールされたテンプレートの一覧が含まれています。 をクリックして**R**を選択して**R プロジェクト**です。 **名前**ボックスに、入力`dbtest` をクリック**OK**です。



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>12.&nbsp;[SQL Server マシン ラーニング Services (In-database) セットアップ](r/set-up-sql-server-r-services-in-database.md)

*最終更新日: 2017 年-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_11) | [次](#TitleNum_13))

<!-- Source markdown line 111.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4d355f6494b417dd90dce3943e7176eaece7336e 20bddb8ffd4cf3774b812a7376c70b95ccc57e92  (PR=3980  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



   + データベース エンジン サービス
   + R Services (データベース内)

7. インストールが完了したら、コンピューターを再起動します。


**<a name="bkmk2017top"></a>SQL Server 2017 Machine Learning Services (In-database) のインストールします。**


> [!div class="checklist"]
> * データベース エンジンと機械学習の機能をインストールします。
> * インストール後の手順が必要: 機械学習を有効にして再起動
> * 省略可能なインストール後の手順: ファイアウォール規則を追加、ユーザーを追加、変更、またはサービス アカウントの構成、リモート データ サイエンス クライアントを設定します。

**作業を開始します。**

1. 実行...!テキストの NotShown--ssNoVersion--./../includes/ssnoversion-md.md)] の設定です。

2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**です。

     ![Machine Learning のサービスをインストール (In-Database)--media/2017setup-installation-page-mlsvcs.png「Machine Learning のサービスとデータベース エンジンのインストールを開始する」)

3. **機能の選択** ページで、次のオプションを選択します。

    + 選択**データベース エンジン サービス**です。 機械学習を使用する各インスタンス、データベース エンジンが必要です。

    + 選択**機械学習の Services (In-database)**です。 このオプションは r です。 データベースで使用するためのサポートをインストールします。このオプションを選択した後に、機械学習の言語を選択できます。 、R のみを選択することができますか、R と Python の両方を追加することができます。

    ![Machine Learning サービス機能 selection--media/2017setup-features-page-mls-rpy.png"R のこれらの機能を選択してデータベース内にサービス")

    Python または R 言語のオプションを選択しない場合、セットアップ ウィザードは、言語固有のコンポーネントをインストールしないと SQL Server 信頼スタート パッドが含まれます extensibility framework のみをインストールします。  一般に、少なくとも 1 つの言語を最初にインストールすることをお勧めします。 ただし、すぐに、バインディング プロセスを使用して、機械学習のコンポーネントをアップグレードする場合は、このオプションを使用する場合があります。 詳細については、[R Services--use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md のインスタンスをアップグレードする使用 SqlBindR) を参照してください。



&nbsp;

&nbsp;

---

<a name="TitleNum_13"/>

### <a name="13-nbsp-unattended-installation-of-machine-learning-services-in-databaserunattended-installs-of-sql-server-r-servicesmd"></a>13.&nbsp;[Machine Learning Services (In-database) の無人インストール](r/unattended-installs-of-sql-server-r-services.md)

*最終更新日: 2017 年-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_12) | [次](#TitleNum_14))

<!-- Source markdown line 75.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ad203c90adff3f515b5f16472fad9753be7a421d 6925a9276bcd4a80babc7504de50400f1a5a2940  (PR=3765  ,  Filename=unattended-installs-of-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



次の例は、追加 Python 言語で、サイレントの無人実行に必要な引数が SQL Server 2017 Machine Services (In-database) のインストールを示しています。

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

SQL Server 2017 の Python のために必要なフラグを注意してください。

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

**名前付きインスタンスに R、Python の両方をインストールします。**


次の例、サイレントの無人実行に必要な引数が SQL Server 2017 Machine Services (In-database) のインストール、名前付きインスタンスにします。 R、Python の両方の言語が追加されます。

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

**<a name="OldInstall"></a>SQL Server 2016 用コマンド ライン インストール**


次の例では、追加の R 言語で、サイレントの無人実行に必要な引数が SQL Server 2016 のインストールを示します。



&nbsp;

&nbsp;

---

<a name="TitleNum_14"/>

### <a name="14-nbsp-step-3-explore-and-visualize-the-datatutorialssqldev-py3-explore-and-visualize-the-datamd"></a>14.&nbsp;[手順 3: 探索し、データの視覚化](tutorials/sqldev-py3-explore-and-visualize-the-data.md)

*更新日: 2017 年 11 月 30 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([前へ](#TitleNum_13))

<!-- Source markdown line 66.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 47edcfbd8da7cf1ea1ad03a05f86d3cd26014827 674a7c7d0e8290fc91970ed2aeda3b97d5165d75  (PR=4150  ,  Filename=sqldev-py3-explore-and-visualize-the-data.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    Class 4: `tip_amount` > $20

**T-SQL で Python を使用してプロットを作成します。**


データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 視覚エフェクトは、データ、外れ値の分布を理解するため、このような強力なツールであるために、Python は、データの視覚化多くのパッケージを提供します。 **Matplotlib**モジュールの視覚エフェクト、人気のあるライブラリの 1 つは、ヒストグラム、散布、ボックス プロット、およびその他のデータ探索のグラフを作成するための多くの関数が含まれています。

このセクションでは、ストアド プロシージャを使用してプロットを操作する方法を学習します。 はなく、サーバー上のイメージを開くよりもに、Python オブジェクトを格納`plot`として**varbinary**データ、および、書き込み、ファイルにしたり共有したりできる他の場所を表示します。

**Varbinary データとしてプロットを作成します。**


**Revoscalepy** SQL Server 2017 Machine Learning サービスに含まれているモジュールに似た機能をサポートしている、 **RevoScaleR** R. 用のパッケージ この例は、Python の該当するショートカットを使用して`rxHistogram`からデータに基づくヒストグラムをプロットする、. です。テキストの NotShown tsql--./../includes/tsql-md.md)] のクエリ。

ストアド プロシージャが返すシリアル化された Python`figure`オブジェクトのストリームとして**varbinary**データ。 バイナリ データを直接表示することはできませんが、逆シリアル化し、金額を表示するクライアントでの Python コードを使用してクライアント コンピューター上の画像ファイルを保存します。

1. ストアド プロシージャを作成_SerializePlots_PowerShell スクリプトは、既にしなかった場合は、します。

    - 変数`@query`クエリ テキストを定義`SELECT tipped FROM nyctaxi_sample`、スクリプトの入力変数の引数としての Python コード ブロックに渡される`@input_data_1`です。
    - Python スクリプトが非常に単純な: **matplotlib** `figure`オブジェクトが、ヒストグラム、散布図のプロットに使用され、これらのオブジェクトは、シリアル化を使用して、`pickle`ライブラリです。







## <a name="similar-articles"></a>類似した記事

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

このセクションでは、パブリック GitHub.com リポジトリ [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新規または最近更新されたアーティクルを持つサブジェクト領域

- [新規 + 更新 (3 + 14): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新しい + 更新 (1 + 0): **SQL 用に Analysis Services** docs](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (87 + 0): **SQL の分析プラットフォーム システム**に関するドキュメント](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [新規 + 更新 (5 + 4): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (0 + 1): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (2 + 2): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (10 + 9): **Linux 上の SQL** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (2 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (4 + 2): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 1): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (21 + 0): **SQL Operations Studio** に関するドキュメント](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [新規 + 更新 (5 + 1): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新しい + 更新 (0 + 1): **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (1 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新しい + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [新規 + 更新 (0 + 2): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>サブジェクト領域に新規または最近更新されたアーティクルを持たない

- [新規 + 更新 (0 + 0): **SQL の Data Migration Assistant (DMA)** に関するドキュメント](../dma/new-updated-dma.md)
- [新しい + 更新 (0 0 以降): **SQL のように、ActiveX データ オブジェクト (ADO)** docs](../ado/new-updated-ado.md)
- [新しい + 更新 (0 0 以降): **SQL の Data Quality Services** docs](../data-quality-services/new-updated-data-quality-services.md)
- [新しい + 更新 (0 0 以降):**データ マイニング拡張機能 (DMX) の SQL** docs](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新しい + 更新 (0 0 以降): **SQL の多次元式 (MDX)** docs](../mdx/new-updated-mdx.md)
- [新しい + 更新 (0 0 以降): **SQL に対する ODBC (Open Database Connectivity)** docs](../odbc/new-updated-odbc.md)
- [新しい + 更新 (0 0 以降): **SQL 用の PowerShell** docs](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **Tools for SQL**  に関するドキュメント](../tools/new-updated-tools.md)
- [新しい + 更新 (0 0 以降): **SQL 用の XQuery** docs](../xquery/new-updated-xquery.md)


