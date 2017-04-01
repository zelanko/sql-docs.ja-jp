---
title: "プッシュ サブスクリプションの削除 | Microsoft Docs"
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
  - "削除、サブスクリプション"
  - "プッシュ サブスクリプション [SQL Server レプリケーション]、削除"
  - "サブスクリプションの削除"
  - "サブスクリプション [SQL Server レプリケーション]、プッシュ"
ms.assetid: 3c4847e2-aed9-4488-b45d-8164422bdb10
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# プッシュ サブスクリプションの削除
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プッシュ サブスクリプションを削除する方法について説明します。  
  
 **このトピックの内容**  
  
-   **プッシュ サブスクリプションを削除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリッシャー側でプッシュ サブスクリプションを削除 (から、 **ローカル パブリケーション** フォルダーに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]) またはサブスクライバー (から、 **ローカル サブスクリプション** フォルダー)。 サブスクリプションを削除しても、サブスクリプションのオブジェクトやデータは削除されません。これらは手動で削除する必要があります。  
  
#### パブリッシャーでプッシュ サブスクリプションを削除するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  削除するサブスクリプションに関連付けられているパブリケーションを展開します。  
  
4.  サブスクリプションの場合を右クリックし、をクリックし、 **削除**です。  
  
5.  確認のダイアログ ボックスで、サブスクライバーに接続してサブスクリプション情報を削除するかどうかを選択します。 **[サブスクライバーへの接続]** チェック ボックスをオフにした場合は、後でサブスクライバーに接続してこの情報を削除する必要があります。  
  
#### サブスクライバーでプッシュ サブスクリプションを削除するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  クリックして、削除するサブスクリプションを右クリックして **削除**します。  
  
4.  確認のダイアログ ボックスで、パブリッシャーに接続してサブスクリプション情報を削除するかどうかを選択します。 **[パブリッシャーへの接続]** チェック ボックスをオフにした場合は、後でパブリッシャーに接続してこの情報を削除する必要があります。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 プッシュ サブスクリプションは、レプリケーション ストアド プロシージャを使用してプログラムで削除できます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを削除するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_dropsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)します。 **@publication** と **@subscriber**を指定します。 **@article** に **all**を指定します。 (省略可能)ディストリビューターにアクセスできない場合の値を指定 **1** の **@ignore_distributor** 、ディストリビューターの関連オブジェクトを削除せずに、サブスクリプションを削除します。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_subscription_cleanup & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) サブスクリプション データベースのレプリケーション メタデータを削除します。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを削除するには  
  
1.  パブリッシャーで実行 [sp_dropmergesubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md), を指定して **@publication**, 、**@subscriber** と **@subscriber_db**します。 (省略可能)ディストリビューターにアクセスできない場合の値を指定 **1** の **@ignore_distributor** 、ディストリビューターの関連オブジェクトを削除せずに、サブスクリプションを削除します。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_mergesubscription_cleanup & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、および **@publication**します。 これにより、サブスクリプション データベースのマージ メタデータが削除されます。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、トランザクション パブリケーションへのプッシュ サブスクリプションを削除します。  
  
 [!code-sql[HowTo#sp_droptransubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_1.sql)]  
  
 この例では、マージ パブリケーションへのプッシュ サブスクリプションを削除します。  
  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/delete-a-push-subscription_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 プッシュ サブスクリプションの削除に使用する RMO クラスは、プッシュ サブスクリプションをサブスクライブするパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションを削除するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> プロパティです。  
  
4.  設定、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをサブスクリプションがあることを確認します。 このプロパティの値が **false**の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> メソッドです。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションを削除するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A> プロパティです。  
  
4.  設定、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをサブスクリプションがあることを確認します。 このプロパティの値が **false**の場合、手順 2. でサブスクリプション プロパティが不適切に定義されたか、サブスクリプションが存在していません。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Subscription.Remove%2A> メソッドです。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってプッシュ サブスクリプションを削除できます。  
  
 [!code-csharp[HowTo#rmo_DropTranPushSub](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpushsub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPushSub](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpushsub)]  
  
## 参照  
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  