---
title: 'チュートリアル: レプリケーション用の SQL Server の準備 - パブリッシャー、ディストリビューター、サブスクライバー | Microsoft Docs'
ms.custom: ''
ms.date: 04/02/2018
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
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1468095ba959f7baf383b68cfaab65dab2591af6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriber"></a>チュートリアル: レプリケーション用の SQL Server の準備 - パブリッシャー、ディストリビューター、サブスクライバー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
レプリケーション トポロジを構成するには、事前にセキュリティ計画を立てることが重要です。 このチュートリアルでは、レプリケーション トポロジのセキュリティを向上する方法と、データのレプリケートで最初のステップとなるディストリビューションの構成方法を学習します。 他のチュートリアルを行う前に、まずこのチュートリアルを実行してください。  
  
> [!NOTE]  
> サーバー間でデータを安全にレプリケートするには、「 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)」の推奨事項をすべて実践してください。  
  
## <a name="what-you-will-learn"></a>学習する内容  
このチュートリアルでは、サーバーを準備し、レプリケーションを最小の特権で安全に実行できるようにする方法を説明します。  

このチュートリアルでは、次の内容を学習します。
> [!div class="checklist"]
> * レプリケーション用の Windows アカウントの作成
> * スナップショット フォルダーの準備
> * ディストリビューションの構成

## <a name="prerequisites"></a>Prerequisites
このチュートリアルは、データベースの基本的な操作は理解しているが、レプリケーション機能についてはあまり詳しくないユーザーを対象としています。 

このチュートリアルを完了するには、システムに SQL Server Management Studio (SSMS) およびこれらのコンポーネントが必要です。  
  
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


**このチュートリアルの推定所要時間: 30 分**
  
## <a name="create-windows-accounts-for-replication"></a>レプリケーション用の Windows アカウントの作成
このセクションでは、レプリケーション エージェントを実行するための Windows アカウントを作成します。 また、次のエージェントを実行するための別の Windows アカウントをローカル サーバー上に作成します。  
  
|エージェント|場所|アカウント名|  
|---------|------------|----------------|  
|スナップショット エージェント|パブリッシャー|<*machine_name*>\repl_snapshot|  
|ログ リーダー エージェント (Log Reader Agent)|パブリッシャー|<*machine_name*>\repl_logreader|  
|ディストリビューション エージェント|パブリッシャーおよびサブスクライバー|<*machine_name*>\repl_distribution|  
|マージ エージェント|パブリッシャーおよびサブスクライバー|<*machine_name*>\repl_merge|  
  
> [!NOTE]  
> レプリケーション チュートリアルでは、パブリッシャーとディストリビューターが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の同じインスタンス (NODE1\SQL2016) を共有し、サブスクライバー インスタンス (NODE2\SQL2016) はリモートです。 パブリッシャーとサブスクライバーが同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを共有することもできますが、これは必須条件ではありません。 パブリッシャーとサブスクライバーが同じインスタンスを共有している場合、サブスクライバー側でアカウントの作成に使用される手順は必要ありません。  

### <a name="create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>パブリッシャー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成する
  
1.  パブリッシャー側で、[コントロール パネル] の **[管理ツール]** から **[コンピューターの管理]** を開きます。  
  
2.  **[システム ツール]** の **[ローカル ユーザーとグループ]** を展開します。  
  
3.  **[ユーザー]** を右クリックし、 **[新しいユーザー]** を選択します。  
     
4.  **[ユーザー名]** ボックスに「**repl_snapshot**」と入力し、パスワードおよびその他の必要な情報を入力し、**[作成]** を選択して repl_snapshot アカウントを作成します。 

       ![新しいユーザー](media/tutorial-preparing-the-server-for-replication/newuser.png)
  
5.  同様に、repl_logreader、repl_distribution、repl_merge の各アカウントを作成します。  
 
    ![ユーザーのレプリケーション](media/tutorial-preparing-the-server-for-replication/replusers.png)
  
6.  **[閉じる]** を選択します。  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>サブスクライバー側でレプリケーション エージェントを実行するためのローカル Windows アカウントを作成するには  
  
1.  サブスクライバー側で、[コントロール パネル] の **[管理ツール]** から **[コンピューターの管理]** を開きます。  
  
2.  **[システム ツール]** の **[ローカル ユーザーとグループ]** を展開します。  
  
3.  **[ユーザー]** を右クリックし、 **[新しいユーザー]** を選択します。  
  
4.  **[ユーザー名]** ボックスに「 **repl_distribution** 」と入力し、パスワードおよびその他の必要な情報を入力し、 **[作成]** を選択して repl_distribution アカウントを作成します。  
  
5.  同様にして、repl_merge アカウントも作成します。  
  
6.  **[閉じる]** を選択します。  

**参照**: [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)  

## <a name="prepare-the-snapshot-folder"></a>スナップショット フォルダーの準備
このセクションでは、パブリケーション スナップショットの作成と保存に使用されるスナップショット フォルダーを設定する方法を学習します。 

### <a name="create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>スナップショット フォルダーの共有を作成し、アクセス許可を与える  
  
1.  Windows エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ フォルダーに移動します。 既定の場所は、C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data です。  
  
2.  **repldata**という名前の新しいフォルダーを作成します。  
  
3.  フォルダーを右クリックし、**[プロパティ]** を選択します。  
  
    A. **[repldata のプロパティ]** ダイアログ ボックスの **[共有]** タブで、**[詳細な共有]** を選択します。  
  
    B. **[詳細な共有]** ダイアログ ボックスで、**[このフォルダーを共有する]** を選択し、**[アクセス許可]** を選択します。  

       ![Repl データの共有](media/tutorial-preparing-the-server-for-replication/repldata.png)

6.  **[repldata のアクセス許可]** ダイアログ ボックスで **[追加]** を選択します。 **[選択するオブジェクト名を入力してください]** ボックスに、前に作成したスナップショット エージェント アカウントの名前を <*Publisher_Machine_Name>***\repl_snapshot** として入力します。 **[名前の確認]** を選択し、**[OK]** を選択します。  

    ![共有アクセス許可の追加](media/tutorial-preparing-the-server-for-replication/addshareperms.png)

7. 手順 6 を繰り返して以前に作成したその他の 2 つのアカウント <*Publisher_Machine_Name > * * * \repl_merge** と <*Publisher_Machine_Name > * * * \repl_distribution** を追加します。

8. これら 3 つのアカウントが追加されたら、次のアクセス許可を割り当てます。      
    - repl_distribution - 読み取り  
    - repl_merge - 読み取り  
    - repl_snapshot - フル コントロール    

  ![共有されるアクセス許可](media/tutorial-preparing-the-server-for-replication/sharedpermissions.png)

9. 共有のアクセス許可が正しく構成されたら、**[OK]** を選択して、**[repldata のアクセス許可]** ダイアログ ボックスを閉じます。 **[OK]** を選択して **[詳細な共有]** ダイアログ ボックスを閉じます。 

10.  **[repldata のプロパティ]** で、**[セキュリティ]** タブを選択し、**[編集]** を選択します。  

       ![セキュリティの編集](media/tutorial-preparing-the-server-for-replication/editsecurity.png)   

11. **[repldata のアクセス許可]** ダイアログ ボックスで **[追加]** を選択します。**[選択するオブジェクト名を入力してください]** ボックスに、前に作成したスナップショット エージェント アカウントの名前を <*Publisher_Machine_Name>***\repl_snapshot** として入力します。 **[名前の確認]** を選択し、**[OK]** を選択します。  

    ![APS セキュリティのアクセス許可](media/tutorial-preparing-the-server-for-replication/addsecuritypermissions.png)

  
12.  前の手順を繰り返して、ディストリビューション エージェント (<*Publisher_Machine_Name>***\repl_distribution**) とマージ エージェント (<* Publisher_Machine_Name>***\repl_merge**) のアクセス許可を追加します。  
    
  
13. 次のアクセス許可が与えられていることを確認します。  
  
    - repl_distribution - 読み取り
    - repl_merge - 読み取り
    - repl_snapshot - フル コントロール   
 
    ![Repl データ ユーザーのアクセス許可](media/tutorial-preparing-the-server-for-replication/replpermissions.png) 

14. **[共有]** タブを再度選択し、共有の**ネットワーク パス**をメモします。 後で**スナップショット フォルダー**を構成するときにこのパスが必要になります。  

    ![ネットワーク パス](media/tutorial-replicating-data-between-continuously-connected-servers/networkpath.png)

15. **[OK]** を選択して **[repldata のプロパティ]** ダイアログ ボックスを閉じます。 
 
**参照**:  
[スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  

## <a name="configure-distribution"></a>ディストリビューションの構成
このセクションでは、パブリッシャー側のディストリビューションを構成し、パブリケーション データベースとディストリビューション データベースに対して必要なアクセス許可を設定します。 ディストリビューターを構成済みの場合は、このセクションを開始する前に、パブリッシングとディストリビューションを無効にする必要があります。 特に実稼働環境で既存のレプリケーション トポロジを維持する必要がある場合は、このレッスンを実行しないでください。   
  
パブリッシャー側のリモート ディストリビューターの構成は、このチュートリアルの対象外です。  

### <a name="configure-distribution-at-the-publisher"></a>パブリッシャー側でディストリビューションを構成する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを右クリックし、 **[ディストリビューションの構成]** を選択します。  

    ![ディストリビューションの構成](media/tutorial-preparing-the-server-for-replication/configuredistribution.png)
  
    > [!NOTE]  
    > 実際のサーバー名ではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] localhost **を使用して** に接続すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が **'localhost'** サーバーに接続できないことを示す警告とメッセージが表示されます。 警告ダイアログで **[OK]** を選択します。 **[サーバーへの接続]** ダイアログで、 **[サーバー名]** を **localhost** から使用しているサーバーの名前に変更します。 **[接続]** を選択します。  
  
    ディストリビューション構成ウィザードが起動します。  
  
3.  **[ディストリビューター]** ページで、**['&lt;サーバー名&gt;' を独自のディストリビューターとする (SQL Server はディストリビューション データベースとログを作成します)]** を選択し、**[次へ]** を選択します。  

    ![それ自体がディストリビューターとして機能するサーバー](media/tutorial-preparing-the-server-for-replication/serverdistributor.png)
  
4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されていない場合は、[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**エージェントの起動**] ページで **[はい]** を選択し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスが自動的に起動するように構成します。 **[次へ]** を選択します。  

     
5.  **[スナップショット フォルダー]** テキスト ボックスにパス \\\\<*Publisher_Machine_Name>***\repldata** を入力し、**[次へ]** を選択します。 このパスは、共有のプロパティを構成した後に repldata のプロパティ フォルダーの **[ネットワーク パス]** に以前表示されていたパスと一致する必要があります。 

    ![Repl データ スナップショット フォルダー](media/tutorial-preparing-the-server-for-replication/repldatasnapshot.png)
  
6.  ウィザードの残りのページでは、既定値をそのまま使用します。  
    
    ![ディストリビューション ウィザードの既定値](media/tutorial-preparing-the-server-for-replication/distributionwizarddefaults.png)
  
7.  **[完了]** をクリックしてディストリビューションを有効にします。 

    ディストリビューターを構成するときにこのエラーが表示される可能性があります。 これは、SQL Server エージェント アカウントの開始に使用されるアカウントが、システムの管理者ではないことを示します。 SQL Server エージェントを手動で開始して、既存のアカウントにこれらのアクセス許可を付与するか、SQL Server エージェントが使用するアカウントを変更する必要があります。 

     ![エージェント開始エラー](media/tutorial-preparing-the-server-for-replication/startingagenterror.png)

    SQL Server Management Studio が管理者権限で実行されている場合は、SSMS 内から手動で SQL エージェントを起動できます。  
        ![SSMS からのエージェントの起動](media/tutorial-preparing-the-server-for-replication/ssmsstartagent.png) 

    >[!NOTE]
    > SQL エージェントが自動的に起動しない場合は、SSMS で SQL Server エージェントを右クリックし、**更新**します。  それでも停止状態である場合、**SQL Server 構成マネージャー**から手動で起動する必要があります。    
  
### <a name="setting-database-permissions-at-the-publisher"></a>パブリッシャー側のデータベース権限を設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、**[セキュリティ]** を展開して **[ログイン]** を右クリックし、**[新しいログイン]** をクリックします。  

    ![[新しいログイン]](media/tutorial-preparing-the-server-for-replication/newlogin.png)
  
2.  **[全般]** ページで、**[検索]** を選択し、**[選択するオブジェクト名を入力します]** ボックスに「<*Publisher_Machine_Name > ***\repl_snapshot**」と入力し、**[名前の確認]** を選択して、**[OK]** を選択します。  

    ![Repl スナップショット ログインの追加](media/tutorial-preparing-the-server-for-replication/addsnapshotlogin.png)
  
3.  **[このログインにマップされたユーザー]** の一覧にある **[ユーザー マッピング]** ページで、 **ディストリビューション** データベースと [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの両方を選択します。  
  
    [データベース ロールのメンバーシップ] の一覧で、両方のデータベースのログイン用に **db_owner** ロールを選択します。  

    ![Repl スナップショット DB 所有者](media/tutorial-preparing-the-server-for-replication/dbowner.png)
  
4.  **[OK]** を選択して、ログインを作成します。  
  
5.  その他のローカル アカウント (repl_distribution、repl_logreader、および repl_merge) のログインを作成するために手順 1 ～ 4 を繰り返します。 これらのログインも、**ディストリビューション** データベースと **AdventureWorks** データベースの固定データベース ロール **db_owner** のメンバーとなっているユーザーにマップする必要があります。  

    ![SSMS の Repl ユーザー](media/tutorial-preparing-the-server-for-replication/usersinssms.png)
  
  
**参照**:  
[[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)  
[レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)  

## <a name="next-steps"></a>次の手順
サーバーをレプリケーション用に正常に準備しました。 次の記事では、トランザクション レプリケーションを構成する方法を説明します。 

詳細については、次の記事に進んでください
> [!div class="nextstepaction"]
> [次の手順](tutorial-replicating-data-between-continuously-connected-servers.md)

  
  
