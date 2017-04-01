---
title: "パブリッシングおよびディストリビューションの無効化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パブリッシングの無効化"
  - "パブリッシング [SQL Server replication]、無効化"
  - "ディストリビューションの無効化 [SQL Server レプリケーション]"
  - "レプリケーションの削除"
  - "レプリケーション [SQL Server]、削除"
  - "レプリケーションの無効化"
  - "ディストリビューションの無効化"
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# パブリッシングおよびディストリビューションの無効化
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリッシングとディストリビューションを無効にする方法について説明します。  
  
 次の操作を実行できます。  
  
-   ディストリビューターですべてのディストリビューション データベースを削除します。  
  
-   ディストリビューターを使用するすべてのパブリッシャーを無効にし、それらのパブリッシャーのすべてのパブリケーションを削除します。  
  
-   パブリケーションへのすべてのサブスクリプションを削除します。 パブリケーション データベースおよびサブスクリプション データベースのデータは削除されませんが、パブリケーション データベースとの同期リレーションシップは失われます。 サブスクライバーにあるデータを削除するには、手動で削除する必要があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
-   **パブリッシングおよびディストリビューションを無効にするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   パブリッシングおよびディストリビューションを無効にするには、すべてのディストリビューション データベースおよびパブリケーション データベースをオンラインにする必要があります。 ディストリビューション データベースまたはパブリケーション データベースに対して、 *データベース スナップショット* が存在する場合、これらを削除してからパブリッシングおよびディストリビューションを無効にする必要があります。 データベース スナップショットは、データベースの読み取り専用のオフライン コピーで、レプリケーション スナップショットとは関連がありません。 詳細については、次を参照してください。 [データベース スナップショットと #40 です。SQL Server と #41;](../../relational-databases/databases/database-snapshots-sql-server.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリッシングとディストリビューションの無効化ウィザードを使用して、パブリッシングおよびディストリビューションを無効化します。  
  
#### パブリッシングおよびディストリビューションを無効化するには  
  
1.   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で無効化するパブリッシャーまたはディストリビューターに接続して、サーバー ノードを展開します。  
  
2.  右クリックし、 **レプリケーション** フォルダー、およびクリック **を無効にするパブリッシングおよびディストリビューションを**します。  
  
3.  パブリッシングとディストリビューションの無効ウィザードの手順に従って操作します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリッシングおよびディストリビューションは、レプリケーションのストアド プロシージャを使用してプログラムから無効にできます。  
  
#### パブリッシングおよびディストリビューションを無効化するには  
  
1.  レプリケーション関連のすべてのジョブを停止します。 ジョブ名の一覧については、「 [レプリケーション エージェントのセキュリティ モデル](../../relational-databases/replication/security/replication-agent-security-model.md)」の「SQL Server エージェントのエージェント セキュリティ」セクションを参照してください。  
  
2.  各サブスクライバーでサブスクリプション データベースで実行 [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) データベースからレプリケーション オブジェクトを削除します。 このストアド プロシージャでは、ディストリビューターのレプリケーション ジョブは削除されません。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) データベースからレプリケーション オブジェクトを削除します。  
  
4.  パブリッシャーでは、リモート ディストリビューターを使用している場合は、実行 [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)します。  
  
5.  ディストリビューターで実行 [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)します。 このストアド プロシージャは、ディストリビューターに登録されている各パブリッシャーについて一度ずつ実行する必要があります。  
  
6.  ディストリビューターで実行 [sp_dropdistributiondb](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md) をディストリビューション データベースを削除します。 このストアド プロシージャは、ディストリビューターの各ディストリビューション データベースについて実行する必要があります。 これにより、ディストリビューション データベースに関連付けられているキュー リーダー エージェント ジョブがすべて削除されます。  
  
7.  ディストリビューターで実行 [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) 、サーバーからディストリビューターの指定を削除します。  
  
    > [!NOTE]  
    >  実行する前に、すべてのレプリケーション パブリッシングおよびディストリビューション オブジェクトが削除されなかった場合 [sp_dropdistpublisher](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md) と [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md), 、これらの手順はエラーを返します。 パブリッシャーまたはディストリビューターが削除されるときに、レプリケーションに関連するオブジェクトを削除する、 **@no_checks** パラメーターを設定する必要があります **1**します。 パブリッシャーまたはディストリビューターがオフラインか、到達できない場合、 **@ignore_distributor** パラメーターに設定できる **1** できるように、これらを削除することができます。 ただし、すべて発行し、残されたオブジェクトを配布する必要があります手動で削除します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例は、サブスクリプション データベースからレプリケーション オブジェクトを削除するスクリプトです。  
  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_1.sql)]  
  
 次の例は、パブリッシャーおよびディストリビューターとして機能しているサーバー上のパブリッシングおよびディストリビューションを無効にし、ディストリビューション データベースを削除するスクリプトです。  
  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/disable-publishing-and-d_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
#### パブリッシングおよびディストリビューションを無効化するには  
  
1.  ディストリビューターを利用するパブリケーションへのサブスクリプションをすべて削除します。 詳細については、「 [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md) 」および「 [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md)」を参照してください。  
  
2.  パブリッシャーとディストリビューターが同じサーバーにある場合、ディストリビューターを利用するパブリケーションをすべて削除し、すべてのデータベースに対するパブリッシングを無効にします。 詳しくは、「 [Delete a Publication](../../relational-databases/replication/publish/delete-a-publication.md)」をご覧ください。  
  
3.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
4.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> クラスです。 指定、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> プロパティ、およびパス、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 3 からのオブジェクト。  
  
5.  (省略可能)呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得し、パブリッシャーがあることを確認します。 このメソッドが **false**を返した場合、手順 4. で設定したパブリッシャーの名前が誤っていたか、このディストリビューターではこのパブリッシャーが使用されていません。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> メソッドです。 パブリッシャーとディストリビューターが別々のサーバーにあり、パブリッシャーにパブリケーションが存在しないことを最初に確認せずにディストリビューターでパブリッシャーをアンインストールする必要がある場合は、 **force** に *true* を渡します。  
  
7.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 渡す、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 3 からのオブジェクト。  
  
8.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> メソッドです。 **force** に *true* を渡すと、すべてのローカル パブリケーション データベースが無効になっているか、ディストリビューション データベースがアンインストールされているかどうかを最初に確認せずに、ディストリビューターのレプリケーション オブジェクトをすべて削除します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、ディストリビューターのパブリッシャーの登録を削除し、ディストリビューション データベースを削除して、ディストリビューターをアンインストールします。  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 次の例では、最初にローカル パブリケーション データベースを無効にしたりディストリビューション データベースを削除せずに、ディストリビューターをアンインストールします。  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## 参照  
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  