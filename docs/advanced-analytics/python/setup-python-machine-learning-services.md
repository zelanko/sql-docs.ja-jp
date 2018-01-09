---
title: "Python の Machine Learning のサービスのセットアップと構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/20/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: abc79124569635f3aafaaa309e25e2c827fa5d9b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="set-up-python-machine-learning-services-in-database"></a>Python Machine Learning Services (In-database) を設定します。

  この記事の内容を実行して、Python のために必要なコンポーネントをインストールする方法を説明する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ ウィザード、および対話的なプロンプトに従っています。

## <a name="machine-learning-options-in-sql-server-setup"></a>機械学習の SQL Server セットアップのオプション

選択、 **Machine Learning サービス**機能、および選択**Python**言語として。

**共有機能**セクションには、個別のインストール オプションが含まれています。 **Machine Learning Server (スタンドアロン)**です。 このオプションは、SQL Server がない、または SQL Server の計算コンテキストの使用を要求せず、サーバー上の Python コードの使用をサポートします。 したがって、ことをお勧めする*しない*SQL Server インスタンスと同じコンピューターにインストールします。 代わりに、別のコンピューターに Machine Learning Server (スタンドアロン) をインストールします。

インストールが完了したら、外部実行可能ファイルを使用してスクリプトの実行を許可するインスタンスを再構成します。 Machine learning のワークロードをサポートするためにサーバーにさらに変更する必要があります。 構成の変更は、一般に、インスタンスの再起動またはスタート パッド サービスの再起動が必要です。

### <a name="prerequisites"></a>Prerequisites

+ SQL Server 2017 が必要です。 SQL Server の以前のバージョンでは、Python の統合はサポートされていません。
+ 必ず、データベース エンジンをインストールしてください。 Python スクリプトのデータベースでを実行するには、SQL Server のインスタンスが必要です。
+ 前提条件は、Python コンポーネントのセットアップの一部としてインストールされます。
+ フェールオーバー クラスター上の Python サービス機械学習をインストールすることはできません。 Python のプロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。
   
  この問題を回避するには、Python サービスを使用するスタンドアロン SQL Server インスタンスに必要なテーブルをコピーするのにレプリケーションを使用することができます。 また、Python コンピューターのサービスをスタンドアロンの AlwaysOn 設定を使用していて、可用性グループの一部の機械学習をインストールできます。

+ SQL Server のインスタンスは Anaconda ディストリビューションのコピーを使用するため、Python の他のバージョンとサイド バイ サイド インストールがあります。 ただし、SQL Server の外部の SQL Server コンピューターで Python を使用するコードを実行するは、さまざまな問題につながることができます。
    
    - 別のライブラリと、さまざまな実行可能ファイルを使用して SQL Server で実行しているときよりも、異なる結果を取得します。
    - 外部ライブラリで実行されている Python スクリプトは、先頭のリソースの競合する SQL Server で管理できません。
  
> [!IMPORTANT]
> セットアップが完了したら、必ずこの記事で説明されている追加のインストール後の構成手順を完了してください。 次の手順には、外部のスクリプトを使用する SQL Server を有効にして、あなたに代わって Python ジョブを実行する SQL Server に必要なアカウントを追加することが含まれます。

### <a name="unattended-installation"></a>無人インストール

無人インストールを実行するには、Python に固有の引数および SQL Server セットアップのコマンド ライン オプションを使用します。 詳細については、次を参照してください。 [Python Machine Learning のサービスと SQL server の無人インストール](unattended-installs-of-sql-server-python-services.md)です。

##  <a name="bkmk_installPythonInDatabase"></a>手順 1: 機械学習の SQL Server 上のサービス (In-database) をインストールします。

1. SQL Server 2017 のセットアップ ウィザードを実行します。
  
2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**です。

    ![データベース内に Python をインストールします。](media/2017setup-installation-page-mlsvcs.PNG)
   
3. **[機能の選択]** ページで、次のオプションを選択します。
  
    -   **データベース エンジン サービス**
  
         SQL Server では、Python を使用するには、データベース エンジンのインスタンスをインストールする必要があります。 既定または名前付きインスタンスのいずれかを使用することができます。
  
    -   **機械学習の Services (In-database)**
  
         このオプションは、Python スクリプトの実行をサポートするデータベースのサービスをインストールします。

    -   **Python** Python 3.5 実行可能ファイルを取得し、Anaconda ディストリビューションからライブラリを選択するには、このオプションをオンにします。 インスタンスごとに 1 つの言語をインストールします。
        
        ![Python のためのオプションの機能](media/ml-svcs-features-python-highlight.png "Python のセットアップ オプション")

        > [!NOTE]
        > 
        > オプションを選択しない**Machine Learning Server (スタンドアロン)**です。 Machine Learning のサーバーをインストールするオプション**共有機能**は別のコンピューターに使用するものです。 たとえば、同じバージョンの機械学習データ科学者のラップトップなどのプロジェクトの開発に使用する別のコンピューター上のコンポーネントをインストールすることができます。

4. **Python のインストールに同意する**] ページで、[ **Accept**です。
  
     実行可能ファイルでの Python Anaconda から Python パッケージをダウンロードするには、この使用許諾契約書が必要です。
     
     ![Python のライセンス契約](media/ml-svcs-license-python.png "使用許諾契約書の Python")
  
    > [!NOTE]
    >  使用しているコンピューターがインターネットにアクセスを持たない場合に、個別にインストーラーをダウンロードするには、この時点でセットアップが一時停止できます。 詳細については、次を参照してください。[インターネットにアクセスできないコンポーネントをインストールする](../r/installing-ml-components-without-internet-access.md)です。
  
     選択**Accept**、まで待ってから、**次**ボタンになり、アクティブ、を選択**次へ**です。
  
5. **インストールの準備完了** ページで、これらの選択が含まれていることを確認し、選択**インストール**です。
  
     + データベース エンジン サービス
     + Machine Learning Services (データベース内)
     + Python
  
    これらの選択での Python を使用するために必要な最小構成を表します。[!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]です。
    
    ![Python をインストールする準備が](media/ready-to-install-python.png "Python のインストールに必要なコンポーネント")

    必要に応じて、パスの下のフォルダーの場所を書き留めます`..\Setup Bootstrap\Log`構成ファイルが格納されます。 セットアップが完了したら、概要ファイルにインストールされているコンポーネントを確認することができます。

6. インストールが完了した後、コンピューターを再起動します。

##  <a name="bkmk_enableFeature"></a>手順 2: Python スクリプトの実行を有効にします。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 

    > [!TIP]
    > ダウンロードして、このページから、適切なバージョンをインストールすることができます:[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。
    > 
    > プレビュー リリースのも試すことができます[SQL 操作 Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is)、管理タスクと SQL Server に対してクエリをサポートします。
  
2. Machine Learning のサービスがインストールされているインスタンスに接続し、次のコマンドを実行します。

   ```SQL
   sp_configure
   ```

    プロパティ `external scripts enabled` の値は、この時点では **0** であることが必要です。 この機能が既定でオフにするためです。 機能する必要があります明示的に有効にする管理者によって R または Python スクリプトを実行する前にします。
    
3.  Python をサポートする外部のスクリプト機能を有効にするには、次のステートメントを実行します。
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    実行しない場合は、R 言語の機能を既に有効になっている、Python の 2 番目の時間を再構成します。 基になるの機能拡張のプラットフォームでは、両方の言語をサポートします。

4. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの SQL Server サービスを再起動します。 SQL Server のサービスも自動的に再起動すると、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

    使用してサービスを再起動することができます、 **Services**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)です。

## <a name="step-3-verify-that-the-external-script-execution-feature-is-running"></a>手順 3: は、外部スクリプト実行機能が実行されていることを確認してください。

すぐに Python スクリプトの起動に使用するすべてのコンポーネントが実行されていることを確認してください。

1. SQL Server Management Studio で、新しいクエリ ウィンドウを開き、次のコマンドを実行します。
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。
    
2. 開く、 **Services**パネルまたは SQL Server 構成マネージャー、スタート パッド サービスのインスタンスが実行されていることを確認してください。 スタート パッドが実行されていない場合は、サービスを再起動します。
  
    SQL Server の複数のインスタンスをインストールした場合、R または有効になっている Python を含む任意のインスタンスは、独自のスタート パッド サービスがします。

    R、Python の両方を 1 つのインスタンスをインストールする場合は、1 つだけのスタート パッドはインストールされます。 言語ごとに、個別の言語固有のランチャー DLL が追加されます。 詳細については、次を参照してください。 [Python の統合をサポートするにはコンポーネント](new-components-in-sql-server-to-support-python-integration.md)です。 
   
3. スタート パッドを実行している場合では、次のような単純な Python スクリプトを実行する必要がありますできる[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'OutputDataSet = InputDataSet',
    @input_data_1 = N'SELECT 1 AS col'
    ```
    
    **結果**
    
    *<code>&nbsp;&nbsp;</code>* *1*

> [!NOTE]
> 列または Python スクリプトで使用される見出しでは返されませんをデザインします。 出力の列名を追加するには、戻り値のデータ セットのスキーマを指定する必要があります。 そのため、列の名前付けと SQL データ型を指定することは、ストアド プロシージャの結果にパラメーターを使用します。
> 
> たとえば、任意の列名を生成するのには、次の行を追加できます。`WITH RESULT SETS ((Col1 AS int))`

## <a name="step-4-additional-configuration"></a>手順 4: 追加の構成

前のコマンドが成功した場合は、SQL Server Management Studio、Visual Studio コード、またはサーバーに T-SQL ステートメントを送信できるその他のクライアントから Python コマンドを実行することができます。

コマンドの実行時にエラーを取得した場合は、次の一覧を確認します。 サービスまたはデータベースに、適切な構成を追加する必要があります。

> [!NOTE]
> 
> 表示されているすべての変更が必要であり、必要なし があります。 要件は、SQL Server、およびデータベースに接続し、外部のスクリプトを実行するユーザーを想定する方法をインストールした、セキュリティ スキーマによって異なります。

###  <a name="bkmk_configureAccounts"></a>スタート パッドのアカウントのグループの暗黙の認証を有効にします。

セットアップの間に、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスのセキュリティ トークンの下でタスクを実行するために、新しい Windows ユーザー アカウントが多数作成されます。 ユーザーが、外部クライアントから Python または R スクリプトを送信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用可能なワーカー アカウントをアクティブにします。 呼び出し元のユーザーの id にマップし、ユーザーの代理としてスクリプトを実行します。

これと呼ばれる*黙示的な認証*であり、データベース エンジンのサービスです。 このサービスは、SQL Server 2016 および SQL Server 2017 でセキュリティで保護された外部スクリプト実行をサポートします。

これらのアカウントは、Windows ユーザー グループ **SQLRUserGroup**で見ることができます。 既定では、20 のワーカー アカウントが作成された、外部スクリプトを実行するために十分な数より多くのジョブは通常です。

> [!IMPORTANT]
> Worker グループの名前は**SQLRUserGroup** R または Python をインストールするかどうかに関係なく。 インスタンスごとに 1 つのグループがあります。

リモート データ サイエンス クライアントからスクリプトを実行する必要があるあり、Windows 認証を使用して、追加の考慮事項があります。 これらのワーカー アカウントにサインインするアクセス許可を与える必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あなたの代理としてのインスタンス。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプ ローラーを展開して**セキュリティ**です。 右クリックし、**ログイン**を選択して**新しいログイン**です。
2. **ログイン - 新規**ダイアログ ボックスで、**検索**です。
3. 選択**オブジェクトの種類**を選択して**グループ**です。 他のすべてをクリアします。
4. **を選択するオブジェクト名を入力**、型*SQLRUserGroup*を選択して**名前の確認**です。
5. インスタンスのスタート パッド サービスに関連付けられているローカル グループの名前が、" *インスタンス名\SQLRUserGroup*" などに解決されます。 **[OK]** を選択します。
6. 既定では、グループが割り当てられている、**パブリック**ロール、データベース エンジンに接続するアクセス許可を持つとします。
7. **[OK]** を選択します。

> [!NOTE]
> 使用する場合、 **SQL ログイン**スクリプトを実行して、SQL Server のコンピューティング コンテキストで、この余分な手順は必要ありません。

### <a name="give-users-permission-to-run-external-scripts"></a>ユーザーを外部スクリプトを実行する権限を付与します。

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、自分で実行している Python スクリプト独自のインスタンスで、通常、管理者としてスクリプトを実行します。 したがって、さまざまな操作と、データベース内のすべてのデータを暗黙のアクセス許可があります。

ただし、ほとんどのユーザーにはこのような高度な権限はありません。 たとえば、組織内の SQL ログインを使用して、一般に、データベースにアクセスするユーザーには、高度な権限はありません。 したがって、Python を使用しているユーザーごとにする必要があります権限を付与 Machine Learning のサービスのユーザー Python が使用されている各データベースで外部のスクリプトを実行します。 ここでは、どのようにします。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> 権限は、サポートされているスクリプト言語に固有ではありません。 つまり、R スクリプトのスクリプトと Python スクリプトの別のアクセス許可レベルがありません。 これらの言語の個別のアクセス許可を維持する必要がある場合は、別々 のインスタンスに R、Python をインストールします。

### <a name="give-your-users-read-write-or-data-definition-language-ddl-permissions-to-databases"></a>ユーザー、読み取り、書き込み、またはデータ定義のデータベースへの言語 (DDL) のアクセス許可を付与します。

ユーザーがスクリプトを実行中に、ユーザーは、他のデータベースからデータを読み取る必要があります。 ユーザーは、結果を格納およびデータ テーブルに書き込むために新しいテーブルを作成する必要もあります。

Windows ユーザー アカウントまたは R または Python スクリプトを実行している SQL ログインごとに、特定のデータベースに適切なアクセス許可があることを確認してください: `db_datareader`、 `db_datawriter`、または`db_ddladmin`です。

たとえば、次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、SQL ログイン*MySQLLogin*で T-SQL クエリを実行する権限、 *ML_Samples*データベース。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

各ロールに含まれる権限の詳細については、次を参照してください。[データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)です。

### <a name="ensure-that-the-sql-server-installation-supports-remote-connections"></a>SQL Server のインストールがリモート接続をサポートしていることを確認してください。

リモート コンピューターから接続できない場合、ファイアウォールが SQL Server へのアクセスを許可するかどうかを確認してください。 既定のインストールでは、リモート接続を無効にすることがあります、または SQL Server で使用される特定のポートがファイアウォールによってブロックされる可能性があります。 詳細については、次を参照してください。[データベース エンジン アクセス用に Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)です。

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>データ サイエンス クライアント上のインスタンス用の ODBC データ ソースを作成する

機械学習データ サイエンス クライアント コンピューターでソリューションを作成する場合があります。 2 つのオプションがある場合は、計算コンテキストとして、SQL Server コンピューターを使用してコードを実行する必要があります。 SQL ログインを使用して、インスタンスへのアクセスや、Windows を使用してアカウント。

+ SQL ログインの: ログインがデータを読み取り、データベースで適切なアクセス許可を持っていることを確認します。 追加することでこれを行う*への接続*と*選択*権限、またはへのログインを追加することによって、`db_datareader`ロール。 オブジェクトを作成するには、割り当てる`DDL_admin`権限です。 テーブルにデータを保存する必要がある場合に追加、`db_datawriter`ロール。

+ Windows 認証: インスタンス名とその他の接続情報を指定するデータ サイエンス クライアントで ODBC データ ソースを作成する必要があります。 詳細については、次を参照してください。 [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)です。

## <a name="additional-optimizations"></a>さらに最適化

すべての作業がある場合、これでは、機械学習をサポートするためにサーバーを最適化することもまたはインストールには、モデルが事前トレーニング済みです。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

スクリプトを同時に実行される多くのユーザーの場合、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server の Machine Learning のサービスのユーザー アカウント プールを変更する](../r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

### <a name="optimize-the-server-for-script-execution"></a>スクリプトの実行用のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップがサービスのさまざまなサーバーの分散を最適化します。 これらのサービスには、ETL プロセス、レポート、監査、および使用するアプリケーションが含まれます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。

既定の設定を使用する場合の外部スクリプトの実行リソースが制限またはスロットルで調整、メモリを消費する操作で特にことがあります。 機械学習に優先順位がある場合は、外部スクリプトのジョブが優先順位を付けるし、適切なリソースを確実既定のデータベース設定を変更します。 これらの変更を含めることができます。

+ 割り当てられたメモリの量を減らす、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン。
+ 実行アカウントの数を増やし、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。 これは、リソースの数が増加せずが同時に実行できるスクリプトの数が増加します。

SQL Server Enterprise Edition を使用する場合は、Python の外部リソース プールを構成するリソース ガバナーを使用します。 詳細については、次の各資料を参照してください。

-   外部リソースの管理用にリソース プールを構成します
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)
  
-   データベース エンジン用に予約されるメモリの量を変更します
  
     [サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)
  
-   によって開始可能ワーカー アカウントの数を変更します。[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]
  
     [SQL Server R Services のユーザー アカウント プールを変更します。](../r/modify-the-user-account-pool-for-sql-server-r-services.md)

SQL Server Standard Edition を使用しており、リソース ガバナーを持っていない場合は、サーバーのリソースを管理するための動的管理ビュー、および拡張イベントを使用できます。 また、この目的では、Windows イベントの監視を使用することができます。 詳細については、次を参照してください。[監視と R サービスを管理する](../r/managing-and-monitoring-r-solutions.md)です。

### <a name="upgrade-the-machine-learning-components"></a>コンピューターをアップグレードするコンポーネントの学習

SQL Server 2017 を使用して、マシン学習サービスをインストールするときに、リリースの公開時に、コンポーネントのバージョンを取得します。 修正プログラムを適用するか、SQL Server インスタンスをアップグレードするたびに、マシン学習コンポーネントは、アップグレードもします。

機械学習はサポートされているよりも高速なスケジュールでコンポーネントをアップグレードする Microsoft Machine Learning のサーバーをインストールすることによって、SQL Server のリリースでします。 これを行うときに取得することもなどの Machine Learning のサーバーの最新のリリースでサポートされている新しい機能。

+ 更新プログラム用 Python パッケージを[revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)と[for Python microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)です。
+ [モデルを事前トレーニング済み](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)イメージの分類とテキストの分析のためです。

インスタンスをアップグレードする方法については、次を参照してください。[バインディングからのアップグレードの R コンポーネント](..\r\use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

### <a name="tutorials"></a>チュートリアル

ビルドし、マシン学習ソリューションの配置を SQL Server で Python を使用する方法の例については、以下のチュートリアルを参照してください。

[T-SQL で Python を使用します。](../tutorials/run-python-using-t-sql.md)

[Python を revoscalepy を使用してモデルを作成します。](../tutorials/use-python-revoscalepy-to-create-model.md)
