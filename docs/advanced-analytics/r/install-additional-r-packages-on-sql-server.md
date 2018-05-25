---
title: SQL Server の Machine Learning のサービスに新しい R パッケージをインストール |Microsoft ドキュメント
description: SQL Server 2016 の R Services または SQL Server 2017 Machine Learning Services (In-database) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 20ef7181c5ab8c0494f73b205dddcdf1ac0a620e
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="install-new-r-packages-on-sql-server"></a>SQL Server に新しい R パッケージをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。 SQL Server のバージョンがある場合、および、サーバーがインターネットに接続を持つかどうかに応じて、新しい R パッケージをインストールするための複数の方法はあります。 新しいパッケージのインストールの次の方法は、考えられます。

| アプローチ                           | 権限  | リモート/ローカル |
|------------------------------------|---------------------------|-------|
| [従来の R パッケージ マネージャーを使用します。](#bkmk_rInstall)  | 管理 | Local |
| [RevoScaleR の使用](use-revoscaler-to-manage-r-packages.md) | 管理 | Local |
| [T-SQL (外部ライブラリの作成) を使用します。](install-r-packages-tsql.md) | セットアップ、その後のデータベース ロールの管理 | both 
| [MiniCRAN を使用して、ローカル リポジトリを作成するには](create-a-local-package-repository-using-minicran.md) | セットアップ、その後のデータベース ロールの管理 | both |

## <a name="bkmk_rInstall"></a> インターネット接続経由での R パッケージをインストールします。

標準の R ツールを使用するには SQL Server 2016 のインスタンスに新しいパッケージをインストールするコンピューターを提供する、SQL Server 2017 開いているポート 80 や管理者権限します。

> [!IMPORTANT] 
> 現在のインスタンスに関連付けられている既定のライブラリにパッケージをインストールすることを確認します。 ユーザーのディレクトリにパッケージをインストールことはありません。

この手順が RGui を使用しますが、RTerm またはその他の R コマンド ライン ツールを管理者特権でのアクセスをサポートするを使用することができます。

### <a name="install-a-package-using-rgui"></a>RGui を使用してパッケージをインストールします。

1. [インスタンスのライブラリの場所を特定](installing-and-managing-r-packages.md)です。 R ツールがインストールされているフォルダーに移動します。 たとえば、SQL Server 2017 既定のインスタンスの既定のパスはとおりです。 `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe を右クリックし **管理者として実行**です。 必要なアクセス許可がない、データベース管理者に連絡し、必要なパッケージの一覧を指定します。

1. コマンドラインからパッケージ名がわかっている場合を入力できます。`install.packages("the_package-name")`二重引用符は、パッケージ名に必要です。

1. ミラー サイトを求められたら、現在の場所は便利では任意のサイトを選択します。

ターゲットのパッケージは、その他のパッケージに依存している場合、R インストーラーは自動的に依存関係をダウンロードして、インストールします。

SQL Server 2016 の R Services および SQL Server 2017 Machine Learning Services のサイド バイ サイド インスタンスなど、SQL Server の複数のインスタンスがある場合は、両方のコンテキストでパッケージを使用する場合、インスタンスごとに個別にインストールを実行します。 パッケージは、インスタンス間で共有することはできません。

## <a name = "bkmk_offlineInstall"></a> R ツールを使用してオフラインのインストール

サーバーがインターネットにアクセスを持たない場合、パッケージの準備をする追加の手順が必要です。 インターネット アクセスが許可されていないサーバーで R パッケージをインストールするには、次の必要があります。

+ 事前に依存関係を分析します。
+ 対象パッケージをインターネットにアクセスできるコンピューターにダウンロードします。
+ 同じコンピューターに、必要なパッケージをダウンロードして、1 つのパッケージ アーカイブ内のすべてのパッケージを配置します。
+ なっていない zip 形式の場合は、アーカイブを zip 圧縮します。
+ パッケージのアーカイブをサーバー上の場所にコピーします。
+ アーカイブ ファイルをソースとして指定する対象パッケージをインストールします。

> [!IMPORTANT] 
> > すべての依存関係を分析することを必ずおよびダウンロード**すべて**必須パッケージ**する前に**インストールを開始します。 お勧め[miniCRAN](https://mran.microsoft.com/package/miniCRAN)このプロセスにします。 この R パッケージ リストを受け取り、パッケージをインストールしてなどの依存関係を分析するすべての zip ファイルを取得します。 miniCRAN は、サーバー コンピューターにコピーできる 1 つのリポジトリを作成します。
> 
> 詳細については、「 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。](create-a-local-package-repository-using-minicran.md)

この手順では、ことと必要とする、zip 形式の形式でサーバーにコピーする準備がすべてのパッケージを準備することを前提としています。

1. パッケージのコピーがファイルを zip 形式または複数のパッケージのすべてのパッケージを含む完全なリポジトリがサーバーにアクセスできる場所の形式を zip 形式です。

2. インスタンスの R ツールがインストールされているサーバー上のフォルダーを開きます。 たとえば、SQL Server 2016 の R Services のシステムを Windows のコマンド プロンプトを使用している場合は、切り替える`C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`です。

3. RGui または RTerm と選択 を右クリックして**管理者として実行**です。

4. R コマンドを実行`install.packages`パッケージまたはリポジトリの名前とその zip ファイルの場所を指定します。

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    このコマンドは、R パッケージを抽出`mynewpackage`ディレクトリにコピーを保存すると仮定した場合、ローカル zip ファイルから`C:\Temp\Downloaded packages`、し、ローカル コンピューターにパッケージをインストールします。 パッケージがすべての依存関係を持つ、インストーラーは、ライブラリ内の既存のパッケージを確認します。 依存関係を含むリポジトリを作成した場合、インストーラーは必要なパッケージをインストールします。

    場合は、必要なパッケージは、インスタンス ライブラリに存在しない、その zip ファイルに見つかりません対象パッケージのインストールは失敗します。

## <a name="tips-for-package-installation"></a>パッケージのインストールに関するヒント

このセクションでは、さまざまなヒントと SQL Server で R パッケージのインストールに関連する一般的な質問を示します。

###  <a name="packageVersion"></a> 適切なパッケージのバージョンと形式を取得します。

CRAN と Bioconductor などの R パッケージの複数のソースがあります。 R 言語の公式サイト (<https://www.r-project.org/>) これらのリソースの多くを一覧表示します。 多くのパッケージは、GitHub のソース コードを取得する場所に発行されます。 最後に、社内の誰かによって開発された R パッケージが与えられている可能性がありますかを記述したカスタム パッケージ。

元に関係なく、パッケージをインストールする前に Windows プラットフォームのバイナリ形式を入手していることを確認します。 

### <a name="bkmk_zipPreparation"></a> Zip ファイルとしてパッケージをダウンロードします。

サーバーのインストールに、インターネットにアクセスせず、オフライン インストールの zip ファイルの形式でパッケージのコピーをダウンロードする必要があります。 **パッケージを解凍できません。**

たとえば、次の手順は、の正しいバージョンを取得するようになりましたについて説明します。、 [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html)パッケージを Bioconductor、コンピューターがインターネットにアクセスしていると仮定してからです。

1.  **[パッケージ アーカイブ]** ボックスの一覧で、 **Windows バイナリ** バージョンを見つけます。

2.  リンクを右クリックします。ZIP ファイル、および選択**として保存ターゲット**です。

3.  Zip 形式のパッケージが格納されているをクリックして、ローカル フォルダーに移動**保存**です。

    このプロセスにより、パッケージのローカル コピーが作成されます。 

4. ダウンロード エラーが発生した場合は、さまざまなミラー サイトを再試行してください。

5. パッケージのアーカイブをダウンロードすると、パッケージをインストールまたは zip 形式のパッケージをインターネット アクセスが許可されていないサーバーにコピーできます。

> [!TIP]
> 場合は、誤ってバイナリをダウンロードする代わりに、パッケージをインストールすると、ダウンロードした zip ファイルのコピーがコンピューターにも保存されます。 ファイルの場所を決定するパッケージがインストールされているステータス メッセージをご覧ください。 インターネット アクセスが許可されていないサーバーには、その zip ファイルをコピーできます。
> 
> ただし、このメソッドを使用してパッケージを取得するときに、依存関係は含まれません。 

### <a name="bkmk_packageDependencies"></a> 必要なパッケージを取得します。

R パッケージは、多くの場合、これらのいくつかできない可能性があります、インスタンスによって使用される既定の R ライブラリで、その他の複数のパッケージに依存します。 場合もありますパッケージには、既にインストールされている依存パッケージの別のバージョンが必要です。

使用することをお勧めを複数のパッケージをインストールまたは正しいパッケージの種類とバージョン、組織内のすべてのユーザーを取得することを確認する必要がある場合、 [miniCRAN](https://mran.microsoft.com/package/miniCRAN)完全な依存関係チェーンを分析するパッケージ。 minicRAN では、複数のユーザーまたはコンピューター間で共有できるローカル リポジトリを作成します。 詳細については、次を参照してください。 [miniCRAN を使用して、ローカルのパッケージ リポジトリを作成する](create-a-local-package-repository-using-minicran.md)です。


### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>ライブラリをインストールして、既にインストールされているパッケージを把握しています。

何もインストールする前に以前、コンピューター上の R 環境を変更した場合の一時停止後、R の環境変数をことを確認して`.libPath`は 1 つのパスを使用します。

このパスは、インスタンスの R_SERVICES フォルダーを指す必要があります。 詳細については、どのパッケージが既にインストールされているかを決定する方法などを参照してください。 [SQL Server と共にインストールされている R パッケージ](installing-and-managing-r-packages.md)です。

### <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>スタンドアロン R または Python サーバーとのサイド バイ サイド インストール

コンピューターにあるデータベース内分析 (SQL Server 2017 Machine Learning Services および SQL Server 2016 R サービス) に加えて SQL Server 2017 Microsoft Machine Learning サーバー (スタンドアロン) または SQL Server 2016 R Server (スタンドアロン) をインストールした場合ごとに、すべての R ツールとライブラリの重複を削除しない R のインストールを区切ります。

R_SERVER ライブラリにインストールされているパッケージは、スタンドアロン サーバーでのみ使用され、SQL Server (In-database) のインスタンスからはアクセスできません。 常に使用する、`R_SERVICES`ライブラリ データベースに SQL Server を使用するパッケージをインストールするときにします。
