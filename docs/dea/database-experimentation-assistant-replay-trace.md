---
title: SQL Server アップグレードのトレースを再生する
description: SQL Server アップグレードのために Database Experimentation Assistant を使用したトレースの再生
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: b1607aefdc8495f374b2586b0b896f20e87f62d1
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056705"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>Database Experimentation Assistant でトレースを再生する

Database Experimentation Assistant (DEA) では、アップグレードされたテスト環境に対してキャプチャされたトレースファイルを再生できます。 たとえば、SQL Server 2008 R2 で実行される実稼働ワークロードを考えてみます。 ワークロードのトレースファイルは、2回再生する必要があります。1回目は、運用環境で実行される同じバージョンの SQL Server を持つ環境で、SQL Server 2016 などのアップグレードターゲット SQL Server バージョンを持つ環境で再び再生する必要があります。

> [!NOTE]
> このアクションを実行するには、分散再生トレースを実行するようにバーチャルマシンまたは物理マシンを手動で設定する必要があります。 詳細については、「[分散再生コントローラーとクライアントのセットアップ](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/)」を参照してください。
>
>

## <a name="create-a-trace-replay"></a>トレース再生を作成する

DEA で、メニューアイコンを選択します。 展開されたメニューで、再生アイコンの横にある **[トレースの再生]** を選択します。

![メニューの [再生トレース] を選択します。](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-open.png)

> [!NOTE]
> 分散再生コントローラーコンピューターには、リモートに使用するユーザーアカウントに対するアクセス許可が必要です。
>

### <a name="grant-access-to-the-distributed-replay-controller"></a>分散再生コントローラーへのアクセスを許可する

1. コマンドプロンプトで、「 **dcomcnfg** 」と入力して、**コンポーネントサービス**インターフェイスを開きます。
1. [**コンポーネントサービス** > **コンピューター** > **マイコンピューター** > **DCOM 構成** > **dreplaycontroller**] を展開します。
1. **[Dreplaycontroller]** を右クリックし、 **[プロパティ]** を選択します。
1. **[セキュリティ]** タブで、 **[編集]** を選択してユーザーアカウントを追加します。
1. **[OK]** を選択します。

### <a name="verify-setup"></a>セットアップの確認

1.  **SQL Server インストールパス**: SQL Server がインストールされている場所へのパスを入力します。 たとえば、C:\\Program Files (x86)\\Microsoft SQL Server\\120 です。
1.  **コントローラーコンピューター名**: コントローラーとして設定されているコンピューターの名前を入力します。 このマシンでは、SQL Server 分散再生 controller という名前の Windows サービスが実行されています。 分散再生コントローラーは、分散再生クライアントのアクションを調整します。 各分散再生環境には、コントローラーのインスタンスを 1 つだけ置くことができます。
1.  **クライアントコンピューター名**: 各クライアントコンピューターの名前をコンマで区切って入力します。 例: client1、次のようになります。 最大5つのクライアントコントローラーを使用できます。 クライアントは、SQL Server 分散再生 client という名前の Windows サービスを実行する、物理または仮想の1つ以上のマシンです。 分散再生クライアントは、SQL Server のインスタンスに対するワークロードをシミュレートします。 各分散再生環境には、1 つまたは複数のクライアントを置くことができます。
1.  **[次へ]** を選択します。

### <a name="select-a-trace"></a>トレースの選択

1.  **[トレースファイルのパス]** : 入力トレース (.trc) ファイルへのパスを入力します。
1.  **再生前処理出力を格納するパス**:  
    \- IRF ファイルをまだ持っていない場合は、IRF ファイルとその他の前処理出力を格納する場所へのパスを入力します。  
    \- IRF ファイルが既にある場合は、IRF ファイルのパスを入力します。
1. **[次へ]** を選択します。

### <a name="replay-a-trace"></a>トレースを再生する

1.  **トレースファイル名**: トレースファイル名を入力します。
1.  **ファイルの最大サイズ (MB)** : トレースファイルのロールオーバーサイズの値を入力します。 既定値は 200 MB です。 カスタム値を入力できます。
1.  **保存する再生トレース出力のパス**: 出力 .trc ファイルのパスを入力します。
1.  **SQL Server インスタンス名**: トレースを再生する SQL Server インスタンスの名前を入力します。
1.  **[スタート]** を選択します。

入力した情報が有効な場合は、分散再生プロセスが開始されます。 そうしないと、正しくない情報を含むテキスト boses が赤色で強調表示されます。 入力した値が正しいことを確認し、 **[開始]** を選択します。

再生が終了するまで待って、指定した場所を確認します。 再生の進行状況を監視するには、左側のメニューの下部にあるベルアイコンを選択します。

![再生トレースの進行状況](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-progress.png)

## <a name="frequently-asked-questions-about-trace-replay"></a>トレースの再生に関してよく寄せられる質問

### <a name="what-security-permissions-do-i-need-to-start-a-replay-capture-on-my-target-server"></a>対象サーバーで再生キャプチャを開始するには、どのようなセキュリティアクセス許可が必要ですか。

- DEA アプリケーションでトレース操作を実行する Windows ユーザーには、SQL Server を実行しているターゲットコンピューターに対する sysadmin 権限が必要です。 これらのユーザー権限は、トレースを開始するために必要です。
- SQL Server を実行している対象コンピュータが実行されているサービスアカウントには、指定されたトレースファイルパスへの書き込みアクセス権が必要です。
- 分散再生クライアントサービスを実行するサービスアカウントは、SQL Server を実行している対象コンピューターに接続し、クエリを実行するためのユーザー権限を持っている必要があります。

### <a name="can-i-start-more-than-one-replay-in-the-same-session"></a>同じセッションで複数の再生を開始することはできますか。

はい。複数の再生を開始し、同じセッションで完了するように追跡できます。

### <a name="can-i-start-more-than-one-replay-in-parallel"></a>複数の再生を並列で開始することはできますか。

はい。ただし、**コントローラー Plus クライアント**で選択されているのと同じコンピューターセットではありません。 コントローラーとクライアントがビジー状態になります。 並列再生を開始するには、**コントローラーとクライアント**の下に別のコンピューターセットを設定します。

### <a name="how-long-does-a-replay-typically-take-to-finish"></a>再生は通常、終了するまでにどれくらいの時間がかかりますか。

通常、再生には、ソーストレースとソーストレースの前処理にかかる時間を足した時間がかかります。 ただし、コントローラーに登録されているクライアントコンピューターが、再生によって生成される負荷を管理するのに十分ではない場合、再生の完了に時間がかかることがあります。 コントローラーには、最大16台のクライアントコンピューターを登録できます。

### <a name="how-large-do-target-trace-files-get"></a>ターゲットトレースファイルのサイズはどのくらいですか?

ターゲットトレースファイルは、ソーストレースのサイズの 5 ~ 15 倍の範囲内である可能性があります。 ファイルサイズは、実行されるクエリの数に基づいています。 たとえば、クエリプランの blob のサイズが大きい場合があります。 これらのクエリの統計が頻繁に変更されると、より多くのイベントがキャプチャされます。

### <a name="why-do-i-need-to-restore-databases"></a>データベースを復元する必要があるのはなぜですか。

SQL Server は、ステートフルなリレーショナルデータベース管理システムです。 A/B テストを適切に実行するには、データベースの状態が常に保持されている必要があります。 そうしないと、再生中に運用環境に表示されないクエリのエラーが表示されることがあります。 これらのエラーを回避するには、ソースキャプチャの前にバックアップを実行することをお勧めします。 同様に、再生中のエラーを回避するには、SQL Server を実行しているターゲットコンピューターでバックアップを復元する必要があります。

### <a name="what-does-pass--on-the-replay-page-mean"></a>再生ページの "pass%" は何を意味していますか?

**パス%** は、クエリの割合が渡されることを意味します。 エラーの数が予想されるかどうかを診断できます。 エラーが発生する可能性があります。または、データベースの整合性が失われたことが原因でエラーが発生する可能性があります。 **パス%** の値が予期したものと異なる場合は、トレースを停止し、SQL Profiler のトレースファイルを調べて、どのクエリが成功しなかったかを確認できます。

### <a name="how-can-i-look-at-the-trace-events-that-were-collected-during-replay"></a>再生中に収集されたトレースイベントを確認するにはどうすればよいですか。

ターゲットトレースファイルを開き、SQL Profiler で表示します。 または、再生キャプチャを変更する場合、すべての SQL Server スクリプトは、C:\\Program Files (x86)\\Microsoft Corporation\\Database Experimentation Assistant\\スクリプト\\StartReplayCapture .sql にあります。

### <a name="what-trace-events-does-dea-collect-during-replay"></a>再生中に収集されるトレースイベントは何ですか。

DEA は、パフォーマンスに関連する情報を含むトレースイベントをキャプチャします。 キャプチャの構成は、StartReplayCaptureTrace スクリプトに含まれています。 これらのイベントは、 [sp_trace_setevent (transact-sql) リファレンスドキュメント](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)に記載されている一般的な SQL Server トレースイベントです。

## <a name="troubleshoot-trace-replay"></a>トレース再生のトラブルシューティング

### <a name="i-cant-connect-to-the-computer-thats-running-sql-server"></a>を実行しているコンピューターに接続できません SQL Server

- SQL Server を実行しているコンピューターの名前が有効であることを確認します。 確認するには、SQL Server Management Studio (SSMS) を使用してサーバーに接続してみてください。
- ファイアウォールの構成で SQL Server を実行しているコンピューターへの接続がブロックされていないことを確認します。
- ユーザーが必要なユーザー権限を持っていることを確認します。
- 分散再生クライアントのサービスアカウントに SQL Server を実行しているコンピューターへのアクセス権があることを確認します。

詳細については、% temp%\\DEA のログを参照してください。 問題が解決しない場合は、製品チームにお問い合わせください。

### <a name="i-cant-connect-to-the-distributed-replay-controller"></a>分散再生コントローラーに接続できません

- コントローラーコンピューターで分散再生コントローラーサービスが実行されていることを確認してください。 確認するには、分散再生管理ツールを使用します (コマンド `dreplay.exe status -f 1`を実行します)。
- 再生がリモートで開始された場合:
  - DEA を実行しているコンピューターがコントローラーに対して ping を正常に実行できることを確認します。 **[再生環境の構成]** ページの指示に従って、ファイアウォールの設定によって接続が許可されていることを確認します。 詳細については、「 [SQL Server 分散再生](https://docs.microsoft.com/sql/tools/distributed-replay/sql-server-distributed-replay?view=sql-server-2017)」を参照してください。
  - 分散再生コントローラーのユーザーに対して、DCOM リモート起動とリモートアクティブ化が許可されていることを確認します。
  - 分散再生コントローラーのユーザーに対して、DCOM リモートアクセスユーザー権限が許可されていることを確認してください。

### <a name="the-trace-file-path-exists-on-my-machine-why-cant-distributed-replay-controller-find-it"></a>トレースファイルのパスは、コンピューター上に存在します。 分散再生コントローラーが見つからないのはなぜですか。

分散再生は、ローカルディスクリソースにのみアクセスできます。 再生を開始する前に、ソーストレースファイルを分散再生コントローラーマシンにコピーする必要があります。 また、 **[新しい再生]** ページでパスを指定する必要があります。 

UNC パスは分散再生と互換性がありません。 分散再生パスは、最初のソーストレースファイル (拡張子を含む) へのローカルな絶対パスである必要があります。

### <a name="why-cant-i-browse-for-files-on-the-new-replay-page"></a>新しい再生ページでファイルを参照できないのはなぜですか。

リモートコンピューターのフォルダーを参照できないため、ファイルの参照は役に立ちません。 絶対パスのコピーと貼り付けの方が効率的です。

### <a name="i-started-replay-with-a-trace-but-distributed-replay-didnt-replay-any-events"></a>トレースで再生を開始しましたが、分散再生イベントは再生されませんでした

この問題は、トレースファイルのイベントの再生方法に関する情報がない場合に発生する可能性があります。 指定されたトレースファイルのパスがソーストレースファイルであるかどうかを確認します。 ソーストレースファイルは、StartCaptureTrace スクリプトで指定された構成を使用して作成されます。

### <a name="i-see-unexpected-error-occurred-when-i-try-to-preprocess-my-trace-files-by-using-the-sql-server-2017-distributed-replay-controller"></a>"予期しないエラーが発生しました。" SQL Server 2017 分散再生コントローラーを使用してトレースファイルをプリプロセスする場合

この問題は、SQL Server 2017 の RTM バージョンで知られています。 詳細については、「 [DReplay 機能を使用して SQL Server 2017 でキャプチャされたトレースを再生するときに予期しないエラー](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a)」を参照してください。  
  
この問題は、SQL Server 2017 の最新の累積的な更新プログラム1で対処されています。 [SQL Server 2017 の累積的な更新プログラム 1](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017)の最新バージョンをダウンロードします。

## <a name="next-steps"></a>次の手順

- 提案された変更に関する洞察を得るために役立つ分析レポートを作成するには、「[レポートの作成](database-experimentation-assistant-create-report.md)」を参照してください。

- DEA とデモの19分の概要については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
