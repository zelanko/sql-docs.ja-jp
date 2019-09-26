---
title: Windows に SQL Server Machine Learning Services (Python、R) をインストールする
titleSuffix: ''
description: この記事では、Windows に SQL Server Machine Learning Services をインストールする方法について説明します。 Machine Learning Services を使用すると、データベース内で Python および R スクリプトを実行できます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bdd1a9e20379ae66335baa7d3c415cf68e570d47
ms.sourcegitcommit: 2f56848ec422845ee81fb84ed321a716c677aa0e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71271918"
---
# <a name="install-sql-server-machine-learning-services-python-and-r-on-windows"></a>Windows に SQL Server Machine Learning Services (Python および R) をインストールする

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、Windows に SQL Server Machine Learning Services をインストールする方法について説明します。 Machine Learning Services を使用すると、データベース内で Python および R スクリプトを実行できます。

## <a name="bkmk_prereqs"></a>インストール前のチェックリスト

+ R または Python 言語サポートを使用して Machine Learning Services をインストールする場合は、SQL Server 2017 (またはそれ以降) のセットアップが必要です。 SQL Server 2016 のインストールメディアを使用している場合は、 [SQL Server R Services (データベース内)](sql-r-services-windows-install.md)をインストールして、R 言語のサポートを受けることができます。

+ データベースエンジンのインスタンスが必要です。 R または Python の機能だけをインストールすることはできませんが、既存のインスタンスに段階的に追加することはできます。

+ ビジネス継続性のために、Machine Learning Services では[Always On 可用性グループ](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server)がサポートされています。 各ノードに Machine Learning Services をインストールし、パッケージを構成する必要があります。

+ Machine Learning Services のインストールは、SQL Server 2017 のフェールオーバークラスターではサポートされ*ていません*。 ただし、SQL Server 2019 でサポートされ*て*います。 
 
+ Machine Learning Services をドメインコントローラーにインストールしないでください。 セットアップの Machine Learning Services の部分は失敗します。

+ データベース内のインスタンスを実行しているのと同じコンピューターに**共有機能** > **Machine Learning Server (スタンドアロン)** をインストールしないでください。 スタンドアロンサーバーは同じリソースに対して競合し、両方のインストールのパフォーマンスを低下させることになります。

+ 他のバージョンの R および Python とのサイドバイサイドインストールはサポートされていますが、推奨されません。 SQL Server インスタンスは、オープンソースの R および Anaconda ディストリビューションの独自のコピーを使用するため、サポートされています。 ただし、SQL Server 外の SQL Server コンピューターで R および Python を使用するコードを実行すると、さまざまな問題が発生する可能性があるため、お勧めしません。
    
  + SQL Server でを実行しているときとは別のライブラリと実行可能ファイルを使用し、異なる結果を得ることができます。
  + 外部ライブラリで実行されている R および Python スクリプトは、SQL Server で管理できないため、リソースの競合が発生します。
  
> [!IMPORTANT]
> セットアップが完了したら、この記事で説明されている構成後の手順を完了してください。 これらの手順には、外部スクリプトを使用するための SQL Server の有効化と、ユーザーに代わって R ジョブや Python ジョブを実行するために SQL Server に必要なアカウントの追加が含まれます。 通常、構成を変更するには、インスタンスを再起動するか、スタートパッドサービスを再起動する必要があります。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2017 のセットアップウィザードを開始します。 
  
2. **インストール** タブで、**新規 SQL Server スタンドアロンインストールを選択するか、既存のインストールに機能を追加**します。

   ![新しい SQL Server スタンドアロンインストール](media/2017setup-installation-page-mlsvcs.PNG)
   
3. **[機能の選択]** ページで、次のオプションを選択します。
  
    -   **データベース エンジン サービス**
  
         SQL Server で R および Python を使用するには、データベースエンジンのインスタンスをインストールする必要があります。 既定のインスタンスと名前付きインスタンスのどちらを使用してもかまいません。
  
    -   **Machine Learning Services (データベース内)**
  
         このオプションを選択すると、R および Python スクリプトの実行をサポートするデータベースサービスがインストールされます。

    -   **R**

        Microsoft R パッケージ、インタープリター、およびオープンソース R を追加するには、このオプションをオンにします。 

    -   **Python**

        このオプションをオンにすると、Microsoft Python パッケージ、Python 3.5 実行可能ファイル、Anaconda ディストリビューションからライブラリを選択できます。
        
        ![R および Python の機能オプション](media/2017setup-features-page-mls-rpy.png "Python のセットアップオプション")

        > [!NOTE]
        > 
        > **[Machine Learning Server (スタンドアロン)]** のオプションは選択しないでください。 **[共有機能]** の下に Machine Learning Server をインストールするオプションは、別のコンピューターでの使用を目的としています。

4. **[R のインストールに同意する]** ページで、 **[同意]** する を選択します。 このライセンス契約には、microsoft R Open が含まれています。これには、Microsoft 開発チームの拡張 R パッケージと接続プロバイダーと共に、オープンソースの R 基本パッケージとツールの配布が含まれます。

5. [ **Python のインストールに同意**します] ページで、[**同意**する] を選択します。 Python オープンソースライセンス契約には、Anaconda および関連するツールに加えて、Microsoft 開発チームのいくつかの新しい Python ライブラリも含まれています。
     
     ![Python ライセンスに対する契約](media/2017setup-python-license.png "Python の使用許諾契約書")
  
    > [!NOTE]
    >  使用しているコンピューターがインターネットにアクセスできない場合は、この時点でセットアップを一時停止して、インストーラーを個別にダウンロードすることができます。 詳細については、「[インターネットにアクセスせずに machine learning コンポーネントをインストール](../install/sql-ml-component-install-without-internet-access.md)する」を参照してください。
  
     **[Accept]** \ (同意 \) を選択し、 **[次へ]** ボタンがアクティブになるまで待ち、 **[次へ]** を選択します。
  
6. **[インストールの準備完了]** ページで、これらの選択が含まれていることを確認し、 **[インストール]** を選択します。
  
    + データベース エンジン サービス
    + Machine Learning Services (データベース内)
    + R または Python、あるいはその両方

    構成ファイルが格納されているパス`..\Setup Bootstrap\Log`の下にあるフォルダーの場所をメモしておきます。 セットアップが完了したら、概要ファイルにインストールされているコンポーネントを確認できます。

7. セットアップが完了したら、コンピューターを再起動するように指示された場合は、ここで実行します。 セットアップが完了した時点で、インストール ウィザードによるメッセージを確認することが重要です。 詳細については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files)」を参照してください。

## <a name="set-environment-variables"></a>環境変数の設定

R 機能の統合のみの場合、 **MKL_CBWR**環境変数を設定し[て](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr)、Intel MATH Kernel Library (MKL) 計算からの一貫した出力を確保する必要があります。

1. コントロールパネルで、[**システムとセキュリティ** >  > ] [システム] [システム**設定** > ] **[環境変数]** をクリックします。

2. 新しいユーザー変数またはシステム変数を作成します。 

  + 変数名をに設定します`MKL_CBWR`
  + 変数の値をに設定します。`AUTO`

この手順では、サーバーを再起動する必要があります。 スクリプトの実行を有効にする場合は、すべての構成作業が完了するまで再起動を停止できます。

<a name="bkmk_enableFeature"></a>

## <a name="enable-script-execution"></a>スクリプトの実行を有効にする

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 

    > [!TIP]
    > 適切なバージョンは、次のページからダウンロードしてインストールできます。[SQL Server Management Studio (SSMS) をダウンロードしてください](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)。
    > 
    > また、SQL Server に対する管理タスクとクエリをサポートする[Azure Data Studio](../../azure-data-studio/what-is.md)を使用することもできます。
  
2. Machine Learning Services をインストールしたインスタンスに接続し、 **[新しいクエリ]** をクリックしてクエリウィンドウを開き、次のコマンドを実行します。

    ```sql
    sp_configure
    ```

    プロパティ `external scripts enabled` の値は、この時点では **0** であることが必要です。 これは、機能が既定で無効になっているためです。 この機能は、R または Python スクリプトを実行する前に、管理者が明示的に有効にする必要があります。
    
3.  外部スクリプト機能を有効にするには、次のステートメントを実行します。
    
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    R 言語の機能を既に有効にしている場合は、Python の再構成をもう一度実行しないでください。 基になる拡張プラットフォームでは、両方の言語がサポートされています。

## <a name="restart-the-service"></a>サービスを再起動します。

インストールが完了したら、次のスクリプトの実行を有効にする前に、データベースエンジンを再起動します。

サービスを再起動すると、関連[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]するサービスも自動的に再起動されます。

サービスを再起動するには、SSMS でインスタンスの右クリック**restart**コマンドを使用するか、コントロールパネルの **[サービス]** パネルを使用するか、または[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)を使用します。

## <a name="verify-installation"></a>インストールの確認

[カスタムレポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)またはセットアップログで、インスタンスのインストール状態を確認します。

外部スクリプトの起動に使用されるすべてのコンポーネントが実行されていることを確認するには、次の手順に従います。

1. SQL Server Management Studio で、新しいクエリウィンドウを開き、次のコマンドを実行します。
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。
    
2. **[サービス]** パネルまたは SQL Server 構成マネージャーを開き、 **SQL Server Launchpad サービス**が実行されていることを確認します。 R または Python がインストールされているデータベースエンジンインスタンスごとに1つのサービスを用意する必要があります。 サービスの詳細については、「[機能拡張フレームワーク](../concepts/extensibility-framework.md)」を参照してください。 
   
3. スタートパッドが実行されている場合は、単純な R および Python スクリプトを実行して、外部スクリプトランタイムが SQL Server と通信できることを確認できる必要があります。

   で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]新しい**クエリ**ウィンドウを開き、次のようなスクリプトを実行します。
    
    + R の場合
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Python の場合
    
    ```sql
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    **結果**

    スクリプトの実行には、最初に外部スクリプトランタイムが読み込まれるときに少し時間がかかります。 結果は次のようになります。

    | hello |
    |----|
    | 1|

> [!NOTE]
> Python スクリプトで使用される列または見出しは、設計上、返されません。 出力の列名を追加するには、戻り値のデータセットのスキーマを指定する必要があります。 これを行うには、ストアドプロシージャの WITH RESULTS パラメーターを使用して、列に名前を付け、SQL データ型を指定します。
> 
> たとえば、次の行を追加して、任意の列名を生成できます。`WITH RESULT SETS ((Col1 AS int))`

<a name="apply-cu"></a>

## <a name="apply-updates"></a>更新プログラムの適用

最新の累積的な更新プログラムをデータベースエンジンと機械学習コンポーネントの両方に適用することをお勧めします。

インターネットに接続されているデバイスでは、通常、累積更新プログラムは Windows Update によって適用されますが、次の手順を使用して、管理された更新プログラムを適用することもできます。 データベースエンジンの更新プログラムを適用すると、同じインスタンスにインストールしたすべての R または Python 機能の累積更新プログラムがセットアップによって取得されます。 

切断されたサーバーでは、追加の手順が必要です。 詳細については、「[インターネットにアクセスできないコンピューターにインストールする > 累積的な更新プログラムを適用](sql-ml-component-install-without-internet-access.md#apply-cu)する」を参照してください。

1. 既にインストールされているベースラインインスタンスを使用して開始する:SQL Server 2017 の初期リリース

2. 累積更新プログラムの一覧にアクセスします。[SQL Server 2017 の更新プログラム](https://sqlserverupdates.com/sql-server-2017-updates/)

3. 最新の累積的な更新プログラムを選択します。 実行可能ファイルは自動的にダウンロードおよび抽出されます。

4. セットアップを実行します。 ライセンス条項に同意し、[機能の選択] ページで、累積的な更新プログラムが適用されている機能を確認します。 機械学習機能を含む、現在のインスタンスにインストールされているすべての機能が表示されます。 すべての機能を更新するために必要な CAB ファイルがダウンロードされます。

  ![インストールされている機能の概要](media/cumulative-update-feature-selection.png)

5. ウィザードを続行し、R および Python ディストリビューションのライセンス条項に同意します。 

## <a name="additional-configuration"></a>その他の構成

外部スクリプトの検証手順が成功した場合は、SQL Server Management Studio、Visual Studio Code、または T-sql ステートメントをサーバーに送信できるその他のクライアントから R または Python コマンドを実行できます。

コマンドの実行中にエラーが発生した場合は、このセクションの追加の構成手順を確認してください。 場合によっては、サービスまたはデータベースに対して適切な構成を追加する必要があります。

インスタンスレベルでは、追加の構成には次のものが含まれます。

* [SQL Server Machine Learning Services のファイアウォール構成](../../advanced-analytics/security/firewall-configuration.md)
* [追加のネットワークプロトコルを有効にする](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [リモート接続を有効にする](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [SQLRUserGroup のログインを作成する](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)
* ディスク[クォータを管理](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas)して、ディスク領域を消費するタスクを実行する外部スクリプトを回避する

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
Windows の SQL Server 2019 では、分離メカニズムが変更されました。 これは、 **SQLRUserGroup**、ファイアウォール規則、ファイルのアクセス許可、および暗黙の認証に影響します。 詳細については、「 [Machine Learning Services の分離の変更](sql-server-machine-learning-services-2019.md)」を参照してください。
::: moniker-end

<a name="bkmk_configureAccounts"></a> 
<a name="permissions-external-script"></a> 

データベースでは、次の構成の更新が必要になる場合があります。

* [SQL Server するためのアクセス許可をユーザーに付与する Machine Learning Services](../../advanced-analytics/security/user-permission.md)

> [!NOTE]
> 追加の構成が必要かどうかは、SQL Server をインストールしたセキュリティスキーマと、ユーザーがデータベースに接続して外部スクリプトを実行することを期待する方法によって異なります。

## <a name="suggested-optimizations"></a>推奨される最適化

すべての作業が完了したので、機械学習をサポートするようにサーバーを最適化したり、事前トレーニング済みのモデルをインストールしたりすることもできます。

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
### <a name="add-more-worker-accounts"></a>ワーカーアカウントを追加する

多くのユーザーがスクリプトを同時に実行することが予想される場合は、スタートパッドサービスに割り当てられているワーカーアカウントの数を増やすことができます。 詳細については、「 [SQL Server Machine Learning Services のユーザーアカウントプールを変更](../administration/modify-user-account-pool.md)する」を参照してください。
::: moniker-end

### <a name="optimize-the-server-for-script-execution"></a>スクリプトの実行用にサーバーを最適化する

セットアップの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定の設定は、データベースエンジンによってサポートされるさまざまなサービス (抽出、変換、読み込み (ETL) プロセス、レポート、監査、およびなど) について、サーバーのバランスを最適化することを目的としています。データを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するアプリケーション。 そのため、既定の設定では、特にメモリを集中的に使用する操作で、機械学習用のリソースが制限または調整されることがあります。

Machine learning ジョブの優先順位とリソースを適切に設定するには、SQL Server Resource Governor を使用して外部リソースプールを構成することをお勧めします。 また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースエンジンに割り当てられているメモリの量を変更したり、 [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービスで実行されるアカウントの数を増やしたりすることもできます。

- 外部リソースを管理するためのリソースプールを構成するには、「[外部リソースプールの作成](../../t-sql/statements/create-external-resource-pool-transact-sql.md)」を参照してください。
  
- データベース用に予約されているメモリの量を変更するには、「[サーバーメモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)」を参照してください。
  
- で[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]開始できる R アカウントの数を変更するには、「 [machine learning のユーザーアカウントプールを変更](../administration/modify-user-account-pool.md)する」を参照してください。

Standard Edition を使用していて、Resource Governor がない場合は、動的管理ビュー (Dmv) と拡張イベントを使用して、Windows イベント監視を使用してサーバーリソースを管理できます。 詳細については、「 [R services の監視と管理](../r/managing-and-monitoring-r-solutions.md)」と「 [Python サービスの監視と管理](../python/managing-and-monitoring-python-solutions.md)」を参照してください。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールする

SQL Server 用に作成する R ソリューションでは、基本的な R 関数、SQL Server と共にインストールされた独自のパッケージの関数、および SQL Server によってインストールされたオープンソース R のバージョンと互換性のあるサードパーティ製の R パッケージを呼び出すことができます。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターに R が別途インストールされている場合、またはユーザーライブラリにパッケージをインストールした場合は、これらのパッケージを T-sql から使用することはできません。

R パッケージをインストールして管理するには、データベースレベルでパッケージを共有するようにユーザーグループを設定するか、ユーザーが独自のパッケージをインストールできるようにデータベースロールを構成します。 詳細については、「 [SQL Server での新しい R パッケージのインストール](../r/install-additional-r-packages-on-sql-server.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

R 開発者はいくつかの簡単な例を試して、SQL Server での R の動作方法の基本を確認できます。 次の手順については、以下のリンクをご覧ください。

+ [チュートリアル: T-SQL での R の実行](../tutorials/quickstart-r-create-script.md)
+ [チュートリアル: R 開発者向けのデータベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python 開発者は、次のチュートリアルに従って、SQL Server で Python を使用する方法を学習できます。

+ [チュートリアル: T-SQL での Python の実行](../tutorials/run-python-using-t-sql.md)
+ [チュートリアル: Python 開発者向けのデータベース内分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づいた機械学習の例については、[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)を参照してください。
