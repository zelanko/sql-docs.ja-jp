---
title: SQL Server のアップグレード アシスタントで実験をデータベースでのトレースをキャプチャします。
description: データベース実験アシスタントでのトレースをキャプチャします。
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
manager: jroth
ms.openlocfilehash: dc53a9e1d151e07ce7e2eebf1444fd0d0065f8be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794496"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>データベース実験アシスタントでのトレースをキャプチャします。

キャプチャしたサーバー イベントのログを含むトレース ファイルを作成するのにトレースのキャプチャでデータベース実験アシスタント (DEA) を使用することができます。 キャプチャしたサーバー イベントは、特定の期間中に特定のサーバーで発生するイベントです。 トレースのキャプチャは、サーバーあたり 1 回実行する必要があります。

トレースのキャプチャを開始する前に、すべてのターゲット データベースをバックアップすることを確認します。

クエリの SQL Server でキャッシュと評価の結果に影響を与える可能性があります。 評価の結果の一貫性を向上させるために、サービス アプリケーション SQL Server (MSSQLSERVER) サービスを再起動することお勧めしましています。

## <a name="create-a-trace-capture"></a>トレースのキャプチャを作成します。

1. DEA では、左側のメニューのメニュー アイコンを選択します。 展開されたメニューで、次のように選択します。**トレースのキャプチャ**カメラ アイコンの横にあります。

    ![メニューで トレースのキャプチャを選択します。](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-capture.png)

1. **新しいキャプチャ**、入力するか、次の情報を選択します。

    - **SQL Server インスタンス名**:サーバー トレースをキャプチャする SQL Server を実行しているコンピューターの名前を入力します。
    - **データベース名**:データベースの追跡を開始するデータベースの名前を入力します。 データベースを指定しない場合、トレースは、すべてのデータベース サーバー上でキャプチャされます。
    - **トレース ファイル名**:キャプチャのトレース ファイルの名前を入力します。
    - **最大ファイル サイズ (MB)** :ファイルのロール オーバーのサイズを選択します。 選択したファイルのサイズで必要に応じて、新しいファイルが作成されます。 ロール オーバーの推奨されるサイズは、200 MB です。
    - **期間 (分) で**:トレース キャプチャが実行する時間 (分単位) を選択します。
    - **出力トレース ファイルを格納するパス**:トレース ファイルの保存先を選択します。 

    > [!NOTE]
    > トレース ファイルにファイル パスは、SQL Server を実行しているコンピューターでなければなりません。 場合は、SQL Server サービスは、特定のアカウントに設定されていない、サービスが書き込まれるトレース ファイルの指定されたフォルダーにアクセス許可書き込み必要があります可能性があります。
    >
    >

    ![[新しいキャプチャ] ページ](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-inputs.png)

## <a name="start-the-trace-capture"></a>トレースのキャプチャを開始します。

入力するか、必要な情報を選択すると、選択**開始**トレースのキャプチャを開始します。 入力した情報が有効な場合は、トレースのキャプチャ プロセスが開始されます。 それ以外の場合、無効なエントリを持つテキスト ボックスは、赤で強調表示されます。 

選択または入力した値が正しいし、確認**開始**します。

トレースのキャプチャが完了するとで指定したファイルの場所に新しいトレース ファイルを検索を実行している**出力トレース ファイルを格納するパス**します。 キャプチャの進行状況を監視するには、左側のメニューの下部にあるベルのアイコンを選択します。

![進行状況のトレースをキャプチャします。](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-progress.png)

### <a name="trace-file"></a>[トレース ファイル]

トレースのキャプチャは、指定した場所に .trc ファイルを書き込みます。 トレース ファイルには、SQL Server データベースのアクティビティのトレース結果が含まれています。 TRC ファイルが検出され、SQL Server によって報告されたエラーの詳細情報に設計されています。

## <a name="frequently-asked-questions-about-trace-capture"></a>トレースのキャプチャについてよく寄せられる質問

次はいくつかに関してよく寄せられる質問 DEA のトレース キャプチャします。

### <a name="what-events-are-captured-when-i-run-a-trace-capture-on-a-production-database"></a>実稼働データベースのトレース キャプチャを実行すると、どのようなイベントがキャプチャされますか。

次の表では、イベントとトレースの収集された対応する列のデータの一覧を示します。
  
|イベント名|テキスト データ (1)|バイナリ データ (2)|データベース ID (3)|ホスト名 (8)|アプリケーション名 (10)|ログイン名 (11)|SPID (12)|開始時刻 (14)|終了時刻 (15)|データベース名 (35)|イベント シーケンス (中 51 時間)|IsSystem (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC: (10) が完了しました**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC: (11) の開始**||*|*|*|*|*|*|*||*|*|*|  
|**RPC Output Parameter (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL:BatchCompleted (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL:BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**Audit Login (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Audit Logout (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**CursorOpen (53)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorPrepare (70)**|*||*|*|*|*|*|*||*|*|*|  
|**Prepare SQL (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec Prepared SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**CursorExecute (74)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorUnprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorClose (78)**|*||*|*|*|*|*|*||*|*|*|  

### <a name="is-there-a-performance-effect-on-my-production-server-when-trace-capture-is-running"></a>実稼働サーバーにパフォーマンスに影響をトレースのキャプチャを実行するときにでしょうか。
    
はい、トレース コレクションの実行時の最小限のパフォーマンスに影響があります。 テストの結果で、3% のメモリ不足に関するが見つかりました。
    
### <a name="what-kind-of-permissions-are-required-for-capturing-traces-on-a-production-workload"></a>どのような種類のアクセス許可は、実稼働ワークロードのトレースをキャプチャするために必要なでしょうか。
    
- DEA アプリケーションで、トレース操作を実行する Windows ユーザーによっては、SQL Server を実行しているコンピューター上の sysadmin 権限が必要です。
- SQL Server を実行するコンピューターで使用されるサービス アカウントには、指定されたトレース ファイルのパスへの書き込みアクセスが必要です。

### <a name="can-i-capture-traces-for-the-entire-server-or-only-on-a-single-database"></a>サーバーの全体または 1 つのデータベースでのみのトレースをキャプチャすることができますか。
    
DEA を使用して、または単一のデータベースのすべてのデータベース サーバーでトレースをキャプチャできます。
    
### <a name="i-have-a-linked-server-configured-in-my-production-environment-do-those-queries-show-up-in-the-traces"></a>実稼働環境で構成されているリンク サーバーがあります。 これらのクエリに表示、トレースしますか。
    
サーバー全体のトレース キャプチャを実行している場合、トレースは、リンク サーバー クエリなど、すべてのクエリをキャプチャします。 サーバー全体のトレース キャプチャを実行するのままに、**データベース名**ボックス**新しいキャプチャ**空です。
    
### <a name="whats-the-minimum-recommended-time-for-production-workload-traces"></a>実稼働ワークロードのトレースの推奨される時間の最小値とは何ですか。
    
ワークロード全体を最もよく表す時間を選択することをお勧めします。 これにより、ワークロードのすべてのクエリで、分析が実行されます。
    
### <a name="how-important-is-to-take-a-database-backup-right-before-i-start-a-trace-capture"></a>方法に重要なトレースのキャプチャを開始する前に、データベースのバックアップの適切なを実行することですか。
    
トレースのキャプチャを開始する前に、すべてのターゲット データベースをバックアップすることを確認します。 ターゲット 1 と 2 をターゲットにキャプチャされたトレースが再生されます。 データベースの状態が同一でない、実験の結果がずれています。

### <a name="can-i-collect-xevents-instead-of-traces-and-can-i-replay-xevents"></a>トレースではなく XEvents を収集でき、XEvents を再生できますか。
    
可能。 DEA XEvents をサポートしています。 DEA の最新バージョンをダウンロードして試してみてください。

## <a name="troubleshoot-trace-captures"></a>トレースのキャプチャをトラブルシューティングします。

トレースのキャプチャを実行すると、エラーが発生した場合は、次の前提条件を確認します。

- SQL Server を実行しているコンピューターの名前が有効であることを確認します。 で確認するのには、SQL Server Management Studio (SSMS) を使用して SQL Server を実行しているコンピューターに接続してみてください。
- ファイアウォールの構成が SQL Server を実行しているコンピューターへの接続をブロックしないことを確認します。
- ユーザーがブログの投稿に記載されている権限を持っていることを確認します。[再生 FAQ](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-replay-faq/)します。
- トレースの名前が、標準のロール オーバー規則に従っていないことを確認します (キャプチャ\_1)。 代わりに、キャプチャのようなトレースの名前を試す\_1A または Capture1 します。

いくつか表示される可能性のあるエラーとその解決方法を次に示します。

|可能性のあるエラー|ソリューション|  
|---|---|  
|開始できません、SQL Server のターゲットでトレース確認に必要な権限があるかどうかと、SQL Server アカウントが指定されたトレース ファイルのパス (53) の Sql エラー コードへの書き込みアクセス|DEA ツールを実行しているユーザーは、SQL Server を実行しているコンピューターへのアクセスに必要です。 ユーザーには、sysadmin ロールを割り当てる必要があります。|  
|開始できません、SQL Server のターゲットでトレース確認に必要な権限があるかどうかと、SQL Server アカウントが指定されたトレース ファイルのパスの Sql エラー コード (19062) への書き込みアクセス|指定されたトレースのパスが存在しないか、フォルダーは、(NETWORK SERVICE など) の SQL server サービスが実行されているアカウントに対する書き込みアクセス許可がありません。 パスが存在する必要があり、トレースを開始するのに必要なアクセス許可が必要です。|  
|DEA トレースの現在は、ターゲット サーバー上で実行中です。|アクティブなトレースは、対象サーバーで実行されています。 サーバー全体のトレースが既に実行されている場合は、新しいトレースを開始できません。|  
|トレースをキャプチャするため、要求されたデータベースを開くことができません。 このエラーは、不正なデータベース名によって発生する可能性があります。|指定されたデータベースが存在しないまたは現在のユーザーにアクセスできなくなります。 適切なデータベース名を使用します。|  

というラベルが付いた他のエラーを表示する場合は*Sql エラー コード*を参照してください[システム エラー メッセージ](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/cc645603(v=sql.105))詳細な説明と解決策です。
    
## <a name="next-steps"></a>次のステップ

- キャプチャしたトレースを再生する前に、SQL server Distributed Replay のツールを構成する方法についてを参照してください。[構成の再生](database-experimentation-assistant-configure-replay.md)します。

- DEA とデモンストレーションを 19 分については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
