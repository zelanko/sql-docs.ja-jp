---
title: インストール SQL Server Machine Learning サービス (In-database) Windows - SQL Server で機械学習
description: SQL Server または Windows の SQL Server 2017 Machine Learning Services の SQL Server インストールの手順での Python での R です。
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4cd076ae79db7537235aa2a57fe4992ac0993473
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510809"
---
# <a name="install-sql-server-machine-learning-services-on-windows"></a>SQL Server Machine Learning では、Windows サービスをインストールします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 以降、R と Python のサポートで、データベース内分析が提供されます**SQL Server Machine Learning Services**、後継[SQL Server R Services](../r/sql-server-r-services.md) SQL Server 2016 で導入されました。 関数ライブラリは、R と Python で使用可能なし、データベース エンジンのインスタンス上の外部スクリプトとして実行します。 

この記事を実行して、machine learning コンポーネントをインストールする方法を説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ ウィザード、および次の画面に表示されます。

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

+ SQL Server 2017 (またはそれ以上) のセットアップは、R、Python、または Java 言語のサポートと Machine Learning サービスをインストールする場合に必要です。 インストールすることができる場合、代わりに SQL Server 2016 のインストール メディアがある、 [SQL Server 2016 R Services (In-database)](sql-r-services-windows-install.md) R 言語サポートを取得します。

+ データベース エンジンのインスタンスが必要です。 機能をインストールするだけ R または Python を既存のインスタンスに増分の追加にできます。

+ ビジネス継続性の[Always On 可用性グループ](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server)Machine Learning サービスはサポートされています。 Machine Learning のサービスをインストールし、各ノードで、パッケージを構成する必要があります。

+ Machine Learning サービスのインストールは*はサポートされていません*で SQL Server 2017 フェールオーバー クラスターにします。 ただし、その*はサポートされて*SQL Server 2019 とします。 
 
+ ドメイン コント ローラーで Machine Learning サービスをインストールできません。 セットアップの Machine Learning サービスの部分は失敗します。

+ インストールしない**共有機能** > **Machine Learning Server (スタンドアロン)** 同じコンピューター上の in-database インスタンスを実行します。 スタンドアロン サーバーは、同じリソースを両方のインストールのパフォーマンスを弱体化の競合が発生します。

+ R と Python の他のバージョンとサイド バイ サイドでインストールがサポートされていますが、推奨されません。 SQL Server インスタンスは、独自のコピーのオープン ソース R および Anaconda ディストリビューションを使用するためサポートされます。 さまざまな問題となる SQL Server の外部の SQL Server コンピューターで R と Python を使用するコードを実行している可能性があるためにお勧めしません。
    
  + 別のライブラリと、さまざまな実行可能ファイルを使用して SQL Server で実行するときよりも、異なる結果を取得します。
  + リソースの競合をリードする、SQL Server が外部ライブラリで実行されている R と Python スクリプトを管理することはできません。
  
> [!IMPORTANT]
> セットアップが完了したら、必ずこの記事で説明する構成後の手順を完了してください。 この手順では、外部スクリプトを使用する SQL Server を有効にして、あなたに代わって R と Python のジョブを実行する SQL Server に必要なアカウントを追加します。 構成の変更は、一般に、インスタンスの再起動またはスタート パッド サービスの再起動が必要です。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2017 のセットアップ ウィザードを起動します。 ダウンロードすることができます。 
  
2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**します。

   ![SQL Server の新規スタンドアロン インストール](media/2017setup-installation-page-mlsvcs.PNG)
   
3. **[機能の選択]** ページで、次のオプションを選択します。
  
    -   **データベース エンジン サービス**
  
         SQL Server で R と Python を使用するには、データベース エンジンのインスタンスをインストールする必要があります。 既定値または名前付きインスタンスのいずれかを使用することができます。
  
    -   **Machine Learning Services (データベース内)**
  
         このオプションは、R をサポートするデータベース サービスをインストールし、Python スクリプトの実行します。

    -   **R**

        Microsoft R パッケージ、インタープリター、およびオープン ソース R. を追加するには、このオプションを確認してください。 

    -   **Python**

        Microsoft Python パッケージ、Python 3.5 の実行可能ファイルを追加するには、このオプションをオンにし、Anaconda ディストリビューションからライブラリを選択します。
        
        ![R と Python のオプションの機能](media/2017setup-features-page-mls-rpy.png "Python のセットアップ オプション")

        > [!NOTE]
        > 
        > オプションを選択しない**Machine Learning Server (スタンドアロン)** します。 Machine Learning Server をインストールするオプション**共有機能**もので、別のコンピューターに使用します。

4. **R のインストールに同意する**] ページで、[ **Accept**します。 この使用許諾契約書では、オープン ソース R 基本パッケージとツール、拡張 R パッケージおよび接続プロバイダー、Microsoft 開発チームからのディストリビューションが含まれる Microsoft R Open、について説明します。

5. **Python のインストールに同意する**] ページで、[ **Accept**します。 Python のオープン ソース ライセンス契約には、Anaconda と関連ツール、および Microsoft 開発チームからのいくつかの新しい Python ライブラリも含まれます。
     
     ![Python のライセンス契約](media/2017setup-python-license.png "使用許諾契約書 for Python")
  
    > [!NOTE]
    >  使用しているコンピューターがインターネットへのアクセスを持たない場合に、個別にインストーラーをダウンロードするには、この時点でのセットアップが一時停止できます。 詳細については、[インターネットへのアクセスなしで machine learning コンポーネントをインストール](../install/sql-ml-component-install-without-internet-access.md)を参照してください。
  
     選択**Accept**、まで、 **[次へ]** ボタンがアクティブ、順に選択します **[次へ]** します。
  
6. **インストールの準備完了** ページで、これらの選択が含まれていることを確認し、選択**インストール**します。
  
    + データベース エンジン サービス
    + Machine Learning Services (データベース内)
    + R、Python、またはその両方

    パスの下のフォルダーの場所をメモして`..\Setup Bootstrap\Log`構成ファイルが格納されます。 セットアップが完了したら、概要ファイルにインストールされているコンポーネントを確認できます。

7. セットアップが完了したら、コンピューターを再起動するように指示される場合ようになりました。 セットアップが完了した時点で、インストール ウィザードによるメッセージを確認することが重要です。 詳細については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files)」を参照してください。

## <a name="set-environment-variables"></a>環境変数な設定

R の機能統合のみに設定する必要があります、 **MKL_CBWR**環境変数を[出力を一貫性のある](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr)Intel 数値演算ライブラリ (MKL) 計算から。

1. コントロール パネルで、次のようにクリックします**システムとセキュリティ** > **システム** > **システムの詳細設定** >   **。環境変数**します。

2. 新しいユーザーまたはシステム変数を作成します。 

  + セットを変数名を指定 `MKL_CBWR`
  + 変数の値に設定します。 `AUTO`

この手順では、サーバーを再起動する必要があります。 スクリプトの実行を有効にしようとする場合は、すべての構成作業が完了するまでは、再起動時に留保することができます。

<a name="bkmk_enableFeature"></a>

## <a name="enable-script-execution"></a>スクリプトの実行を有効にします。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 

    > [!TIP]
    > ダウンロードして、このページから、適切なバージョンをインストールすることができます。[SQL Server Management Studio (SSMS) をダウンロードしてください](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)。
    > 
    > プレビュー リリースを試すこともできます[Azure Data Studio](../../azure-data-studio/what-is.md)、管理タスクと SQL Server に対してクエリをサポートします。
  
2. Machine Learning サービスがインストールされているインスタンスに接続し、をクリックして**新しいクエリ**クエリ ウィンドウを開いて、次のコマンドを実行します。

   ```sql
   sp_configure
   ```

    プロパティ `external scripts enabled` の値は、この時点では **0** であることが必要です。 この機能が既定でオフにするためです。 機能する必要があります明示的に有効にする管理者によって R または Python スクリプトを実行する前にします。
    
3.  外部のスクリプト機能を有効にするには、次のステートメントを実行します。
    
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    R 言語の機能が既に有効な場合は実行しないでください Python の 2 番目の時間を再構成します。 基になる拡張機能プラットフォームには、両方の言語がサポートしています。

## <a name="restart-the-service"></a>サービスを再起動します。

インストールが完了したら、スクリプトの実行を有効にすると、次に進む前に、データベース エンジンを再起動します。

関連するサービスを再起動しても自動的に再起動[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

右クリックを使用してサービスを再起動する**再起動**コマンドを使用してまたは SSMS では、インスタンスを**サービス**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>インストールの確認

インスタンスのインストール状態を確認[カスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)またはログをセットアップします。

次の手順を使用すると、外部スクリプトを起動するのにために使用するすべてのコンポーネントが実行されていることを確認できます。

1. SQL Server Management studio で新しいクエリ ウィンドウを開き、次のコマンドを実行します。
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。
    
2. 開く、**サービス**パネルまたは SQL Server 構成マネージャー、ことを確認および**SQL Server スタート パッド サービス**が実行されています。 R がデータベース エンジンのインスタンスごとに 1 つのサービスが必要または Python をインストールします。 サービスの詳細については、[Extensibility framework](../concepts/extensibility-framework.md)を参照してください。 
   
3. スタート パッドが実行されている場合は、外部スクリプトのランタイムは、SQL Server と通信できることを確認する単純な R と Python のスクリプトを実行できる必要があります。

   新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、次のようなスクリプトを実行します。
    
    + R 用
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Python 用
    
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

    を初めて実行する、外部スクリプトのランタイムが読み込まれるとき、スクリプトは少しことができます。 結果は、次のようになります。

    | hello |
    |----|
    | 1|


<!--  The preceding 'hello' table is NOT rendering properly on live Docs.
Instead, the RAW markdown for the table is being displayed.  Probable bug in this markdown source,
due to stricter rules imposed by 'markdig' engine (replaced 'DFM').
I will inform HeidiSteen  [GeneMi, 2019/01/17]
-->


> [!NOTE]
> 列または Python スクリプトで使用されている見出しでは返されません、設計します。 出力の列名を追加するには、戻り値のデータ セットのスキーマを指定する必要があります。 そのため、列の名前を付けると、SQL データ型を指定することは、ストアド プロシージャの結果でパラメーターを使用します。
> 
> たとえば、任意の列名を生成するには、次の行を追加できます。 `WITH RESULT SETS ((Col1 AS int))`

<a name="apply-cu"></a>

## <a name="apply-updates"></a>更新プログラムを適用します。

データベース エンジンと machine learning のコンポーネントの両方に、最新の累積的な更新プログラムを適用することをお勧めします。

インターネットに接続されたデバイスは、累積的更新プログラムは、Windows update では、一般的に適用されますが、制御された更新プログラムの次の手順を使用することもできます。 データベース エンジンの更新プログラムを適用すると、セットアップは、同じインスタンスにインストールされている R または Python の機能の累積的更新プログラムを取得します。 

切断されたサーバーは、追加の手順が必要です。 詳細については、[インターネット アクセスなしでコンピューターにインストール > の累積更新プログラムを適用](sql-ml-component-install-without-internet-access.md#apply-cu)を参照してください。

1. 既にインストールされているベースライン インスタンスで開始します。SQL Server 2017 の最初のリリース

2. 累積更新プログラムの一覧を参照してください。[SQL Server 2017 更新プログラム](https://sqlserverupdates.com/sql-server-2017-updates/)

3. 最新の累積的な更新プログラムを選択します。 実行可能ファイルがダウンロードされ、自動的に抽出します。

4. セットアップを実行します。 ライセンス条項に同意し、[機能の選択] ページで、累積的更新プログラムの適用対象の機能を確認します。 Machine learning の機能を含む、現在のインスタンスのインストールされているすべての機能が表示されます。 セットアップでは、すべての機能を更新するために必要な CAB ファイルをダウンロードします。

  ![インストールされている機能の概要](media/cumulative-update-feature-selection.png)

5. R と Python のディストリビューションのライセンス条項を使用して、ウィザードの手順を続行します。 

## <a name="additional-configuration"></a>その他の構成

外部スクリプトの検証手順が成功した場合は、SQL Server Management Studio、Visual Studio Code、または T-SQL ステートメントをサーバーに送信できるその他のクライアントから R または Python のコマンドを実行することができます。

コマンドの実行時にエラーを取得した場合は、このセクションでは追加の構成手順を確認します。 サービスまたはデータベースに追加の適切な構成を作成する必要があります。

インスタンス レベルでは、追加の構成が含まれます。

* [SQL Server Machine Learning サービスのファイアウォールの構成](../../advanced-analytics/security/firewall-configuration.md)
* [その他のネットワーク プロトコルを有効にします。](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [リモート接続を有効にします。](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [SQLRUserGroup のログインを作成します。](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

<a name="bkmk_configureAccounts"></a> 
<a name="permissions-external-script"></a> 

データベースでは、次の構成の更新する必要があります。

* [SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与します。](../../advanced-analytics/security/user-permission.md)

> [!NOTE]
> 追加の構成が必要かどうかは、SQL Server、およびユーザーがデータベースに接続し、外部スクリプトの実行が予想される方法をインストールした、セキュリティ スキーマに依存します。

## <a name="suggested-optimizations"></a>提案されている最適化

、Machine learning をサポートするためにサーバーを最適化することもできたすべてを動作、または事前トレーニング済みモデルをインストールします。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

多くのユーザーがスクリプトを同時に実行される場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、[SQL Server Machine Learning Services のユーザー アカウント プールを変更](../administration/modify-user-account-pool.md)を参照してください。

### <a name="optimize-the-server-for-script-execution"></a>スクリプトの実行のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、データベース エンジンは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査を含めることがでサポートされているサービスのさまざまなサーバーのバランスを最適化するためのものと使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 そのため、既定の設定で、機械学習用リソースの場合もありますが制限または抑制され、メモリを消費する操作で特にを見つける可能性があります。

Machine learning ジョブは優先順位を設定しを適切にリソースを確認するには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更したい場合がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するを参照してください。[外部リソース プールの作成](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約済みメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)します。
  
- によって開始できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[machine learning のユーザー アカウント プールを変更する](../administration/modify-user-account-pool.md)します。

Standard Edition を使用している、リソース ガバナーがない場合は、動的管理ビュー (Dmv) は、拡張イベントと監視サーバーのリソースを管理するために、Windows イベントを使用することができます。 詳細については、[の監視と R Services を管理](../r/managing-and-monitoring-r-solutions.md)と[監視と Python のサービスを管理する](../python/managing-and-monitoring-python-solutions.md)を参照してください。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

R ソリューションを SQL Server を作成する基本的な R 関数、SQL Server と共にインストールされている独自のパッケージと R パッケージのサード パーティからの関数は SQL Server がインストールされているオープン ソース R のバージョンと互換性のある呼び出すことができます。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールがある場合、またはユーザー ライブラリにパッケージをインストールした場合は、T-SQL からそれらのパッケージを使用することはできません。

インストールして、R パッケージを管理するためのプロセスでは、SQL Server 2016 および SQL Server 2017 で異なります。 SQL Server 2016 では、データベース管理者は、ユーザーが必要な R パッケージをインストールする必要があります。 SQL Server 2017 では、データベースごとのレベルでパッケージを共有するユーザー グループを設定するか、または独自のパッケージをインストールするユーザーを有効にするデータベース ロールを構成します。 詳細については、[SQL サーバーに新しい R パッケージをインストールする](../r/install-additional-r-packages-on-sql-server.md)を参照してください。


## <a name="next-steps"></a>次のステップ

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: T-SQL での R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [チュートリアル: R の開発者向けのデータベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python の開発者は、これらのチュートリアルに従って、SQL Server で Python を使用する方法を学ぶことができます。

+ [チュートリアル: T-SQL での Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [チュートリアル: Python 開発者向けのデータベース内分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../tutorials/machine-learning-services-tutorials.md)します。
