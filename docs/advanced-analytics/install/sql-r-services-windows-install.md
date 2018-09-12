---
title: SQL Server 2016 R Services (In-database) のインストール |Microsoft Docs
description: SQL Server で R は、Windows 上の SQL Server 2016 R Services をインストールするときに使用できます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4df8391974214452c6b8b3226c3c9a845e4b556b
ms.sourcegitcommit: 8008ea52e25e65baae236631b48ddfc33014a5e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44311682"
---
# <a name="install-sql-server-2016-r-services"></a>SQL Server 2016 R Services をインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、インストールして構成する方法を説明します**SQL Server 2016 R Services**します。 SQL Server 2016 をした場合は、SQL Server で R コードの実行を有効にするには、この機能をインストールします。

SQL Server 2017 での R 統合が提供されています[Machine Learning サービス](../r/r-server-standalone.md)Python の加算を反映します。 R 統合し SQL Server 2017 インストール メディアがある場合は、次を参照してください。 [SQL Server 2017 Machine Learning Services のインストール](sql-machine-learning-services-windows-install.md)機能を追加します。 

## <a name="bkmk_prereqs"> </a> インストール前のチェックリスト

+ データベース エンジンのインスタンスが必要です。 既存のインスタンスに増分追加できますが、だけの R をインストールすることはできません。

+ フェールオーバー クラスターに R Services をインストールできません。 R プロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。

+ ドメイン コント ローラーでは、R のサービスをインストールしません。 セットアップの R Services の部分は失敗します。

+ インストールしない**共有機能** > **R Server (スタンドアロン)** 同じコンピューター上の in-database インスタンスを実行します。 

  SQL Server インスタンスは、独自のコピーのオープン ソース R および Anaconda ディストリビューションを使用するため、R と Python の他のバージョンとサイド バイ サイドでインストールがあります。 ただし、SQL Server の外部の SQL Server コンピューターで R と Python を使用するコードを実行している可能性をさまざまな問題があります。
    
  + 別のライブラリと、さまざまな実行可能ファイルを使用して SQL Server で実行するときよりも、異なる結果を取得します。
  + リソースの競合をリードする、SQL Server が外部ライブラリで実行されている R と Python スクリプトを管理することはできません。
  
以前のバージョンの Revolution Analytics 開発環境または RevoScaleR パッケージを使用した場合、または SQL Server 2016 のプレリリース版をインストールした場合は、それらをアンインストールする必要があります。 RevoScaleR とその他の独自のパッケージのバージョンを実行することはできません。 以前のバージョンの削除については、次を参照してください。[アップグレードと SQL Server Machine Learning Services のインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)します。

> [!IMPORTANT]
> セットアップが完了したら、必ずこの記事で説明されている追加の構成後の手順を完了してください。 この手順では、外部スクリプトを使用する SQL Server を有効にして、あなたに代わって R ジョブを実行する SQL Server に必要なアカウントを追加します。 構成の変更は、一般に、インスタンスの再起動またはスタート パッド サービスの再起動が必要です。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  

## <a name="bkmk2016top"></a>セットアップを実行

ローカル インストールの場合は、セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。

1. SQL Server 2016 のセットアップ ウィザードを起動します。

2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**します。
    
   ![R Services (In-database) をインストール](media/2016-setup-installation-rsvcs.png "と R Services のデータベース エンジンのインストールを開始")
   
3. **機能の選択**ページで、次のオプションを選択します。

   - 選択**データベース エンジン サービス**します。 データベース エンジンは、machine learning を使用する各インスタンスに必要です。
   - 選択**R Services (In-database)** します。 R です。 データベースで使用するためのサポートをインストール
    
     ![R Services 機能の選択](media/2016setup-rsvcs-features.png "の R サービス データベース内のこれらの機能を選択します")

    > [!IMPORTANT]
    > 同時に R Server と R Services をインストールすることはできません。 SQL Server に R Server、データ サイエンティストや開発者は、接続に使用する環境を作成するには、(スタンドアロン) をインストールし、R ソリューションの配置は通常します。 そのため、両方を同一のコンピューターにインストールする必要はありません。

4.  **Microsoft R Open のインストールに同意する**] ページで [ **Accept**します。
  
    オープン ソース R 基本パッケージとツール、拡張 R パッケージおよび接続プロバイダー、Microsoft R の開発チームからのディストリビューションが含まれる Microsoft R Open をダウンロードするには、この使用許諾契約書が必要です。
  
5. 使用許諾契約書を承諾すると、インストーラーを準備している間に一時停止にがあります。 クリックして**次**ボタンが使用できるになります。

6. **インストールの準備完了**] ページで、次のものが含まれていますし、[確認**インストール**します。

   + データベース エンジン サービス
   + R Services (データベース内)

    パスの下のフォルダーの場所をメモして`..\Setup Bootstrap\Log`構成ファイルが格納されます。 セットアップが完了したら、概要ファイルにインストールされているコンポーネントを確認できます。

7. セットアップが完了したら、コンピューターを再起動するように指示される場合ようになりました。 セットアップが完了した時点で、インストール ウィザードによるメッセージを確認することが重要です。 詳細については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files)」を参照してください。


##  <a name="bkmk_enableFeature"></a>スクリプトの実行を有効にします。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 

    > [!TIP]
    > ダウンロードして、このページから、適切なバージョンをインストールすることができます:[ダウンロード SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)します。
    > 
    > プレビュー リリースのも試すことができます[SQL Operations Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is)、管理タスクと SQL Server に対してクエリをサポートします。
  
2. Machine Learning サービスがインストールされているインスタンスに接続し、をクリックして**新しいクエリ**クエリ ウィンドウを開いて、次のコマンドを実行します。

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

関連するサービスを再起動しても自動的に再起動[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

右クリックを使用してサービスを再起動する**再起動**コマンドを使用してまたは SSMS では、インスタンスを**サービス**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>インストールの確認

次の手順を使用すると、外部スクリプトを起動するのにために使用するすべてのコンポーネントが実行されていることを確認できます。

1. SQL Server Management studio で新しいクエリ ウィンドウを開き、次のコマンドを実行します。
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。

2. 開く、**サービス**パネルまたは SQL Server 構成マネージャー、ことを確認および**SQL Server スタート パッド サービス**が実行されています。 R がデータベース エンジンのインスタンスごとに 1 つのサービスが必要または Python をインストールします。 サービスの詳細については、次を参照してください。 [Extensibility framework](../concepts/extensibility-framework.md)します。

7. スタート パッドが実行されている場合は、外部スクリプトのランタイムは、SQL Server と通信できることを確認する単純な R を実行できる必要があります。 

    新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、次のようなスクリプトを実行します。
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    を初めて実行する、外部スクリプトのランタイムが読み込まれるとき、スクリプトは少しことができます。 結果は、次のようになります。

    | hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> その他の構成

外部スクリプトの検証手順が成功した場合は、SQL Server Management Studio、Visual Studio Code、または T-SQL ステートメントをサーバーに送信できるその他のクライアントから Python のコマンドを実行できます。

コマンドの実行時にエラーを取得した場合は、このセクションでは追加の構成手順を確認します。 サービスまたはデータベースに追加の適切な構成を作成する必要があります。

追加の変更を必要とする一般的なシナリオは次のとおりです。

* [Windows ファイアウォールの着信接続を構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [その他のネットワーク プロトコルを有効にします。](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [リモート接続を有効にします。](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [リモート ユーザーに組み込みの権限を拡張します。](#bkmk_configureAccounts)
* [外部スクリプトを実行するアクセス許可を付与](#bkmk_AllowLogon)
* [個々 のデータベースへのアクセスを許可](#permissions-db)

> [!NOTE]
> 表示されているすべての変更が必要ですと必要なしに可能性があります。 要件は、SQL Server、およびユーザーがデータベースに接続し、外部スクリプトの実行が予想される方法をインストールした、セキュリティ スキーマによって異なります。 追加のトラブルシューティングのヒントについてはこちら:[アップグレードとインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>スタート パッド アカウントのグループの暗黙の認証を有効にします。

セットアップ中に、いくつかの新しい Windows ユーザー アカウントを作成して、セキュリティ トークンの下でタスクを実行するため、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービス。 ユーザーは、外部のクライアントから R スクリプトを送信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用可能なワーカー アカウントをアクティブに、呼び出し元のユーザーの id にマップし、ユーザーの代理として、R スクリプトを実行します。 データベース エンジンのこの新しいサービスが呼び出される外部のスクリプトを安全に実行をサポートしている*暗黙の認証*します。

これらのアカウントを表示するには、Windows ユーザー グループで**SQLRUserGroup**します。 既定では、20 個のワーカー アカウントが作成になり、R を実行するための十分な数のジョブは通常します。

ただし、リモート データ サイエンス クライアントから R スクリプトを実行する必要があります、Windows 認証を使用している場合は、する必要があります許可するこれらのワーカー アカウントにサインインするため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あなたに代わってインスタンス。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]** を展開し、 **[ログイン]** を右クリックして、 **[新しいログイン]** を選択します。
2. **ログイン - 新規**ダイアログ ボックスで、**検索**します。
3. 選択、**オブジェクトの種類**と**グループ**チェック ボックス、およびその他のすべてのチェック ボックスをオフにします。
4. クリックして**詳細**を検索する場所がクリックして、現在のコンピューターであることを確認**検索開始**します。
5. 以降の 1 つが表示されるまで、サーバー上のグループ アカウントの一覧をスクロール`SQLRUserGroup`します。
    
    + スタート パッド サービスに関連付けられているグループの名前、_既定のインスタンス_だけは常に**SQLRUserGroup**します。 このアカウントは、既定のインスタンスのみを選択します。
    + 使用する場合、_名前付きインスタンス_、インスタンス名が、既定の名前に追加されます`SQLRUserGroup`します。 そのため、インスタンスは、"MLTEST"という名前は、このインスタンスの既定のユーザー グループ名なります**SQLRUserGroupMLTest**します。
5. クリックして**OK**を高度な検索 ダイアログ ボックスを閉じ、インスタンスの正しいアカウントを選択したことを確認します。 各インスタンスには、独自のスタート パッド サービスだけとそのサービスに対して作成されたグループを使用できます。
6. をクリックして**OK**を閉じるにはもう一度、 **[ユーザーまたはグループ**] ダイアログ ボックス。
7. **ログイン - 新規**ダイアログ ボックスで、をクリックして**OK**。 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。

### <a name="bkmk_AllowLogon"></a>外部スクリプトを実行するアクセス許可をユーザーに与える

> [!NOTE]
> SQL Server のコンピューティング コンテキストで R スクリプトを実行するために SQL ログインを使用する場合はこの手順は必要ありません。

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独自のインスタンスで、通常、スクリプトを実行する管理者は、少なくともデータベース所有者は、さまざまな操作、データベース、および新しいパッケージをインストールする機能のすべてのデータの暗黙的なアクセス許可を持たない必要に応じて。

ただし、エンタープライズのシナリオで、SQL ログインを使用して、データベースにアクセスするユーザーを含むほとんどのユーザーはありませんこのような高度な権限。 したがって、R スクリプトを実行するユーザーごとに、外部スクリプトを使用する各データベースでスクリプトを実行するユーザーのアクセス許可を付与する必要があります。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> セットアップのヘルプが必要ですか。 すべての手順を実行したかわかりませんか。 インストールの状態を確認し、追加の手順を実行するには、これらのカスタム レポートを使用します。 
> 
> [カスタム レポートを使用して Machine Learning サービスの監視](../r/monitor-r-services-using-custom-reports-in-management-studio.md)します。

### <a name="permissions-db"></a> ユーザーの読み取り、書き込み、またはデータベースに DDL のアクセス許可を付与します。

R を実行するために使用するユーザー アカウント可能性があります必要があります、他のデータベースからデータを読み取る結果を格納する新しいテーブルを作成し、テーブルにデータを書き込みます。 そのため、ユーザーごとに実行されるように R スクリプト、ユーザーがデータベースで適切な権限を持っていることを確認します*db_datareader*、 *db_datawriter*、または*db_ddladmin*。

たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、SQL ログイン *MySQLLogin* に、 *RSamples* データベースで T-SQL クエリを実行する権限を与えています。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

各ロールに含まれるアクセス許可の詳細については、次を参照してください。[データベース レベル ロール](../../relational-databases/security/authentication-access/database-level-roles.md)します。


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>データ サイエンス クライアント上のインスタンス用の ODBC データ ソースを作成する

データ サイエンス クライアント コンピューターで R ソリューションを作成し、計算コンテキストとして SQL Server コンピューターを使用してコードを実行する必要がある場合は、SQL ログインまたは統合 Windows 認証のいずれかを使用することができます。

* SQL ログインの場合は、読み取るデータが存在するデータベースに対する適切なアクセス許可をログインが持っていることを確認します。 追加することによって行うことができます*への接続*と*選択*アクセス許可、またはログインを追加することで、 *db_datareader*ロール。 オブジェクトを作成する必要があるログインでは、追加*DDL_admin*権限。 ログインをテーブルにデータを保存する必要がありますが、ログインを追加、 *db_datawriter*ロール。

* Windows 認証: インスタンス名と他の接続情報を指定するデータ サイエンス クライアントで ODBC データ ソースを構成する必要があります。 詳細については、次を参照してください。 [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)します。

## <a name="suggested-optimizations"></a>提案されている最適化

、Machine learning をサポートするためにサーバーを最適化することもできたすべてを動作、または事前トレーニング済みモデルをインストールします。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

頻度の高い、R を使用すると思われる場合、または実行中のスクリプトを同時に多くのユーザーが予想される場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server Machine Learning Services のユーザー アカウント プールを変更](../r/modify-the-user-account-pool-for-sql-server-r-services.md)します。

### <a name="bkmk_optimize"></a>外部スクリプト実行のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、データベース エンジンは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査を含めることがでサポートされているサービスのさまざまなサーバーのバランスを最適化するためのものと使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 そのため、既定の設定で、機械学習用リソースの場合もありますが制限または抑制され、メモリを消費する操作で特にを見つける可能性があります。

Machine learning ジョブは優先順位を設定しを適切にリソースを確認するには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更したい場合がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するを参照してください。[外部リソース プールの作成](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約済みメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)します。
  
- によって開始できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[machine learning のユーザー アカウント プールを変更する](../r/modify-the-user-account-pool-for-sql-server-r-services.md)します。

Standard Edition を使用している、リソース ガバナーがない場合は、動的管理ビュー (Dmv) は、拡張イベントと監視には、R で使用されているサーバーのリソースを管理するために Windows イベントを使用することができます。詳細については、次を参照してください。[の監視と R Services を管理](../r/managing-and-monitoring-r-solutions.md)します。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

R ソリューションを SQL Server を作成する基本的な R 関数、SQL Server と共にインストールされている独自のパッケージと R パッケージのサード パーティからの関数は SQL Server がインストールされているオープン ソース R のバージョンと互換性のある呼び出すことができます。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールがある場合、またはユーザー ライブラリにパッケージをインストールした場合は、T-SQL からそれらのパッケージを使用することはできません。

インストールして、R パッケージを管理するためのプロセスでは、SQL Server 2016 および SQL Server 2017 で異なります。 SQL Server 2016 では、データベース管理者は、ユーザーが必要な R パッケージをインストールする必要があります。 SQL Server 2017 では、データベースごとのレベルでパッケージを共有するユーザー グループを設定するか、または独自のパッケージをインストールするユーザーを有効にするデータベース ロールを構成します。 詳細については、次を参照してください。[新しい R パッケージをインストール](../r/install-additional-r-packages-on-sql-server.md)します。


## <a name="get-help"></a>ヘルプの参照

インストールまたはアップグレードに関するヘルプ よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](../r/upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態を確認し、一般的な問題を修正には、これらのカスタム レポートをお試しください。

* [SQL Server R Services 用のカスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>次の手順

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: T-SQL で R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [R の開発者向けチュートリアル: データベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../tutorials/machine-learning-services-tutorials.md)します。


