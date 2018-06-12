---
title: Windows サービス (In-database) を学習の SQL Server 2017 マシンのインストール |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 23fed22efe90a91905c4b36c967ad5fa72717b3f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585874"
---
# <a name="install-sql-server-2017-machine-learning-services-in-database-on-windows"></a>Windows サービス (In-database) を学習の SQL Server 2017 マシンをインストールします。 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server の Machine Learning サービス コンポーネントは、データベース内の予測分析、統計的分析、視覚化、および機械学習アルゴリズムを追加します。 関数ライブラリは R および Python で使用可能であり、データベース エンジンのインスタンスで外部のスクリプトとして実行します。 

この記事を実行して、マシン学習コンポーネントをインストールする方法を説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ ウィザード、および次の画面に表示されます。

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

+ SQL Server 2017 セットアップは、R、Python、またはその両方の言語サポートの Machine Learning のサービスをインストールする場合に必要です。 代わりに SQL Server 2016 インストール メディアがあるを場合は、インストール[SQL Server 2016 R Services (In-database)](sql-r-services-windows-install.md) R 言語のサポートを取得します。

+ データベース エンジンのインスタンスが必要です。 R だけをインストールすることはできません Python 機能がありますが追加することもできますに増分既存のインスタンスにします。

+ フェールオーバー クラスターでは、Machine Learning のサービスをインストールしません。 R、Python のプロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。

+ ドメイン コント ローラーでは、Machine Learning のサービスを取り付けないでください。 セットアップの Machine Learning サービス部分は失敗します。

+ インストールしない**共有機能** > **Machine Learning Server (スタンドアロン)** 同じコンピューターにデータベースのインスタンスを実行します。 スタンドアロン サーバーは、同じリソースを両方のインストールのパフォーマンスを弱体化の競合が発生します。

+ R、Python の他のバージョンとサイド バイ サイド インストールはサポートが、推奨されません。 SQL Server インスタンスは、オープン ソース R および Anaconda ディストリビューションのコピーを使用するためサポートされます。 SQL Server の外部の SQL Server コンピューターの R、Python を使用するコードを実行しているがさまざまな問題につながるためにお勧めしません。
    
  + 別のライブラリと、さまざまな実行可能ファイルを使用して SQL Server で実行しているときよりも、異なる結果を取得します。
  + 外部ライブラリで実行される R と Python スクリプトは、先頭のリソースの競合する SQL Server で管理できません。
  
> [!IMPORTANT]
> セットアップが完了したら、必ずこの記事で説明されているインストール後の構成手順を完了してください。 次の手順には、外部のスクリプトを使用する SQL Server を有効にして、あなたに代わって R、Python のジョブを実行する SQL Server に必要なアカウントを追加することが含まれます。 構成の変更は、一般に、インスタンスの再起動またはスタート パッド サービスの再起動が必要です。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>セットアップの実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2017 のセットアップ ウィザードを起動します。 ダウンロードすることができます。 
  
2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**です。

   ![機械学習のデータベース内にサービスをインストールします。](media/2017setup-installation-page-mlsvcs.PNG)
   
3. **[機能の選択]** ページで、次のオプションを選択します。
  
    -   **データベース エンジン サービス**
  
         SQL Server で R、Python を使用するには、データベース エンジンのインスタンスをインストールする必要があります。 既定または名前付きインスタンスのいずれかを使用することができます。
  
    -   **Machine Learning Services (データベース内)**
  
         このオプションは、R をサポートするデータベースのサービスをインストールし、Python スクリプトの実行します。

    -   **R**

        Microsoft R パッケージ、インタープリター、およびオープン ソース r です。 追加するには、このオプションを確認します。 

    -   **Python**

        Microsoft Python パッケージ、Python 3.5 の実行可能ファイルを追加するには、このオプションをオンにし、Anaconda ディストリビューションからライブラリを選択します。
        
        ![機能の R、Python オプション](media/2017setup-features-page-mls-rpy.png "Python のセットアップ オプション")

        > [!NOTE]
        > 
        > オプションを選択しない**Machine Learning Server (スタンドアロン)** です。 Machine Learning のサーバーをインストールするオプション**共有機能**は別のコンピューターに使用するものです。

4. **R のインストールに同意する**] ページで、[ **Accept**です。 この使用許諾契約書は、オープン ソース R 基本パッケージとツール、拡張 R パッケージおよび接続プロバイダー、Microsoft 開発チームからのディストリビューションが含まれる Microsoft R Open、について説明します。

5. **Python のインストールに同意する**] ページで、[ **Accept**です。 Python のオープン ソース ライセンス契約は、Anaconda と関連するツール、および Microsoft 開発チームの一部の新しい Python ライブラリにも説明します。
     
     ![Python のライセンス契約](media/2017setup-python-license.png "使用許諾契約書の Python")
  
    > [!NOTE]
    >  使用しているコンピューターがインターネットにアクセスを持たない場合に、個別にインストーラーをダウンロードするには、この時点でセットアップが一時停止できます。 詳細については、次を参照してください。[インターネットにアクセスできないマシン ラーニング コンポーネントをインストール](../install/sql-ml-component-install-without-internet-access.md)です。
  
     選択**Accept**、まで待ってから、**次**ボタンになり、アクティブ、を選択**次へ**です。
  
6. **インストールの準備完了** ページで、これらの選択が含まれていることを確認し、選択**インストール**です。
  
    + データベース エンジン サービス
    + Machine Learning Services (データベース内)
    + R、Python、またはその両方

    パスの下のフォルダーの場所をメモして`..\Setup Bootstrap\Log`構成ファイルが格納されます。 セットアップが完了したら、概要ファイルにインストールされているコンポーネントを確認することができます。

## <a name="restart-the-service"></a>サービスを再起動します。

インストールが完了したら、スクリプトの実行を有効にすると、次に進む前に、データベース エンジンを再起動します。

表記も自動的に再起動すると、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

右クリックを使用してサービスを再起動することができます**再起動**SSMS で、またはを使用して、インスタンスのコマンド、 **Services**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md).

## <a name="bkmk_enableFeature"></a>外部スクリプトの実行を有効にします。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 

    > [!TIP]
    > ダウンロードして、このページから、適切なバージョンをインストールすることができます:[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。
    > 
    > プレビュー リリースのも試すことができます[SQL Operations Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is)、管理タスクと SQL Server に対してクエリをサポートします。
  
2. Machine Learning のサービスがインストールされているインスタンスに接続し、をクリックして**新しいクエリ**をクエリ ウィンドウを開き、次のコマンドを実行します。

   ```SQL
   sp_configure
   ```

    プロパティ `external scripts enabled` の値は、この時点では **0** であることが必要です。 この機能が既定でオフにするためです。 機能する必要があります明示的に有効にする管理者によって R または Python スクリプトを実行する前にします。
    
3.  外部のスクリプト機能を有効にするには、次のステートメントを実行します。
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    実行しない場合は、R 言語の機能を既に有効になっている、Python の 2 番目の時間を再構成します。 基になるの機能拡張のプラットフォームでは、両方の言語をサポートします。

4. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの SQL Server サービスを再起動します。 SQL Server のサービスも自動的に再起動すると、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

    右クリックを使用してサービスを再起動することができます**再起動**SSMS で、またはを使用して、インスタンスのコマンド、 **Services**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>インストールの確認

外部スクリプトの起動に使用するすべてのコンポーネントが実行されていることを確認するのにには、次の手順を使用します。

1. SQL Server Management Studio で、新しいクエリ ウィンドウを開き、次のコマンドを実行します。
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。
    
2. 開く、 **Services**パネルまたは SQL Server 構成マネージャー、ことを確認し、 **SQL Server スタート パッド サービス**が実行されています。 R をデータベース エンジンのインスタンスごとに 1 つのサービスが必要、または Python をインストールします。 実行されていない場合は、サービスを再起動します。 詳細については、次を参照してください。 [Python の統合をサポートするにはコンポーネント](../python/new-components-in-sql-server-to-support-python-integration.md)です。 
   
3. スタート パッドを実行している場合は、外部スクリプトのランタイムは、SQL Server と通信できることを確認する簡単な R と Python スクリプトを実行することができます。

   新しく開きます**クエリ**ウィンドウに[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、次のようスクリプトを実行します。
    
    + R の
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Python の
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

 **結果**

    スクリプトは、外部スクリプトの実行時の読み込みを初めて実行するときは少しことができます。 結果は、次のようにする必要があります。

    | hello |
    |----|
    | @shouldalert|


> [!NOTE]
> 列または Python スクリプトで使用される見出しでは返されませんをデザインします。 出力の列名を追加するには、戻り値のデータ セットのスキーマを指定する必要があります。 そのため、列の名前付けと SQL データ型を指定することは、ストアド プロシージャの結果にパラメーターを使用します。
> 
> たとえば、任意の列名を生成するのには、次の行を追加できます。 `WITH RESULT SETS ((Col1 AS int))`

## <a name="additional-configuration"></a>その他の構成

外部スクリプトの検証手順が成功した場合は、SQL Server Management Studio、Visual Studio コード、またはサーバーに T-SQL ステートメントを送信できるその他のクライアントから Python コマンドを実行することができます。

コマンドの実行時にエラーを取得した場合は、このセクションで追加の構成手順を確認します。 サービスまたはデータベースに、適切な構成を追加する必要があります。

追加の変更を必要とする一般的なシナリオは次のとおりです。

* [着信接続用に Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [追加のネットワーク プロトコルを有効にします。](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [リモート接続を有効にします。](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [リモート ユーザーに組み込みの権限を拡張します。](#bkmk_configureAccounts)
* [外部スクリプトを実行するアクセス許可を付与します。](#permissions-external-script)
* [個々 のデータベースにアクセスを許可](#permissions-db)

> [!NOTE]
> 表示されているすべての変更が必要であり、必要なし があります。 要件は、SQL Server、およびデータベースに接続し、外部のスクリプトを実行するユーザーを想定する方法をインストールした、セキュリティ スキーマによって異なります。 追加のトラブルシューティングのヒントをご覧ください:[アップグレードとインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)

###  <a name="bkmk_configureAccounts"></a> スタート パッドのアカウントのグループの暗黙の認証を有効にします。

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

### <a name="permissions-external-script"></a> ユーザーを外部スクリプトを実行する権限を付与します。

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、自分で実行している R または Python スクリプト独自のインスタンスで、通常、管理者としてスクリプトを実行します。 したがって、さまざまな操作と、データベース内のすべてのデータを暗黙のアクセス許可があります。

ただし、ほとんどのユーザーにはこのような高度な権限はありません。 たとえば、組織内の SQL ログインを使用して、一般に、データベースにアクセスするユーザーには、高度な権限はありません。 そのため、R、または Python を使用しているユーザーごとにする必要があります権限を付与 Machine Learning のサービスのユーザー言語が使用されている各データベースで外部のスクリプトを実行します。 ここでは、どのようにします。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> 権限は、サポートされているスクリプト言語に固有ではありません。 つまり、R スクリプトのスクリプトと Python スクリプトの別のアクセス許可レベルがありません。 これらの言語の個別のアクセス許可を維持する必要がある場合は、別々 のインスタンスに R、Python をインストールします。

### <a name="permissions-db"></a> ユーザー、読み取り、書き込み、またはデータ定義のデータベースへの言語 (DDL) のアクセス許可を付与します。

ユーザーがスクリプトを実行中に、ユーザーは、他のデータベースからデータを読み取る必要があります。 ユーザーは、結果を格納およびデータ テーブルに書き込むために新しいテーブルを作成する必要もあります。

Windows ユーザー アカウントまたは R または Python スクリプトを実行している SQL ログインごとに、特定のデータベースに適切なアクセス許可があることを確認してください: `db_datareader`、 `db_datawriter`、または`db_ddladmin`です。

たとえば、次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは、SQL ログイン*MySQLLogin*で T-SQL クエリを実行する権限、 *ML_Samples*データベース。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

各ロールに含まれる権限の詳細については、次を参照してください。[データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)です。


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>データ サイエンス クライアント上のインスタンス用の ODBC データ ソースを作成する

機械学習データ サイエンス クライアント コンピューターでソリューションを作成する場合があります。 2 つのオプションがある場合は、計算コンテキストとして、SQL Server コンピューターを使用してコードを実行する必要があります。 SQL ログインを使用して、インスタンスへのアクセスや、Windows を使用してアカウント。

+ SQL ログインの: ログインがデータを読み取り、データベースで適切なアクセス許可を持っていることを確認します。 追加することでこれを行う*への接続*と*選択*権限、またはへのログインを追加することによって、`db_datareader`ロール。 オブジェクトを作成するには、割り当てる`DDL_admin`権限です。 テーブルにデータを保存する必要がある場合に追加、`db_datawriter`ロール。

+ Windows 認証: インスタンス名とその他の接続情報を指定するデータ サイエンス クライアントで ODBC データ ソースを作成する必要があります。 詳細については、次を参照してください。 [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)です。

## <a name="suggested-optimizations"></a>推奨される最適化

すべての作業がある場合、これでは、機械学習をサポートするためにサーバーを最適化することもまたはインストールには、モデルが事前トレーニング済みです。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

スクリプトを同時に実行される多くのユーザーの場合、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server の Machine Learning のサービスのユーザー アカウント プールを変更する](../r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

### <a name="optimize-the-server-for-script-execution"></a>スクリプトの実行用のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査などを含むデータベース エンジンによってサポートされているサービスのさまざまなサーバーの分散を最適化するものでは、使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 したがって、既定の設定で、機械学習用リソースの制限やスロットルで調整、メモリを消費する操作で特にが場合がありますを見つける可能性があります。

Machine learning のジョブは優先順位を付けるしを適切なリソースには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更する可能性がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するのを参照してください。[外部リソース プールを作成して](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約されているメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)です。
  
- によって起動できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[機械学習のユーザー アカウント プールを変更する](../r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

Standard Edition を使用しており、リソース ガバナーを持っていない場合は、動的管理ビュー (Dmv) は、拡張イベントと Windows イベントのサーバーのリソースを管理するために、監視を行うこともできます。 詳細については、次を参照してください。[監視と R サービスを管理する](../r/managing-and-monitoring-r-solutions.md)と[監視および Python サービスを管理する](../python/managing-and-monitoring-python-solutions.md)です。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

R ソリューションを SQL Server を作成するには、基本的な R 関数、SQL Server、および SQL Server がインストールされているオープン ソース R のバージョンと互換性のあるサード パーティの R パッケージと共にインストールされる properietary packes から関数を呼び出すことができます。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールをした場合、あるいはユーザー ライブラリへのパッケージをインストールした場合は、T-SQL からこれらのパッケージを使用することはできません。

インストールして、R パッケージを管理するためのプロセスは、SQL Server 2016 および SQL Server 2017 で異なります。 SQL Server 2016 では、データベース管理者は、ユーザーが必要な R パッケージをインストールする必要があります。 SQL Server の 2017 で、データベース レベルでは、上のパッケージを共有するユーザー グループを設定またはユーザーが独自のパッケージをインストールするデータベース ロールを構成できます。 詳細については、次を参照してください。 [SQL サーバーに新しい R パッケージをインストールする](../r/install-additional-r-packages-on-sql-server.md)です。


## <a name="get-help"></a>ヘルプの参照

ヘルプをインストールまたはアップグレードが必要ですか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次のステップ

R の開発者は、単純な例についてで始めることができ、SQL Server での R の動作の基礎を学習します。 次の手順は、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R 開発者向けチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python 開発者は、これらのチュートリアルに従って SQL Server で Python を使用する方法を学習できます。

+ [チュートリアル: T-SQL で Python を実行します。](../tutorials/run-python-using-t-sql.md)
+ [Python 開発者のためのチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-python-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。
