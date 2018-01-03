---
title: "SQL Server の外部スクリプトの実行に関する一般的な問題 |Microsoft ドキュメント"
ms.custom: SQL2016_New_Updated
ms.date: 10/11/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4f515ba26c4eeae70eaf9244c0eaedaa954954b4
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="common-issues-with-external-script-execution-in-sql-server"></a>SQL Server の外部スクリプトの実行に関する一般的な問題

この記事には、既知の問題と SQL Server で R または Python コードの実行に関する一般的な問題の一覧が含まれています。

作業を開始する前に、システムに関するいくつかの情報を収集することをお勧めします。 学習する方法についてを参照してください[トラブルシューティングのためのデータ収集](data-collection-ml-troubleshooting-process.md)です。

また、初期セットアップや構成に固有の一般的な問題の一覧を確認します。[セットアップおよびアップグレードに関する FAQ](r/upgrade-and-installation-faq-sql-server-r-services.md)です。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="launchpad-issues"></a>スタート パッドの問題

SQL Server の信頼されたスタート パッド サービスは、外部のスクリプトと R、Python、またはその他の外部のランタイムとの通信の実行を管理します。 複数の問題は、開始、構成の問題など、変更、またはネットワーク プロトコルがありませんからスタート パッドを防ぐことができます。

トラブルシューティング プロセスの一環として、次の質問に答えることで開始します。

- でしたスタート パッド常に実行が失敗する、または動作が停止しましたか。
- どのようなサービス アカウントは、スタート パッドで実行されているか。
- スタート パッド サービス アカウントには、どのようなユーザー権利がありますか。

### <a name="determine-whether-launchpad-is-running"></a>スタート パッドを実行するかどうかを調べる

1. 開く、 **Services**パネル (Services.msc)。 または、コマンドラインから入力**SQLServerManager13.msc**または**SQLServerManager14.msc**を開くには[SQL Server 構成マネージャー](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)です。

2. スタート パッドを実行しているサービス アカウントをメモしてをおきます。 R、または Python が有効になっている各インスタンスに対して独自のスタート パッド サービスのインスタンスが必要です。 たとえば、名前付きインスタンスのサービスようになります_MSSQLLaunchpad$ InstanceName_です。

3. サービスが停止している場合は再起動します。 構成で問題があるか、システム イベント ログにメッセージを公開およびサービスがもう一度停止している場合は再起動します。 詳細については、サービスが停止した理由に関するシステム イベント ログを確認します。

4. RSetup.log の内容を確認し、セットアップでエラーがないことを確認します。 たとえば、メッセージ*コード 0 で終了する*を開始するサービスの失敗を示します。

5. その他のエラーを探して rlauncher.log の内容を確認します。

### <a name="check-the-launchpad-service-account"></a>スタート パッド サービス アカウントを確認します。

既定のサービス アカウントである可能性があります"NT Service\$SQL2016"または"NT Service\$SQL2017"です。 最後の部分は、SQL インスタンス名によって異なる場合があります。

低い特権のサービス アカウントを使用して、スタート パッド サービス (Launchpad.exe) が実行されます。 ただし、R、Python を起動し、データベース インスタンスとの通信、スタート パッド サービス アカウント、次のユーザー権限が必要です。

- サービスとしてログオン (SeServiceLogonRight)
- プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)
- スキャン チェックを行わない (SeChangeNotifyPrivilege)
- (SeIncreaseQuotaSizePrivilege) プロセスに対してメモリ クォータを調整します。

これらのユーザー権利のについては、「Windows 特権と権利」のセクションを参照してください。[構成の Windows サービス アカウントと権限](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)です。

> [!TIP]
> SQL サーバーの診断のサポート診断プラットフォーム (SDP) ツールの使用に慣れている場合は、名前 MachineName_UserRights.txt の出力ファイルの確認を SDP を使用できます。

### <a name="review-launchpad-requirements"></a>スタート パッドの要件を確認します。

いくつかの問題のいずれかにより、スタート パッドを起動できなくなります。 スタート パッド サービスを開始および停止可能性があります。 またはクラッシュ、またはサービスは、接続タイムアウトを設定して停止可能性があります。 このような場合は、システムが通常されて変更されたかスタート パッドを実行できないように構成されています。

#### <a name="determine-whether-8dot3-notation-is-enabled"></a>8dot3 表記が有効かどうか

SQL Server 2016 R Services (In-database) を R では、互換性のためを使用して短いファイル名の作成をサポートするために、機能がインストールされているドライブを必要な*8dot3 表記*です。 8.3 ファイル名とも呼ばれますが、*短いファイル名*、または長いファイル名の代わりとして Microsoft Windows の以前のバージョンとの互換性のため使用されます。

R をインストールするボリュームが短いファイル名をサポートしていない場合は、SQL Server から R を起動するプロセスでは、正しい実行可能ファイルを検索できない可能性があり、スタート パッドは開始されません。

回避策としては、SQL Server がインストールされていると、R Services がインストールされているボリューム上の 8dot3 の表記が有効にできます。 次に、R Services 構成ファイルに作業ディレクトリの短い名前を指定する必要があります。

1. 8dot3 表記を有効にするで fsutil ユーティリティを実行、 *8dot3name*引数」の説明に従って: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx)です。

2. RLauncher.config ファイルを開き、8dot3 表記が有効にした後のプロパティに注意してください`WORKING_DIRECTORY`です。 このファイルを検索する方法については、次を参照してください。 [Machine Learning のトラブルシューティングのためのデータ収集](data-collection-ml-troubleshooting-process.md)です。

3. Fsutil ユーティリティを使用して、*ファイル*WORKING_DIRECTORY で指定されているフォルダーの短いファイル パスを指定する引数。

4. WORKING_DIRECTORY プロパティで指定した同じの作業ディレクトリを指定する構成ファイルを編集します。 または、別の作業ディレクトリを指定し、8dot3 表記と互換性が既に既存のパスを選択します。

> [!NOTE] 
> この制約はその後のリリースで除去されました。 この問題が発生した場合は、次のいずれかをインストールします。
> * SQL Server 2016 SP1 および CU1: [SQL Server の累積更新プログラム 1](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1)です。
> * SQL Server 2016 RTM、累積的な更新プログラム 3、およびそのこの[修正プログラム](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3)、これは要求時に使用します。

#### <a name="the-user-group-for-launchpad-cannot-log-on-locally"></a>スタート パッドのユーザー グループがローカルでログオンできません。

SQL Server が Windows ユーザー グループを作成する機械学習サービスのセットアップ中に**SQLRUserGroup**し、これをスタート パッドに SQL Server に接続し、外部スクリプトのジョブを実行するために必要なすべての権限を持つプロビジョニングとします。 このユーザー グループが有効になっている場合は、Python スクリプトの実行にも使用します。

ただし、組織では制限の厳しいセキュリティ ポリシーが適用されて、このグループに必要な権限が削除された可能性が手動で、またはポリシーによって自動的に失効する可能性があります。 権限が削除されている場合は、スタート パッドが SQL Server に接続できなくと SQL Server は、外部のランタイムを呼び出すことはできません。

問題を解決するには、グループ **SQLRUserGroup** に**ローカルのログオンを許可する**システム権限があることを確認します。

詳細については、次を参照してください。[構成の Windows サービス アカウントと権限](https://msdn.microsoft.com/library/ms143504.aspx#Windows)です。

#### <a name="improper-setup-leading-to-mismatched-dlls"></a>先頭の不一致の Dll に不適切なセットアップ

他の機能では、patch、サーバーとデータベース エンジンをインストールして、元のメディアを使用して、機械学習機能を後で追加、間違ったバージョンの Machine Learning のコンポーネントをインストールする可能性があります。 スタート パッドは、バージョンの不一致を検出すると、シャット ダウンし、ダンプ ファイルを作成します。

この問題を避けるためには、必ずサーバー インスタンスとして同じパッチ レベルに新機能をインストールします。

**間違ったやり方をアップグレードする:**

1. R Services なしの SQL Server 2016 をインストールします。
2. SQL Server 2016 Cumulative Update 2 にアップグレードします。
3. R Services (In-database) をインストールするには、RTM メディアを使用します。

**アップグレードを適切な方法:**

1. R Services なしの SQL Server 2016 をインストールします。
2. SQL Server 2016 を必要な修正プログラムのレベルにアップグレードします。 たとえば、Service Pack 1 とし、累積更新プログラム 2 をインストールします。
3. 修正レベルで機能を追加するに SP1 および CU2 のセットアップを再実行し、R Services (In-database) を選択します。 

#### <a name="check-whether-a-user-has-rights-to-run-external-scripts"></a>ユーザーが外部のスクリプトを実行する権限を持っているかどうかを確認します。

スタート パッドが正しく構成されている場合でもは、ユーザーが R または Python スクリプトを実行するアクセス許可を持たない場合、エラーを返します。

データベース管理者が、SQL Server がインストールされている、またはデータベースの所有者は、このアクセス許可が自動的に付与されます。 ただし、他のユーザー通常より権限が制限されます。 R スクリプトを実行しようとすると、それらと、スタート パッドのエラーが発生します。

SQL Server Management Studio での問題を解決するのには、セキュリティ管理者は、次のスクリプトを実行しても、SQL ログインまたは Windows ユーザー アカウントに変更できます。

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

詳細については、次を参照してください。 [GRANT (TRANSACT-SQL](../t-sql/statements/grant-transact-sql.md)です。

### <a name="common-launchpad-errors"></a>スタート パッドの一般的なエラー

このセクションでは、スタート パッドを返す最も一般的なエラー メッセージを一覧表示します。

#### <a name="error-unable-to-launch-runtime-for-r-script"></a>エラー:*ランタイム R スクリプトを起動できませんでした。*

(Python の使用も) R ユーザーの Windows グループが R Services を実行しているインスタンスにログオンできない場合は、次のエラーを参照してください可能性があります。

- R スクリプトを実行しようとしたときに生成されるエラー:

    * *'R' スクリプトのランタイムを起動できません。'R' ランタイムの構成を確認してください。*

    * *外部スクリプト エラーが発生しました。ランタイムを起動できません。*

- によって生成されたエラー、[!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)]サービス。

    * *ランチャー RLauncher.dll を初期化できませんでした*

    * *ランチャー dll が登録されていません!*

    * *セキュリティ ログは、NT サービス アカウントがログオンできなかったことを示します*

このユーザー グループに必要なアクセス許可を付与する方法については、次を参照してください。 [SQL Server R Services セットアップ](r/set-up-sql-server-r-services-in-database.md)です。

> [!NOTE]
> SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。

#### <a name="error-logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>エラー:*ログオン エラー: 要求されたログオンの種類は、ユーザーに許可されていません*

既定では、[!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)]起動時に次のアカウントを使用して:`NT Service\MSSQLLaunchpad`です。 によって、アカウントが構成されている[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]セットアップにすべての必要な権限を付与します。

スタート パッドに、別のアカウントを割り当てる、または権利を削除する SQL Server コンピューターのポリシーをアカウントが必要なアクセス許可がないと、このエラーを発生する可能性があります。

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Logon failure: the user has not been granted the requested logon type at this computer*

新しいサービス アカウントに必要なアクセス許可を付与するには、ローカル セキュリティ ポリシーのアプリケーションを使用し、アカウントのアクセス許可を次のアクセス許可を含めるを更新します。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

#### <a name="error-unable-to-communicate-with-the-launchpad-service"></a>エラー:*スタート パッド サービスと通信できません*

インストールし、機械学習を有効にした R または Python スクリプトを実行しようとしたときにこのエラーが発生した場合を実行している、インスタンスのスタート パッド サービスを停止した可能性があります。

1. Windows コマンド プロンプトから SQL Server 構成マネージャーを開きます。 詳細については、「 [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)」を参照してください。

2. インスタンスについて、SQL Server スタート パッドを右クリックし **プロパティ**です。

3. 選択、**サービス**タブをクリックし、サービスが実行されていることを確認します。 実行されていない場合は、変更、**開始モード**に**自動**、し、**適用**です。

4. Machine learning のスクリプトを実行できるように、問題を修正通常、サービスを再起動します。 再起動に問題が解決しない場合、パスおよび引数を注意してください。、**バイナリ パス**プロパティ、および、次の操作。

    A. 起動の .config ファイルを確認し、作業ディレクトリが有効であることを確認します。

    B. スタート パッドで使用される Windows グループが、SQL Server インスタンスに接続できることを確認してください」の説明に従って、[前のセクション](#bkmk_LaunchpadTS)です。

    c. サービスのプロパティを変更する場合は、スタート パッド サービスを再起動します。

#### <a name="error-fatal-error-creation-of-tmpfile-failed"></a>エラー: *tmpFile の致命的なエラーを作成できませんでした*

このシナリオでは、マシン学習機能が正常にインストールし、スタート パッドを実行しています。 単純な R または Python コードを実行しようとするはスタート パッドが次のようなエラーで失敗します。 

>*R スクリプトのランタイムと通信できません。R ランタイムの要件を確認してください。*

同時に、外部スクリプトの実行時は STDERR メッセージの一部として、次のメッセージを書き込みます。 

>*致命的なエラー: 失敗 tmpfile を作成します。*

このエラーは、スタート パッドを使用して試みているアカウントに、データベースにログオンする権限がないことを示します。 このような状況は、厳密なセキュリティ ポリシーが実装された場合に発生します。 これは、大文字と小文字であるかどうかを決定するには、SQL Server ログを確認して、MSSQLSERVER01 アカウントがログインで拒否されたかどうかを確認します。 R に固有のログで、同じ情報が提供される\_SERVICES または PYTHON\_SERVICES です。 ExtLaunchError.log を探します。

既定では、20 のアカウントを設定し、MSSQLSERVER20 を介して名前 MSSQLSERVER01、Launchpad.exe プロセスに関連付けられています。 R、Python または頻繁に使用する場合は、アカウントの数を増やすことができます。

この問題を解決するには、グループがあることを確認します*ローカル ログオンを許可する*machine learning の機能をインストールおよび有効になっているローカル インスタンスへのアクセス許可。 一部の環境でこのアクセス許可レベルは、ネットワーク管理者から GPO の例外を必要があります。

## <a name="r-script-issues"></a>R スクリプトの問題

このセクションには、R スクリプトを実行し、R スクリプトのエラーに固有のいくつかの一般的な問題が含まれています。 一覧ではありません、包括的な R パッケージが多数あるし、エラーは、同じの R パッケージのバージョン間で異なる場合があります。 R スクリプトのエラーを投稿することをお勧め、 [Microsoft R Server フォーラム](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR)をサポートする、機械学習 R Services (In-database)、Python、Microsoft R クライアント、および Microsoft R でマシン学習サービスで使用されるコンポーネントサーバー。

### <a name="multiple-r-instances-on-the-same-computer"></a>同じコンピューター上の複数の R インスタンス

さまざまなバージョンで、同じの R パッケージの複数のコピーと同様に、同じコンピューター上の R の複数のディストリビューション気づいたらやすいことができます。 たとえば、Machine Learning Server (スタンドアロン) と Machine Learning Services (In-database) の両方をインストールする場合、インストーラーは別のバージョンの R ライブラリを作成します。 

コマンドラインからスクリプトを実行しようとして、使用しているどのライブラリがわからない場合に、このような重複は問題になります。 または、誤って別のライブラリにパッケージをインストールし、後で不思議に思えるかもしれません SQL Server からパッケージを見つけられない理由があります。

+ 新しいパッケージのインストールまたはの R ライブラリとツールがインストールされている SQL Server インスタンスを使用するため除くトラブルシューティングなど、限られた場合を直接使用しないでください。 
+ インストールすることができます、R コマンド ライン ツールを使用する必要がある場合[Microsoft R クライアント](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client)です。 
+ SQL Server では、R パッケージのデータベース内の管理を提供します。 これは、ユーザー間で共有できる R パッケージ ライブラリを作成する最も簡単な方法です。 詳細については、次を参照してください。 [for SQL Server の R パッケージの管理](r/r-package-management-for-sql-server-r-services.md)です。

### <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>SQL のコンピューティング コンテキストで R を実行しているときに、ワークスペースをオフにしないで

R コンソールで作業するときは、一般的なは、ワークスペースをオフにして、そのことが予期しない結果に、SQL の計算コンテキスト。

`revoScriptConnection`SQL Server から呼び出される R セッションに関する情報を含む R ワークスペースにオブジェクト。 ただしかどうか、R コードは ワークスペースをオフにするコマンド (など`rm(list=ls())`)、セッションとの R ワークスペースには、他のオブジェクトに関するすべての情報はもオフにします。

この問題を回避するには、SQL Server で R を実行しているときに、変数およびその他のオブジェクトの区別しないで消去しないでください。 使用して特定の変数を削除することができます、**削除**関数。

```R
remove('name1', 'name2', ...)
```

複数の変数を削除する場合は、一時変数の名前を一覧に保存し、一覧に定期的なガベージ コレクションを実行お勧めします。

### <a name="implied-authentication-for-remote-execution-via-odbc"></a>ODBC 経由でリモート実行の暗黙の認証

接続する場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] R を実行するコンピューターのコマンドを使用して、 **RevoScaleR**関数、サーバーにデータを書き込む ODBC 呼び出しを使用するとエラーを発生可能性があります。 このエラーは、Windows 認証を使用している場合にのみ発生します。

R Services に対して作成されるワーカー アカウントに、サーバーに接続する権限がないことです。 したがって、あなたの代理として ODBC 呼び出しを実行できません。 問題は、ため、SQL ログインを持つ資格情報は、明示的にクライアントから渡される、R し、次の SQL Server インスタンスに ODBC に SQL ログインを持つ生じません。 ただし、SQL ログインを使用しても安全性は低く Windows 認証を使用するよりもします。

リモートでの SQL Server が開始したスクリプトから安全に渡される Windows 資格情報を有効にするには、資格情報をエミュレートする必要があります。 このプロセスと呼ばれる_黙示的な認証_です。 この作業をするためには、SQL Server コンピューターの R または Python スクリプトを実行しているワーカー アカウントが適切なアクセス許可が必要です。

1. 開いている[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]R コードを実行するインスタンスの管理者として。

2. 次のスクリプトを実行します。 ユーザー グループの場合、名前、既定値を変更して、コンピューター名とインスタンス名を編集することを確認します。

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

### <a name="the-r-script-works-outside-of-t-sql-but-not-in-a-stored-procedure"></a>T-SQL の外部で、ストアド プロシージャではなく、R スクリプトの動作します。

ストアド プロシージャで R コードをラップする前に、外部の IDE でまたは RTerm RGui などの R ツールのいずれかの R コードを実行することをお勧めします。 これらのメソッドを使用するには、テストおよび R. によって返される詳細なエラー メッセージを使用してコードをデバッグすることができます。

ただし、場合があります、外部の IDE またはユーティリティで完全に動作するコードが失敗するストアド プロシージャの実行または SQL Server のコンピューティング コンテキストにします。 このような場合は、さまざまなパッケージを SQL Server で動作しないことを想定する前に検索する問題があります。

1. スタート パッドが実行されているかどうかを確認します。

2. メッセージ入力データまたは出力データに互換性がないか、サポートされていないデータ型の列が含まれているかどうかを確認します。 たとえば、SQL データベースでクエリは、Guid または RowGUIDs、どちらもサポートされていないを多くの場合、返されます。 詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

3. SQL Server のコンピューティング コンテキストのすべてのパラメーターがサポートされているかどうかを決定する個々 の R 関数のヘルプ ページを確認します。 ScaleR ヘルプ コマンドを使用して、インライン R ヘルプ、または参照してください[パッケージ参照](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)です。

### <a name="you-get-different-results-from-the-same-script-when-running-in-sql-compared-to-other-environments"></a>SQL と比較してその他の環境で実行されているときに、同じスクリプトから異なる結果を取得します。

R スクリプトは、いくつかの理由、SQL Server のコンテキストで別の値を返すことができます。

- 暗黙の型変換は、データが SQL Server と R. の間で渡されるときに、自動的に一部のデータ型の実行します。詳細については、次を参照してください。 [R ライブラリとデータ型](r/r-libraries-and-data-types.md)です。

- ビット数が倍であるかどうかを確認します。 たとえば、32 ビットおよび 64 ビットの浮動小数点ポイント ライブラリの算術演算の結果の違いは少なくありません。

- NaNs が任意の操作で生成されたかどうかを決定します。 結果がこれを無効にできます。

- ゼロに近い数値の逆数を取得すると、若干の違いが増幅されることができます。

- 蓄積されたエラーの丸めなどの値がゼロではなく 0 未満にする可能性があります。

### <a name="error-not-enough-quota-to-process-this-command"></a>エラー:*このコマンドを処理するのに十分なクォータ*

このエラーは、いくつかの方法のいずれかの意味があります。

- スタート パッドは、外部のクエリを実行するが不足している外部ユーザーがあります。 たとえば、同時に、20 を超える外部クエリを実行しているだけ 20 の既定のユーザーがある場合は、1 つまたは複数のクエリが失敗します。

- R タスクの処理に使用できるは、メモリ不足です。 このエラーは、環境では、既定で SQL Server 可能性がありますを使用しているコンピューターのリソースの 70% までを頻繁に起こります。 R でリソースの大きい値の使用をサポートするためにサーバーの構成を変更する方法については、次を参照してください。 [R コードの運用](r/operationalizing-your-r-code.md)です。

### <a name="error-cant-find-package"></a>エラー:*パッケージを見つけることができません*

場合は SQL Server で R コードを実行し、このメッセージが表示される SQL Server の外部、同じコードを実行したときに、メッセージを取得できませんでした、パッケージが SQL Server で使用される既定ライブラリの場所にインストールされていないことを意味します。

このエラーは、さまざまな方法で発生することができます。

- サーバーで、新しいパッケージをインストールしたが、R では、ユーザーのライブラリにパッケージがインストールされているため、アクセスが拒否されました。

- R Services をインストールし、別の R ツールをインストールまたは Microsoft R Server (スタンドアロン)、Microsoft R クライアント RStudio など、ライブラリの設定し、などです。

インスタンスによって使用される R パッケージ ライブラリの場所を特定するのには、SQL Server Management Studio (またはその他のデータベースのクエリ ツール) を開きます、インスタンスに接続および次のストアド プロシージャを実行します。

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>サンプルの結果

*外部スクリプトからの STDOUT メッセージ:*

*[1]"c:\\プログラム ファイル\\Microsoft SQL Server\\MSSQL13 です。SQL2016\\R_SERVICES"*

*[1]"c:/program ファイルまたは Microsoft SQL Server/MSSQL13 です。SQL2016/R_SERVICES/ライブラリ"*

問題を解決するには、SQL Server インスタンスのライブラリにパッケージを再インストールする必要があります。

>[!NOTE]
>Microsoft R の最新バージョンを使用する SQL Server 2016 のインスタンスをアップグレードした場合は、既定のライブラリの場所は異なります。 詳細については、次を参照してください。 [R Services のインスタンスをアップグレードする使用 SqlBindR](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

## <a name="next-steps"></a>次の手順

[Machine Learning のサービスのトラブルシューティングと既知の問題](machine-learning-troubleshooting-faq.md)

[機械学習のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

[アップグレードとインストールに関してよく寄せられる質問](r/upgrade-and-installation-faq-sql-server-r-services.md)

[データベース エンジンの接続をトラブルシューティングします。](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
