---
title: "プル サブスクリプションの削除 | Microsoft Docs"
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
  - "removing subscriptions"
  - "deleting subscriptions"
  - "pull subscriptions [SQL Server replication], deleting"
  - "サブスクリプション [SQL Server レプリケーション]、プル"
ms.assetid: 997c0b8e-d8d9-4eed-85b1-6baa1f8594ce
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# プル サブスクリプションの削除
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プル サブスクリプションを削除する方法について説明します。  
  
 **このトピックの内容**  
  
-   **プル サブスクリプションを削除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリッシャーでプル サブスクリプションを削除 (から、 **ローカル パブリケーション** フォルダーに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) またはサブスクライバー (から、 **ローカル サブスクリプション** フォルダー)。 サブスクリプションを削除しても、サブスクリプションのオブジェクトやデータは削除されません。これらは手動で削除する必要があります。  
  
#### パブリッシャーでプル サブスクリプションを削除するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  削除するサブスクリプションに関連付けられているパブリケーションを展開します。  
  
4.  サブスクリプションの場合を右クリックし、をクリックし、 **削除**します。  
  
5.  確認のダイアログ ボックスで、サブスクライバーに接続してサブスクリプション情報を削除するかどうかを選択します。 **[サブスクライバーへの接続]** チェック ボックスをオフにする場合は、後でサブスクライバーに接続してこの情報を削除する必要があります。  
  
#### サブスクライバーでプル サブスクリプションを削除するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  クリックして、削除するサブスクリプションを右クリックして **削除**です。  
  
4.  確認のダイアログ ボックスで、パブリッシャーに接続してサブスクリプション情報を削除するかどうかを選択します。 **[パブリッシャーへの接続]** チェック ボックスをオフにした場合は、後でパブリッシャーに接続してこの情報を削除する必要があります。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 プル サブスクリプションは、レプリケーション ストアド プロシージャを使用してプログラムで削除できます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって変わります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを削除するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_droppullsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)です。 指定 **@publication**, 、**@publisher**, 、および **@publisher_db**します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_dropsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)です。 **@publication** と **@subscriber**を指定します。 **@article** に **all**を指定します。 (省略可能)ディストリビューターにアクセスできない場合の値を指定 **1** の **@ignore_distributor** 、ディストリビューターの関連オブジェクトを削除せずに、サブスクリプションを削除します。  
  
#### マージ パブリケーションに対するプル サブスクリプションを削除するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_dropmergepullsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)です。 指定 **@publication**, 、**@publisher**, 、および **@publisher_db**します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_dropmergesubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)です。 指定 **@publication**, 、**@subscriber**, 、および **@subscriber_db**します。 値を指定して **プル** の **@subscription_type**します。 (省略可能)ディストリビューターにアクセスできない場合の値を指定 **1** の **@ignore_distributor** 、ディストリビューターの関連オブジェクトを削除せずに、サブスクリプションを削除します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、トランザクション パブリケーションへのプル サブスクリプションを削除します。 最初のバッチはサブスクライバーで実行され、次のバッチはパブリッシャーで実行されます。  
  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_1.sql)]  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_2.sql)]  
  
 次の例では、マージ パブリケーションに対するプル サブスクリプションを削除します。 最初のバッチはサブスクライバーで実行され、次のバッチはパブリッシャーで実行されます。  
  
 [!code-sql[HowTo#sp_dropmergepullsubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_3.sql)]  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-pull-subscription_4.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってプル サブスクリプションを削除できます。 プル サブスクリプションの削除に使用する RMO クラスは、プル サブスクリプションをサブスクライブするパブリケーションの種類によって決まります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションを削除するには  
  
1.  使用して、サブスクライバーとパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラス、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> プロパティです。 手順 1. のサブスクライバー接続設定を使用して、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
3.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをサブスクリプションがあることを確認します。 このプロパティの値が **false**の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> メソッドです。  
  
5.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> 手順 1. のパブリッシャーの接続を使用してクラスです。 指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> と <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、手順 5. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。  
  
7.  呼び出す、 <xref:Microsoft.SqlServer.Replication.TransPublication.RemovePullSubscription%2A> メソッドです。 *subscriber* パラメーターと *subscriberDB* パラメーターに、サブスクライバーの名前とサブスクリプション データベースを指定します。  
  
#### マージ パブリケーションに対するプル サブスクリプションを削除するには  
  
1.  使用して、サブスクライバーとパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラス、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> プロパティです。 手順 1. の接続設定を使用して、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
3.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをサブスクリプションがあることを確認します。 このプロパティの値が **false**の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PullSubscription.Remove%2A> メソッドです。  
  
5.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 1. のパブリッシャーの接続を使用してクラスです。 指定 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> と <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>します。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、手順 5. で指定したプロパティが誤っているか、サーバーにパブリケーションが存在していません。  
  
7.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePublication.RemovePullSubscription%2A> メソッドです。 *subscriber* パラメーターと *subscriberDB* パラメーターに、サブスクライバーの名前とサブスクリプション データベースを指定します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションに対するプル サブスクリプションを削除し、パブリッシャー側のサブスクリプション登録を削除します。  
  
 [!code-csharp[HowTo#rmo_DropTranPullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpullsub)]  
  
 次の例では、マージ パブリケーションに対するプル サブスクリプションを削除し、パブリッシャー側のサブスクリプション登録を削除します。  
  
 [!code-csharp[HowTo#rmo_DropMergePullSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepullsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePullSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepullsub)]  
  
## 参照  
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  