---
title: "パブリケーションの削除 | Microsoft Docs"
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
  - "パブリケーションの除去"
  - "パブリケーション [SQL Server レプリケーション]、削除"
  - "アーティクル [SQL Server レプリケーション]、削除"
  - "パブリケーションの削除"
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# パブリケーションの削除
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリケーションを削除する方法について説明します。  
  
 **このトピックの内容**  
  
-   **パブリケーションを削除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **内の** [ローカル パブリケーション] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]フォルダーからパブリケーションを削除します。  
  
#### パブリケーションを削除するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  クリックして、削除するパブリケーションを右クリックして **削除**します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリケーションは、レプリケーションのストアド プロシージャを使用してプログラムから削除できます。 どのストアド プロシージャを使用するかは、削除するパブリケーションの種類によって異なります。  
  
> [!NOTE]  
>  パブリケーションを削除しても、パブリッシュされたオブジェクトはパブリケーション データベースから削除されず、対応するオブジェクトはサブスクリプション データベースから削除されません。 これらのオブジェクトは、必要に応じて `DROP <object>` コマンドを使用し、手動で削除します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションを削除するには  
  
1.  次のいずれかの操作を行います。  
  
    -   単一のパブリケーションを削除するには実行 [sp_droppublication](../../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。  
  
    -   すべてのパブリケーションを削除し、パブリッシュされたデータベースからすべてのレプリケーション オブジェクトを削除、実行 [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) パブリッシャーです。 **@type** には **tran**を指定します。 (省略可能)ディストリビューターにアクセスできない場合、またはデータベースの状態が要注意またはオフラインの場合は、指定の値 **1** の **@force**します。 (省略可能)データベースの名前を指定 **@dbname** 場合 [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) パブリケーション データベースに対しては実行されません。  
  
        > [!NOTE]  
        >  値を指定する **1** の **@force** データベースでパブリッシング オブジェクトのレプリケーション関連のままに可能性があります。  
  
2.  (省略可能)このデータベースに他のパブリケーションが存在しない場合、実行 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) スナップショット パブリケーションまたはトランザクション レプリケーションを使用して、現在のデータベースの公開を無効にします。  
  
3.  (省略可能)サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_subscription_cleanup](../../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) サブスクリプション データベースに残っているレプリケーション メタデータを削除します。  
  
#### マージ パブリケーションを削除するには  
  
1.  次のいずれかの操作を行います。  
  
    -   単一のパブリケーションを削除するには実行 [sp_dropmergepublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。  
  
    -   すべてのパブリケーションを削除し、パブリッシュされたデータベースからすべてのレプリケーション オブジェクトを削除、実行 [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) パブリッシャーです。 **@type** には **merge**を指定します。 (省略可能)ディストリビューターにアクセスできない場合、またはデータベースの状態が要注意またはオフラインの場合は、指定の値 **1** の **@force**します。 (省略可能)データベースの名前を指定 **@dbname** 場合 [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) パブリケーション データベースに対しては実行されません。  
  
        > [!NOTE]  
        >  値を指定する **1** の **@force** データベースでパブリッシング オブジェクトのレプリケーション関連のままに可能性があります。  
  
2.  (省略可能)このデータベースに他のパブリケーションが存在しない場合、実行 [sp_replicationdboption & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) マージ レプリケーションを使用して、現在のデータベースの公開を無効にします。  
  
3.  (省略可能)サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_mergesubscription_cleanup & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md) サブスクリプション データベースで、残っているレプリケーション メタデータを削除します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例は、トランザクション パブリケーションを削除し、データベースのトランザクション パブリッシングを無効にする方法を示しています。 すべてのサブスクリプションがあらかじめ削除されていることを想定しています。 詳細については、「 [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) 」または「 [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md)」を参照してください。  
  
 [!code-sql[HowTo#sp_droppublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_1.sql)]  
  
 次の例は、マージ パブリケーションを削除し、データベースのマージ パブリッシングを無効にする方法を示しています。 すべてのサブスクリプションがあらかじめ削除されていることを想定しています。 詳細については、「 [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) 」または「 [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md)」を参照してください。  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってパブリケーションを削除できます。 パブリケーションの削除に使用する RMO クラスは、削除するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションを削除するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
4.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをパブリケーションが存在することを確認します。 このプロパティの値が **false**である場合は、手順 3. でパブリケーション プロパティが不適切に定義されたか、パブリケーションが存在していません。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> メソッドです。  
  
6.  (省略可) このデータベースに他のトランザクション パブリケーションが存在する場合は、次に示すように、トランザクション パブリッシングに対してデータベースを無効にすることができます。  
  
    1.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティのインスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. のです。  
  
    2.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドにより **false**が返された場合は、データベースが存在することを確認してください。  
  
    3.  設定、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> プロパティを **false**します。  
  
    4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドです。  
  
7.  接続を閉じます。  
  
#### マージ パブリケーションを削除するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
4.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをパブリケーションが存在することを確認します。 このプロパティの値が **false**である場合は、手順 3. でパブリケーション プロパティが不適切に定義されたか、パブリケーションが存在していません。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> メソッドです。  
  
6.  (省略可) このデータベースに他のマージ パブリケーションが存在する場合は、次に示すように、マージ パブリッシングに対してデータベースを無効にすることができます。  
  
    1.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティのインスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1 からです。  
  
    2.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドです。 このメソッドが **false**を返す場合、データベースが存在するかどうかを確認してください。  
  
    3.  設定、 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> プロパティを **false**します。  
  
    4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドです。  
  
7.  接続を閉じます。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションを削除します。 このデータベースに対して他のトランザクション パブリケーションが存在しない場合は、トランザクション パブリッシングも無効になります。  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 次の例では、マージ パブリケーションを削除します。 このデータベースに対して他のマージ パブリケーションが存在しない場合は、マージ パブリッシングも無効になります。  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## 参照  
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  