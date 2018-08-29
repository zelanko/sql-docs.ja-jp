---
title: スタート パッド サービスと SQL Server の外部スクリプトの実行に関する一般的な問題 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9a556a83e57dc41109914ff9da82405abd8b24e1
ms.sourcegitcommit: e4e9f02b5c14f3bb66e19dec98f38c012275b92c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "43118410"
---
# <a name="common-issues-with-launchpad-service-and-external-script-execution-in-sql-server"></a>スタート パッド サービスと SQL Server の外部スクリプトの実行に関する一般的な問題
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

 SQL Server Trusted Launchpad サービスは、R と Python の外部スクリプトの実行をサポートします。 SQL Server 2016 R Services では、SP1 は、サービスを提供します。 SQL Server 2017 には、初期インストールの一部としてスタート パッドの表記が含まれています。

複数の問題は、開始、構成の問題など、変更、またはネットワーク プロトコルがありませんからスタート パッドを防ぐことができます。 この記事では、多くの問題のトラブルシューティングの指針を提供します。 イテレーションのいずれに質問を投稿できます、 [Machine Learning Server フォーラム](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR)します。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス

## <a name="determine-whether-launchpad-is-running"></a>スタート パッドが実行されているかどうかを判断します。

1. 開く、**サービス**パネル (Services.msc)。 または、コマンドラインから次のように入力します。 **SQLServerManager13.msc**または**SQLServerManager14.msc**を開く[SQL Server 構成マネージャー](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)します。

2. スタート パッドが実行されているサービス アカウントをメモしてをおきます。 R または Python が有効になっているインスタンスごとに独自のスタート パッド サービス インスタンスが必要です。 たとえば、名前付きインスタンスのサービスなどになります_MSSQLLaunchpad$ InstanceName_します。

3. サービスが停止している場合は再起動します。 構成で問題があるか、システム イベント ログにメッセージが発行およびサービスがもう一度停止している場合は再起動します。 詳細については、サービスが停止した理由について、システム イベント ログを確認します。

4. RSetup.log の内容を確認し、セットアップ時にエラーがないことを確認します。 たとえば、メッセージ*コード 0 で終了*を開始するサービスの失敗を示します。

5. 他のエラーを検索するには、rlauncher.log の内容を確認します。

## <a name="check-the-launchpad-service-account"></a>スタート パッド サービス アカウントを確認してください。

既定のサービス アカウントがあります"NT Service\$SQL2016"または"NT Service\$SQL2017"。 最後の部分は、SQL インスタンスの名前に応じて異なる場合があります。

スタート パッド サービス (Launchpad.exe) は、低特権サービス アカウントを使用して実行されます。 ただし、スタート パッド サービス アカウントを R と Python を開始し、データベース インスタンスとの通信を次のユーザー権限が必要です。

- サービスとしてログオン (SeServiceLogonRight)
- プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)
- スキャン チェックを行わない (SeChangeNotifyPrivilege)
- プロセス (SeIncreaseQuotaSizePrivilege) に対してメモリ クォータを調整します。

これらのユーザー権利の詳細については、「Windows 特権および権限」のセクションを参照してください。[構成 Windows サービス アカウントとアクセス許可](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)します。

> [!TIP]
> SQL Server 診断サポート診断プラットフォーム (SDP) ツールの使用に慣れている場合は、MachineName_UserRights.txt という名前の出力ファイルの確認を SDP を使用できます。

## <a name="user-group-for-launchpad-cannot-log-on-locally"></a>スタート パッドのユーザー グループがローカルでログオンできません。

SQL Server Machine Learning サービスのセットアップ中に、Windows ユーザー グループを作成します**SQLRUserGroup**とスタート パッドが SQL Server に接続し、外部スクリプト ジョブを実行するために必要なすべての権限を持つをプロビジョニングします。 このユーザー グループが有効になっている場合は、Python スクリプトの実行にも使用します。

ただし、組織はより制限の厳しいセキュリティ ポリシーが適用されますには、このグループに必要な権限が削除された可能性が手動で、またはポリシーによって自動的に失効される可能性があります。 権限が削除されている場合は、スタート パッドは、SQL Server に接続できなくでき、SQL Server が外部のランタイムを呼び出すことはできません。

問題を解決するには、グループ **SQLRUserGroup** に**ローカルのログオンを許可する**システム権限があることを確認します。

詳細については、次を参照してください。[構成 Windows サービス アカウントとアクセス許可](../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)します。

## <a name="permissions-to-run-external-scripts"></a>外部スクリプトを実行するアクセス許可

スタート パッドが正しく構成されている場合でも、ユーザーが R または Python スクリプトを実行するためのアクセス許可を持っていない場合エラーを返します。

データベース管理者として SQL Server のインストール、またはデータベースの所有者は、このアクセス許可が自動的に付与されます。 ただし、他のユーザーは、通常より権限が制限されます。 R スクリプトを実行しようとする場合は、スタート パッド エラーが発生します。

SQL Server Management studio で、問題を解決するには、セキュリティ管理者は、次のスクリプトを実行して、SQL ログインまたは Windows ユーザー アカウントを変更できます。

```SQL
GRANT EXECUTE ANY EXTERNAL SCRIPT TO <username>
```

詳細については、次を参照してください。 [GRANT (TRANSACT-SQL](../t-sql/statements/grant-transact-sql.md)します。

## <a name="common-launchpad-errors"></a>スタート パッドの一般的なエラー

このセクションでは、スタート パッドを返す最も一般的なエラー メッセージが一覧表示します。

## <a name="unable-to-launch-runtime-for-r-script"></a>「ランタイム R スクリプトを起動できません。」

(Python の使用も) R ユーザーの Windows グループが R Services を実行しているインスタンスにログオンできない場合、次のエラーが表示されます。

- R スクリプトを実行しようとするときに生成されるエラー:

    * *'R' スクリプトのランタイムを起動できません。'R' ランタイムの構成を確認してください。*

    * *外部スクリプト エラーが発生しました。ランタイムを起動できません。*

- によって生成されたエラー、[!INCLUDE[rsql_launchpad](../includes/rsql-launchpad-md.md)]サービス。

    * *ランチャー RLauncher.dll を初期化できませんでした*

    * *ランチャー dll が登録されていません!*

    * *セキュリティ ログは、NT サービス アカウントがログオンできなかったことを示します*

このユーザー グループに必要なアクセス許可を付与する方法については、次を参照してください。 [SQL Server の 2016 R Services をインストール](install/sql-r-services-windows-install.md)します。

> [!NOTE]
> SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。

## <a name="logon-failure-the-user-has-not-been-granted-the-requested-logon-type"></a>"ログオン失敗: 要求されたログオンの種類は、ユーザーに付与されていません"

既定では、[!INCLUDE[rsql_launchpad_md](../includes/rsql-launchpad-md.md)]起動時に次のアカウントを使用して:`NT Service\MSSQLLaunchpad`します。 によって、アカウントが構成されている[!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]セットアップに必要なすべての権限を持っています。

場合、スタート パッドに別のアカウントを割り当てる場合、または、権限が SQL Server マシンでのポリシーによって削除された場合、アカウントが必要なアクセス許可がないと、このエラーが発生する可能性があります。

>*ERROR_LOGON_TYPE_NOT_GRANTED 1385 (0x569) Logon failure: the user has not been granted the requested logon type at this computer*

新しいサービス アカウントに必要なアクセス許可を付与するには、ローカル セキュリティ ポリシー アプリケーションを使用し、次のアクセス許可を追加、アカウントのアクセス許可を更新します。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

## <a name="unable-to-communicate-with-the-launchpad-service"></a>「スタート パッド サービスと通信できません」

インストールして、machine learning を有効にし、R または Python スクリプトを実行しようとするときにこのエラーが発生した場合は、実行されているインスタンスのスタート パッド サービスを停止した可能性があります。

1. Windows コマンド プロンプトから SQL Server 構成マネージャーを開きます。 詳細については、「 [SQL Server Configuration Manager](https://docs.microsoft.com/sql/relational-databases/sql-server-configuration-manager)」を参照してください。

2. インスタンスの場合は、SQL Server スタート パッドを右クリックし **プロパティ**します。

3. 選択、**サービス**タブをクリックし、サービスが実行されていることを確認します。 実行されていない場合は、変更、**モードの開始**に**自動**、し、**適用**します。

4. Machine learning スクリプトが実行できるように、問題を修正は、通常、サービスを再起動します。 再起動に問題が解決しない場合、パスと引数を注意してください。、**バイナリ パス**プロパティ、および次の操作。

    A. ランチャーの .config ファイルを確認し、作業ディレクトリが有効であることを確認します。

    B. スタート パッドで使用される Windows グループが、SQL Server インスタンスに接続できることを確認する」の説明に従って、[前のセクション](#bkmk_LaunchpadTS)します。

    c. サービスのプロパティを変更する場合は、スタート パッド サービスを再起動します。

## <a name="fatal-error-creation-of-tmpfile-failed"></a>「TmpFile の致命的なエラーの作成に失敗しました」

このシナリオでは、machine learning の機能が正常にインストールし、スタート パッドが実行されています。 いくつか単純な R または Python のコードを実行しようとするが、スタート パッドは、次のようなエラーで失敗します。 

>*R スクリプトのランタイムと通信できません。R ランタイムの要件を確認してください。*

同時に、外部スクリプトのランタイムは STDERR メッセージの一部として、次のメッセージを書き込みます。 

>*致命的なエラー: 失敗 tmpfile を作成します。*

このエラーは、スタート パッドが使用しようとするアカウントにデータベースにログオンする権限がないことを示します。 このような状況は、厳密なセキュリティ ポリシーが実装された場合に発生します。 これは、大文字と小文字であるかどうかを確認するのに SQL Server のログを確認し、確認を MSSQLSERVER01 アカウントがログインで拒否されたかどうかを確認します。 R に固有のログで、同じ情報が提供される\_サービスまたは PYTHON\_サービス。 ExtLaunchError.log を探します。

既定では、20 個のアカウントが設定して、MSSQLSERVER20 を通じて名 MSSQLSERVER01、Launchpad.exe プロセスに関連付けられています。 R または Python を頻繁に使用する場合は、アカウントの数を増やすことができます。

この問題を解決するために、グループがあります*ローカル ログオンを許可する*の機械学習機能をインストールして有効には、ローカル インスタンスへのアクセス許可。 一部の環境でこのアクセス許可レベルは、ネットワーク管理者から GPO の例外を必要があります。

## <a name="not-enough-quota-to-process-this-command"></a>「このコマンドを処理するクォータが不足しています」

このエラーは、いくつかのいずれかの意味があります。

- スタート パッドには、外部のクエリを実行するが不足している外部ユーザーがあります。 たとえば、同時に、20 を超える外部クエリを実行するいるし、20 の既定ユーザーのみが、1 つまたは複数のクエリが失敗します。

- メモリ不足が R タスクを処理します。 このエラーは、SQL Server を使用して、コンピューターのリソースの最大 70%、既定の環境でほとんどの場合は発生します。 R でリソースの大きい使用をサポートするために、サーバーの構成を変更する方法については、次を参照してください。 [R コードの運用](r/operationalizing-your-r-code.md)します。

## <a name="cant-find-package"></a>「パッケージを見つけることができません」

このメッセージを取得し、SQL Server の外部、同じコードを実行したときに、メッセージを取得できませんでしたが SQL Server で R コードが実行される場合、は、SQL Server で使用される既定のライブラリの場所にパッケージがインストールされていないことを意味します。

このエラーは、さまざまな方法で発生することができます。

- サーバーで、新しいパッケージをインストールしたが、R では、ユーザー ライブラリにパッケージがインストールされているため、アクセスが拒否されました。

- R Services をインストールし、別の R ツールをインストールまたはなどの Microsoft R Server (スタンドアロン)、Microsoft R Client は、RStudio、ライブラリのセットし、など。

インスタンスによって使用される R パッケージ ライブラリの場所を確認するのには、インスタンスに接続する SQL Server Management Studio を開いて (またはその他のデータベース クエリ ツール) を次のストアド プロシージャを実行します。

```SQL
EXEC sp_execute_external_script @language = N'R',  
@script = N' print(normalizePath(R.home())); print(.libPaths());'; 
```

#### <a name="sample-results"></a>サンプルの結果

*外部スクリプトからの STDOUT メッセージ:*

*[1]"c:\\プログラム ファイル\\Microsoft SQL Server\\MSSQL13 します。SQL2016\\R_SERVICES"*

*[1]"c:/プログラム ファイルまたは Microsoft SQL Server/MSSQL13 します。SQL2016/R_SERVICES/ライブラリ"*

問題を解決するには、SQL Server インスタンスのライブラリにパッケージを再インストールする必要があります。

>[!NOTE]
>Microsoft R の最新バージョンを使用する SQL Server 2016 のインスタンスをアップグレードした場合、既定のライブラリの場所は異なります。 詳細については、次を参照してください。 [R Services のインスタンスをアップグレードする使用 SqlBindR](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。

## <a name="launchpad-shuts-down-due-to-mismatched-dlls"></a>Dll が一致しないため、スタート パッドをシャット ダウン

他の機能、修正プログラム、サーバーとデータベース エンジンをインストールし、元のメディアを使用して、Machine Learning 機能を後で追加、間違ったバージョンの Machine Learning コンポーネントをインストールする場合があります。 スタート パッドには、バージョンの不一致が検出されたら、シャット ダウンされ、ダンプ ファイルを作成します。

この問題を回避するには、サーバー インスタンスとして同じパッチ レベルに新機能をインストールすることを確認します。

**間違ったやり方をアップグレードする:**

1. R Services なしの SQL Server 2016 をインストールします。
2. SQL Server 2016 Cumulative Update 2 にアップグレードします。
3. RTM メディアを使用して R Services (In-database) をインストールします。

**アップグレードする正しい方法:**

1. R Services なしの SQL Server 2016 をインストールします。
2. 必要なパッチ レベルには、SQL Server 2016 をアップグレードします。 たとえば、Service Pack 1 とし、累積更新プログラム 2 をインストールします。
3. 修正レベルで機能を追加するに SP1 および CU2 のセットアップを再度実行し、R Services (In-database) を選択します。 

## <a name="launchpad-fails-to-start-if-8dot3-notation-is-required"></a>スタート パッドが 8dot3 表記が必要な場合の開始に失敗しました。

> [!NOTE] 
> 以前のシステムでは、スタート パッドを 8dot3 表記法の要件がある場合を開始できないことができます。 この要件は、今後のリリースで削除されました。 SQL Server 2016 R Services のお客様は、次のいずれかでインストールする必要があります。
> * SQL Server 2016 SP1 と CU1: [Cumulative Update 1 for SQL Server](https://support.microsoft.com/help/3208177/cumulative-update-1-for-sql-server-2016-sp1)します。
> * SQL Server 2016 RTM、累積的な更新プログラム 3、およびそのこの[修正プログラム](https://support.microsoft.com/help/3210110/on-demand-hotfix-update-package-for-sql-server-2016-cu3)オンデマンドで提供されています。

R を使用した互換性のため、SQL Server 2016 R Services (In-database) を使用して短いファイル名の作成をサポートするために、機能がインストールされているドライブが必要な*8dot3 表記*します。 8.3 ファイル名とも呼ばれますが、*短いファイル名*、または長いファイル名の代替として Microsoft Windows の以前のバージョンと互換性のため使用されます。

R をインストールしているボリュームが短いファイル名をサポートしていない場合は、SQL Server から R を起動するプロセスでは、適切な実行可能ファイルを検索できない可能性があり、スタート パッドは開始されません。

回避策としては、SQL Server がインストールされていると、R Services がインストールされているボリュームで 8dot3 表記が有効にできます。 次に、R Services 構成ファイルに作業ディレクトリの短い名前を指定する必要があります。

1. 8dot3 表記を有効にするで fsutil ユーティリティを実行、 *8dot3name*引数」の説明に従って: [fsutil 8dot3name](https://technet.microsoft.com/library/ff621566(v=ws.11).aspx)します。

2. RLauncher.config ファイルを開き、8dot3 表記が有効にした後のプロパティに注意してください`WORKING_DIRECTORY`します。 このファイルを検索する方法については、次を参照してください。 [Machine Learning のトラブルシューティングのためのデータ収集](data-collection-ml-troubleshooting-process.md)します。

3. Fsutil ユーティリティを使用して、*ファイル*WORKING_DIRECTORY に指定されているフォルダーの短いファイル パスを指定する引数。

4. WORKING_DIRECTORY のプロパティで入力した同じ作業ディレクトリを指定する構成ファイルを編集します。 または、別の作業ディレクトリを指定し、8dot3 表記と互換性が既に既存のパスを選択します。


## <a name="next-steps"></a>次の手順

[Machine Learning サービスのトラブルシューティングと既知の問題](machine-learning-troubleshooting-faq.md)

[Machine learning のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

[アップグレードとインストールに関してよく寄せられる質問](r/upgrade-and-installation-faq-sql-server-r-services.md)

[データベース エンジンの接続をトラブルシューティングします。](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
