---
title: SQL Server 2016 R Services (In-database) のインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
keywords:
- SQL Server R Services のインストール
- SQL Server の Machine Learning のサービスをインストールします。
- R Services セットアップします。
- SQL の機械学習をインストールします。
ms.assetid: ''
caps.latest.revision: ''
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Active
ms.openlocfilehash: 7a00eb7f3151ad95818feee1d981170164f44345
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="install-sql-server-2016-r-services-in-database"></a>SQL Server 2016 R Services (In-Database) をインストールする 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、インストールして構成する方法を説明します。 **SQL Server 2016 R Services (In-database)**です。 SQL Server 2016 がある場合は、SQL Server で R コードの実行を有効にするには、この機能をインストールします。

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

+ SQL Server 2016 セットアップは、R Services をインストールする場合に必要です。 インストールする必要がある代わりに、SQL Server 2017 インストール メディアがあれば、 [SQL Server 2017 Machine Learning Services (In-database)](sql-machine-learning-services-windows-install.md)を SQL Server のバージョンの R 統合を取得します。

+ データベース エンジンのインスタンスが必要です。 だけ、R がありますが、既存のインスタンスを増分追加することができますをインストールすることはできません。

+ フェールオーバー クラスターでは、R Services をインストールしません。 R のプロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。

+ ドメイン コント ローラーでは、R Services を取り付けないでください。 セットアップの R Services の部分は失敗します。

+ インストールしない**共有機能** > **R Server (スタンドアロン)**同じコンピューターにデータベースのインスタンスを実行します。 

+ SQL Server のインスタンスは、オープン ソース R および Anaconda ディストリビューションのコピーを使用するため、R、Python の他のバージョンとサイド バイ サイド インストールが可能です。 ただし、SQL Server の外部の SQL Server コンピューターの R、Python を使用するコードを実行しているは、さまざまな問題につながることができます。
    
  + 別のライブラリと、さまざまな実行可能ファイルを使用して SQL Server で実行しているときよりも、異なる結果を取得します。
  + 外部ライブラリで実行される R と Python スクリプトは、先頭のリソースの競合する SQL Server で管理できません。
  
以前のバージョンの Revolution Analytics 開発環境または RevoScaleR パッケージを使用した場合、または SQL Server 2016 のプレリリース版をインストールした場合は、それらをアンインストールする必要があります。 RevoScaleR とその他の独自のパッケージの新旧のバージョンを実行することはサポートされていません。 以前のバージョンの削除については、次を参照してください。[アップグレードおよび SQL Server の Machine Learning のサービスのインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)です。

> [!IMPORTANT]
> セットアップが完了したら、必ずこの記事で説明されている追加のインストール後の構成手順を完了してください。 次の手順には、外部のスクリプトを使用する SQL Server を有効にして、あなたに代わって R ジョブを実行する SQL Server に必要なアカウントを追加することが含まれます。 構成の変更は、一般に、インスタンスの再起動またはスタート パッド サービスの再起動が必要です。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  

## <a name="bkmk2016top"></a>セットアップを実行します。

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2016 のセットアップ ウィザードを起動します。

2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**です。
    
   ![R Services (In-database) をインストール](media/2016-setup-installation-rsvcs.png "R Services のデータベース エンジンのインストールを開始")
   
3. **機能の選択** ページで、次のオプションを選択します。

   - 選択**データベース エンジン サービス**です。 機械学習を使用する各インスタンス、データベース エンジンが必要です。
   - 選択**R Services (In-database)**です。 R です。 データベースで使用するためのサポートをインストール
    
     ![R Services 機能の選択](media/2016setup-rsvcs-features.png "の R サービス データベース内のこれらの機能を選択")

    > [!IMPORTANT]
    > 同時に R サーバーと R Services をインストールすることはできません。 通常インストール R Server (スタンドアロン) データ科学者や開発者は、接続に使用する環境を作成する SQL Server にして R ソリューションを展開します。 そのため、両方を同一のコンピューターにインストールする必要はありません。

4.  **Microsoft R Open のインストールに同意する**] ページで [ **Accept**です。
  
    オープン ソース R 基本パッケージとツール、拡張 R パッケージおよび接続プロバイダー、Microsoft R 開発チームからのディストリビューションが含まれる Microsoft R Open をダウンロードするには、この使用許諾契約書が必要です。
  
5. 使用許諾契約を承諾すると、インストーラーを準備している間ありますは一時停止です。 をクリックして**次**ボタンが使用可能なになります。

6. **インストールの準備完了** ページで、次の項目が含まれています、ことを確認を選択し、**インストール**です。

   + データベース エンジン サービス
   + R Services (データベース内)

    パスの下のフォルダーの場所をメモして`..\Setup Bootstrap\Log`構成ファイルが格納されます。 セットアップが完了したら、概要ファイルにインストールされているコンポーネントを確認することができます。

7. インストールが完了したら、コンピューターを再起動します。

##  <a name="bkmk_enableFeature"></a>外部スクリプトの実行を有効にします。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 

    > [!TIP]
    > ダウンロードして、このページから、適切なバージョンをインストールすることができます:[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。
    > 
    > プレビュー リリースのも試すことができます[SQL 操作 Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is)、管理タスクと SQL Server に対してクエリをサポートします。
  
2. Machine Learning のサービスがインストールされているインスタンスに接続し、をクリックして**新しいクエリ**をクエリ ウィンドウを開き、次のコマンドを実行します。

   ```SQL
   sp_configure
   ```
    プロパティ `external scripts enabled` の値は、この時点では **0** であることが必要です。 この機能が既定でオフにするためです。 機能する必要があります明示的に有効にする管理者によって R または Python スクリプトを実行する前にします。
     
3. 外部のスクリプト機能を有効にするには、次のステートメントを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>サービスを再起動します。

インストールが完了したら、スクリプトの実行を有効にすると、次に進む前に、データベース エンジンを再起動します。

表記も自動的に再起動すると、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

右クリックを使用してサービスを再起動することができます**再起動**SSMS で、またはを使用して、インスタンスのコマンド、 **Services**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>インストールの確認

外部スクリプトの起動に使用するすべてのコンポーネントが実行されていることを確認するのにには、次の手順を使用します。

1. SQL Server Management Studio で、新しいクエリ ウィンドウを開き、次のコマンドを実行します。
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。

2. 開く、 **Services**パネルまたは SQL Server 構成マネージャー、ことを確認し、 **SQL Server スタート パッド サービス**が実行されています。 R をデータベース エンジンのインスタンスごとに 1 つのサービスが必要、または Python をインストールします。 実行されていない場合は、サービスを再起動します。 詳細については、次を参照してください。 [Python の統合をサポートするにはコンポーネント](../python/new-components-in-sql-server-to-support-python-integration.md)です。

7. スタート パッドを実行している場合は、外部スクリプトのランタイムは、SQL Server と通信できることを確認する簡単な R を実行することができます。 

    新しく開きます**クエリ**ウィンドウに[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、次のようスクリプトを実行します。
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    スクリプトは、外部スクリプトの実行時の読み込みを初めて実行するときは少しことができます。 結果は、次のようにする必要があります。

    | hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> その他の構成

外部スクリプトの検証手順が成功した場合は、SQL Server Management Studio、Visual Studio コード、またはサーバーに T-SQL ステートメントを送信できるその他のクライアントから Python コマンドを実行することができます。

コマンドの実行時にエラーを取得した場合は、このセクションで追加の構成手順を確認します。 サービスまたはデータベースに、適切な構成を追加する必要があります。

追加の変更を必要とする一般的なシナリオは次のとおりです。

* [着信接続用に Windows ファイアウォールを構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [追加のネットワーク プロトコルを有効にします。](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [リモート接続を有効にします。](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [リモート ユーザーに組み込みの権限を拡張します。](#bkmk_configureAccounts)
* [外部スクリプトを実行するアクセス許可を付与します。](#bkmk_AllowLogon)
* [個々 のデータベースにアクセスを許可](#permissions-db)

> [!NOTE]
> 表示されているすべての変更が必要であり、必要なし があります。 要件は、SQL Server、およびデータベースに接続し、外部のスクリプトを実行するユーザーを想定する方法をインストールした、セキュリティ スキーマによって異なります。 追加のトラブルシューティングのヒントをご覧ください:[アップグレードとインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>スタート パッドのアカウント グループの暗黙の認証を有効にします。

セキュリティ トークンの下にタスクを実行するため、セットアップ中にいくつかの新しい Windows ユーザー アカウントの作成、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービス。 ユーザーが、外部クライアントから R スクリプトを送信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用可能なワーカー アカウントをアクティブに、呼び出し元のユーザーの id にマップし、ユーザーの代理として、R スクリプトを実行します。 データベース エンジンのこの新しいサービスが、セキュリティで保護された外部スクリプトの実行と呼ばれるをサポートしている*黙示的な認証*です。

これらのアカウントを表示するには、Windows ユーザー グループに**SQLRUserGroup**です。 既定では、20 のワーカー アカウントが作成された、R を実行するために十分な数より多くのジョブは通常です。

ただしをする場合、リモート データ サイエンス クライアントから R スクリプトを実行する必要がある Windows 認証を使用している必要がありますを付与するこれらのワーカー アカウントにサインインするアクセス許可、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あなたの代理としてのインスタンス。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]**を展開し、 **[ログイン]**を右クリックして、 **[新しいログイン]**を選択します。
2. **ログイン - 新規**ダイアログ ボックスで、**検索**です。
3. 選択、**オブジェクトの種類**と**グループ**のチェック ボックス、およびその他のすべてのチェック ボックスをオフにします。
4. をクリックして**詳細**、検索する場所がクリックして、現在のコンピューターであることを確認**今すぐ検索**です。
5. 1 つの先頭に表示されるまで、サーバー上のグループ アカウントの一覧をスクロール`SQLRUserGroup`です。
    
    + スタート パッド サービスに関連付けられているグループの名前、_既定のインスタンス_だけは常に**SQLRUserGroup**です。 既定のインスタンスに対してのみ、このアカウントを選択します。
    + 使用している場合、_名前付きインスタンス_、インスタンス名が既定の名前に追加されます`SQLRUserGroup`です。 そのため場合、インスタンスは、"MLTEST"という名前は、このインスタンスの既定のユーザー グループ名になります**SQLRUserGroupMLTest**です。
5. をクリックして**OK**を高度な検索 ダイアログ ボックスを閉じ、インスタンスの正しいアカウントを選択していることを確認します。 各インスタンスには、独自のスタート パッド サービスだけとそのサービスに対して作成されたグループを使用できます。
6. をクリックして**OK**を閉じるにはもう一度、 **[ユーザーまたはグループ**] ダイアログ ボックス。
7. **ログイン - 新規**ダイアログ ボックスで、をクリックして**OK**です。 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。

### <a name="bkmk_AllowLogon"></a>ユーザーを外部スクリプトを実行する権限を付与します。

> [!NOTE]
> SQL Server のコンピューティング コンテキストで R スクリプトを実行するための SQL ログインを使用する場合はこの手順は必要ありません。

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独自のインスタンスで通常スクリプトを実行する管理者は、またはデータベース所有者は、少なくとも、さまざまな操作、データベース、および新しいパッケージをインストールする機能のすべてのデータの暗黙的なアクセス許可を持たない必要に応じて。

ただし、エンタープライズのシナリオで、SQL ログインを使用して、データベースにアクセスするユーザーを含むほとんどのユーザーはありませんこのような高度な権限。 そのため、R スクリプトを実行するユーザーごとに、外部スクリプトを使用する各データベースでスクリプトを実行するユーザーのアクセス許可を付与する必要があります。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> セットアップのヘルプが必要ですか。 すべての手順を実行したかわかりませんか。 これらのカスタム レポートを使用して、インストール状態をチェックして、追加の手順を実行します。 
> 
> [カスタム レポートを使用して、マシン学習サービスを監視](../r/monitor-r-services-using-custom-reports-in-management-studio.md)です。

### <a name="permissions-db"></a> ユーザーの読み取り、書き込み、またはデータベースに DDL のアクセス許可を付与します。

ユーザー アカウント R を実行するために使用可能性があります必要がある他のデータベースからデータを読み取る、結果を格納する新しいテーブルを作成してテーブルにデータを書き込みます。 そのため、ユーザーごとに実行されるように R スクリプト、ユーザーがデータベースで適切な権限を持っていることを確認します*db_datareader*、 *db_datawriter*、または*db_ddladmin*。

たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、SQL ログイン *MySQLLogin* に、 *RSamples* データベースで T-SQL クエリを実行する権限を与えています。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

各ロールに含まれる権限の詳細については、次を参照してください。[データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)です。


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>データ サイエンス クライアント上のインスタンス用の ODBC データ ソースを作成する

データ サイエンス クライアント コンピューターで R ソリューションを作成し、計算コンテキストとして、SQL Server コンピューターを使用してコードを実行する必要がある場合は、SQL ログインまたは統合 Windows 認証を使用することができます。

* SQL ログインの場合は、読み取るデータが存在するデータベースに対する適切なアクセス許可をログインが持っていることを確認します。 できるように追加することで*への接続*と*選択*権限、またはへのログインを追加することで、 *db_datareader*ロール。 オブジェクトを作成する必要があるログインの場合は、追加*DDL_admin*権限です。 ログイン、テーブルにデータを保存する必要がありますを追加するログインの*db_datawriter*ロール。

* Windows 認証: インスタンス名とその他の接続情報を指定するデータ サイエンス クライアントに ODBC データ ソースを構成する必要があります。 詳細については、次を参照してください。 [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)です。

## <a name="suggested-optimizations"></a>推奨される最適化

すべての作業がある場合、これでは、機械学習をサポートするためにサーバーを最適化することもまたはインストールには、モデルが事前トレーニング済みです。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

頻度の高い、R を使用すると思われる場合、または同時に実行中のスクリプトに多数のユーザーの予定の場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server の Machine Learning のサービスのユーザー アカウント プールを変更する](../r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

### <a name="bkmk_optimize"></a>外部スクリプトの実行用のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査などを含むデータベース エンジンによってサポートされているサービスのさまざまなサーバーの分散を最適化するものでは、使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 したがって、既定の設定で、機械学習用リソースの制限やスロットルで調整、メモリを消費する操作で特にが場合がありますを見つける可能性があります。

Machine learning のジョブは優先順位を付けるしを適切なリソースには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更する可能性がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するのを参照してください。[外部リソース プールを作成して](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約されているメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)です。
  
- によって起動できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[機械学習のユーザー アカウント プールを変更する](../r/modify-the-user-account-pool-for-sql-server-r-services.md)です。

Standard Edition を使用しており、リソース ガバナーを持っていない場合は、動的管理ビュー (Dmv) は、拡張イベントと Windows イベントの R. によって使用されているサーバーのリソースを管理するために、監視を使用することができます。詳細については、次を参照してください。[監視と R サービスを管理する](../r/managing-and-monitoring-r-solutions.md)です。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

R ソリューションを SQL Server を作成するには、基本的な R 関数、SQL Server、および SQL Server がインストールされているオープン ソース R のバージョンと互換性のあるサード パーティの R パッケージと共にインストールされる properietary packes から関数を呼び出すことができます。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールをした場合、あるいはユーザー ライブラリへのパッケージをインストールした場合は、T-SQL からこれらのパッケージを使用することはできません。

インストールして、R パッケージを管理するためのプロセスは、SQL Server 2016 および SQL Server 2017 で異なります。 SQL Server 2016 では、データベース管理者は、ユーザーが必要な R パッケージをインストールする必要があります。 SQL Server の 2017 で、データベース レベルでは、上のパッケージを共有するユーザー グループを設定またはユーザーが独自のパッケージをインストールするデータベース ロールを構成できます。 詳細については、次を参照してください。[パッケージの管理](../r/r-package-management-for-sql-server-r-services.md)です。


## <a name="get-help"></a>ヘルプの参照

ヘルプをインストールまたはアップグレードが必要ですか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次の手順

R の開発者は、単純な例についてで始めることができ、SQL Server での R の動作の基礎を学習します。 次の手順は、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R 開発者向けチュートリアル: データベース内の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。


