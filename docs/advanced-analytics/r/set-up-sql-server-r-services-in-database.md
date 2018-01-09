---
title: "SQL Server マシン ラーニング Services (In-database) を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "SQL Server R Services のインストール"
- "SQL Server の Machine Learning のサービスをインストールします。"
- "R Services セットアップします。"
- "SQL の機械学習をインストールします。"
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: "36"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 04f2502853e21968f2edaac927247eb45730d000
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="set-up-sql-server-machine-learning-services-in-database"></a>SQL Server マシン ラーニング Services (In-database) セットアップします。

このトピックでは、インストールして、次の機械学習で SQL Server データベース内の分析をサポートする機能を構成する方法について説明します。

+ **SQL Server 2016 R Services (In-database)**です。 SQL Server 2016 がある場合は、SQL Server で R コードの実行を有効にするには、この機能をインストールします。 データベース エンジンが必要です。

    [機械学習で SQL Server 2016 セットアップします。](#bkmk_2016top)

+ **SQL Server 2017 Machine Learning Services (In-database)**です。 SQL Server 2017 がある場合は、このコードを実行する R (または Python) SQL Server をインストールします。 データベース エンジンが必要です。 

    [機械学習で SQL Server 2017 設定します。](#bkmk_2017top)

+ Machine learning サーバー**ありません**SQL Server

    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップには、マシンの学習のコンポーネントは、データベース エンジンと SQL Server では実行されません「スタンドアロン」バージョンをインストールするオプションも含まれています。  一般に、SQL Server をホストするコンピューターとは異なるコンピューターでこのオプションをインストールすることをお勧めします。
    
    [機械学習のスタンドアロン サーバーのセットアップ](create-a-standalone-r-server.md)です。

この記事には、使用するセットアップのプロセスがについて説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップ ウィザードです。 コマンド ライン インストールの場合、またはオフラインのサーバーで使用するインストーラーをダウンロードするには、次の記事を参照してください。

+ [コマンドラインから SQL Server の R をインストールします。](unattended-installs-of-sql-server-r-services.md)
+ [コマンドラインから SQL Server 用 Python をインストールします。](../python/unattended-installs-of-sql-server-python-services.md)
+ [コマンドラインからスタンドアロン machine learning サーバーをインストールします。](install-microsoft-r-server-from-the-command-line.md)
+ [いないインターネット ace を備えたサーバーで machine learning のコンポーネントをインストールします。](installing-ml-components-without-internet-access.md)

**適用されます:** SQL Server 2016、SQL Server 2017

## <a name="bkmk_prereqs"></a>インストール前のチェックリスト

+ Machine learning データベース内には、SQL Server 2016 以降が必要です。 

+ サポートされている言語: 

    + SQL Server 2016 では、R がのみがサポートされます。 

    + R もいくつかの制限と Azure SQL Database のプレビュー機能として利用できます。 詳細については、次を参照してください[Azure SQL データベースでの R の使用。](using-r-in-azure-sql-database.md)

    + Python を使用するには、SQL Server 2017 以降が必要です。

+ 以前のバージョンの Revolution Analytics 開発環境または RevoScaleR パッケージを使用した場合、または SQL Server 2016 のプレリリース版をインストールした場合は、それらをアンインストールする必要があります。 サイド バイ サイド インストールはサポートされていません。 以前のバージョンの削除については、次を参照してください。[アップグレードおよび SQL Server の Machine Learning のサービスのインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)です。

+ ドメイン コント ローラーで SQL Server 2016 の R Services または SQL Server 2017 Machine Learning Services をインストールすることはできません。 セットアップの R Services または Machine Learning のサービスの一部が失敗します。

+ 機械学習をフェールオーバー クラスターに機能をインストールすることはできません。 外部スクリプト プロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。 この問題を回避するには、次のいずれかの操作を行います。
    * レプリケーションを使用すると、有効になっている機械学習で SQL Server インスタンスに必要なテーブルをコピーできます。
    * AlwaysOn を使用し、可用性グループの一部は、スタンドアロン コンピューターでは、機械学習をインストールします。

+ 機械学習フレームワークでは、セットアップが完了したら、追加の構成が必要です。 正確な手順は、組織とセキュリティ ポリシー、サーバーの構成、および想定されるユーザーによって異なります。 すべての手順を確認し、環境内で必要な追加の構成を確認することをお勧めします。

## <a name="bkmk2016top"></a>SQL Server 2016 R Services (In-database) のインストールします。

> [!div class="checklist"]
> * データベース エンジンと機械学習の機能をインストールします。
> * インストール後の手順が必要: 機械学習を有効にして再起動
> * 省略可能なインストール後の手順: ファイアウォール規則を追加、ユーザーを追加、変更、またはサービス アカウントの構成、リモート データ サイエンス クライアントの設定

**SQL Server 2016 セットアップ ウィザードを使用します。**

1. SQL Server セットアップ ウィザードを実行します。

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
  
    使用しているコンピューターがインターネットにアクセスを持たない場合」の説明に従って、個別にインストーラーをダウンロードするには、この時点でセットアップを一時停止することができます[インターネットにアクセスできないインストールの R コンポーネント](installing-ml-components-without-internet-access.md)です。
  
5. 使用許諾契約を承諾すると、インストーラーを準備している間ありますは一時停止です。 をクリックして**次**ボタンが使用可能なになります。

6. **インストールの準備完了** ページで、次の項目が含まれています、ことを確認を選択し、**インストール**です。

   + データベース エンジン サービス
   + R Services (データベース内)

7. インストールが完了したら、コンピューターを再起動します。


## <a name="bkmk2017top"></a>SQL Server 2017 Machine Learning Services (In-database) のインストールします。

> [!div class="checklist"]
> * データベース エンジンと機械学習の機能をインストールします。
> * インストール後の手順が必要: 機械学習を有効にして再起動
> * 省略可能なインストール後の手順: ファイアウォール規則を追加、ユーザーを追加、変更、またはサービス アカウントの構成、リモート データ サイエンス クライアントを設定します。

**開始するには**

1. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップを実行します。
  
2. **インストール**] タブで [ **SQL Server の新規スタンドアロン インストールまたは既存のインストールに機能の追加**です。

     ![Machine Learning Services (In-database) をインストール](media/2017setup-installation-page-mlsvcs.png "Machine Learning のサービスとデータベース エンジンのインストールを開始")

3. **機能の選択** ページで、次のオプションを選択します。
   
    + 選択**データベース エンジン サービス**です。 機械学習を使用する各インスタンス、データベース エンジンが必要です。

    + 選択**機械学習の Services (In-database)**です。 このオプションは r です。 データベースで使用するためのサポートをインストールします。このオプションを選択した後に、機械学習の言語を選択できます。 、R のみを選択することができますか、R と Python の両方を追加することができます。
   
    ![Machine Learning サービス機能の選択](media/2017setup-features-page-mls-rpy.png "の R サービス データベース内のこれらの機能を選択")

    Python または R 言語のオプションを選択しない場合、セットアップ ウィザードは、言語固有のコンポーネントをインストールしないと SQL Server 信頼スタート パッドが含まれます extensibility framework のみをインストールします。  一般に、少なくとも 1 つの言語を最初にインストールすることをお勧めします。 ただし、すぐに、バインディング プロセスを使用して、機械学習のコンポーネントをアップグレードする場合は、このオプションを使用する場合があります。 詳細については、次を参照してください。 [R Services のインスタンスをアップグレードする使用 SqlBindR](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

    お勧めする**しない**同じコンピューターにスタンドアロンと、データベース内の機能をインストールし、同時にインストールしないことです。 通常、ソリューションを展開するときに、Machine Learning サーバー データ科学者や開発者は、接続に使用する環境を作成するには、(スタンドアロン) を SQL サーバーにインストールはします。 そのため、両方を同一のコンピューターにインストールする必要はありません。

4.  機械学習の契約のライセンスを取得します。 によっては、どの言語をインストールしている、R、Python、またはその両方のライセンス契約に同意する必要があります。

    + R: この使用許諾契約のライセンス条項は、オープン ソース R 基本パッケージとツール、拡張 R パッケージおよび接続プロバイダー、Microsoft 開発チームからのディストリビューションが含まれる Microsoft R Open、について説明します。
  
    + Python のライセンス条項。 Python のオープン ソース ライセンス契約は、Anaconda と関連するツール、および Microsoft 開発チームの一部の新しい Python ライブラリにも説明します。

    をクリックして**Accept**をアグリーメントを示します。 コンポーネントは、準備している間は一時停止、**次**ボタンができるようになります。

    使用しているコンピューターがインターネットにアクセスを持たない場合」の説明に従って、個別にインストーラーをダウンロードするには、この時点でセットアップを一時停止することができます:[インターネットにアクセスできないマシン ラーニング コンポーネントをインストール](installing-ml-components-without-internet-access.md)です。

6. **インストールの準備完了** ページで、次の項目が含まれています、ことを確認を選択し、**インストール**です。

   - データベース エンジン サービス
   - Machine Learning Services (データベース内)
   - R、Python、またはその両方

7. インストールが完了したら、セットアップ ログの場所をメモを行い、コンピューターを再起動します。

###  <a name="bkmk_enableFeature"></a>必要なインストール後の手順

セキュリティ上の理由から、マシン学習機能は無効既定では、機能がインストールされている場合でもです。 サーバー管理者は、機能を有効にする必要があり、インスタンスを再起動します。 

このセクションでは、機械学習のインスタンスを再構成する方法について説明します。 構成では、外部のサービス アカウントを設定し、スタート パッド サービスを開始します。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開きます。 まだインストールされていない場合は、SQL Server セットアップ ウィザードを再実行してダウンロード リンクを開き、インストールすることができます。
  
2. 機械学習がインストールされているインスタンスに接続し、次のコマンドを実行します。

   ```SQL
   sp_configure
   ```

    値を探して、**外部のスクリプトを有効になっている**対象となるプロパティ**0**します。 機能は、無効になって既定では、画面の領域を削減するためです。
     
3. 外部のスクリプト機能を有効にするには、次のステートメントを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
4. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの SQL Server サービスを再起動します。 SQL Server のサービスも自動的に再起動すると、関連する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

    使用してサービスを再起動することができます、 **Services**パネルまたは SQL Server 構成マネージャーを使用して、コントロール パネルの します。

5. SQL Server Management Studio で、外部スクリプト実行サービスを有効することを確認するには、新しい開きます**クエリ**ウィンドウ、および、次のコマンドを実行します。
  
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```
    この時点で、**run_value** が 1 に設定されている必要があります。
    
6. 開く、 **Services**パネル、およびスタート パッド サービスのインスタンスが実行されていることを確認してください。 複数のインスタンスをインストールした場合は、各インスタンスに独自のスタート パッド サービスがあります。

7. 外部スクリプトのランタイムは、SQL Server と通信できることを確認する単純なスクリプトを実行することをお勧めします。 

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

    スクリプトは、外部スクリプトの実行時の読み込みを初めて実行するときは少しことができます。 結果は、次のようにする必要があります。

    | hello |
    |----|
    | @shouldalert|


8. エラーが発生した場合は、インストールが完了したら、またはトラブルシューティング ガイドを参照する必要があります (省略可能) の変更を説明するセクションに進みます。

    + [省略可能なインストール後の手順: サービスと権限の構成](#bkmk_FollowUp) 
    + [機械学習で SQL Server のトラブルシューティング](upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="bkmk_FollowUp"></a>省略可能なインストール後の手順

機械学習、ユース ケースによっては、サーバー、ファイアウォールが、サービス、またはデータベースのアクセス許可が使用するアカウントに追加の変更を加える必要があります。 変更する必要がありますはケースによって異なります。

追加の変更を必要とする一般的なシナリオは次のとおりです。

* SQL Server への着信接続を許可するファイアウォール ルールを変更します。
* 追加のネットワーク プロトコルを有効にします。
* サーバーがリモート接続をサポートしていることを確認します。
* 有効にする*黙示的な認証*ユーザーがリモート データ サイエンス クライアントから SQL Server データにアクセスし、RODBC パッケージまたは他の ODBC プロバイダーを使用してコードを実行します。
* 個々 のデータベースへのアクセスをユーザーに付与します。
* スタート パッド サービスとの通信を妨げるセキュリティの問題を修正します。
* ユーザーがコードを実行したり、パッケージをインストールする権限を持っていることを確認できます。

> [!NOTE]
> 表示されているすべての変更は、必要があります。 ただし、すべての項目を自分のシナリオに該当するかどうかを確認することをお勧めします。

追加のトラブルシューティングのヒントをご覧ください:[アップグレードとインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)

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

ただし、エンタープライズのシナリオで、SQL ログインを使用して、データベースにアクセスするユーザーを含むほとんどのユーザーはありませんこのような高度な権限。 そのため、R または Python スクリプトを実行するユーザーごとに、外部スクリプトを使用する各データベースでスクリプトを実行するユーザーのアクセス許可を付与する必要があります。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> セットアップのヘルプが必要ですか。 すべての手順を実行したかわかりませんか。 これらのカスタム レポートを使用して、インストール状態をチェックして、追加の手順を実行します。 
> 
> [カスタム レポートを使用して、マシン学習サービスを監視](monitor-r-services-using-custom-reports-in-management-studio.md)です。

### <a name="ensure-that-the-sql-server-computer-supports-remote-connections"></a>SQL Server コンピューターがリモート接続をサポートしていることを確認してください。

リモート コンピューターから接続できない場合は、サーバーがリモート接続を許可するかどうかを確認します。 既定では、リモート接続は無効にことがあります。

また、ファイアウォールが SQL Server へのアクセスを許可するかどうかを確認します。 既定では、SQL Server で使用されるポートは多くの場合、ファイアウォールによってブロックされます。 Windows ファイアウォールを使用している場合は、次を参照してください。[データベース エンジン アクセス用に Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)です。

### <a name="give-your-users-read-write-or-ddl-permissions-to-the-database"></a>ユーザーの読み取り、書き込み、またはデータベースに DDL のアクセス許可を付与します。

R または Python の実行に使用するユーザー アカウント可能性があります必要がある他のデータベースからデータを読み取る、結果を格納する新しいテーブルを作成およびテーブルにデータを書き込みます。 そのため、ユーザーごとに実行されるように R または Python スクリプト、ユーザーがデータベースで適切な権限を持っていることを確認します*db_datareader*、 *db_datawriter*、または*作業。ddladmin*です。

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

SQL Server で、スクリプトの実行機能が動作することを確認した後は、SQL Server Management Studio、Visual Studio コード、またはサーバーに T-SQL ステートメントを送信できるその他のクライアントから R、Python のコマンドを実行できます。 これを行うには、前は機械学習の頻繁に使用をサポートするか、新しい R パッケージを追加するには、システム構成にいくつかの変更を加えることができます。

このセクションでは、いくつかの一般的な最適化と機械学習の学習活動を一覧表示します。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

頻度の高い、R を使用すると思われる場合、または同時に実行中のスクリプトに多数のユーザーの予定の場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server の Machine Learning のサービスのユーザー アカウント プールを変更する](modify-the-user-account-pool-for-sql-server-r-services.md)です。

### <a name="bkmk_optimize"></a>外部スクリプトの実行用のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査などを含むデータベース エンジンによってサポートされているサービスのさまざまなサーバーの分散を最適化するものでは、使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 したがって、既定の設定で、機械学習用リソースの制限やスロットルで調整、メモリを消費する操作で特にが場合がありますを見つける可能性があります。

Machine learning のジョブは優先順位を付けるしを適切なリソースには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更する可能性がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するのを参照してください。[外部リソース プールを作成して](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約されているメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)です。
  
- によって起動できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[機械学習のユーザー アカウント プールを変更する](modify-the-user-account-pool-for-sql-server-r-services.md)です。

Standard Edition を使用しており、リソース ガバナーを持っていない場合は、動的管理ビュー (Dmv) は、拡張イベントと Windows イベントの R. によって使用されているサーバーのリソースを管理するために、監視を使用することができます。詳細については、次を参照してください。[監視と R サービスを管理する](managing-and-monitoring-r-solutions.md)です。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

使用する、追加の R パッケージをインストールする分ほどをかかります。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールをした場合、あるいはユーザー ライブラリへのパッケージをインストールした場合は、T-SQL からこれらのパッケージを使用することはできません。

インストールして、R パッケージを管理するためのプロセスは、SQL Server 2016 および SQL Server 2017 で異なります。 たとえば、SQL Server の 2017 でするレベルでは、データベース、パッケージを共有するユーザー グループを設定またはユーザー独自のパッケージをインストールするデータベース ロールを構成します。 詳細については、次を参照してください。[パッケージの管理](r-package-management-for-sql-server-r-services.md)です。

SQL Server 2016 では、データベース管理者は、ユーザーが必要な R パッケージをインストールする必要があります。

管理アクセス権もインスタンス ライブラリに追加の Python パッケージのインストールに必要です。

### <a name="upgrade-the-machine-learning-components"></a>コンピューターをアップグレードするコンポーネントの学習

SQL Server の machine learning の機能をインストールするときに、リリースまたはサービス パックが発行されたときに、最新だった R または Python のコンポーネントのバージョンを取得します。 修正プログラムを適用したり、サーバーをアップグレードするたびに、マシン学習コンポーネントは、アップグレードもします。

ただし、機械学習はサポートされているよりも高速なスケジュールでコンポーネントをアップグレードすると呼ばれるプロセスを使用して、SQL Server のリリースによって_バインディング_です。 SQL Server インスタンスをバインドするときに両方 R または Python のバージョンをアップグレードしてより頻繁なアップグレードをサポートする別のサポート ポリシーを変更します。 

このようなアップグレードが含まれます。

* 新しい R パッケージ
+ などの Api を使用する Microsoft パッケージ[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)です。
* [モデルを事前トレーニング済み](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)イメージの分類とテキストの分析のためです。

SQL Server インスタンスをアップグレードする方法については、次を参照してください。[バインディングから machine learning のコンポーネントをアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。


### <a name="tutorials"></a>チュートリアル

簡単な例の概要を SQL Server での R の動作の基本については、次を参照してください。 [transact-sql を使用して R コード](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)です。

実際のシナリオに基づく機械学習の例を表示するを参照してください。[機械学習のチュートリアル](../tutorials/machine-learning-services-tutorials.md)です。

### <a name="troubleshooting"></a>トラブルシューティング

問題が発生した場合は、 アップグレードしようとしていますか。 よく寄せられる質問と既知の問題への回答は、次の記事を参照してください。

* [アップグレードとインストールに関する FAQ - Machine Learning サービス](upgrade-and-installation-faq-sql-server-r-services.md)

インスタンスのインストール状態をチェックして、一般的な問題を修正、これらのカスタム レポートを実行してください。

* [SQL Server R Services のカスタム レポート](\r\monitor-r-services-using-custom-reports-in-management-studio.md)
