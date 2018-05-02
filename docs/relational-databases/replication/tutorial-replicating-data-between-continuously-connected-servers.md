---
title: 'チュートリアル: 2 つの常時接続サーバー間のレプリケーション (トランザクション) を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de374f4372f62741ff3c49a9433cf339cecf3d26
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-two-fully-connected-servers-transactional"></a>チュートリアル: 2 つの常時接続サーバー間のレプリケーション (トランザクション) を構成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
トランザクション レプリケーションは、常時接続サーバー間でデータを移動する際の問題を解決する有効なソリューションです。 レプリケーション ウィザードを使用すると、レプリケーション トポロジを簡単に設定し、管理できます。 このチュートリアルでは、常時接続サーバー間にトランザクション レプリケーション トポロジを設定する方法を学習します。 トランザクション レプリケーションのしくみについては、[トランザクション レプリケーションの概要](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication)に関するページを参照してください。 
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、トランザクション レプリケーションによって 1 つのデータベースから別のデータベースにデータをパブリッシュする方法を学習します。 

このチュートリアルでは、次の内容を学習します。
> [!div class="checklist"]
> * トランザクション レプリケーションを使用してパブリッシャーを作成する
> * トランザクション パブリッシャーのサブスクライバーを作成する
> * サブスクリプションを検証し、待機時間を計測する
> * エラーのトラブルシューティングの手法
  
  
## <a name="prerequisites"></a>Prerequisites  
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。 このチュートリアルを学習するには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。  
  
このチュートリアルを使用するには、システムに SQL Server Management Studio (SSMS) とこれらのコンポーネントが必要です。  
  
-   パブリッシャー サーバー側 (レプリケーション元) :  
  
    -   SQL Server Express または SQL Compact を除く [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の任意のエディション。 (これらのエディションはレプリケーションのパブリッシャーとして使用できません)。   
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] サンプル データベース。 セキュリティ強化のため、既定ではサンプル データベースがインストールされません。  
  
-   サブスクライバー サーバー側 (レプリケーション先) :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の任意のエディション。ただし、 [!INCLUDE[ssEW](../../includes/ssew-md.md)]は除きます。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] は、トランザクション レプリケーションのサブスクライバーとして使用できません。  
  
- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。
- [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads) をインストールする。
- [AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases)をダウンロードする。 SSMS でデータベースを復元する方法の詳細については、「[SSMS を使用してデータベース バックアップを復元する](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)」を参照してください。 
 
>[!NOTE]
> - 3 つ以上離れたバージョンの SQL Server では、レプリケーションはサポートされていません。 詳細については、「[Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/)」(Repl トポロジでサポートされている SQL バージョン) を参照してください。
> - [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、固定サーバー ロール **sysadmin** のメンバーとしてログインし、パブリッシャーとサブスクライバーに接続する必要があります。 sysadmin ロールの詳細については、「[サーバー レベルのロール](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles)」を参照してください。  
  
  
**このチュートリアルの推定所要時間: 60 分。**  
  
## <a name="configure-the-publisher-for-transactional-replication"></a>トランザクション レプリケーションのパブリッシャーを構成する
このセクションでは、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してトランザクション パブリケーションを作成し、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの **Product** テーブルからフィルター選択したサブセットをパブリッシュします。 また、ディストリビューション エージェントにより使用される SQL Server ログインをパブリケーション アクセス リスト (PAL) に追加します。 このチュートリアルを行うには、前のチュートリアル「 [レプリケーションに備えたサーバーの準備](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md)」を完了している必要があります。


### <a name="create-a-publication-and-define-articles"></a>パブリケーションを作成し、アーティクルを定義する
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2. **[SQL Server エージェント]** を右クリックし、**[開始]** を選択します。 パブリケーションを作成する前に、SQL Server エージェントが実行されている必要があります。 この方法でエージェントが起動しない場合は、**SQL Server 構成マネージャー**から手動で起動する必要があります。 
3. **[レプリケーション]** フォルダーを展開し、**[ローカル パブリケーション]** フォルダーを右クリックして、**[新しいパブリケーション]** を選択します。  これによりパブリケーションの新規作成ウィザードが起動します。  

    ![新しいパブリケーション](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
  
3. [パブリケーション データベース] ページで [[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]] を選択し、**[次へ]** を選択します。  
  
4. [パブリケーションの種類] ページで **[トランザクション パブリケーション]** を選択し、**[次へ]** を選択します。  

    ![トランザクション レプリケーション](media/tutorial-replicating-data-between-continuously-connected-servers/tranrepl.png)
  
5. [アーティクル] ページで、**[テーブル]** ノードを展開し、**[Product]** チェック ボックスをオンにします。 次に、**[Product]** を展開し、**[ListPrice]** と **[StandardCost]** の横のチェック ボックスをオフにします。 **[次へ]** を選択します。  

    ![パブリッシュするアーティクル](media/tutorial-replicating-data-between-continuously-connected-servers/replarticles.png)
  
6. [テーブル行のフィルター選択] ページで、**[追加]** を選択します。   
  
7. **[フィルターの追加]** ダイアログ ボックスで **[SafetyStockLevel]** 列を選択し、右矢印を選択して、フィルター選択クエリの Filter ステートメントの WHERE 句にこの列を追加します。 次に、WHERE 句の修飾子に次のように手動で入力します。  
  
    ```sql  
    WHERE [SafetyStockLevel] < 500  
    ```
  
    ![Filter ステートメント](media/tutorial-replicating-data-between-continuously-connected-servers/filter.png)
  
8. **[OK]** を選択し、 **[次へ]** を選択します。  
  
9. **[スナップショットをすぐに作成し、サブスクリプションを初期化できるようにそのスナップショットを保持する]** チェック ボックスをオンにして、**[次へ]** を選択します。  

    ![スナップショット エージェント](media/tutorial-replicating-data-between-continuously-connected-servers/snapshot.png)
  
10. [エージェント セキュリティ] ページで、 **[スナップショット エージェントのセキュリティ設定を使用する]** チェック ボックスをオフにします。   
  
    A. スナップショット エージェントの **[セキュリティ設定]** を選択して、**[プロセス アカウント]** ボックスに「<*パブリッシャー コンピューター名>***\repl_snapshot**」と入力し、このアカウントのパスワードを入力して **[OK]** をクリックします。  

    ![[スナップショット エージェントのセキュリティ]](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagentsecurity.png)
  
12. 同様に、ログ リーダー エージェントのプロセス アカウントとして <*パブリッシャー コンピューター名*>**\repl_logreader** を設定し、**[完了]** を選択します。  

    ![[ログ リーダー エージェントのセキュリティ]](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentsecurity.png)   

  
13. [ウィザードの完了] ページで、 **[パブリケーション名]** ボックスに「**AdvWorksProductTrans**」と入力し、**[完了]** を選択します。  

    ![パブリケーションの名前](media/tutorial-replicating-data-between-continuously-connected-servers/advworksproducttrans.png)
  
14. パブリケーションが作成されたら、**[閉じる]** を選択してウィザードを閉じます。 

    パブリケーションを作成しようとしたときに、SQL Server エージェントが実行されていないと、次のエラーが発生する可能性があります。 これは、パブリケーションは正常に作成されたが、スナップショット エージェントが起動できなかったことを示しています。 これが発生した場合は、SQL Server エージェントを起動してから、手動でスナップショット エージェントを起動する必要があります。 この手順については、次のセクションで説明します。 

    ![スナップショット エージェントが起動できない](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenterror.png)
    
  
### <a name="to-view-the-status-of-snapshot-generation"></a>スナップショット生成の状態を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksProductTrans]** を右クリックして、**[スナップショット エージェントの状態の表示]** を選択します。  

    ![スナップショット エージェントの状態](media/tutorial-replicating-data-between-continuously-connected-servers/viewsnapshot.png)
  
3.  パブリケーションのスナップショット エージェントの現在の状態が表示されるので、 スナップショット ジョブが正常に終了していることを確認してから次のセクションに進みます。
          
    最初にパブリケーションを作成したときに、SQL Server エージェントが実行されていないと、パブリケーションの**スナップショット エージェントの状態**をチェックしたときに、スナップショット エージェントの '実行履歴がない' と表示されます。 その場合は、**[開始]** を選択して、スナップショット エージェントを起動します。 

       ![スナップショット エージェントの起動](media/tutorial-replicating-data-between-continuously-connected-servers/startsnapshotagent.png)
     
       ここでエラーが発生する場合は、「[スナップショット エージェントを使用したエラーのトラブルシューティング](#troubleshoot-erros-with-snapshot-agent)」を参照してください。 

  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>ディストリビューション エージェントのログインを PAL に追加するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksProductTrans]** パブリケーションを右クリックして、**[プロパティ]** を選択します。  **[パブリケーションのプロパティ]** ダイアログ ボックスが表示されます。    
  
    A. **[パブリケーション アクセス リスト]** ページを選択して、**[追加]** を選択します。  
    B. **[パブリケーション アクセスの追加]** ダイアログ ボックスで、<*パブリッシャー コンピューター名>***\repl_distribution** を選択して **[OK]** を選択します。 **[OK]** を選択します。

   
   ![PAL リストへのログインの追加](media/tutorial-replicating-data-between-continuously-connected-servers/tranreplproperties.png)

**参照**:  
[レプリケーションのプログラミング概念](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  

## <a name="create-a-subscription-to-the-transactional-publication"></a>トランザクション パブリケーションへのサブスクリプションの作成
このセクションでは、前の手順で作成したパブリケーションにサブスクライバーを追加します。 このチュートリアルでは、リモート サブスクライバー (NODE2\SQL2016) を使用しますが、サブスクリプションはローカルでパブリッシャーに追加することもできます。 

### <a name="to-create-the-subscription"></a>サブスクリプションを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーを展開し、**[AdvWorksProductTrans]** パブリケーションを右クリックして、**[新しいサブスクリプション]** を選択します。  サブスクリプションの新規作成ウィザードが起動します。 
 
    ![[新しいサブスクリプション]](media/tutorial-replicating-data-between-continuously-connected-servers/newsub.png)     
  
3.  [パブリケーション] ページで **[AdvWorksProductTrans]** を選択し、**[次へ]** を選択します。  

    ![Tran パブリッシャーの選択](media/tutorial-replicating-data-between-continuously-connected-servers/selectpub.png)
  
4.  [ディストリビューション エージェントの場所] ページで、**[ディストリビューターですべてのエージェントを実行する]** を選択し、**[次へ]** を選択します。  プル サブスクリプションとプッシュ サブスクリプションの詳細については、「[パブリケーションのサブスクライブ](https://docs.microsoft.com/en-us/sql/relational-databases/replication/subscribe-to-publications)」を参照してください。

    ![ディストリビューターでエージェントを実行する](media/tutorial-replicating-data-between-continuously-connected-servers/runagentsatdist.png)
  
5.  [サブスクライバー] ページでサブスクライバー インスタンスの名前が表示されない場合は、**[サブスクライバーの追加]** を選択し、ドロップダウン リストから **[SQL Server サブスクライバーの追加]** を選択します。 これにより **[サーバーへの接続]** ダイアログ ボックスが表示されます。 サブスクライバー インスタンス名を入力し、**[接続]** を選択します。  
    
    A. サブスクライバーが追加されたら、そのサブスクライバーのインスタンス名の横にあるチェック ボックスをオンにします。 次に、**[サブスクリプション データベース]** の下で **[新しいデータベース]** を選択します。   

  ![サブスクライバー サーバーの追加](media/tutorial-replicating-data-between-continuously-connected-servers/addsub.png)

7. これにより **[新しいデータベース]** ダイアログ ボックスが表示されます。 **[データベース名]** ボックスに「**ProductReplica**」と入力し、**[OK]**、**[次へ]** の順に選択します。 
  
    ![ProductReplica DB](media/tutorial-replicating-data-between-continuously-connected-servers/productreplica.png)
  
8.  **[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスで、省略記号 (**...**) ボタンを選択します。 **[プロセス アカウント]** ボックスに「<*パブリッシャー コンピューター名>***\repl_distribution**」を入力し、次に、このアカウントのパスワードを入力して、**[OK]**、**[次へ]** の順に選択します。

    ![ディストリビューション アカウントの追加](media/tutorial-replicating-data-between-continuously-connected-servers/adddistaccount.png)
  
9. 以降のページでは既定値をそのまま採用し、**[完了]** を選択してウィザードを終了します。  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>サブスクライバー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でサブスクライバーに接続し、**[セキュリティ]** を展開して **[ログイン]** を右クリックし、**[新しいログイン]** を選択します。     
  
    A. **[全般]** ページの **[ログイン名]** の下で **[検索]** を選択し、<*サブスクライバー コンピューター名>***\repl_distribution** のログインを追加します。
    B. **[ユーザー マッピング]** ページで、**ProductReplica** データベースにログイン **db_owner** を付与します。 

    ![サブスクライバーでのログイン](media/tutorial-replicating-data-between-continuously-connected-servers/loginforsub.png)

2. **[OK]** を選択して、**[新しいログイン]** ダイアログ ボックスを閉じます。 

  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>サブスクリプションの同期状態を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続して、サーバー ノードを展開し、 **[レプリケーション]** フォルダーを展開します。  
  
2.  **[ローカル パブリケーション]** フォルダーで、**AdvWorksProductTrans** パブリケーションを展開し、**ProductReplica** データベースのサブスクリプションを右クリックして、**[同期の状態の表示]** を選択します。 サブスクリプションの現在の同期状態が表示されます。  
    ![同期の状態の表示](media/tutorial-replicating-data-between-continuously-connected-servers/viewsyncstatus.png)
3.  **[AdvWorksProductTrans]** の下にサブスクリプションが表示されない場合は、F5 キーを押して一覧を更新します。  
  
**参照**:  
[スナップショットを使用したサブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  

## <a name="measuring-replication-latency"></a>レプリケーションの待機時間の計測
このセクションでは、トレーサー トークンを使って、変更内容がサブスクライバーにレプリケートされているかどうかを確認し、待機時間を決定します。 待機時間は、パブリッシャー側で行われた変更がサブスクライバーに表示されるのにかかる時間です。
  
1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、**[レプリケーション モニターの起動]** を選択します。

    ![レプリケーション モニターの起動](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)

2. 左ペインでパブリッシャー グループを展開し、パブリッシャー インスタンスを展開して、**[AdvWorksProductTrans]** パブリケーションを選択します。  
  
    A. **[トレーサー トークン]** タブを選択します。  
    B. **[トレーサーの挿入]** を選択します。    
    c. **[パブリッシャーからディストリビューターまで]** 列、 **[ディストリビューターからサブスクライバーまで]** 列、および **[合計待機時間]** 列で、トレーサー トークンの経過時間を表示します。 **[保留中]** と表示された場合は、トークンが特定のポイントに到達していないことを示します。


   ![トレーサー トークン](media/tutorial-replicating-data-between-continuously-connected-servers/tracertoken.png)


**参照**   
[Measure Latency and Validate Connections for Transactional Replication](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

## <a name="error-troubleshooting-methodology"></a>エラーのトラブルシューティングの手法
このセクションでは、基本的なレプリケーション同期エラーのトラブルシューティングを行う方法を説明します。 このセクションは、トラブルシューティングの目的で、レプリケーション コンポーネントを移動する方法を紹介することを目的としていることに注意してください。 ただし、実際に発生するエラーは、ここで説明されているものと異なる可能性があり、それには別の解決策が必要になります。 その場合は、さらにトラブルシューティングを行う必要がありますが、それについてはこのチュートリアルの対象外です。 


### <a name="troubleshoot-errors-with-snapshot-agent"></a>スナップショット エージェントを使用したエラーのトラブルシューティング
**スナップショット エージェント**は、スナップショットを生成し、それを指定したスナップショット フォルダーに書き込むエージェントです。 

1. スナップショット エージェントの状態を表示するには、レプリケーションの下の **[ローカル パブリケーション]** ノードを展開し、パブリケーション **[AdvWorksProductTrans]** を右クリック  > **[スナップショット エージェントの状態の表示]** を選択します。 
2. **[スナップショット エージェントの状態]** でエラーが報告された場合は、**スナップショット エージェント**のジョブ履歴で詳細を確認することができます。 これにアクセスするには、**オブジェクト エクスプローラー**で **[SQL Server エージェント]** を展開し、**[ジョブの利用状況モニター]** を開きます。 

    A. **[カテゴリ]** で並べ替えて、カテゴリ 'REPL Snapshot' で**スナップショット エージェント**を識別します。 

    B. その**スナップショット エージェント**を右クリックして、**[履歴の表示]** を選択します。 

   ![スナップショット エージェントの履歴](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenthistory.png)
    
1. **スナップショット エージェントの履歴**で、関連するログ エントリを選択します。 これは通常、エラーを報告している (エラーは赤い X 印で示されます) エントリの*前*の 1 行または 2 行です。  ログの下にあるテキスト ボックス内のメッセージ テキストを確認します。 

    ![拒否されたスナップショット エージェントのアクセス](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotaccessdenied.png)

        The replication agent had encountered an exception.
        Exception Message: Access to path '\\node1\repldata.....' is denied.


  スナップショット フォルダーに Windows のアクセス許可が正しく構成されていない場合は、**スナップショット エージェント**に 'アクセスが拒否されました' エラーが表示されます。 repldata フォルダーで <*パブリッシャー コンピューター名>***\repl_snapshot** アカウントのアクセス許可を確認する必要があります。 詳細については、「[スナップショット フォルダーの共有を作成し、アクセス許可を与える](tutorial-preparing-the-server-for-replication.md#create-a-share-for-the-snapshot-folder-and-assign-permissions)」を参照してください。

### <a name="troubleshoot-errors-with-log-reader-agent"></a>ログ リーダー エージェントを使用したエラーのトラブルシューティング
**ログ リーダー エージェント**は、パブリッシャー データベースに接続して、'for replication' とマークされているすべてのトランザクションのトランザクション ログをスキャンします。 そして、それらのトランザクションを**ディストリビューション** データベースに追加します。 

1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、**[レプリケーション モニターの起動]** を選択します。  

    ![レプリケーション モニターの起動](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)
  
    レプリケーション モニターが起動します。![レプリケーション モニター](media/tutorial-replicating-data-between-continuously-connected-servers/replmonitor.png) 
   
2. 赤い X 印は、パブリケーションが同期していないことを示しています。 左側で **[マイ パブリッシャー]** を展開してから、関連するパブリッシャー サーバーを展開します。  
  
3.  左側で **[AdvWorksProductTrans]** パブリケーションを選択してから、いずれかのタブで赤い X 印を探して、どこに問題があるかを特定します。 この場合、赤い X 印は **[エージェント] タブ**にあり、いずれかのエージェントでエラーが発生していることを示しています。 

    ![エージェントのエラー](media/tutorial-replicating-data-between-continuously-connected-servers/agenterror.png)

4. **[エージェント] タブ**を選択して、どのエージェントでエラーが発生しているかを特定します。 

    ![エラーが発生しているログ リーダー](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentfailure.png)


5. このビューには、**スナップショット エージェント**と**ログ リーダー エージェント**の 2 つのエージェントが表示されます。 エラーが発生しているエージェントには赤の X 印が付けられます。この場合は、**ログ リーダー エージェント** に赤の X 印が付いており、そこに問題があることが示されています。 エラーを報告している行 (この場合は**ログ リーダー エージェント**) をダブルクリックします。 これにより、選択したエージェントの**エージェント履歴** (この場合は**ログ リーダー エージェント**履歴) が起動されます。 これはエラーに関する詳細情報を提供します。 
    
    ![ログ リーダーのエラー](media/tutorial-replicating-data-between-continuously-connected-servers/logreadererror.png)

       Status: 0, code: 20011, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.
       The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.
       Status: 0, code: 15517, text: 'Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission.'.
       Status: 0, code: 22037, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.        

6. 前述のエラーは通常、パブリッシャー データベースの所有者が正しく設定されていないことが原因で発生します。 これは通常、データベースが復元されている場合に発生します。 これを確認するには、**オブジェクト エクスプローラー**で **[データベース]** を展開し、**[AdventureWorks2012]** を右クリック  > **[プロパティ]** を選択します。 **[ファイル]** ページの下に所有者が存在することを確認します。 このフィールドが空白の場合は、これが問題の原因と考えられます。 

    ![DB のプロパティ](media/tutorial-replicating-data-between-continuously-connected-servers/dbproperties.png)

7. **[ファイル]** ページで所有者が空白の場合は、**AdventureWorks2012** データベースのコンテキスト内で**新しいクエリ ウィンドウ**を開きます。 次の T-SQL コード スニペットを実行します。

    ```sql
    -- set the owner of the database to 'sa' or a specific user account, without the brackets. 
    EXEC sp_changedbowner '<useraccount>'
    -- example for sa: exec sp_changedbowner 'sa'
    -- example for user account: exec sp_changedbowner 'sqlrepro\administrator' 
    ```

8. **ログ リーダー エージェント**を再起動する必要があります。 これを行うには、**オブジェクト エクスプローラー**で **[SQL Server エージェント]** ノードを展開し、**[ジョブの利用状況モニター]** を開きます。 **[カテゴリ]** で並べ替え、**'REPL-LogReader'** カテゴリによって**ログ リーダー エージェント**を識別します。 **ログ リーダー エージェント** ジョブを右クリックし、**[Start Job at Step]\(ステップでジョブを開始\)** を選択します。 

    ![ログ リーダー エージェントの再起動](media/tutorial-replicating-data-between-continuously-connected-servers/startjobatstep.png)

9. **レプリケーション モニター**をもう一度開いて、パブリケーションが現在同期されていることを確認します。 まだ開いていない場合は、**オブジェクト エクスプローラー**で **[レプリケーション]** を右クリックして見つけることができます。 
10. **[AdvWorksProductTrans]** パブリケーション、**[エージェント]** タブの順に選択し、**[ログ リーダー エージェント]** をダブルクリックして、エージェントの履歴を開きます。 これで、**ログ リーダー エージェント**が実行中で、コマンドをレプリケートしているか、"レプリケートされたトランザクションが存在しない" のいずれかが示されるはずです。

    ![実行中のログ リーダー](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderrunning.png)

### <a name="troubleshoot-errors-with-distribution-agent"></a>ディストリビューション エージェントを使用したエラーのトラブルシューティング
**ディストリビューション エージェント**は、**ディストリビューション** データベースで見つかったデータを取り出し、それをサブスクライバーに適用します。 

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、**[レプリケーション モニターの起動]** を選択します。  
2. **[レプリケーション モニター]** で、**[AdvWorksProductTrans]** パブリケーションを選択し、**[すべてのサブスクリプション]** タブを選択します。サブスクリプションを右クリックし、**[詳細表示]** を選択します。

    ![ディストリビューションの詳細表示](media/tutorial-replicating-data-between-continuously-connected-servers/viewdetails.png)

2. **[ディストリビューターからサブスクライバーまで]** 履歴ダイアログ ボックスが開き、エージェントで発生しているエラーの内容を明確にします。 

     ![ディストリビューション エージェントのエラー履歴](media/tutorial-replicating-data-between-continuously-connected-servers/disthistoryerror.png)
    
        Error messages:
        Agent 'NODE1\SQL2016-AdventureWorks2012-AdvWorksProductTrans-NODE2\SQL2016-7' is retrying after an error. 89 retries attempted. See agent job history in the Jobs folder for more details.

3. このエラーは、**ディストリビューション エージェント**が再試行していることを示します。 詳細を確認するには、**オブジェクト エクスプローラー**で **SQL Server エージェント**を展開  > **[ジョブの利用状況モニター]** を選択します。 **[カテゴリ]** でジョブを並べ替えます。 

    A. カテゴリ **'REPL-Distribution'** で**ディストリビューション エージェント**を識別します。 エージェントを右クリックして、**[履歴の表示]** を選択します。

    ![ディストリビューション エージェントの履歴の表示](media/tutorial-replicating-data-between-continuously-connected-servers/viewdistagenthistory.png)

5. いずれかのエラー エントリを選択し、ウィンドウの下部にエラー テキストを表示します。  

    ![ディストリビューション エージェントの不正なパスワード](media/tutorial-replicating-data-between-continuously-connected-servers/distpwwrong.png)
    
        Message:
        Unable to start execution of step 2 (reason: Error authenticating proxy NODE1\repl_distribution, system error: The user name or password is incorrect.)

6. このエラーは、**ディストリビューション エージェント**で使用されているパスワードが正しくないことを示しています。 これを解決するには、**オブジェクト エクスプローラー**で **[レプリケーション]** ノードを展開し、サブスクリプションを右クリックして、**[プロパティ]** を選択します。 **[エージェント プロセス アカウント]** の横にある省略記号 (...) を選択して、パスワードを変更します。

    ![ディストリビューション エージェントのパスワードの変更](media/tutorial-replicating-data-between-continuously-connected-servers/distagentpwchange.png)

7. **オブジェクト エクスプローラー**で **[レプリケーション]** を右クリックして、**レプリケーション モニター**をもう一度チェックします。 **[すべてのサブスクリプション]** の下の赤い X 印は、**ディストリビューション エージェント**で引き続きエラーが発生していることを示しています。 **[レプリケーション モニター]** でサブスクリプションを右クリック  > **[詳細表示]** を選択して、**[ディストリビューターからサブスクライバーまで]** の履歴を開きます。 ここでは、異なるエラーが表示されるようになります。 

    ![ディストリビューション エージェントが接続できない](media/tutorial-replicating-data-between-continuously-connected-servers/distagentcantconnect.png)
           
        Connecting to Subscriber 'NODE2\SQL2016'        
        Agent message code 20084. The process could not connect to Subscriber 'NODE2\SQL2016'.
        Number:  18456
        Message: Login failed for user 'NODE2\repl_distribution'.

8. このエラーは、ユーザー **NODE2\repl_distribution** のログインが失敗したため、**ディストリビューション エージェント**がサブスクライバーに接続できなかったことを示しています。 さらに詳しく調べるには、サブスクライバーに接続して、**オブジェクト エクスプローラー**で **[管理]** ノードの下の*現在の* **SQL エラー ログ**を開きます。 

    ![サブスクライバーのログイン失敗](media/tutorial-replicating-data-between-continuously-connected-servers/loginfailed.png) このエラーが表示される場合は、サブスクライバーにログインが見つからないことを意味します。 これを解決するには、「[サブスクライバー側のデータベース アクセス許可を設定するには](#setting-database-permissions-at-the-subscriber)」を参照してください。

9. ログイン エラーを解決したら、もう一度**レプリケーション モニター**を確認してください。 すべての問題が解決されると、**[パブリケーション名]** の横に緑色の矢印が表示され、**[すべてのサブスクリプション]** の下の [状態] が **[実行中]** になります。 **[サブスクリプション]** を右クリックして **[ディストリビューターからサブスクライバーまで]** 履歴をもう一度起動して、成功を確認します。 初めてディストリビューション エージェントを実行する場合は、次の図に示すように、スナップショットがサブスクライバーに一括コピーされます。 

     ![ディストリビューション エージェントの成功](media/tutorial-replicating-data-between-continuously-connected-servers/distagentsuccess.png)   

  ## <a name="next-steps"></a>次の手順
トランザクション レプリケーション用にパブリッシャーとサブスクライバーの両方を正しく構成しました。  これで、パブリッシャーで **Product** テーブルに対してデータを挿入、更新、または削除することができます。 その後、サブスクライバーで **Product** テーブルに対してクエリを実行して、レプリケートされた変更を表示することができます。 次の記事では、マージ レプリケーションを構成する方法について説明します。  

詳細については、次の記事に進んでください
> [!div class="nextstepaction"]
> [次の手順](tutorial-replicating-data-with-mobile-clients.md)

  
