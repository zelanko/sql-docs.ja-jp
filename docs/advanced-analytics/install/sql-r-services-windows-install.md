---
title: インストール SQL Server 2016 R Services (In-database) - SQL Server Machine Learning
description: R プログラミング言語のサポートを Windows 上の SQL Server 2016 R Services のデータベース エンジンを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/03/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bc9762470b6e2a836c29f53ebfc3ffeadbcc381f
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454686"
---
# <a name="install-sql-server-2016-r-services"></a>SQL Server 2016 R Services をインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、インストールして構成する方法を説明します**SQL Server 2016 R Services**します。 SQL Server 2016 をした場合は、SQL Server で R コードの実行を有効にするには、この機能をインストールします。

SQL Server 2017 での R 統合が提供されています[Machine Learning サービス](../r/r-server-standalone.md)Python の加算を反映します。 R 統合し SQL Server 2017 インストール メディアがある場合は、次を参照してください。 [SQL Server 2017 Machine Learning Services のインストール](sql-machine-learning-services-windows-install.md)機能を追加します。 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>インストール前のチェックリスト

+ データベース エンジンのインスタンスが必要です。 既存のインスタンスに増分追加できますが、だけの R をインストールすることはできません。

+ ビジネス継続性の[Always On 可用性グループ](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server)R サービスはサポートされています。 R サービスをインストールし、各ノードで、パッケージを構成する必要があります。

+ フェールオーバー クラスターに R Services をインストールできません。 R プロセスを分離するために使用されるセキュリティ メカニズムは、Windows Server フェールオーバー クラスター環境と互換性がありません。

+ ドメイン コント ローラーでは、R のサービスをインストールしません。 セットアップの R Services の部分は失敗します。

+ インストールしない**共有機能** > **R Server (スタンドアロン)** 同じコンピューター上の in-database インスタンスを実行します。 

  SQL Server インスタンスは、独自のコピーのオープン ソース R および Anaconda ディストリビューションを使用するため、R と Python の他のバージョンとサイド バイ サイドでインストールがあります。 ただし、SQL Server の外部の SQL Server コンピューターで R と Python を使用するコードを実行している可能性をさまざまな問題があります。
    
  + 別のライブラリと、さまざまな実行可能ファイルを使用して SQL Server で実行するときよりも、異なる結果を取得します。
  + リソースの競合をリードする、SQL Server が外部ライブラリで実行されている R と Python スクリプトを管理することはできません。
  
以前のバージョンの Revolution Analytics 開発環境または RevoScaleR パッケージを使用した場合、または SQL Server 2016 のプレリリース版をインストールした場合は、それらをアンインストールする必要があります。 RevoScaleR とその他の独自のパッケージのバージョンを実行することはできません。 以前のバージョンを削除することについては、次を参照してください。[アップグレードと SQL Server Machine Learning Services のインストールに関する FAQ](../r/upgrade-and-installation-faq-sql-server-r-services.md)します。

> [!IMPORTANT]
> セットアップが完了したら、必ずこの記事で説明されている追加の構成後の手順を完了してください。 この手順では、外部スクリプトを使用する SQL Server を有効にして、あなたに代わって R ジョブを実行する SQL Server に必要なアカウントを追加します。 構成の変更は、一般に、インスタンスの再起動またはスタート パッド サービスの再起動が必要です。

## <a name="get-the-installation-media"></a>インストール メディアを入手する

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>インストールのパッチ要件 

SQL Server の前提条件としてインストールされる特定のバージョンの Microsoft VC++ 2013 ランタイム バイナリに問題が見つかりました。 VC ランタイム バイナリに対するこの更新プログラムをインストールしないと、特定のシナリオにおいて、SQL Server で安定性の問題が発生する可能性があります。 SQL Server をインストールする前に、「[SQL Server リリース ノート](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)」にある手順に従って、ご使用のコンピューターに VC ランタイム バイナリのパッチが必要かどうかを確認してください。  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>セットアップの実行

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

## <a name="set-environment-variables"></a>環境変数な設定

R の機能統合のみに設定する必要があります、 **MKL_CBWR**環境変数を[出力を一貫性のある](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr)Intel 数値演算ライブラリ (MKL) 計算から。

1. コントロール パネルで、次のようにクリックします**システムとセキュリティ** > **システム** > **システムの詳細設定** >   **。環境変数**します。

2. 新しいユーザーまたはシステム変数を作成します。 

  + セットを変数名を指定 `MKL_CBWR`
  + 変数の値に設定します。 `AUTO`

この手順では、サーバーを再起動する必要があります。 スクリプトの実行を有効にしようとする場合は、すべての構成作業が完了するまでは、再起動時に留保することができます。

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>スクリプトの実行を有効にします。

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
     
3. 外部のスクリプト機能を有効にするには、次のステートメントを実行します。
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>サービスを再起動します。

インストールが完了したら、スクリプトの実行を有効にすると、次に進む前に、データベース エンジンを再起動します。

関連するサービスを再起動しても自動的に再起動[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

右クリックを使用してサービスを再起動する**再起動**コマンドを使用してまたは SSMS では、インスタンスを**サービス**パネル コントロール パネルで、またはを使用して[SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>インストールの確認

使用して、インスタンスのインストール状態を確認[カスタム レポート](../r/monitor-r-services-using-custom-reports-in-management-studio.md)します。

次の手順を使用すると、外部スクリプトを起動するのにために使用するすべてのコンポーネントが実行されていることを確認できます。

1. SQL Server Management studio で新しいクエリ ウィンドウを開き、次のコマンドを実行します。
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    この時点で、**run_value** が 1 に設定されている必要があります。

2. 開く、**サービス**パネルまたは SQL Server 構成マネージャー、ことを確認および**SQL Server スタート パッド サービス**が実行されています。 R がデータベース エンジンのインスタンスごとに 1 つのサービスが必要または Python をインストールします。 サービスの詳細については、次を参照してください。 [Extensibility framework](../concepts/extensibility-framework.md)します。

7. スタート パッドが実行されている場合は、外部スクリプトのランタイムは、SQL Server と通信できることを確認する単純な R を実行できる必要があります。 

    新しく開きます**クエリ**ウィンドウ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、次のようなスクリプトを実行します。
    
    ```sql
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

<a name="apply-cu"></a>

## <a name="apply-updates"></a>更新プログラムを適用します。

データベース エンジンと machine learning のコンポーネントの両方に、最新の累積的な更新プログラムを適用することをお勧めします。

インターネットに接続されたデバイスは、累積的更新プログラムは、Windows update では、一般的に適用されますが、制御された更新プログラムの次の手順を使用することもできます。 データベース エンジンの更新プログラムを適用するときは、同じインスタンスにインストールされている R ライブラリの累積的更新プログラムのセットアップが引き出されます。 

切断されたサーバーは、追加の手順が必要です。 詳細については、次を参照してください。[インターネット アクセスなしでコンピューターにインストール > の累積更新プログラムを適用](sql-ml-component-install-without-internet-access.md#apply-cu)します。

1. 既にインストールされているベースライン インスタンスで開始します。最初のリリースの SQL Server 2016、SQL Server 2016 SP 1、または SQL Server 2016 SP 2。

2. 累積更新プログラムの一覧を参照してください。[SQL Server 2016 更新プログラム](https://sqlserverupdates.com/sql-server-2016-updates/)

3. 最新の累積的な更新プログラムを選択します。 実行可能ファイルがダウンロードされ、自動的に抽出します。

4. セットアップを実行します。 ライセンス条項に同意し、[機能の選択] ページで、累積的更新プログラムの適用対象の機能を確認します。 R Services を含む、現在のインスタンスにインストールされているすべての機能が表示されます。 セットアップでは、すべての機能を更新するために必要な CAB ファイルをダウンロードします。

5. R のディストリビューションのライセンス条項を使用して、ウィザードの手順を続行します。 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>その他の構成

外部スクリプトの検証手順が成功した場合は、SQL Server Management Studio、Visual Studio Code、または T-SQL ステートメントをサーバーに送信できるその他のクライアントから Python のコマンドを実行できます。

コマンドの実行時にエラーを取得した場合は、このセクションでは追加の構成手順を確認します。 サービスまたはデータベースに追加の適切な構成を作成する必要があります。

インスタンス レベルでは、追加の構成が含まれます。

* [SQL Server Machine Learning サービスのファイアウォールの構成](../../advanced-analytics/security/firewall-configuration.md)
* [その他のネットワーク プロトコルを有効にします。](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [リモート接続を有効にします。](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [ディスク クォータ管理](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas)ディスク領域を使い果たすのあるタスクを実行している外部スクリプトを回避するには

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

データベースでは、次の構成の更新する必要があります。

* [SQL Server Machine Learning サービスへのアクセス許可をユーザーに付与します。](../../advanced-analytics/security/user-permission.md)
* [データベース ユーザーとしての SQLRUserGroup の追加](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

> [!NOTE]
> 表示されているすべての変更が必要ですと必要なしに可能性があります。 要件は、SQL Server、およびユーザーがデータベースに接続し、外部スクリプトの実行が予想される方法をインストールした、セキュリティ スキーマによって異なります。 追加のトラブルシューティングのヒントについてはここにあります。[アップグレードとインストールに関してよく寄せられる質問](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>提案されている最適化

、Machine learning をサポートするためにサーバーを最適化することもできたすべてを動作、または事前トレーニング済みモデルをインストールします。

### <a name="add-more-worker-accounts"></a>複数のワーカー アカウントを追加します。

頻度の高い、R を使用すると思われる場合、または実行中のスクリプトを同時に多くのユーザーが予想される場合は、スタート パッド サービスに割り当てられているワーカー アカウントの数を増やすことができます。 詳細については、次を参照してください。 [SQL Server Machine Learning Services のユーザー アカウント プールを変更](../administration/modify-user-account-pool.md)します。

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>外部スクリプト実行のサーバーを最適化します。

既定の設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セットアップは、データベース エンジンは、抽出、変換、および読み込み (ETL) プロセス、レポート、監査を含めることがでサポートされているサービスのさまざまなサーバーのバランスを最適化するためのものと使用するアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ。 そのため、既定の設定で、機械学習用リソースの場合もありますが制限または抑制され、メモリを消費する操作で特にを見つける可能性があります。

Machine learning ジョブは優先順位を設定しを適切にリソースを確認するには、SQL Server リソース ガバナーを使用して、外部リソース プールを構成することをお勧めします。 割り当てられているメモリの量を変更したい場合がありますも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース エンジン、または実行するアカウントの数を増やす、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]サービス。

- 外部リソースを管理するためのリソース プールを構成するを参照してください。[外部リソース プールの作成](../../t-sql/statements/create-external-resource-pool-transact-sql.md)です。
  
- データベースの予約済みメモリの量を変更するを参照してください。[サーバー メモリ構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)します。
  
- によって開始できる R アカウントの数を変更する[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]を参照してください[machine learning のユーザー アカウント プールを変更する](../administration/modify-user-account-pool.md)します。

Standard Edition を使用している、リソース ガバナーがない場合は、動的管理ビュー (Dmv) は、拡張イベントと監視には、R で使用されているサーバーのリソースを管理するために Windows イベントを使用することができます。詳細については、次を参照してください。[の監視と R Services を管理](../r/managing-and-monitoring-r-solutions.md)します。

### <a name="install-additional-r-packages"></a>追加の R パッケージをインストールします。

R ソリューションを SQL Server を作成する基本的な R 関数、SQL Server と共にインストールされている独自のパッケージと R パッケージのサード パーティからの関数は SQL Server がインストールされているオープン ソース R のバージョンと互換性のある呼び出すことができます。

SQL Server で使用するパッケージは、インスタンスによって使用される既定のライブラリにインストールする必要があります。 コンピューターで、R の別のインストールがある場合、またはユーザー ライブラリにパッケージをインストールした場合は、T-SQL からそれらのパッケージを使用することはできません。

インストールして、R パッケージを管理するためのプロセスでは、SQL Server 2016 および SQL Server 2017 で異なります。 SQL Server 2016 では、データベース管理者は、ユーザーが必要な R パッケージをインストールする必要があります。 SQL Server 2017 では、データベースごとのレベルでパッケージを共有するユーザー グループを設定するか、または独自のパッケージをインストールするユーザーを有効にするデータベース ロールを構成します。 詳細については、次を参照してください。[新しい R パッケージをインストール](../r/install-additional-r-packages-on-sql-server.md)します。

## <a name="next-steps"></a>次のステップ

R 開発者は、簡単な例で作業を開始し、SQL Server での R の動作の基本を学習します。 次の手順で、次のリンクを参照してください。

+ [チュートリアル: T-SQL での R を実行します。](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [チュートリアル: R の開発者向けのデータベース内分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

実際のシナリオに基づく機械学習の例を表示するを参照してください。 [Machine learning のチュートリアル](../tutorials/machine-learning-services-tutorials.md)します。