---
title: "パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "05/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パラメーター化されたフィルター [SQL Server レプリケーション]、スナップショット"
  - "スナップショット [SQL Server レプリケーション]、パラメーター化されたフィルターおよび"
  - "フィルター [SQL Server レプリケーション]、パラメーター化"
ms.assetid: 00dfb229-f1de-4d33-90b0-d7c99ab52dcb
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パラメーター化されたフィルターでマージ パブリケーションのスナップショットを作成する方法ついて説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **パラメーター化されたフィルターを使用してマージ パブリケーションのスナップショットを作成するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   パラメーター化されたフィルターを使用してマージ パブリケーションのスナップショットを生成する際には、最初にすべてのパブリッシュ済みデータとサブスクリプションのサブスクライバー メタデータを含む標準 (スキーマ) スナップショットを生成する必要があります。 詳細については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。 スキーマ スナップショットを作成した後で、パブリッシュ済みデータのサブスクライバー固有のパーティションを含むスナップショットを作成できます。  
  
-   パブリケーション内の 1 つ以上のアーティクルにフィルターを適用して、各サブスクリプション固有の重複しないパーティションが得られる場合、マージ エージェントが実行されるたびにメタデータがクリーンアップされます。 これは、パーティション スナップショットの有効期間が短時間で切れてしまうことを意味します。 このオプションを使用する場合は、サブスクライバーに対してスナップショットの生成と配信を許可することを検討する必要があります。 フィルター オプションの詳細については、「'パーティションのオプション] の設定」セクションを参照してください。 [パラメーター化されたフィルターを使用してマージ パブリケーションのスナップショットを](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 上のパーティションのスナップショットを生成、 **データ パーティション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。 サブスクライバーには、スナップショットの生成と配信の開始や、スナップショットの生成を許可できます。  
  
 1 つ以上のパーティションに対してスナップショットを生成する前に、以下の作業を行う必要があります。  
  
1.  新規パブリーケーション ウィザードを使用してマージ パブリケーションを作成し、ウィザードの **[フィルターの追加]** ページで 1 つ以上のパラメーター化された行フィルターを指定します。 詳しくは、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
2.  パブリケーションのスキーマ スナップショットを生成します。 既定では、新規パブリケーション ウィザードが完了すると、スキーマ スナップショットが生成されます。また、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]からスキーマ スナップショットを生成することもできます。  
  
#### スキーマ スナップショットを生成するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、スナップショットを作成するパブリケーションを右クリックして **[スナップショット エージェントの状態**します。  
  
4.   **スナップショット エージェントの状態の表示 - \< パブリケーション>** ダイアログ ボックスで、をクリックして **開始**します。  
  
     スナップショット エージェントによるスナップショットの生成が完了すると、"[100%] 17 個のアーティクルのスナップショットが生成されました。" などのメッセージが表示されます。  
  
#### サブスクライバーにスナップショットの生成と配信を許可するには  
  
1.   **データ パーティション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、 **自動的にパーティションを定義し、新しいサブスクライバーで同期するときに必要な場合は、スナップショットを生成**します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
#### スナップショットの生成と更新を行うには  
  
1.   **データ パーティション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、をクリックして **追加**します。  
  
2.  値を入力、 **HOST_NAME()** や **SUSER_SNAME()** スナップショットを作成するパーティションに関連付けられた値。  
  
3.  オプションでスナップショットの更新スケジュールを指定します。  
  
    1.  選択 **スケジュールのスケジュールで実行するには、このパーティションのスナップショット エージェント**  
  
    2.  スナップショットの既定の更新スケジュールをそのまま使用するか、または **[変更]** をクリックして別のスケジュールを指定します。  
  
4.  をクリックして **OK**, を返すことをする、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
5.  プロパティ グリッドでパーティションを選択し、 **[今すぐ選択したスナップショットを生成する]**をクリックします。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 ストアド プロシージャとスナップショット エージェントを使用して、次を実行できます。  
  
-   サブスクライバーが初めて同期されたときに、スナップショットの生成と適用を要求できるようにします。  
  
-   各パーティションのスナップショットを事前に生成します。  
  
-   各サブスクライバーのスナップショットを手動で生成できます。  
  
    > [!IMPORTANT]  
    >  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
#### サブスクライバーでスナップショットの生成と配信を開始するためのパブリケーションを作成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 次のパラメーターを指定します。  
  
    -   **@publication**に、パブリケーション名を指定します。  
  
    -   値 **true** の **@allow_subscriber_initiated_snapshot**, 、サブスクライバーはスナップショット処理を開始できます。  
  
    -   (省略可能)に対して同時に実行可能な動的スナップショット プロセスの数 **@max_concurrent_dynamic_snapshots**です。 最大限の数のプロセスが実行しているときに、サブスクライバーがスナップショットを生成しようとすると、そのプロセスはキューに格納されます。 既定では、同時プロセスの数に限度はありません。  
  
2.  パブリッシャーで実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 1. で使用されるパブリケーションの名前を指定 **@publication** と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 資格情報を [レプリケーション スナップショット エージェント](../../relational-databases/replication/agents/replication-snapshot-agent.md) 実行 **@job_login** と **@password**します。 エージェントが使用する場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに、認証の値も指定する必要があります **0** の **@publisher_security_mode** と [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。 初期スナップショットの作成と、スナップショット エージェントのカスタム スケジュールの定義については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
3.  実行 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) パブリケーションにアーティクルを追加します。 このストアド プロシージャは、パブリケーション内の各アーティクルについて 1 回ずつ実行する必要があります。 パラメーター化されたフィルターを使用する場合を使用する 1 つ以上のアーティクルのパラメーター化された行フィルターを指定する必要があります、 **@subset_filterclause** パラメーター。 詳しくは、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
4.  その他の記事は、パラメーター化された行フィルターに基づいてフィルター処理されますが、実行 [sp_addmergefilter & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) 結合またはアーティクル間に論理レコード リレーションシップを定義します。 このストアド プロシージャは、定義する各リレーションシップにつき 1 回ずつ実行する必要があります。 詳しくは、「 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
5.  マージ エージェントでサブスクライバーを初期化するためにスナップショットが必要な場合、要求側のサブスクリプションのパーティションのスナップショットが自動的に生成されます。  
  
#### パブリケーションを作成し、スナップショットを事前に生成、または自動更新するには  
  
1.  実行 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) パブリケーションを作成します。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
2.  パブリッシャーで実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 1. で使用されるパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@job_login** と **@password**します。 エージェントが使用する場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに、認証の値も指定する必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。 初期スナップショットの作成と、スナップショット エージェントのカスタム スケジュールの定義については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
3.  実行 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) パブリケーションにアーティクルを追加します。 このストアド プロシージャは、パブリケーション内の各アーティクルについて 1 回ずつ実行する必要があります。 パラメーター化されたフィルターを使用する場合は、1 つを使用してアーティクルのパラメーター化された行フィルターを指定する必要があります、 **@subset_filterclause** パラメーター。 詳しくは、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
4.  その他の記事は、パラメーター化された行フィルターに基づいてフィルター処理されますが、実行 [sp_addmergefilter & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) 結合またはアーティクル間に論理レコード リレーションシップを定義します。 このストアド プロシージャは、定義する各リレーションシップにつき 1 回ずつ実行する必要があります。 詳しくは、「 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
5.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), の値を指定する **@publication** 手順 1. のです。 値に注意してください、 **snapshot_jobid** 結果に設定します。  
  
6.  値を変換、 **snapshot_jobid** 手順 5 で取得した **uniqueidentifier**します。  
  
7.  パブリッシャーに対して、 **msdb** データベースを実行 [sp_start_job & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), 、について、手順 6 で取得した変換後の値を指定する **@job_id**します。  
  
8.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepartition & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)します。 手順 1. のパブリケーションの名前を指定 **@publication** とパーティションの定義に使用する値 **@suser_sname** 場合 [SUSER_SNAME & #40 です。Transact SQL と #41;](../../t-sql/functions/suser-sname-transact-sql.md) やフィルター句で使用される **@host_name** 場合 [HOST_NAME & #40 です。Transact SQL と #41;](../../t-sql/functions/host-name-transact-sql.md) フィルター句で使用されます。  
  
9. パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_adddynamicsnapshot_job & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)します。 手順 1. のパブリケーションの名前を指定 **@publication**, の値 **@suser_sname** または **@host_name** からステップ 8、およびジョブのスケジュール。 これにより、指定されたパーティションにパラメーター化スナップショットを生成するジョブが作成されます。 詳しくは、「 [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md)」をご覧ください。  
  
    > [!NOTE]  
    >  このジョブは、手順 2. で定義した初期スナップショット ジョブと同じ Windows アカウントを使用して実行されます。 パラメーター化されたスナップショット ジョブとその関連データのパーティションを削除するには、実行 [sp_dropdynamicsnapshot_job & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropdynamicsnapshot-job-transact-sql.md)します。  
  
10. パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergepartition & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md), の値を指定する **@publication** 手順 1 との値から **@suser_sname** または **@host_name** からステップ 8 です。 値に注意してください、 **dynamic_snapshot_jobid** 結果に設定します。  
  
11. ディストリビューターで、 **msdb** データベースを実行 [sp_start_job & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-start-job-transact-sql.md), 、手順 9. で得られた値を指定する **@job_id**します。 これにより、そのパーティションに対してパラメーター化されたスナップショット ジョブが開始されます。  
  
12. 手順 8. ～ 11. を繰り返し実行して、各サブスクリプションについてパーティション スナップショットを生成します。  
  
#### パブリケーションを作成し、各パーティションのスナップショットを手動で作成するには  
  
1.  実行 [sp_addmergepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) パブリケーションを作成します。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
2.  パブリッシャーで実行 [sp_addpublication_snapshot & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)します。 手順 1. で使用されるパブリケーションの名前を指定 **@publication** とスナップショット エージェントを実行する Windows 資格情報 **@job_login** と **@password**します。 エージェントが使用する場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーに接続するときに、認証の値も指定する必要があります **0** の **@publisher_security_mode** と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン情報 **@publisher_login** と **@publisher_password**します。 これにより、パブリケーション用のスナップショット エージェント ジョブが作成されます。 初期スナップショットの作成と、スナップショット エージェントのカスタム スケジュールの定義については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのパラメーターの指定された値でパブリッシャーを構成する場合を含む *job_login* と *job_password*, 、ディストリビューターにプレーン テキストとして送信されます。 このストアド プロシージャを実行する前に、パブリッシャーとリモート ディストリビューターの間の接続を暗号化する必要があります。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
3.  実行 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) パブリケーションにアーティクルを追加します。 このストアド プロシージャは、パブリケーション内の各アーティクルについて 1 回ずつ実行する必要があります。 パラメーター化されたフィルターを使用する場合に、少なくとも 1 つを使用してアーティクルのパラメーター化された行フィルターを指定する必要があります、 **@subset_filterclause** パラメーター。 詳しくは、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
4.  その他の記事は、パラメーター化された行フィルターに基づいてフィルター処理されますが、実行 [sp_addmergefilter & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) 結合またはアーティクル間に論理レコード リレーションシップを定義します。 このストアド プロシージャは、定義する各リレーションシップにつき 1 回ずつ実行する必要があります。 詳しくは、「 [Define and Modify a Join Filter Between Merge Articles](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
5.  スナップショット ジョブを開始するか、コマンド プロンプトからレプリケーション スナップショット エージェントを実行して、標準のスナップショット スキーマおよびその他のファイルを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
6.  用のパーティション スナップショットの場所を指定して、一括コピー (.bcp) ファイルを生成するコマンド プロンプトからレプリケーション スナップショット エージェントを再実行 **-dynamicsnapshotlocation** 、一方または両方のパーティションを定義する次のプロパティ。  
  
    -   **-Dynamicfilterhostname** -値場合 [HOST_NAME & #40 です。Transact SQL と #41;](../../t-sql/functions/host-name-transact-sql.md) 使用されます。  
  
    -   **-Dynamicfilterlogin** -値場合 [SUSER_SNAME & #40 です。Transact SQL と #41;](../../t-sql/functions/suser-sname-transact-sql.md) 使用されます。  
  
7.  手順 6. を繰り返し実行して、各サブスクリプションについてパーティション スナップショットを生成します。  
  
8.  サブスクリプションごとにマージ エージェントを実行して、初期のパーティション スナップショットをサブスクライバーに適用します。次のプロパティを指定します。  
  
    -   **-Hostname** -HOST_NAME の実際の値がオーバーライドされた場合、パーティションの定義に使用される値。  
  
    -   **-Dynamicsnapshotlocation** -このパーティションの動的スナップショットの場所。  
  
> [!NOTE]  
>  レプリケーション エージェントのプログラミングの詳細については、次を参照してください。 [レプリケーション エージェント実行可能ファイルの概念](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)です。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、サブスクライバーによってスナップショット生成プロセスが開始される場合に、パラメーター化されたフィルターを使用してマージ パブリケーションを作成します。 値が **@job_login** と **@job_password** スクリプト変数を使用して渡されます。  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_1.sql)]  
  
 この例で、各サブスクライバーがパーティションを実行することによって定義パラメーター化されたフィルターを使用してパブリケーションを作成 [sp_addmergepartition](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md) とフィルター選択されたスナップショット ジョブを実行して作成 [sp_adddynamicsnapshot_job](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md) パーティション情報を渡しています。 値が **@job_login** と **@job_password** スクリプト変数を使用して渡されます。  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_2.sql)]  
  
 次の例では、各サブスクライバーでパーティション情報を入力してデータ パーティションとフィルター選択したスナップショット ジョブを作成する必要がある場合に、パラメーター化されたフィルターを使用してパブリケーションを作成します。 レプリケーション エージェントを手動で実行する場合、サブスクライバーではコマンド ライン パラメーターを使用してパーティション情報を入力します。 この例では、パブリケーションに対するサブスクリプションも作成されることを想定しています。  
  
 [!code-sql[HowTo#sp_MergeDynamicPubPartitionManual](../../relational-databases/replication/codesnippet/tsql/create-a-snapshot-for-a-_3.sql)]  
  
```  
  
REM Line breaks are added to improve readability.   
REM In a batch file, commands must be made in a single line.  
REM Run the Snapshot agent from the command line to generate the standard snapshot   
REM schema and other files.   
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub% -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  
  
PAUSE  
  
```  
  
```  
  
REM Run the Snapshot agent from the command line, this time to generate   
REM the bulk copy (.bcp) data for each Subscriber partition.    
SET DistPub=%computername%  
SET PubDB=AdventureWorks2012   
SET PubName=AdvWorksSalesPersonMerge  
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
MD %SnapshotDir%  
  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %PubName%    
-Publisher %DistPub%  -Distributor  %DistPub%  -PublisherDB %PubDB%  -ReplicationType 2    
-OutputVerboseLevel 1  -DistributorSecurityMode 1  -DynamicFilterHostName "adventure-works\Fernando"    
-DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
```  
  
REM Run the Merge Agent for each subscription to apply the partitioned   
REM snapshot for each Subscriber.    
SET Publisher = %computername%  
SET Subscriber = %computername%  
SET PubDB = AdventureWorks2012   
SET SubDB = AdventureWorks2012Replica   
SET PubName = AdvWorksSalesPersonMerge   
SET SnapshotDir=\\%DistPub%\repldata\unc\fernando  
  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publisher  %Publisher%    
-Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB %PubDB%    
-SubscriberDB %SubDB% -Publication %PubName%  -PublisherSecurityMode 1  -OutputVerboseLevel 3    
-Output -SubscriberSecurityMode 1  -SubscriptionType 3 -DistributorSecurityMode 1    
-Hostname "adventure-works\Fernando"  -DynamicSnapshotLocation %SnapshotDir%  
  
PAUSE  
  
```  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 パーティション スナップショットは、プログラムからレプリケーション管理オブジェクト (RMO) を使用して生成できます。その方法を次に示します。  
  
-   サブスクライバーが初めて同期されたときに、スナップショットの生成と適用を要求できるようにします。  
  
-   各パーティションのスナップショットを事前に生成します。  
  
-   スナップショット エージェントを実行してサブスクライバーごとにスナップショットを手動で生成できます。  
  
> [!NOTE]  
>  メタデータがクリーンアップ (P:Microsoft.SqlServer.Replication.MergeArticle.PartitionOption の F:Microsoft.SqlServer.Replication.PartitionOptions.NonOverlappingSingleSubscription の値を指定する、マージ アーティクルを作成する場合) を各サブスクリプションに対して一意では、重複しないパーティションを生成するアーティクルのフィルター処理、時にマージ エージェントが実行されるたびにします。 これは、パーティション スナップショットの有効期間が短時間で切れてしまうことを意味します。 このオプションを使用する場合は、サブスクライバーからスナップショットの生成を要求できるようにする必要があります。 詳細については、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md)」の「適切なフィルター選択オプションの使用」を参照してください。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../includes/msconame-md.md)] を使用します。  
  
#### サブスクライバーでスナップショットの生成と配信を開始するためのパブリケーションを作成するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのパブリケーション データベースで、設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティのインスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1、および呼び出しから、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 場合 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 返します **false**, 、データベースが存在することを確認します。  
  
3.  場合 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> プロパティは **false**, に設定 **true** を呼び出すと <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A>します。  
  
4.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスし、このオブジェクトの次のプロパティを設定します。  
  
    -    <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
    -   パブリッシュされたデータベースの名前 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>します。  
  
    -   実行する動的スナップショット ジョブの最大数 <xref:Microsoft.SqlServer.Replication.MergePublication.MaxConcurrentDynamicSnapshots%2A>します。 サブスクライバーがスナップショットを要求するタイミングは不定です。そのため、同時に複数のサブスクライバーがパーティション スナップショットを要求した場合に、このプロパティを使って、同時に実行できるスナップショット エージェント ジョブの数を制限します。 実行中のジョブが最大数に達した場合は、パーティション スナップショットに対するそれ以降の要求は、実行されているいずれかのジョブが完了するまでキューに格納されます。  
  
    -   ビットごとの論理 OR を使用して (**|** Visual C# の場合と **または** Visual Basic で) 値を追加する演算子 <xref:Microsoft.SqlServer.Replication.PublicationAttributes.AllowSubscriberInitiatedSnapshot> に <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>します。  
  
    -    <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Login%2A> と <xref:Microsoft.SqlServer.Replication.IProcessSecurityContext.Password%2A> のフィールド <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> の資格情報を提供する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] スナップショット エージェント ジョブが実行される Windows アカウントです。  
  
        > [!NOTE]  
        >  設定 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A> のメンバー、パブリケーションを作成するときに推奨される、 **sysadmin** 固定サーバー ロールです。 詳しくは、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」をご覧ください。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> パブリケーションを作成します。  
  
    > [!IMPORTANT]  
    >  リモート ディストリビューター、すべてのプロパティの指定された値でパブリッシャーを構成する場合を含む <xref:Microsoft.SqlServer.Replication.Publication.SnapshotGenerationAgentProcessSecurity%2A>, 、ディストリビューターにプレーン テキストとして送信されます。 発行元と呼び出しの前にリモート ディストリビューター間の接続を暗号化する必要があります、 <xref:Microsoft.SqlServer.Replication.Publication.Create%2A> メソッドです。 詳細については、次を参照してください [データベース エンジンと #40; への暗号化接続の有効化。SQL Server 構成マネージャーと #41;](../../database-engine/configure-windows/enable encrypted connections to the database engine.md)します。  
  
6.  使用して、 <xref:Microsoft.SqlServer.Replication.MergeArticle> プロパティをパブリケーションにアーティクルを追加します。 指定の <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> パラメーター化されたフィルターを定義するには、少なくとも 1 つのアーティクルのプロパティです。 (省略可能)作成 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> を定義するオブジェクト間の結合フィルターの記事です。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
7.  場合の値 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> は **false**, 、呼び出す <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> このパブリケーションの初期スナップショット エージェント ジョブを作成します。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> のメソッド、 <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 4. で作成されたオブジェクト。 これにより、初期スナップショットを生成するエージェント ジョブが開始されます。 初期スナップショットの作成と、スナップショット エージェントのカスタム スケジュールの定義については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
9. (省略可能)値をチェックして **true** の <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> 、初期スナップショットが使用可能な状態を確認するにします。  
  
10. サブスクライバーのマージ エージェントの初回接続時に、パーティション スナップショットが自動的に生成されます。  
  
#### パブリケーションを作成し、スナップショットを事前に生成したり、自動的に更新するには  
  
1.  インスタンスを使用して、 <xref:Microsoft.SqlServer.Replication.MergePublication> マージ パブリケーションを定義するクラス。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
2.  使用して、 <xref:Microsoft.SqlServer.Replication.MergeArticle> プロパティをパブリケーションにアーティクルを追加します。 指定の <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> プロパティをパラメーター化されたフィルターを定義し、いずれかを作成するには、少なくとも 1 つのアーティクルについて <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> を定義するオブジェクト間の結合フィルターの記事です。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
3.  場合の値 <xref:Microsoft.SqlServer.Replication.Publication.SnapshotAgentExists%2A> は **false**, 、呼び出す <xref:Microsoft.SqlServer.Replication.Publication.CreateSnapshotAgent%2A> このパブリケーションに対してスナップショット エージェント ジョブを作成します。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.StartSnapshotGenerationAgentJob%2A> のメソッド、 <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 1. で作成されたオブジェクト。 このメソッドにより、初期スナップショットを生成するエージェント ジョブが開始されます。 初期スナップショットを生成する方法、およびスナップショット エージェントのカスタム スケジュールを定義する方法については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
5.  値をチェックして **true** の <xref:Microsoft.SqlServer.Replication.MergePublication.SnapshotAvailable%2A> 、初期スナップショットが使用可能な状態を確認するにします。  
  
6.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePartition> クラスし、次のプロパティの一方または両方を使用するサブスクライバーのパラメーター化されたフィルター条件を設定します。  
  
    -   結果によって、サブスクライバーのパーティションが定義されているかどうかは [SUSER_SNAME & #40 です。Transact SQL と #41;](../../t-sql/functions/suser-sname-transact-sql.md), を使用して <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A>します。  
  
    -   結果によって、サブスクライバーのパーティションが定義されているかどうかは [HOST_NAME & #40 です。Transact SQL と #41;](../../t-sql/functions/host-name-transact-sql.md) オーバー ロードこれを使用して、関数、または <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A>します。  
  
7.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> クラス、および手順 6. と同じプロパティを設定します。  
  
8.  使用して、 <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> サブスクライバー パーティションのフィルター選択されたスナップショットを生成するためのスケジュールを定義するクラス。  
  
9. インスタンスを使用して <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 1 から呼び出して <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergePartition%2A>します。 渡す、 <xref:Microsoft.SqlServer.Replication.MergePartition> 手順 6 でのオブジェクト。  
  
10. インスタンスを使用して <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 1 から呼び出して、 <xref:Microsoft.SqlServer.Replication.MergePublication.AddMergeDynamicSnapshotJob%2A> メソッドです。 渡す、 <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> 手順 7 からオブジェクトと <xref:Microsoft.SqlServer.Replication.ReplicationAgentSchedule> 手順 8 からのオブジェクト。  
  
11. 呼び出す <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergeDynamicSnapshotJobs%2A>, を検索し、 <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob> 返される配列に新しく追加されたパーティション スナップショット ジョブのオブジェクト。  
  
12. 取得、 <xref:Microsoft.SqlServer.Replication.MergeDynamicSnapshotJob.Name%2A> ジョブのプロパティです。  
  
13. 使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
14. SQL Server 管理オブジェクト (SMO) のインスタンスを作成 <xref:Microsoft.SqlServer.Management.Smo.Server> を渡して、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 13 からのオブジェクト。  
  
15. インスタンスを作成、 <xref:Microsoft.SqlServer.Management.Smo.Agent.Job> を渡して、 <xref:Microsoft.SqlServer.Management.Smo.Server.JobServer%2A> のプロパティ、 <xref:Microsoft.SqlServer.Management.Smo.Server> 手順 14 と手順 12. の手順からジョブ名からのオブジェクト。  
  
16. 呼び出す、 <xref:Microsoft.SqlServer.Management.Smo.Agent.Job.Start%2A> パーティション スナップショット ジョブを開始します。  
  
17. 手順 6. から手順 16. を各サブスクライバーについて繰り返します。  
  
#### パブリケーションを作成し、各パーティションのスナップショットを手動で作成するには  
  
1.  インスタンスを使用して、 <xref:Microsoft.SqlServer.Replication.MergePublication> マージ パブリケーションを定義するクラス。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
2.  使用して、 <xref:Microsoft.SqlServer.Replication.MergeArticle> プロパティを指定するパブリケーションにアーティクルを追加、 <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> プロパティをパラメーター化されたフィルターを定義し、いずれかを作成するには、少なくとも 1 つのアーティクルについて <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> を定義するオブジェクト間の結合フィルターの記事です。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
3.  初期スナップショットを生成します。 詳しくは、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」をご覧ください。  
  
4.  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent> クラスのインスタンスを作成し、次の必須プロパティを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publisher%2A> - パブリッシャーの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherDatabase%2A> - パブリケーション データベースの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Publication%2A> - パブリケーションの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.Distributor%2A> - ディストリビューターの名前  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.PublisherSecurityMode%2A> -の値 <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> Windows 統合認証を使用するかの値を <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> SQL Server 認証を使用します。  
  
    -   <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DistributorSecurityMode%2A> -値の <xref:Microsoft.SqlServer.Replication.SecurityMode.Integrated> Windows 統合認証を使用するかの値を <xref:Microsoft.SqlServer.Replication.SecurityMode.Standard> SQL Server 認証を使用します。  
  
5.  値を設定 <xref:Microsoft.SqlServer.Replication.ReplicationType.Merge> の <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.ReplicationType%2A>します。  
  
6.  次に示したプロパティを少なくとも 1 つ設定し、パーティションのパラメーターを定義します。  
  
    -   結果によって、サブスクライバーのパーティションが定義されているかどうかは [SUSER_SNAME & #40 です。Transact SQL と #41;](../../t-sql/functions/suser-sname-transact-sql.md), を使用して <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterLogin%2A>します。  
  
    -   結果によって、サブスクライバーのパーティションが定義されているかどうかは [HOST_NAME & #40 です。Transact SQL と #41;](../../t-sql/functions/host-name-transact-sql.md) オーバー ロードこれを使用して、関数、または <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.DynamicFilterHostName%2A>します。  
  
7.  <xref:Microsoft.SqlServer.Replication.SnapshotGenerationAgent.GenerateSnapshot%2A> メソッドを呼び出します。  
  
8.  手順 4. から手順 7. を各サブスクライバーについて繰り返します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、サブスクライバーがスナップショット生成を要求できるマージ パブリケーションを作成します。  
  
 [!code-csharp[HowTo#rmo_CreateMergePub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepub)]  
  
 次の例では、手動でサブスクライバーのパーティションを作成し、さらに、パラメーター化された行フィルターを使って、マージ パブリケーションのフィルター選択されたスナップショットを作成します。  
  
 [!code-csharp[HowTo#rmo_CreateMergePartition](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergepartition)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergePartition](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergepartition)]  
  
 次の例では、手動でスナップショット エージェントを起動し、パラメーター化された行フィルターを使って、マージ パブリケーションのサブスクライバー用にフィルター選択されたデータ スナップショットを生成します。  
  
 [!code-csharp[HowTo#rmo_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_generatefilteredsnapshot)]  
  
 [!code-vb[HowTo#rmo_vb_GenerateFilteredSnapshot](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_generatefilteredsnapshot)]  
  
## 参照  
 [パラメーター化された行フィルター](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  