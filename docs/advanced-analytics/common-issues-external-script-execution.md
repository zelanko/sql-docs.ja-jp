---
title: スタート パッド サービスと SQL Server の外部スクリプト実行の一般的な問題 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 08ab6e2db6d6cde5e41f7ddb88c8afd1da241df7
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34706840"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>スタート パッド サービスと SQL Server の外部スクリプト実行の一般的な問題
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 SQL Server の信頼されたスタート パッド サービスは、R、Python の外部スクリプトの実行をサポートします。 SQL Server 2016 の R Services では、SP1 は、サービスを提供します。 SQL Server 2017 には、初期インストールの一部としてスタート パッドの表記が含まれています。

複数の問題は、開始、構成の問題など、変更、またはネットワーク プロトコルがありませんからスタート パッドを防ぐことができます。 この記事では、多くの問題のトラブルシューティングのガイダンスを提供します。 いずれかが実行されなかった場合に質問を投稿することができます、 [Machine Learning Server フォーラム](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR)です。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="determine-whether-launchpad-is-running"></a>スタート パッドを実行するかどうかを調べる

1. 開く、 **Services**パネル (Services.msc)。 または、コマンドラインから入力**SQLServerManager13.msc**または**SQLServerManager14.msc**を開くには[SQL Server 構成マネージャー](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)です。

2. スタート パッドを実行しているサービス アカウントをメモしてをおきます。 R、または Python が有効になっている各インスタンスに対して独自のスタート パッド サービスのインスタンスが必要です。 たとえば、名前付きインスタンスのサービスようになります_MSSQLLaunchpad$ InstanceName_です。

3. サービスが停止している場合は再起動します。 構成で問題があるか、システム イベント ログにメッセージを公開およびサービスがもう一度停止している場合は再起動します。 詳細については、サービスが停止した理由に関するシステム イベント ログを確認します。

4. RSetup.log の内容を確認し、セットアップでエラーがないことを確認します。 たとえば、メッセージ*コード 0 で終了する*を開始するサービスの失敗を示します。

5. その他のエラーを探して rlauncher.log の内容を確認します。

## <a name="check-the-launchpad-service-account"></a>スタート パッド サービス アカウントを確認します。

既定のサービス アカウントである可能性があります"NT Service\$SQL2016"または"NT Service\$SQL2017"です。 最後の部分は、SQL インスタンス名によって異なる場合があります。

低い特権のサービス アカウントを使用して、スタート パッド サービス (Launchpad.exe) が実行されます。 ただし、R、Python を起動し、データベース インスタンスとの通信、スタート パッド サービス アカウント、次のユーザー権限が必要です。

- サービスとしてログオン (SeServiceLogonRight)
- プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)
- スキャン チェックを行わない (SeChangeNotifyPrivilege)
- (SeIncreaseQuotaSizePrivilege) プロセスに対してメモリ クォータを調整します。

これらのユーザー権利のについては、「Windows 特権と権利」のセクションを参照してください。[構成の Windows サービス アカウントと権限](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)です。

> [!TIP]
> SQL サーバーの診断のサポート診断プラットフォーム (SDP) ツールの使用に慣れている場合は、名前 MachineName_UserRights.txt の出力ファイルの確認を SDP を使用できます。

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>スタート パッドのユーザー グループがローカルでログオンできません。

SQL Server が Windows ユーザー グループを作成する機械学習サービスのセットアップ中に**SQLRUserGroup**し、これをスタート パッドに SQL Server に接続し、外部スクリプトのジョブを実行するために必要なすべての権限を持つプロビジョニングとします。 このユーザー グループが有効になっている場合は、Python スクリプトの実行にも使用します。

ただし、組織では制限の厳しいセキュリティ ポリシーが適用されて、このグループに必要な権限が削除された可能性が手動で、またはポリシーによって自動的に失効する可能性があります。 権限が削除されている場合は、スタート パッドが SQL Server に接続できなくと SQL Server は、外部のランタイムを呼び出すことはできません。

問題を解決するには、グループ **SQLRUserGroup** に**ローカルのログオンを許可する**システム権限があることを確認します。

詳細については、次を参照してください。[構成の Windows サービス アカウントと権限](https://msdn.microsoft.com/library/ms143504.aspx#Windows)です。

## <a name="permissions-to-run-external-scripts"></a>外部スクリプトを実行するアクセス許可

スタート パッドが正しく構成されている場合でもは、ユーザーが R または Python スクリプトを実行するアクセス許可を持たない場合、エラーを返します。

データベース管理者が、SQL Server がインストールされている、またはデータベースの所有者は、このアクセス許可が自動的に付与されます。 ただし、他のユーザー通常より権限が制限されます。 R スクリプトを実行しようとすると、それらと、スタート パッドのエラーが発生します。

SQL Server Management Studio での問題を解決するのには、セキュリティ管理者は、次のスクリプトを実行しても、SQL ログインまたは Windows ユーザー アカウントに変更できます。

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

詳細については、次を参照してください。 [GRANT (TRANSACT-SQL](../t-sql/statements/grant-transact-sql.md)です。

## <a name="common-launchpad-errors"></a>スタート パッドの一般的なエラー

このセクションでは、スタート パッドを返す最も一般的なエラー メッセージを一覧表示します。

## <a name="unable-to-launch-runtime-for-r-script"></a>「R スクリプトのランタイムを起動できませんでした」

(Python の使用も) R ユーザーの Windows グループが R Services を実行しているインスタンスにログオンできない場合は、次のエラーを参照してください可能性があります。

- R スクリプトを実行しようとしたときに生成されるエラー:

    * *'R' スクリプトのランタイムを起動できません。'R' ランタイムの構成を確認してください。*

    * *外部スクリプト エラーが発生しました。ランタイムを起動できません。*

- によって生成されたエラー、[!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)]サービス。

    * *ランチャー RLauncher.dll を初期化できませんでした*

    * *ランチャー dll が登録されていません!*

    * *セキュリティ ログは、NT サービス アカウントがログオンできなかったことを示します*

このユーザー グループに必要なアクセス許可を付与する方法については、次を参照してください。 [SQL Server の 2016 R Services をインストール](install/sql-r-services-windows-install.md)です。

> [!NOTE]
> SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"ログオン エラー: 要求されたログオンの種類は、ユーザーに許可されていません"

既定では、[!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)]起動時に次のアカウントを使用して:`NT Service\MSSQLLaunchpad`です。 によって、アカウントが構成されている[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]セットアップにすべての必要な権限を付与します。

スタート パッドに、別のアカウントを割り当てる、または権利を削除する SQL Server コンピューターのポリシーをアカウントが必要なアクセス許可がないと、このエラーを発生する可能性があります。

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Logon failure: the user has not been granted the requested logon type at this computer*

新しいサービス アカウントに必要なアクセス許可を付与するには、ローカル セキュリティ ポリシーのアプリケーションを使用し、アカウントのアクセス許可を次のアクセス許可を含めるを更新します。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>「スタート パッド サービスと通信できませんでした」

インストールし、機械学習を有効にした R または Python スクリプトを実行しようとしたときにこのエラーが発生した場合を実行している、インスタンスのスタート パッド サービスを停止した可能性があります。

1. Windows コマンド プロンプトから SQL Server 構成マネージャーを開きます。 詳細については、「 [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)」を参照してください。

2. インスタンスについて、SQL Server スタート パッドを右クリックし **プロパティ**です。

3. 選択、**サービス**タブをクリックし、サービスが実行されていることを確認します。 実行されていない場合は、変更、**開始モード**に**自動**、し、**適用**です。

4. Machine learning のスクリプトを実行できるように、問題を修正通常、サービスを再起動します。 再起動に問題が解決しない場合、パスおよび引数を注意してください。、**バイナリ パス**プロパティ、および、次の操作。

    A. 起動の .config ファイルを確認し、作業ディレクトリが有効であることを確認します。

    B. スタート パッドで使用される Windows グループが、SQL Server インスタンスに接続できることを確認してください」の説明に従って、[前のセクション](#bkmk_LaunchpadTS)です。

    c. サービスのプロパティを変更する場合は、スタート パッド サービスを再起動します。

## <a name="fatal-error-creation-of-tmpfile-failed"></a>「TmpFile の致命的なエラーの作成に失敗しました」

このシナリオでは、マシン学習機能が正常にインストールし、スタート パッドを実行しています。 単純な R または Python コードを実行しようとするはスタート パッドが次のようなエラーで失敗します。 

>*R スクリプトのランタイムと通信できません。R ランタイムの要件を確認してください。*

同時に、外部スクリプトの実行時は STDERR メッセージの一部として、次のメッセージを書き込みます。 

>*致命的なエラー: 失敗 tmpfile を作成します。*

このエラーは、スタート パッドを使用して試みているアカウントに、データベースにログオンする権限がないことを示します。 このような状況は、厳密なセキュリティ ポリシーが実装された場合に発生します。 これは、大文字と小文字であるかどうかを決定するには、SQL Server ログを確認して、MSSQLSERVER01 アカウントがログインで拒否されたかどうかを確認します。 R に固有のログで、同じ情報が提供される\_SERVICES または PYTHON\_SERVICES です。 ExtLaunchError.log を探します。

既定では、20 のアカウントを設定し、MSSQLSERVER20 を介して名前 MSSQLSERVER01、Launchpad.exe プロセスに関連付けられています。 R、Python または頻繁に使用する場合は、アカウントの数を増やすことができます。

この問題を解決するには、グループがあることを確認します*ローカル ログオンを許可する*machine learning の機能をインストールおよび有効になっているローカル インスタンスへのアクセス許可。 一部の環境でこのアクセス許可レベルは、ネットワーク管理者から GPO の例外を必要があります。

## <a name="not-enough-quota-to-process-this-command"></a>「このコマンドを処理するクォータが十分ではありません」

このエラーは、いくつかの方法のいずれかの意味があります。

- スタート パッドは、外部のクエリを実行するが不足している外部ユーザーがあります。 たとえば、同時に、20 を超える外部クエリを実行しているだけ 20 の既定のユーザーがある場合は、1 つまたは複数のクエリが失敗します。

- R タスクの処理に使用できるは、メモリ不足です。 このエラーは、環境では、既定で SQL Server 可能性がありますを使用しているコンピューターのリソースの 70% までを頻繁に起こります。 R でリソースの大きい値の使用をサポートするためにサーバーの構成を変更する方法については、次を参照してください。 [R コードの運用](r/operationalizing-your-r-code.md)です。

## <a name="cant-find-package"></a>「パッケージが見つかりません」

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

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>スタート パッドが一致していない Dll によりシャット ダウン

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

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>スタート パッドの 8dot3 表記が必要な場合の開始に失敗します。

> [!NOTE] 
> 以前のシステムでスタート パッドは 8dot3 表記要件がある場合の開始に失敗します。 この要件は、今後のリリースで削除されました。 SQL Server 2016 の R Services のお客様は、次のいずれかをインストールしてください。
> * SQL Server 2016 SP1 および CU1: [SQL Server の累積更新プログラム 1](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1)です。
> * SQL Server 2016 RTM、累積的な更新プログラム 3、およびそのこの[修正プログラム](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3)、これは要求時に使用します。

SQL Server 2016 R Services (In-database) を R では、互換性のためを使用して短いファイル名の作成をサポートするために、機能がインストールされているドライブを必要な*8dot3 表記*です。 8.3 ファイル名とも呼ばれますが、*短いファイル名*、または長いファイル名の代わりとして Microsoft Windows の以前のバージョンとの互換性のため使用されます。

R をインストールするボリュームが短いファイル名をサポートしていない場合は、SQL Server から R を起動するプロセスでは、正しい実行可能ファイルを検索できない可能性があり、スタート パッドは開始されません。

回避策としては、SQL Server がインストールされていると、R Services がインストールされているボリューム上の 8dot3 の表記が有効にできます。 次に、R Services 構成ファイルに作業ディレクトリの短い名前を指定する必要があります。

1. 8dot3 表記を有効にするで fsutil ユーティリティを実行、 *8dot3name*引数」の説明に従って: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx)です。

2. RLauncher.config ファイルを開き、8dot3 表記が有効にした後のプロパティに注意してください`WORKING_DIRECTORY`です。 このファイルを検索する方法については、次を参照してください。 [Machine Learning のトラブルシューティングのためのデータ収集](data-collection-ml-troubleshooting-process.md)です。

3. Fsutil ユーティリティを使用して、*ファイル*WORKING_DIRECTORY で指定されているフォルダーの短いファイル パスを指定する引数。

4. WORKING_DIRECTORY プロパティで指定した同じの作業ディレクトリを指定する構成ファイルを編集します。 または、別の作業ディレクトリを指定し、8dot3 表記と互換性が既に既存のパスを選択します。


## <a name="next-steps"></a>次のステップ

[Machine Learning のサービスのトラブルシューティングと既知の問題](machine-learning-troubleshooting-faq.md)

[機械学習のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

[アップグレードとインストールに関してよく寄せられる質問](r/upgrade-and-installation-faq-sql-server-r-services.md)

[データベース エンジンの接続をトラブルシューティングします。](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
