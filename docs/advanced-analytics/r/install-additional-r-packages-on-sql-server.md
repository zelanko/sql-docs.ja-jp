---
title: "SQL Server に追加の R パッケージをインストール |Microsoft ドキュメント"
ms.date: 03/05/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: acb1727c85cae1d8176703c93cc77c971980d394
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="install-additional-r-packages-on-sql-server"></a>SQL Server に追加の R パッケージをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。

SQL Server のバージョンがある場合、および、サーバーがインターネットにアクセスを持つかどうかに応じて、新しい R パッケージをインストールするための複数の方法はあります。

+ [インターネットにアクセスできる R ツールを使用して新しいパッケージをインストールします。](#bkmk_rInstall)

    インターネットからパッケージをインストールするのにには、従来の R コマンドを使用します。 これは最も簡単な方法ですが、管理アクセス権が必要です。

    **適用されます:**[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)][!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]です。 必要なのインスタンス[!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] Ddl を使用してパッケージの管理が有効になっていません。

+ [使用して、サーバーに新しい R パッケージをインストール**ありません**インターネットへのアクセス](#bkmk_offlineInstall)

    サーバーがインターネットにアクセスを持たない場合、パッケージの準備をする追加の手順が必要です。 このセクションでは、パッケージとその依存関係のインストールに必要なファイルを準備する方法について説明します。

+ [外部ライブラリの作成ステートメントを使用してパッケージをインストールします。](#bkmk_createlibrary) 

    [外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)ステートメントは、SQL Server 2017 年、R を実行しなくてもパッケージ ライブラリを作成できるようにすることで提供される、Python コードを直接またはします。 ただし、このメソッドは、必要なすべてのパッケージを事前に準備し、その他のデータベース権限が必要ですが必要です。

    **適用されます:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]; 他の制限が適用されます

## <a name="bkmk_rInstall"></a> インターネットを使用して新しい R パッケージをインストールします。

標準の R ツールを使用すると、SQL Server 2016 または SQL Server 2017 のインスタンスに新しいパッケージをインストールします。 このプロセスでは、コンピューターの管理者を使用している必要があります。

> [!IMPORTANT] 
> 現在のインスタンスに関連付けられている既定のライブラリにパッケージをインストールすることを確認します。 ユーザーのディレクトリにパッケージをインストールことはありません。

この手順では、RGui; を使用してパッケージをインストールする方法について説明しますただし、RTerm またはその他の R コマンド ライン ツールを管理者特権でのアクセスをサポートするを使用することができます。

### <a name="install-a-package-using-rgui-or-rterm"></a>RGui または RTerm を使用してパッケージをインストールします。

1. インスタンスは、R ライブラリがインストールされているサーバー上のフォルダーに移動します。

  **[既定のインスタンス]**

    SQL Server 2017: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

  **[名前付きインスタンス]**

    SQL Server 2017: `C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

  機械学習のコンポーネントをアップグレードするバインディングを使用している場合、パスを変更した可能性があります。 常に新しいパッケージをインストールする前に、インスタンス パスを確認します。 

2. RGui.exe を右クリックし **管理者として実行**です。

    必要なアクセス許可がない、データベース管理者に連絡し、必要なパッケージの一覧を指定します。

3. コマンドラインからパッケージ名がわかっている場合を入力できます。`install.packages("the_package-name")`二重引用符は、パッケージ名に必要です。

4. ミラー サイトを求められたら、現在の場所は便利では任意のサイトを選択します。

5. ターゲットのパッケージは、その他のパッケージに依存している場合、R インストーラーは自動的に依存関係をダウンロードして、インストールします。

6. パッケージを使用する必要がある各インスタンスに対して個別にインストールを実行します。 パッケージは、インスタンス間で共有することはできません。

## <a name = "bkmk_offlineInstall"></a> R ツールを使用してオフラインのインストール

インターネット アクセスが許可されていないサーバーで R パッケージをインストールするには、次の必要があります。

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

2. インスタンスは、R ライブラリがインストールされているサーバー上のフォルダーを開きます。 たとえば、Windows のコマンド プロンプトを使用している場合は、RTerm.Exe または RGui.exe が配置されているディレクトリに移動します。

  **[既定のインスタンス]**

    SQL Server 2017: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

  **[名前付きインスタンス]**

    SQL Server 2017: `C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

3. RGui またはコマンド プロンプトを右クリックし、選択**管理者として実行**です。

4. R コマンドを実行`install.packages`パッケージまたはリポジトリの名前とその zip ファイルの場所を指定します。

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    このコマンドは、R パッケージを抽出`mynewpackage`ディレクトリにコピーを保存すると仮定した場合、ローカル zip ファイルから`C:\Temp\Downloaded packages`、し、ローカル コンピューターにパッケージをインストールします。 パッケージがすべての依存関係を持つ、インストーラーは、ライブラリ内の既存のパッケージを確認します。 依存関係を含むリポジトリを作成した場合、インストーラーは必要なパッケージをインストールします。

    場合は、必要なパッケージは、インスタンス ライブラリに存在しない、その zip ファイルに見つかりません対象パッケージのインストールは失敗します。

## <a name="bkmk_createlibrary"></a> DDL ステートメントを使用して、パッケージをインストールします。 

SQL Server 2017 で使用できます、[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)インスタンスまたは特定のデータベースにパッケージまたはパッケージのセットを追加するステートメント。 この DDL ステートメントとサポートのデータベース ロール、パッケージのインストールと管理を容易にするため、データベースの所有者によって R または Python のツールを使用することがなくです。

このプロセスには、R、Python または、従来の方法を使用してパッケージをインストールすると比較すると、いくつかの準備が必要です。

+ すべてのパッケージは、インターネットからダウンロードするのではなく、ローカルのファイルを zip 形式として使用可能にする必要があります。

    サーバー上のファイル システムへのアクセスがない、渡すこともできます完全なパッケージ変数としてバイナリ形式を使用します。 詳細については、次を参照してください。[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)です。

+ パッケージが利用できないために必要な場合、ステートメントが失敗します。 インストールし、サーバーおよびデータベースへのパッケージがアップロードされるかどうかを確認するパッケージの依存関係を分析する必要があります。 使用することをお勧め**miniCRAN**または**igraph**パッケージの依存関係を分析するためです。

+ データベースでは、必要なアクセス許可が必要です。 詳細については、「[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。

### <a name="prepare-the-packages-in-archive-format"></a>アーカイブ形式でパッケージを準備します。

1. 1 つのパッケージをインストールする場合は、zip 形式でパッケージをダウンロードします。 

2. パッケージには、他のパッケージが必要とする場合は、必要なパッケージが利用できることを確認する必要があります。 MiniCRAN を使用して、対象パッケージを分析し、すべての依存関係を識別することができます。 

3. 圧縮されたファイル サーバー上のローカル フォルダーにすべてのパッケージを含む miniCRAN リポジトリにコピーします。

4. 開く、**クエリ**ウィンドウで、管理者特権を持つアカウントを使用します。

5. T-SQL ステートメントを実行`CREATE EXTERNAL LIBRARY`zip 形式のパッケージのコレクションをデータベースにアップロードします。

    たとえば、次のステートメントが名前にパッケージのソースとして、miniCRAN リポジトリ、 **randomForest**パッケージ、その依存関係とします。 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    任意の名前を使用することはできません。外部ライブラリ名の読み込みまたはパッケージを呼び出すときに使用するものと同じ名前が必要です。

6. ライブラリが正常に作成する場合は、ストアド プロシージャ内で呼び出すことによって、SQL Server でパッケージを実行できます。
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

### <a name="known-issues-with-create-external-library"></a>外部ライブラリの作成に関する既知の問題

外部ライブラリの作成は、これらの条件下でサポートされます。

+ 1 つのパッケージをインストールする場合は、依存していません。
+ 依存関係、パッケージをインストールして、すべてのパッケージを事前に準備しました。 

パッケージの依存関係がない場合は、DDL ステートメントが失敗します。 たとえば、このような場合に失敗する、インストール プロセスが確認されています。

+ 第 2 レベルの依存関係のあるパッケージをインストールして、分析には、第 2 レベルのパッケージを拡大できませんでした。 インストールするなど、 **gglot2**と、マニフェストに表示されているすべてのパッケージの識別。 ただし、それらのパッケージがインストールされていない他の依存関係。
+ 一連の異なるバージョンのサポート パッケージを必要とするパッケージをインストールして、サーバーが持っているバージョンが正しくありません。

## <a name="package-installation-tips"></a>パッケージのインストールに関するヒント

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


### <a name="know-which-library-you-are-using-for-installation"></a>インストールを使用しているライブラリを知る

何もインストールする前に以前、コンピューター上の R 環境を変更した場合の一時停止後、R の環境変数をことを確認して`.libPath`は 1 つのパスを使用します。

このパスは、インスタンスの R_SERVICES フォルダーを指す必要があります。 詳細については、次を参照してください。 [SQL Server と共にインストールされている R パッケージ](installing-and-managing-r-packages.md)です。

### <a name="side-by-side-installation-with-r-server"></a>R Server とサイド バイ サイド インストール

SQL Server マシン ラーニング サービスに加えて Microsoft マシン ラーニング Server (スタンドアロン) をインストールした場合、コンピューターがごとに、すべての R ツールとライブラリの重複を削除しない R の別のインストールに必要です。

R_SERVER ライブラリにインストールされているパッケージは、Microsoft R Server によってのみ使用され、SQL Server がアクセスできないされます。 使用してください、`R_SERVICES`ライブラリ SQL Server で使用するパッケージをインストールするときにします。

### <a name="how-to-determine-which-packages-are-already-installed"></a>既にインストールされているパッケージを確認する方法ですか。

 参照してください[SQL Server と共にインストールされている R パッケージ](installing-and-managing-r-packages.md)