---
title: SQL Server のアップグレードには、データベース実験アシスタントを使用したトレースを再生します。
description: データベース実験アシスタントを使用したトレースを再生します。
ms.custom: ''
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
ms.openlocfilehash: 53534d9d269803a4bce0902c1f22349dfe6c57e0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058891"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>データベース実験アシスタントでのトレースを再生します。

データベース実験アシスタント (DEA) をアップグレードされたテスト環境に対してキャプチャしたトレース ファイルを再生できます。 たとえば、SQL Server 2008 R2 で実行されている運用環境のワークロードを検討してください。 ワークロード トレース ファイルを 2 回再生する必要があります。 運用環境で、もう一度アップグレード対象の SQL Server バージョンの SQL Server 2016 などが存在する環境で実行する SQL Server の同じバージョンの環境で 1 回です。

> [!NOTE]
> このアクションを実行するには、手動でその仮想マシンまたは物理マシンの Distributed Replay トレースの実行に設定する必要があります。 詳細については、次を参照してください。[分散再生コント ローラーとクライアントのセットアップ](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/)します。
>
>

## <a name="create-a-trace-replay"></a>トレース再生を作成します。

DEA では、メニュー アイコンを選択します。 展開されたメニューで、次のように選択します。**トレースの再生**再生アイコンの横にあります。

![メニューでトレースの再生を選択します。](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-open.png)

> [!NOTE]
> 分散再生コント ローラー マシンには、リモートを使用するユーザー アカウントにアクセス許可が必要です。
>

### <a name="grant-access-to-the-distributed-replay-controller"></a>分散再生コント ローラーにアクセスを許可

1. コマンド プロンプトで次のように入力します。 **dcomcnfg**を開く、**コンポーネント サービス**インターフェイス。
1. 展開**コンポーネント サービス** > **コンピューター** > **コンピューター** > **DCOM の構成** >  **DReplayController**します。
1. 右クリックして**dreplaycontroller**、し、**プロパティ**します。
1. **セキュリティ**] タブで [**編集**ユーザー アカウントを追加します。
1. **[OK]** を選択します。

### <a name="verify-setup"></a>セットアップを確認します。

1.  **SQL Server のインストール パス**:SQL Server がインストールされているパスを入力します。 たとえば、c:\\Program Files (x86)\\Microsoft SQL Server\\120。
1.  **コント ローラー マシン名**:コント ローラーとして設定されているマシンの名前を入力します。 このマシンには、SQL Server Distributed Replay コント ローラーをという名前の Windows サービスが実行されています。 分散再生コント ローラーは、分散再生クライアントのアクションを統制します。 各分散再生環境には、コントローラーのインスタンスを 1 つだけ置くことができます。
1.  **クライアント コンピューター名**:コンマで区切られた、各クライアント コンピューターの名前を入力します。 例: client1 で、client2 します。 最大 5 つのクライアントのコント ローラーがあることができます。 クライアントは、1 つまたは複数のマシン、物理または仮想 SQL Server Distributed Replay client という名前の Windows サービスを実行します。 分散再生クライアントは、SQL Server のインスタンスに対するワークロードをシミュレートします。 各分散再生環境には、1 つまたは複数のクライアントを置くことができます。
1.  **[次へ]** を選択します。

### <a name="select-a-trace"></a>トレースを選択します

1.  **トレース ファイルのパスを**:入力トレース (.trc) ファイルへのパスを入力します。
1.  **再生の保存先のパスが出力を前処理**:  
    \- IRF ファイルがない場合は、IRF ファイルを保存する場所へのパスを入力し、その他の前処理を出力します。  
    \- IRF ファイル既にある場合は、IRF ファイルへのパスを入力します。
1. **[次へ]** を選択します。

### <a name="replay-a-trace"></a>トレースを再生します。

1.  **トレース ファイル名**:トレース ファイルの名前を入力します。
1.  **最大ファイル サイズ (MB)** :トレース ファイルのロール オーバー サイズの値を入力します。 既定値は、200 MB です。 カスタム値を入力することができます。
1.  **再生のトレース出力を格納するパス**:出力の .trc ファイルのパスを入力します。
1.  **SQL Server インスタンス名**:トレースを再生する SQL Server インスタンスの名前を入力します。
1.  **[スタート]** を選択します。

入力した情報が有効な場合、分散再生プロセスを開始します。 それ以外の場合、正しくない情報を持つテキスト boses が赤で強調表示されます。 入力した値が正しいし、確認**開始**します。

再生が完了するまで待ってから実行すると、指定した場所を参照してください。 再生の進行状況を監視するには、左側のメニューの下部にあるベルのアイコンを選択します。

![進行状況のトレースを再生します。](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-progress.png)

## <a name="frequently-asked-questions-about-trace-replay"></a>トレースの再生に関してよく寄せられる質問

### <a name="what-security-permissions-do-i-need-to-start-a-replay-capture-on-my-target-server"></a>ターゲット サーバー上の再生キャプチャを開始する必要があるどのようなセキュリティ アクセス許可をでしょうか。

- DEA アプリケーションで、トレース操作を実行している Windows ユーザーによっては、SQL Server を実行しているターゲット コンピューター上の sysadmin 権限が必要です。 これらのユーザー権利は、トレースを開始する必要があります。
- SQL Server を実行しているターゲット コンピューターが実行されているサービス アカウントには、指定されたトレース ファイルのパスへの書き込みアクセスが必要です。
- 分散再生クライアント サービスが実行されているサービス アカウントには、SQL Server を実行しているターゲット コンピューターに接続して、クエリを実行するユーザーの権利が必要です。

### <a name="can-i-start-more-than-one-replay-in-the-same-session"></a>同じセッション内で 1 つ以上の再生を開始できます。

はい、複数の再生を開始し、それらを同じセッションで完了するまで追跡できます。

### <a name="can-i-start-more-than-one-replay-in-parallel"></a>並列で 1 つ以上の再生を開始できます。

はいが同じではなくで選択されているマシンの設定、**コント ローラーとクライアント**します。 コント ローラーとクライアントは、ビジー状態になります。 マシンの個別セットを設定**コント ローラーとクライアント**並列の再生を開始します。

### <a name="how-long-does-a-replay-typically-take-to-finish"></a>再生を通常にかかる時間を終了しますか。

再生には、通常、同じトレース ソースとしての時間数とソースのトレースの前処理にかかる時間がかかります。 ただし、コント ローラーに登録されているクライアント コンピューターで再生から生成される負荷を管理するのに十分ではない場合は、再生が完了するまでにかかる場合があります。 最大 16 個のクライアント コンピューターは、コント ローラーを登録できます。

### <a name="how-large-do-target-trace-files-get"></a>ターゲットのトレース ファイルのサイズにはできますか。

5 ~ 15 である可能性があります、ターゲットのトレース ソースのトレースのサイズを掛けたもの。 ファイル サイズは、クエリの数が実行に基づきます。 たとえば、クエリ プランの blob は大きい可能性があります。 多くの場合、これらのクエリの統計情報を変更する場合より多くのイベントがキャプチャされます。

### <a name="why-do-i-need-to-restore-databases"></a>データベースを復元するはなぜですか。

SQL Server は、ステートフルなリレーショナル データベース管理システムです。 A を適切に実行する]、[常に B テストでは、データベースの状態を保持する必要があります。 それ以外の場合、運用環境では表示されません再生中にクエリでエラーが発生する可能性があります。 これらのエラーを防ぐためには、ソースのキャプチャの直前のバックアップを実行することをお勧めします。 同様に、SQL Server を実行しているターゲット コンピューター上のバックアップを復元することが再生中にエラーを防ぐために必要です。

### <a name="what-does-pass--on-the-replay-page-mean"></a>何が「合格 %」再生ページの平均のでしょうか。

**% を渡す**クエリの割合のみが渡されることを意味します。 エラー数が必要かどうかを診断することができます。 エラーが予想される、またはデータベースにその整合性が失われるために、エラーが発生する可能性があります。 場合の値は、**パス %** 期待どおりにならないトレースを停止して、クエリが成功しなかった SQL Profiler トレース ファイルを確認します。

### <a name="how-can-i-look-at-the-trace-events-that-were-collected-during-replay"></a>再生中に収集されたトレース イベントに進めるようでしょうか。

ターゲットのトレース ファイルを開き、SQL Profiler に表示します。 または、すべての SQL Server スクリプトが c: で使用可能な再生キャプチャに変更を加える場合は、\\Program Files (x86)\\Microsoft Corporation\\データベース実験アシスタント\\スクリプト\\StartReplayCapture.sql します。

### <a name="what-trace-events-does-dea-collect-during-replay"></a>DEA は再生中に、どのようなトレース イベントを収集はでしょうか。

DEA は、パフォーマンス関連の情報を含むトレース イベントをキャプチャします。 キャプチャの構成は StartReplayCaptureTrace.sql スクリプトです。 これらのイベントが記載されている一般的な SQL Server トレース イベント、 [sp_trace_setevent (TRANSACT-SQL) のリファレンス ドキュメント](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)します。

## <a name="troubleshoot-trace-replay"></a>トレース再生をトラブルシューティングします。

### <a name="i-cant-connect-to-the-computer-thats-running-sql-server"></a>SQL Server を実行しているコンピューターに接続できません。

- SQL Server を実行しているコンピューターの名前が有効であることを確認します。 で確認するのには、SQL Server Management Studio (SSMS) を使用して、サーバーに接続してみてください。
- ファイアウォールの構成が SQL Server を実行しているコンピューターへの接続をブロックしないことを確認します。
- ユーザーが必要なユーザー権利を持っていることを確認します。
- 分散再生クライアントのサービス アカウントが SQL Server を実行しているコンピューターへのアクセスを持っていることを確認します。

%Temp% に、ログで詳細を表示できます\\DEA します。 問題が解決しない場合は、製品チームにお問い合わせください。

### <a name="i-cant-connect-to-the-distributed-replay-controller"></a>分散再生コント ローラーに接続できません。

- コント ローラー コンピューターの Distributed Replay controller のサービスが実行されていることを確認します。 確認するには、分散再生管理ツールを使用 (コマンドを実行`dreplay.exe status -f 1`)。
- 場合は、再生はリモートで開始します。
  - DEA を実行しているコンピューターがコント ローラーを正常に ping できることを確認します。 ファイアウォールの設定が上の手順に従って接続を許可することを確認、**再生環境の構成**ページ。 詳細については、この記事を参照してください。 [SQL Server Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/sql-server-distributed-replay?view=sql-server-2017)します。
  - Distributed Replay controller のユーザーの DCOM のリモート起動とアクティブ化が許可されることを確認します。
  - 分散再生コント ローラーのユーザーの DCOM のリモート アクセス ユーザーの権限が許可されることを確認します。

### <a name="the-trace-file-path-exists-on-my-machine-why-cant-distributed-replay-controller-find-it"></a>トレース ファイルのパスは、私のコンピューターに存在します。 なぜ分散再生コント ローラーが見つけられないか。

Distributed Replay は、ローカル ディスク リソースのみにアクセスできます。 再生を開始する前に、Distributed Replay コント ローラー マシンにソース トレース ファイルをコピーする必要があります。 また、DEA でパスを指定する必要があります**新しい再生**ページ。 

UNC パスは、Distributed Replay と互換性がありません。 分散再生のパスは、拡張子を含む最初のソース トレース ファイルをローカルの絶対パスである必要があります。

### <a name="why-cant-i-browse-for-files-on-the-new-replay-page"></a>新しい再生ページ上のファイル参照できない理由

リモート コンピューターのフォルダーを参照できません、ために、ファイルの参照は役に立ちません。 コピーと貼り付け、絶対パスより効率的です。

### <a name="i-started-replay-with-a-trace-but-distributed-replay-didnt-replay-any-events"></a>トレース再生を開始したが、Distributed Replay で任意のイベントを再生しませんでした。

トレース ファイルがない再生可能なイベントまたはイベントを再生する方法に関する情報がないために、この問題が発生する可能性があります。 指定されたトレース ファイルのパスがソース トレース ファイルであるかどうかを確認します。 StartCaptureTrace.sql スクリプトで指定される構成を使用して、ソース トレース ファイルが作成されます。

### <a name="i-see-unexpected-error-occurred-when-i-try-to-preprocess-my-trace-files-by-using-the-sql-server-2017-distributed-replay-controller"></a>私は、"Unexpected error occurred!"を参照してください。 SQL Server 2017 の Distributed Replay コント ローラーを使用して、トレース ファイルの前処理を実行しようとすると

この問題は、SQL Server 2017 の RTM バージョンで呼ばれます。 詳細については、次を参照してください。 [DReplay 機能を使用して SQL Server 2017 でキャプチャされたトレースを再生するときに予期しないエラー](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a)します。  
  
問題は、SQL Server 2017 の最新の Cumulative Update 1 で解決されています。 最新バージョンのダウンロード[for SQL Server 2017 Cumulative Update 1](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017)します。

## <a name="next-steps"></a>次のステップ

- 提案された変更を把握するのに役立つ分析レポートを作成するを参照してください。[レポート作成](database-experimentation-assistant-create-report.md)です。

- DEA とデモンストレーションを 19 分については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
