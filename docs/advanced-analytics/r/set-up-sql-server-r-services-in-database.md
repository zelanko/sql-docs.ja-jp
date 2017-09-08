---
title: "SQL Server マシン ラーニング Services (In-database) を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "SQL Server R Services のインストール"
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 36
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: f0065068d53517626c7157c9be884549573ae08b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="set-up-sql-server-machine-learning-services-in-database"></a>SQL Server マシン ラーニング Services (In-database) セットアップします。

このトピックを使用して SQL Server の Machine Learning のサービスを設定する方法について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ ウィザードです。

**適用されます:** SQL Server 2016 R サービス (R のみ)、SQL Server 2017 マシン ラーニング (R および Python)

## <a name="machine-learning-options-in-sql-server-setup"></a>機械学習の SQL Server セットアップのオプション

SQL Server セットアップでは、機械学習をインストールするため、次のオプションを提供します。

* SQL Server データベースとの機械学習をインストールします。

  このオプションを使用して、ストアド プロシージャを使用して R または Python スクリプトを実行できます。 外部接続で実行される R または Python スクリプトの SQL Server コンピューターをリモート計算コンテキストとして使用することもできます。

  このオプションをインストールします。
  
  * SQL Server 2016 では、次のように選択します。 **R Services (In-database)**です。
  * SQL Server の 2017 で選択**Machine Learning Services (In-database)**です。


* スタンドアロン machine learning サーバーをインストールします。

  このオプションでは、機械学習を必要とや SQL Server を使用しないソリューションの開発環境を作成します。 そのため、1 つのホスティングの SQL Server が別のコンピューターでこのオプションをインストールすることを一般にお勧めします。 詳細については、このオプションは、次を参照してください。[スタンドアロン R Server の作成](../r/create-a-standalone-r-server.md)です。

インストール プロセスでは、これらの一部は省略可能な複数の手順が必要です。 省略可能な側面は、両方に依存して機械学習とセキュリティ環境の状態を使用する方法です。 

## <a name="bkmk_prereqs"></a>前提条件

*  R Server と R Services の両方を同時にインストールしないでください。 通常インストール R Server (スタンドアロン) データ科学者や開発者は、接続に使用する環境を作成する SQL Server にして R ソリューションを展開します。 そのため、両方を同一のコンピューターにインストールする必要はありません。

* 以前のバージョンの Revolution Analytics 開発環境または RevoScaleR パッケージを使用した場合、または SQL Server 2016 のプレリリース版をインストールした場合は、それらをアンインストールする必要があります。 サイド バイ サイド インストールはサポートされていません。 以前のバージョンの削除については、次を参照してください。[アップグレードおよび SQL Server R Services のインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)です。

* Machine Learning のサービスは、フェールオーバー クラスターをインストールできません。 外部スクリプト プロセスを分離するために使用されるセキュリティ メカニズムが Windows Server フェールオーバー クラスター環境と互換性がないことです。 この問題を回避するには、次のいずれかの操作を行います。
    * レプリケーションを使用すると、R Services のスタンドアロン SQL Server インスタンスに必要なテーブルをコピーできます。
    * インストール[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]AlwaysOn を使用し、可用性グループの一部は、スタンドアロン コンピューターにします。

> [!IMPORTANT]
> セットアップが完了したら、追加の手順は、機械学習機能を有効にする必要があります。 可能性がありますも必要があります、特定のデータベースにユーザーのアクセス許可を与える変更アカウントの構成またはリモート データ サイエンス クライアントのセットアップします。

##  <a name="bkmk_installExt"></a>手順 1: 拡張機能をインストールし、機械学習の言語の選択

機械学習を使用するのには、SQL Server 2016 以降をインストールする必要があります。 使用する[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、データベース エンジンの少なくとも 1 つのインスタンスが必要です。 既定のインスタンスまたは名前付きインスタンスを使用できます。

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行します。
  
    無人インストールを行う方法については、次を参照してください。[無人を SQL Server R Services のインストール](../r/unattended-installs-of-sql-server-r-services.md)です。
  
2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**です。
   
3. **機能の選択** ページで、R で使用されるデータベース サービスをインストールするジョブや外部のスクリプトと処理をサポートで、次のオプションを選択する拡張機能をインストールします。
   
   **SQL Server 2016**
   - 選択**データベース エンジン サービス**です。
   - 選択**R Services (In-database)**です。

   **SQL Server 2017**
   - 選択**データベース エンジン サービス**です。
   - 選択**機械学習の Services (In-database)**です。
   - 学習の言語を有効にするには、少なくとも 1 つのマシンを選択します。 、R のみを選択することができますか、R と Python の両方を追加することができます。
   
   > [!NOTE]
   > Python または R 言語のオプションを選択しない場合は、セットアップ ウィザードにのみ、extensibility framework、SQL Server の信頼されたスタート パッドが含まれておりがインストールされますが、任意の言語に固有のコンポーネントはインストールされません。 このオプションは、Microsoft の最新のライフ サイクル ポリシーの一部として、SQL Server インスタンスを R または Python にバインドするためです。 詳細については、次を参照してください。 [R Services のインスタンスをアップグレードする使用 SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

4.  **Microsoft R Open のインストールに同意する**] ページで、[ **Accept**です。
  
     オープン ソース R 基本パッケージとツール、拡張 R パッケージおよび接続プロバイダー、Microsoft R 開発チームからのディストリビューションが含まれる Microsoft R Open をダウンロードするには、この使用許諾契約書が必要です。
  
    > [!NOTE]
    >  使用しているコンピューターがインターネットにアクセスを持たない場合」の説明に従って、個別にインストーラーをダウンロードするには、この時点でセットアップを一時停止することができます[インターネットにアクセスできないインストールの R コンポーネント](installing-ml-components-without-internet-access.md)です。
  
5. [ **次へ**] を選択します。

6. **インストールの準備完了** ページで、次の項目が含まれています、ことを確認を選択し、**インストール**です。

   **SQL Server 2016**
   - データベース エンジン サービス
   - R Services (In-Database)

   **SQL Server 2017**
   - データベース エンジン サービス
   - Machine Learning Services (データベース内)
   - R、Python、またはその両方
    
7. インストールが完了したら、コンピューターを再起動します。

##  <a name="bkmk_enableFeature"></a>手順 2: 外部スクリプト サービスを有効にします。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 まだインストールされていない場合は、SQL Server セットアップ ウィザードを再実行してダウンロード リンクを開き、インストールすることができます。
  
2. 機械学習がインストールされているインスタンスに接続し、次のコマンドを実行します。

   ```SQL
   sp_configure
   ```

    値、**外部のスクリプトを有効になっている**プロパティされます**0**します。 既定では、画面の領域を削減する機能が無効になっており、管理者で明示的に許可する必要があるためにです。
     
3. 外部のスクリプト機能を有効にするには、次のステートメントを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
4. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの SQL Server サービスを再起動します。 SQL Server のサービスも自動的に再起動すると、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

    使用してサービスを再起動することができます、 **Services**パネルまたは SQL Server 構成マネージャーを使用して、コントロール パネルの します。

## <a name="bkmk_TestScript"></a>手順 3: は、スクリプトの実行がローカルで動作することを確認してください。

外部スクリプト実行サービスが有効になっていることを確認します。

1. SQL Server Management Studio で開く新しい**クエリ**ウィンドウ、および、次のコマンドを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```
    この時点で、**run_value** が 1 に設定されている必要があります。
    
2. 開く、 **Services**パネル、およびスタート パッド サービスのインスタンスが実行されていることを確認してください。 複数のインスタンスをインストールした場合は、各インスタンスに独自のスタート パッド サービスがあります。
   
3. 新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、次のように単純な R スクリプトを実行します。
  
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```
  
    **[結果]**
  
    *こんにちは* *1*
  
   コマンドの実行、エラーが発生せず、次の手順に進んでください。 一般的な問題の一覧については、エラーが発生した場合は、次を参照してください。[アップグレードとインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)です。

## <a name="bkmk_FollowUp"></a>手順 4: 追加の構成

R、Python、ユース ケースによっては、サーバー、ファイアウォールが、サービス、またはデータベースのアクセス許可が使用するアカウントに追加の変更を加える必要があります。 変更する必要がありますはケースによって異なります。

追加の変更を必要とする一般的なシナリオは次のとおりです。

* SQL Server への着信接続を許可するファイアウォール ルールを変更します。
* 追加のネットワーク プロトコルを有効にします。
* サーバーがリモート接続をサポートしていることを確認します。
* 有効にする*黙示的な認証*ユーザーがリモート R 開発ターミナルから SQL Server のデータにアクセスし、し、RODBC パッケージまたは他の Microsoft ODBC Open Database Connectivity () プロバイダーを使用して R コードを実行します。
* R スクリプトを実行するか、データベースを使用するユーザーのアクセス許可を付与します。
* スタート パッド サービスとの通信を妨げるセキュリティの問題を修正します。
* ユーザーが R コードを実行またはパッケージをインストールする権限を持っていることを確認できます。

> [!NOTE]
> 表示されているすべての変更は、必要があります。 ただし、すべての項目を自分のシナリオに該当するかどうかを確認することをお勧めします。

### <a name="bkmk_configureAccounts"></a>スタート パッドのアカウント グループの暗黙の認証を有効にします。

セキュリティ トークンの下にタスクを実行するため、セットアップ中にいくつかの新しい Windows ユーザー アカウントの作成、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]サービス。 ユーザーが、外部クライアントから R スクリプトを送信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用可能なワーカー アカウントをアクティブに、呼び出し元のユーザーの id にマップし、ユーザーの代理として、R スクリプトを実行します。 データベース エンジンのこの新しいサービスが、セキュリティで保護された外部スクリプトの実行と呼ばれるをサポートしている*黙示的な認証*です。

これらのアカウントを表示するには、Windows ユーザー グループに**SQLRUserGroup**です。 既定では、20 のワーカー アカウントが作成された、R を実行するために十分な数より多くのジョブは通常です。

ただしをする場合、リモート データ サイエンス クライアントから R スクリプトを実行する必要がある Windows 認証を使用している必要がありますを付与するこれらのワーカー アカウントにサインインするアクセス許可、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]あなたの代理としてのインスタンス。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、 **[セキュリティ]**を展開し、 **[ログイン]**を右クリックして、 **[新しいログイン]**を選択します。
2. **ログイン - 新規**ダイアログ ボックスで、**検索**です。
3. 選択、**オブジェクトの種類**と**グループ**のチェック ボックス、およびその他のすべてのチェック ボックスをオフにします。 
4. **を選択するオブジェクト名を入力**、型**SQLRUserGroup**、し、**名前の確認**です。  
    ように、インスタンスのスタート パッド サービスに関連付けられているローカル グループの名前を解決する必要があります*instancename\SQLRUserGroup*です。 
5. [ **OK**] を選択します。
6. 既定では、ログインは **Public** ロールに割り当てられ、データベース エンジンに接続するためのアクセス許可を与えられます。
7. [ **OK**] を選択します。

### <a name="bkmk_AllowLogon"></a>ユーザーを外部スクリプトを実行する権限を付与します。

> [!NOTE]
> SQL Server のコンピューティング コンテキストで R スクリプトを実行するための SQL ログインを使用する場合はこの手順は必要ありません。

インストールした場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]独自のインスタンスで R スクリプトを実行していると、通常、管理者は、スクリプトを実行しているデータベース所有者は、少なくとも、さまざまな操作、データベース、および機能のすべてのデータの暗黙的なアクセス許可を持たない新しい R パッケージのインストールに必要です。

ただし、エンタープライズのシナリオで、SQL ログインを使用して、データベースにアクセスするユーザーを含むほとんどのユーザーはありませんこのような高度な権限。 そのため、R または Python スクリプトを実行するユーザーごとに、外部スクリプトを使用する各データベースでスクリプトを実行するユーザーのアクセス許可を付与する必要があります。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> セットアップのヘルプが必要ですか。 すべての手順を実行したかわかりませんか。 カスタム レポートを使って、R Services のインストール状態を確認できます。 詳しくは、「 [Management Studio でカスタム レポートを使用して R Services を監視する](monitor-r-services-using-custom-reports-in-management-studio.md)」をご覧ください。

### <a name="ensure-that-the-sql-server-computer-supports-remote-connections"></a>SQL Server コンピューターがリモート接続をサポートしていることを確認してください。

リモート コンピューターから接続できない場合は、サーバーがリモート接続を許可するかどうかを確認します。 既定では、リモート接続は無効にことがあります。

また、ファイアウォールが SQL Server へのアクセスを許可するかどうかを確認します。 既定では、SQL Server で使用されるポートは多くの場合、ファイアウォールによってブロックされます。 Windows ファイアウォールを使用している場合は、次を参照してください。[データベース エンジン アクセス用に Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)です。

### <a name="give-your-users-read-write-or-ddl-permissions-to-the-database"></a>ユーザーの読み取り、書き込み、またはデータベースに DDL のアクセス許可を付与します。

R スクリプトを実行中、ユーザー アカウントまたは SQL ログイン可能性があります必要があります、他のデータベースからデータを読み取る、結果を格納する新しいテーブルを作成およびテーブルにデータを書き込みます。

ユーザー アカウントまたは R スクリプトを実行する SQL ログインごとに、アカウントまたはログインがデータベースで適切な権限を持っていることを確認する: *db_datareader*、 *db_datawriter*、または*db_ddladmin*です。

たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは、SQL ログイン *MySQLLogin* に、 *RSamples* データベースで T-SQL クエリを実行する権限を与えています。 このステートメントを実行するには、SQL ログインがサーバーのセキュリティ コンテキストに既に存在している必要があります。

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

各ロールに含まれる権限の詳細については、次を参照してください。[データベース レベルのロール](../../relational-databases/security/authentication-access/database-level-roles.md)です。

### <a name="use-machine-learning-in-an-azure-vm"></a>Azure VM での machine learning を使用します。

Azure の仮想マシンに Machine Learning サービス (または R サービス) をインストールした場合は、いくつか追加の既定値を変更する必要があります。 詳細については、次を参照してください。 [Azure の仮想マシンで SQL Server 機械学習をインストールする](installing-sql-server-r-services-on-an-azure-virtual-machine.md)です。

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>データ サイエンス クライアント上のインスタンス用の ODBC データ ソースを作成する

データ サイエンス クライアント コンピューターで R ソリューションを作成し、計算コンテキストとして、SQL Server コンピューターを使用してコードを実行する必要がある場合は、SQL ログインまたは統合 Windows 認証を使用することができます。

* SQL ログインの場合は、読み取るデータが存在するデータベースに対する適切なアクセス許可をログインが持っていることを確認します。 できるように追加することで*への接続*と*選択*権限、またはへのログインを追加することで、 *db_datareader*ロール。 オブジェクトを作成する必要があるログインの場合は、追加*DDL_admin*権限です。 ログイン、テーブルにデータを保存する必要がありますを追加するログインの*db_datawriter*ロール。

* Windows 認証: インスタンス名とその他の接続情報を指定するデータ サイエンス クライアントに ODBC データ ソースを構成する必要があります。 詳細については、次を参照してください。 [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)です。

## <a name="next-steps"></a>次の手順

SQL Server で、スクリプトの実行機能が動作することを確認した後は、SQL Server Management Studio、Visual Studio コード、またはサーバーに T-SQL ステートメントを送信できるその他のクライアントから R、Python のコマンドを実行できます。

ただし、いくつかは機械学習の頻繁に使用をサポートするか、新しい R パッケージを追加するには、システム構成を変更することができます。

このセクションでは、機械学習をサポートするために行えるいくつかの一般的な変更を一覧表示します。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

頻度の高い、R を使用すると思われる場合、または同時に実行中のスクリプトに多数のユーザーの予定の場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server R Services のユーザー アカウント プールを変更する](modify-the-user-account-pool-for-sql-server-r-services.md)です。

### <a name="bkmk_optimize"></a>外部スクリプトの実行用のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査などを含むデータベース エンジンによってサポートされているサービスのさまざまなサーバーの分散を最適化するものでは、使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 したがって、既定の設定で、機械学習用リソースの制限やスロットルで調整、メモリを消費する操作で特にが場合がありますを見つける可能性があります。

Machine learning のジョブは優先順位を付けるしを適切なリソースには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更する可能性がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するのを参照してください。[外部リソース プールを作成して](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約されているメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)です。
  
- によって起動できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[機械学習のユーザー アカウント プールを変更する](modify-the-user-account-pool-for-sql-server-r-services.md)です。

Standard Edition を使用しており、リソース ガバナーを持っていない場合は、動的管理ビュー (Dmv) は、拡張イベントと Windows イベントの R. によって使用されているサーバーのリソースを管理するために、監視を使用することができます。詳細については、次を参照してください。[監視と R サービスを管理する](managing-and-monitoring-r-solutions.md)です。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

使用する、追加の R パッケージをインストールする分ほどをかかります。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールをした場合、あるいはユーザー ライブラリへのパッケージをインストールした場合は、T-SQL からこれらのパッケージを使用することはできません。 詳細については、次を参照してください。 [SQL Server に追加の R パッケージをインストール](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)です。

データベース レベルでは、上のパッケージを共有するユーザー グループを設定したり、独自のパッケージをインストールするユーザーを有効にするデータベース ロールを構成できます。 詳細については、次を参照してください。[パッケージの管理](r-package-management-for-sql-server-r-services.md)です。

### <a name="upgrade-the-machine-learning-components"></a>コンピューターをアップグレードするコンポーネントの学習

SQL Server 2016 を使用して R Services をインストールするときに、リリースまたはサービス パックが発行されたときに最新だった R コンポーネントのバージョンを取得します。 修正プログラムを適用したり、サーバーをアップグレードするたびに、マシン学習コンポーネントは、アップグレードもします。

ただし、機械学習はサポートされているよりも高速なスケジュールでコンポーネントをアップグレードする Microsoft R Server をインストールして、インスタンスをバインドして、SQL Server のリリースでします。 アップグレードすると、取得することも、次の新機能、Microsoft R Server の最近のリリースでサポートされます。

* 新しい R パッケージを含むパッケージ[sqlrutils](https://docs.microsoft.com/r-server/r-reference/sqlrutils/sqlrutils)、 [olapR](https://docs.microsoft.com/r-server/r-reference/olapr/olapr)、および[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)です。
* [モデルを事前トレーニング済み](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)イメージの分類とテキストの分析のためです。

SQL Server 2016 インスタンスをアップグレードする方法については、次を参照してください。[バインディングからのアップグレードの R コンポーネント](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

インスタンスに関連付けされている R のバージョンがわからない場合は、次などのコマンドを実行できます。

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'
myvar <- version$version.string
OutputDataSet <- as.data.frame(myvar);'
```

> [!NOTE]
> バインディング プロセスを使用してアップグレードは、SQL Server 2017 のもサポートされます。 ただし、現在のアップグレードは SQL Server 2016 インスタンスに対してのみサポートされます。

### <a name="tutorials"></a>チュートリアル

簡単な例の概要を SQL Server での R の動作の基本については、次を参照してください。 [transact-sql を使用して R コード](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)です。

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。

### <a name="troubleshooting"></a>トラブルシューティング

問題が発生した場合は、 アップグレードしようとしていますか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](monitor-r-services-using-custom-reports-in-management-studio.md)

