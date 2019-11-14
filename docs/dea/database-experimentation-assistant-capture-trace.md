---
title: SQL Server アップグレードのトレースをキャプチャする
description: SQL Server アップグレードのために Database Experimentation Assistant でトレースをキャプチャする
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
ms.openlocfilehash: 6c24632875d09125efcd043ae907e87a21847fe9
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056601"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>Database Experimentation Assistant でトレースをキャプチャする

Database Experimentation Assistant (DEA) のトレースキャプチャを使用して、キャプチャされたサーバーイベントのログを含むトレースファイルを作成できます。 キャプチャされたサーバーイベントは、特定の期間に特定のサーバーで発生するイベントです。 トレースキャプチャは、サーバーごとに1回実行する必要があります。

トレースキャプチャを開始する前に、すべてのターゲットデータベースをバックアップしていることを確認してください。

SQL Server のクエリキャッシュは、評価結果に影響を与える可能性があります。 評価結果の一貫性を向上させるために、サービスアプリケーションで SQL Server サービス (MSSQLSERVER) を再起動することをお勧めします。

## <a name="create-a-trace-capture"></a>トレースキャプチャを作成する

1. DEA で、左側のメニューのメニューアイコンを選択します。 展開されたメニューで、カメラ アイコンの横にある **トレースのキャプチャ** を選択します。

    ![メニューの [トレースのキャプチャ] を選択します。](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-capture.png)

1. **[新しいキャプチャ]** の下で、次の情報を入力または選択します。

    - **SQL Server インスタンス名**: サーバートレースをキャプチャする SQL Server を実行しているコンピューターの名前を入力します。
    - **データベース名**: データベーストレースを開始するデータベースの名前を入力します。 データベースを指定しない場合は、サーバー上のすべてのデータベースでトレースがキャプチャされます。
    - **トレースファイル名**: キャプチャのトレースファイルの名前を入力します。
    - **ファイルの最大サイズ (MB)** : ファイルのロールオーバーサイズを選択します。 必要に応じて、選択したファイルサイズに新しいファイルが作成されます。 推奨されるロールオーバーサイズは 200 MB です。
    - **[期間 (分)]** : トレースキャプチャを実行する時間の長さ (分単位) を選択します。
    - **[格納する出力トレースファイルのパス]** : トレースファイルの保存先のパスを選択します。 

    > [!NOTE]
    > トレースファイルへのファイルパスは、SQL Server を実行しているコンピューター上にある必要があります。 SQL Server サービスが特定のアカウントに対して設定されていない場合、トレースファイルを書き込むために、指定したフォルダーに対する書き込みアクセス許可がサービスに必要な場合があります。
    >
    >

    ![新しいキャプチャページ](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-inputs.png)

## <a name="start-the-trace-capture"></a>トレースキャプチャを開始する

必要な情報を入力または選択したら、 **[開始]** を選択してトレースのキャプチャを開始します。 入力した情報が有効な場合は、トレースキャプチャプロセスが開始されます。 そうしないと、無効なエントリを含むテキストボックスが赤色で強調表示されます。 

選択または入力した値が正しいことを確認し、 **[開始]** を選択します。

トレースキャプチャの実行が完了したら、 **[出力トレースファイルを格納するパス]** で指定したファイルの場所で、新しいトレースファイルを見つけます。 左側のメニューの下部にあるベルアイコンを選択して、キャプチャの進行状況を監視します。

![トレースのキャプチャの進行状況](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-progress.png)

### <a name="trace-file"></a>[トレース ファイル]

トレースキャプチャによって、指定した場所に .trc ファイルが書き込まれます。 トレースファイルには、SQL Server データベースのアクティビティのトレース結果が含まれます。 TRC ファイルは、SQL Server によって検出および報告されたエラーに関する詳細情報を提供するように設計されています。

## <a name="frequently-asked-questions-about-trace-capture"></a>トレースキャプチャに関してよく寄せられる質問

DEA でのトレースキャプチャに関してよく寄せられる質問を次に示します。

### <a name="what-events-are-captured-when-i-run-a-trace-capture-on-a-production-database"></a>実稼働データベースでトレースキャプチャを実行すると、どのようなイベントがキャプチャされますか。

次の表に、トレース用に収集するイベントとそれに対応する列データの一覧を示します。
  
|イベント名|テキストデータ (1)|バイナリデータ (2)|データベース ID (3)|ホスト名 (8)|アプリケーション名 (10)|ログイン名 (11)|SPID (12)|開始時刻 (14)|終了時刻 (15)|データベース名 (35)|イベントシーケンス (51)|Issystem で (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC: 完了 (10)**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC: 開始中 (11)**||*|*|*|*|*|*|*||*|*|*|  
|**RPC 出力パラメーター (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL: BatchCompleted (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL: BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**監査ログイン (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**監査ログアウト (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**カーソルを開く (53)**|*||*|*|*|*|*|*||*|*|*|  
|**カーソルの準備 (70)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL の準備 (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec 準備された SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**カーソルの実行 (74)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorUnprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**カーソルを閉じる (78)**|*||*|*|*|*|*|*||*|*|*|  

### <a name="is-there-a-performance-effect-on-my-production-server-when-trace-capture-is-running"></a>トレースキャプチャが実行されている場合、実稼働サーバーにパフォーマンス上の影響はありますか。
    
はい、トレースコレクションの実行中は、パフォーマンスの影響が最小限に抑えられます。 このテストでは、3% のメモリ不足が発生しました。
    
### <a name="what-kind-of-permissions-are-required-for-capturing-traces-on-a-production-workload"></a>運用環境のワークロードでトレースをキャプチャするには、どのような種類のアクセス許可が必要ですか。
    
- DEA アプリケーションでトレース操作を実行する Windows ユーザーには、SQL Server を実行しているコンピューターに対する sysadmin 権限が必要です。
- SQL Server を実行しているコンピューターで使用されるサービスアカウントには、指定されたトレースファイルパスへの書き込みアクセス権が必要です。

### <a name="can-i-capture-traces-for-the-entire-server-or-only-on-a-single-database"></a>サーバー全体または1つのデータベースのみのトレースをキャプチャできますか。
    
DEA を使用すると、サーバー内のすべてのデータベースまたは単一のデータベースのトレースを取り込むことができます。
    
### <a name="i-have-a-linked-server-configured-in-my-production-environment-do-those-queries-show-up-in-the-traces"></a>実稼働環境にリンクサーバーが構成されています。 これらのクエリはトレースに表示されますか。
    
サーバー全体のトレースキャプチャを実行している場合は、リンクサーバークエリを含むすべてのクエリがトレースによってキャプチャされます。 サーバー全体のトレースキャプチャを実行するには、 **[新しいキャプチャ]** の **[データベース名]** ボックスを空のままにします。
    
### <a name="whats-the-minimum-recommended-time-for-production-workload-traces"></a>実稼働ワークロードトレースで推奨される最小時間は何ですか?
    
ワークロード全体を最もよく表す時間を選択することをお勧めします。 そうすることで、ワークロード内のすべてのクエリで分析が実行されます。
    
### <a name="how-important-is-to-take-a-database-backup-right-before-i-start-a-trace-capture"></a>トレースキャプチャを開始する前に、データベースのバックアップを実行することが重要です。
    
トレースキャプチャを開始する前に、すべてのターゲットデータベースをバックアップしていることを確認してください。 ターゲット1とターゲット2でキャプチャされたトレースが再生されます。 データベースの状態が同じでない場合は、実験の結果がスキューされます。

### <a name="can-i-collect-xevents-instead-of-traces-and-can-i-replay-xevents"></a>トレースではなく Xevent を収集することはできますか。 Xevent を再生できますか。
    
可能。 DEA は Xevent をサポートしています。 DEA の最新バージョンをダウンロードし、試してみてください。

## <a name="troubleshoot-trace-captures"></a>トレースキャプチャのトラブルシューティング

トレースキャプチャの実行時にエラーが発生した場合は、次の前提条件を確認してください。

- SQL Server を実行しているコンピューターの名前が有効であることを確認します。 確認するには、SQL Server Management Studio (SSMS) を使用して SQL Server を実行しているコンピューターに接続します。
- ファイアウォール構成で SQL Server を実行しているコンピューターへの接続がブロックされていないことを確認します。
- ブログ投稿の再生に関する[FAQ](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-replay-faq/)に記載されているアクセス許可がユーザーにあることを確認します。
- トレース名が標準のロールオーバー規則 (Capture\_1) に従っていないことを確認します。 代わりに、Capture\_1A または Capture1 のようなトレース名を試してください。

表示される可能性のあるエラーとその解決策を次に示します。

|考えられるエラー|解決方法|  
|---|---|  
|ターゲット SQL Server でトレースを開始できません。必要なアクセス許可があるかどうか、および指定されたトレースファイルパスに対する書き込みアクセス権が SQL Server アカウントにあるかどうかを確認してください。 Sql エラーコード (53)|DEA ツールを実行するユーザーは、SQL Server を実行しているコンピューターにアクセスできる必要があります。 ユーザーに sysadmin ロールが割り当てられている必要があります。|  
|ターゲット SQL Server でトレースを開始できません。必要なアクセス許可があるかどうか、および指定されたトレースファイルパスに対する書き込みアクセス権が SQL Server アカウントにあるかどうかを確認してください。 Sql エラーコード (19062)|指定されたトレースパスが存在しないか、フォルダーに SQL Server サービスを実行しているアカウント (NETWORK SERVICE など) に対する書き込みアクセス許可がありません。 パスが存在し、トレースを開始するために必要なアクセス許可を持っている必要があります。|  
|現在、DEA トレースが対象サーバーで実行されています。|アクティブなトレースは、既に対象サーバーで実行されています。 サーバー全体のトレースが既に実行されている場合、新しいトレースを開始することはできません。|  
|キャプチャトレース用に要求されたデータベースを開くことができません。 このエラーは、データベース名が正しくないことが原因である可能性があります。|指定されたデータベースが存在しないか、現在のユーザーがアクセスできません。 正しいデータベース名を使用してください。|  

*Sql エラーコード*というラベルの他のエラーが表示された場合は、詳細な説明について[データベースエンジンエラー](https://docs.microsoft.com/sql/relational-databases/errors-events/database-engine-events-and-errors)を参照してください。

## <a name="next-steps"></a>次の手順

- キャプチャしたトレースを再生する前に SQL Server の分散再生ツールを構成する方法については、「 [replay の構成](database-experimentation-assistant-configure-replay.md)」を参照してください。

- DEA とデモの19分の概要については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
