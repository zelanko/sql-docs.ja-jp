---
title: 'チュートリアル: サーバーとモバイル クライアントの間のレプリケーション (マージ) を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 04/03/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d9751b7adc3d2cd4169bcd6b3a174de720c05eb9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-a-server-and-mobile-clients-merge"></a>チュートリアル: サーバーとモバイル クライアントの間のレプリケーション (マージ) を構成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
マージ レプリケーションは、中央のサーバーと、常時接続でないモバイル クライアントの間でデータを移動する際の問題を解決する有効なソリューションです。 レプリケーション ウィザードを使用すると、マージ レプリケーション トポロジを簡単に設定し、管理できます。 このチュートリアルでは、モバイル クライアント用のレプリケーション トポロジを設定する方法を学習します。  マージ レプリケーションの詳細については、[マージ レプリケーションの概要](https://docs.microsoft.com/en-us/sql/relational-databases/replication/merge/merge-replication)に関するページを参照してください
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、マージ レプリケーションを使用して中央のデータベースから 1 名以上のモバイル ユーザーにデータをパブリッシュし、各ユーザーが独自にフィルター選択されたデータ サブセットを取得するようにする方法を説明します。 

このチュートリアルでは、次の内容を学習します。
> [!div class="checklist"]
> * マージ レプリケーションのパブリッシャーの構成
> * マージ パブリケーションのモバイル サブスクライバーの追加
> * マージ パブリケーションへのサブスクリプションの同期
  
## <a name="prerequisites"></a>Prerequisites  
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。 このチュートリアルを開始する前に、「[チュートリアル: レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)」を完了しておく必要があります。  
  
このチュートリアルを使用するには、システムに SQL Server Management Studio と次のコンポーネントがインストールされている必要があります。  
  
-   パブリッシャー サーバー側 (レプリケーション元) :  
  
    -   SQL Server Express または SQL Server Compact を除く、SQL Server の任意のエディション。 レプリケーションのパブリッシャーとして使用できないため除きます。   
    -   [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。  
  
-   サブスクライバー サーバー側 (レプリケーション先) :  
  
    -   [!INCLUDE[ssEW](../../includes/ssew-md.md)] を除く SQL Server の任意のエディション。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] は、このチュートリアルで作成するパブリケーションで使用できません。 

- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する方法の詳細については、「[SSMS を使用してデータベース バックアップを復元する](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)」を参照してください。  
 
  
>[!NOTE]
> - 3 つ以上離れたバージョンの SQL Server では、レプリケーションはサポートされていません。 詳細については、「[Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/)」(Repl トポロジでサポートされている SQL バージョン) を参照してください。
> - [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、固定サーバー ロール **sysadmin** のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。 sysadmin ロールの詳細については、「[サーバー レベルのロール](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles)」を参照してください。  
  
  
**このチュートリアルの推定所要時間: 60 分。**  
  
## <a name="configure-a-publisher-for-merge-replication"></a>マージ レプリケーションのパブリッシャーの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
このセクションでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してマージ パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Employee** テーブル、**SalesOrderHeader** テーブル、および **SalesOrderDetail** テーブルのサブセットをパブリッシュします。 ここでは、パラメーター化された行フィルターを使ってこれらのテーブルをフィルター処理し、サブスクリプションごとに一意のデータ部分が含まれるようにします。 また、マージ エージェントにより使用される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインをパブリケーション アクセス リスト (PAL) に追加します。  
  
### <a name="create-merge-publication-and-define-articles"></a>マージ パブリケーションを作成してアーティクルを定義する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2. **オブジェクト エクスプローラー**で **[SQL Server エージェント]** を右クリックして **[開始]** を選択し、SQL Server エージェントを起動します。 この方法でエージェントが起動しない場合は、**SQL Server 構成マネージャー**から手動で起動する必要があります。  
3. **[レプリケーション]** フォルダーを展開し、**[ローカル パブリケーション]** を右クリックして、**[新しいパブリケーション]** を選択します。  パブリケーションの新規作成ウィザードが起動します。  

    ![パブリケーションの新規作成ウィザードを起動する](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
3.  [パブリケーション データベース] ページで [[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、**[次へ]** を選択します。 

      
4.  [パブリケーションの種類] ページで、**[マージ パブリケーション]** を選択し、**[次へ]** を選択します。  
    A. [サブスクライバーの種類] ページで、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のみが選択されていることを確認し、**[次へ]** を選択します。 

    ![マージ レプリケーション](media/tutorial-replicating-data-with-mobile-clients/mergerpl.png)
  
   
6.  [アーティクル] ページで、**[テーブル]** ノードを展開し、**Employee**、**SalesOrderHeader**、および **SalesOrderDetail** の 3 つのテーブルを選択します。 **[次へ]** を選択します。  

    ![マージ アーティクル](media/tutorial-replicating-data-with-mobile-clients/mergearticles.png)

    >[!NOTE]
    > Employee テーブルには、hierarchyid データ型を持つ列 (OrganizationNode) が含まれています。これは、SQL 2017 でレプリケーションに対してのみサポートされています。 SQL 2017 より前のビルドを使用している場合は、双方向のレプリケーションでこの列を使用するとデータ損失の可能性があることを通知するメッセージが画面の下部に表示されます。 このチュートリアルでは、このメッセージは無視してかまいません。 ただし、このデータ型は、サポートされているビルドを使用している場合を除き、実稼働環境でレプリケートしないでください。 hierarchyid データ型のレプリケーションに関する詳細は、「[レプリケートされたテーブルでの hierarchyid 列の使用](https://docs.microsoft.com/en-us/sql/t-sql/data-types/hierarchyid-data-type-method-reference#using-hierarchyid-columns-in-replicated-tables)」を参照してください。
    
  
7.  [テーブル行のフィルター選択] ページで、**[追加]**、**[フィルターの追加]** の順に選択します。  
  
8.  **[フィルターの追加]** ダイアログ ボックスの **[フィルターを適用するテーブルを選択します。]** で、**[Employee (HumanResources)]** を選択します。 **[LoginID]** 列を選択し、右矢印を選択して、この列をフィルター選択クエリの WHERE 句に追加します。さらに、WHERE 句を次のように修正します。  
  
    ```sql 
    WHERE [LoginID] = HOST_NAME()  
    ```  
  
    A. **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]** を選択して、**[OK]** を選択します。  
 
    ![フィルターの追加](media/tutorial-replicating-data-with-mobile-clients/mergeaddfilter.png)

    
  
10. **[テーブル行のフィルター選択]** ページで、**[Employee (Human Resources)]**、**[追加]** の順に選択し、**[選択したフィルターを拡張するために結合を追加する]** を選択します。  
  
    A. **[結合の追加]** ダイアログ ボックスで、**[結合テーブル]** の下の **[Sales.SalesOrderHeader]** を選択します。 **[JOIN ステートメントを手動で作成する]** を選択し、次のように JOIN ステートメントを完成させます。  
  
    ```sql  
    ON [Employee].[BusinessEntityID] =  [SalesOrderHeader].[SalesPersonID] 
    ```  
  
    B. **[結合オプションを指定します]** で、**[一意キー]** を選択して **[OK]** を選択します。

    ![フィルターへの結合の追加](media/tutorial-replicating-data-with-mobile-clients/mergeaddjoin.png)

  
13. [テーブル行のフィルター選択] ページで、**[SalesOrderHeader]**、**[追加]** の順に選択し、**[選択したフィルターを拡張するために結合を追加する]** を選択します。  
  
    A. **[結合の追加]** ダイアログ ボックスで、 **[結合テーブル]** の下の **[Sales.SalesOrderDetail]** をクリックします。    
    B. **[ビルダーを使用してステートメントを作成する]** を選択します。  
    c. **[プレビュー]** ボックスで、JOIN ステートメントが次のようになっていることを確認します。  
  
    ```sql  
    ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID] 
    ```  
  
    d. **[結合オプションを指定します]** で、**[一意キー]** を選択して **[OK]** を選択します。 **[次へ]** を選択します。 

       ![Sales Order テーブルの結合](media/tutorial-replicating-data-with-mobile-clients/joinsalestables.png)
  
21. **[スナップショットをすぐに作成する]** を選択し、**[以下のスケジュールでスナップショット エージェントを実行する]** をオフにして、**[次へ]** を選択します。  

    ![スナップショットをすぐに作成する](media/tutorial-replicating-data-with-mobile-clients/snapshotagent.png)
  
22. [エージェント セキュリティ] ページで、**[セキュリティの設定]** を選択して、**[プロセス アカウント]** ボックスに「<*パブリッシャー コンピューター名>***\repl_snapshot**」と入力します。さらに、このアカウントのパスワードを入力して、**[OK]** を選択します。 **[次へ]** を選択します。  

    ![[スナップショット エージェントのセキュリティ]](media/tutorial-replicating-data-with-mobile-clients/snapshotagentsecurity.png)
  
23. **[ウィザードの完了]** ページで、**[パブリケーション名]** ボックスに「**AdvWorksSalesOrdersMerge**」と入力し、**[完了]** を選択します。  

    ![マージ レプリケーションの命名](media/tutorial-replicating-data-with-mobile-clients/namemergerepl.png)
  
24. パブリケーションが作成されたら、**[閉じる]** を選択します。 **オブジェクト エクスプローラー**で **[レプリケーション]** ノードの下の **[ローカル パブリケーション]** を右クリックして **[更新]** を選択し、新しいマージ レプリケーションを表示します。  
  
### <a name="to-view-the-status-of-snapshot-generation"></a>スナップショット生成の状態を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  [ローカル パブリケーション] フォルダーを展開し、**[AdvWorksSalesOrdersMerge]** を右クリックして、**[スナップショット エージェントの状態の表示]** を選択します。  

    ![スナップショット エージェントの状態の表示](media/tutorial-replicating-data-with-mobile-clients/viewsnapshotagentstatus.png)
  
3.  パブリケーションのスナップショット エージェントの現在の状態が表示されるので、 スナップショット ジョブが正常に終了していることを確認してから次のレッスンに進みます。  
  
### <a name="to-add-the-merge-agent-login-to-the-pal"></a>マージ エージェントのログインを PAL に追加するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  [ローカル パブリケーション] フォルダーを展開し、**[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、**[プロパティ]** を選択します。  
  
    A. **[パブリケーション アクセス リスト]** ページを選択して、**[追加]** を選択します。 
  
    B. [パブリケーション アクセスの追加] ダイアログ ボックスで、<*パブリッシャー コンピューター名>***\repl_merge** を選択して **[OK]** を選択します。 **[OK]** を選択します。 

    ![PAL のマージ](media/tutorial-replicating-data-with-mobile-clients/mergepal.png) 

  
**参照**:  
[パブリッシュされたデータのフィルター選択](../../relational-databases/replication/publish/filter-published-data.md)  
[パラメーター化された行フィルター](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
[Define an Article](../../relational-databases/replication/publish/define-an-article.md)  
  
  
## <a name="creating-a-subscription-to-the-merge-publication"></a>マージ パブリケーションへのサブスクリプションの作成
このセクションでは、前の手順で作成したマージ パブリケーションにサブスクリプションを追加します。 このチュートリアルでは、リモート サブスクライバー (NODE2\SQL2016) を使用します。 次に、サブスクリプション データベースに権限を設定し、新しいサブスクリプション用のフィルター選択データのスナップショットを手動で作成します。   
  
### <a name="add-a-subscriber-for-merge-publication"></a>マージ パブリケーションのサブスクライバーの追加
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクライバーに接続して、サーバー ノードを展開します。 **[レプリケーション]** フォルダーを展開し、**[ローカル サブスクリプション]** フォルダーを右クリックして、**[新しいサブスクリプション]** を選択します。 サブスクリプションの新規作成ウィザードが起動します。

    ![[新しいサブスクリプション]](media/tutorial-replicating-data-with-mobile-clients/newsub.png)
  
2.  **[パブリケーション]** ページで、**[パブリッシャー]** ボックスの一覧の **[SQL Server パブリッシャーの検索]** を選択します。  
  
    A. **[サーバーへの接続]** ダイアログ ボックスで、**[サーバー名]** ボックスにパブリッシャー インスタンスの名前を入力し、**[接続]** を選択します。 

    ![パブリケーションでのパブリッシャーの追加](media/tutorial-replicating-data-with-mobile-clients/publication.png)
  
4.  **[AdvWorksSalesOrdersMerge]** を選択し、**[次へ]** を選択します。  
  
5.  [マージ エージェントの場所] ページで、**[サブスクライバーで各エージェントを実行する]** を選択して、**[次へ]** を選択します。  

    ![プル サブスクリプション](media/tutorial-replicating-data-with-mobile-clients/pullsub.png)
  
6.  [サブスクライバー] ページで、サブスクライバー サーバーのインスタンス名を選択し、**[サブスクリプション データベース]** の一覧で **[新しいデータベース]** を選択します。  
  
    A. **[新しいデータベース]** ダイアログ ボックスで、**[データベース名]** ボックスに「**SalesOrdersReplica**」と入力し、**[OK]**、**[次へ]** の順に選択します。 

    ![Sub に DB を追加](media/tutorial-replicating-data-with-mobile-clients/addsubdb.png)
  
8.  [マージ エージェント セキュリティ] ページで参照ボタン (**[…]**) を選択し、**[プロセス アカウント]** ボックスに「<*サブスクライバー コンピューター名>***\repl_merge**」と入力して、このアカウントのパスワードを入力します。次に **[OK]** を選択し、**[次へ]** を選択し、もう一度 **[次へ]** を選択します。  

    ![[マージ エージェント セキュリティ]](media/tutorial-replicating-data-with-mobile-clients/mergeagentsecurity.png)

9. **[同期スケジュール]** で、**[エージェント スケジュール]** を **[要求時にのみ実行する]** に設定します。 **[次へ]** を選択します。  

    ![同期スケジュール](media/tutorial-replicating-data-with-mobile-clients/mergesyncschedule.png)
  
9. **[サブスクリプションの初期化]** ページで、**[次の場合に初期化]** ボックスの一覧から **[初回同期時]** を選択し、**[次へ]** を 2 回選択します。 

    ![最初の同期](media/tutorial-replicating-data-with-mobile-clients/firstsync.png)

10. [HOST_NAME 値] ページで、**[HOST_NAME 値]** ボックスに値「**adventure-works\pamela0**」と入力して、**[完了]** を選択します。  

    ![hostname](media/tutorial-replicating-data-with-mobile-clients/hostname.png)
  
11. もう一度 **[完了]** を選択し、サブスクリプションが作成されたら **[閉じる]** を選択します。  

### <a name="setting-server-permissions-at-the-subscriber"></a>サブスクライバー側でサーバー アクセス許可を設定する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクライバーに接続し、**[セキュリティ]** を展開して **[ログイン]** を右クリックし、**[新しいログイン]** を選択します。  
  
    A. **[全般]** ページで、**[検索]** を選択し、**[オブジェクト名を入力してください]** フィールドに「<*サブスクライバーのコンピューター名>***\repl_merge*」と入力し、**[名前の確認]** を選択して、**[OK]** を選択します。 
    
    ![サブスクライバーでのログイン](media/tutorial-replicating-data-with-mobile-clients/sublogin.png)
  
1. **[ユーザー マッピング]** ページで、**[SalesOrdersReplica]** データベースを選択し、**[db_owner]** ロールを選択します。  **[セキュリティ保護可能なリソース]** ページで、**[トレースの変更]** に 'Explicit' アクセス許可を付与します。 **[OK]** を選択します。

    ![Sub で DBO としてログインを設定する](media/tutorial-replicating-data-with-mobile-clients/setdbo.png)
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>サブスクリプション用のフィルター選択データのスナップショットを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksSalesOrdersMerge]** パブリケーションを右クリックして、**[プロパティ]** を選択します。  
   
    A. **[データ パーティション]** ページを選択して、**[追加]** を選択します。   
    B. **[データ パーティションの追加]** ダイアログ ボックスで、**[HOST_NAME 値]** ボックスに「**adventure-works\pamela0**」と入力し、**[OK]** を選択します。  
    c. 新しく追加したパーティションを選択して、**[今すぐ選択したスナップショットを生成する]** を選択し、**[OK]** を選択します。 

    ![パーティションの追加](media/tutorial-replicating-data-with-mobile-clients/partition.png)
  
  
**参照**:  
[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
[Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
[パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  

## <a name="synchronize-the-subscription-to-the-merge-publication"></a>マージ パブリケーションへのサブスクリプションの同期

このセクションでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してマージ エージェントを起動して、サブスクリプションを初期化します。 この手順を使用して、パブリッシャーと同期することもできます。   
  
### <a name="to-start-synchronization-and-initialize-the-subscription"></a>同期を開始しサブスクリプションを初期化するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクライバーに接続します。  
2. **SQL Server エージェント**が実行されていることを確認します。 実行されていない場合は、**オブジェクト エクスプローラー**で **[SQL Server エージェント]** を右クリックして **[開始]** を選択します。 この方法でエージェントの起動に失敗する場合は、**SQL Server 構成マネージャー**を使用して手動で起動する必要があります。 
  
2.  **[レプリケーション]** ノードを展開します。 **[ローカル サブスクリプション]** フォルダーで、**SalesOrdersReplica** データベースのサブスクリプションを右クリックし、**[同期の状態の表示]** を選択します。  
  
    A. **[開始]** を選択して、サブスクリプションを初期化します。 

    ![同期状態](media/tutorial-replicating-data-with-mobile-clients/mergesyncstatus.png)
    
  
  
### <a name="next-steps"></a>Next Steps  
マージ レプリケーション用にパブリッシャーとサブスクライバーの両方を正しく構成しました。  パブリッシャーまたはサブスクライバー側で、 **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルに対しデータの挿入、変更、削除を行い、ネットワーク接続が使用できるときにこの手順でパブリッシャーとサブスクライバーの間のデータを同期した後、もう一方のサーバーの **SalesOrderHeader** テーブルまたは **SalesOrderDetail** テーブルにクエリを実行すると、レプリケートされた変更を確認することができます。  
  
**参照**:   
[スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[データベースの同期](../../relational-databases/replication/synchronize-data.md)  
[プル サブスクリプションの同期](../../relational-databases/replication/synchronize-a-pull-subscription.md)  
  
  
  
  
