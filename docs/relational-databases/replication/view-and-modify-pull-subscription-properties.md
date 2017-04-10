---
title: "プル サブスクリプションのプロパティの表示または変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying subscriptions"
  - "viewing replication properties"
  - "modifying replication properties, pull subscriptions"
  - "pull subscriptions [SQL Server replication], modifying"
  - "subscriptions [SQL Server replication], pull"
  - "pull subscriptions [SQL Server replication], properties"
  - "サブスクリプションの変更, SQL Server Management Studio"
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# プル サブスクリプションのプロパティの表示または変更
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プル サブスクリプションのプロパティを表示および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **プル サブスクリプションのプロパティを表示および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリッシャーまたはサブスクライバーからプル サブスクリプションのプロパティを表示、 **サブスクリプションのプロパティ - \< Publisher>: \< PublicationDatabase>** ] ダイアログ ボックスから利用できる [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。 その他のプロパティはサブスクライバーから表示でき、サブスクライバーで変更できます。 パブリッシャーからも、レプリケーション モニターの **[すべてのサブスクリプション]** タブでプロパティを表示できます。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
#### Management Studio でパブリッシャーからのプル サブスクリプション プロパティを表示するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  適切なパブリケーションを展開し、サブスクリプションを右クリックしてをクリックし、 **プロパティ**します。  
  
4.  プロパティを表示して **[OK]**をクリックします。  
  
#### Management Studio でサブスクライバーからのプル サブスクリプション プロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でサブスクライバーに接続して、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル サブスクリプション]** フォルダーを展開します。  
  
3.  サブスクリプションの場合を右クリックし、をクリックし、 **プロパティ**します。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
#### レプリケーション モニターでパブリッシャーからのプル サブスクリプション プロパティを表示するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  サブスクリプションの場合を右クリックし、をクリックし、 **プロパティ**します。  
  
4.  プロパティを表示して **[OK]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 レプリケーション ストアド プロシージャを使用して、プル サブスクリプションを変更し、そのプロパティにプログラムからアクセスできます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションのプロパティを表示するには  
  
1.  サブスクライバーで、次のように実行します。 [sp_helppullsubscription](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、および **@publication**します。 これにより、サブスクライバーのシステム テーブルに格納されている、サブスクリプションに関する情報が返されます。  
  
2.  サブスクライバーで、次のように実行します。 [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、次のいずれかの値と **@publication_type**:  
  
    -   **0** -サブスクリプションがトランザクション パブリケーションに属します。  
  
    -   **1** -サブスクリプションがスナップショット パブリケーションに属します。  
  
3.  パブリッシャーで実行 [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)します。 **@publication** と **@subscriber**を指定します。  
  
4.  パブリッシャーで実行 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), を指定して **@subscriber**します。 これにより、サブスクライバーに関する情報が表示されます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプル サブスクリプションのプロパティを変更するには  
  
1.  サブスクライバーで、次のように実行します。 [sp_change_subscription_properties](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md), を指定して **@publisher**, 、**@publisher_db**, 、**@publication**, 、いずれかの値 **0** (トランザクション) または **1** (スナップショット) を **@publication_type**, 、変更対象のサブスクリプション プロパティ **@property**, 、し、新しい値として **@value**します。  
  
2.  (省略可能)サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md)します。 ディストリビューション エージェント ジョブの ID を指定して **@jobid**, 、し、次のデータ変換サービス (DTS) パッケージのプロパティ。  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     これにより、サブスクリプションの DTS パッケージ プロパティが変更されます。  
  
    > [!NOTE]  
    >  ジョブを実行して ID を取得できる [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)します。  
  
#### マージ パブリケーションに対するプル サブスクリプションのプロパティを表示するには  
  
1.  サブスクライバーで、次のように実行します。 [sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、および **@publication**します。  
  
2.  サブスクライバーで、次のように実行します。 [sp_helpsubscription_properties](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)します。 指定 **@publisher**, 、**@publisher_db**, 、**@publication**, 、および値 2 を **@publication_type**します。  
  
3.  パブリッシャーで実行 [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md) サブスクリプション情報を表示します。 指定する必要があります、特定のサブスクリプションに関する情報を返す **@publication**, 、**@subscriber**, の値との **プル** の **@subscription_type**します。  
  
4.  パブリッシャーで実行 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), を指定して **@subscriber**します。 これにより、サブスクライバーに関する情報が表示されます。  
  
#### マージ パブリケーションに対するプル サブスクリプションのプロパティを変更するには  
  
1.  サブスクライバーで、次のように実行します。 [sp_changemergepullsubscription](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)します。 指定 **@publication**, 、**@publisher**, 、**@publisher_db**, 、変更対象のサブスクリプション プロパティ **@property**, 、し、新しい値として **@value**します。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 プル サブスクリプションのプロパティを表示または変更する際に使用する RMO のクラスは、プル サブスクリプションがサブスクライブされるパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのプル サブスクリプションのプロパティを表示または変更するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションがサーバー上に存在していません。  
  
6.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.TransPullSubscription> プロパティを設定でき、まず、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドです。  
  
7.  (省略可能)新しい設定を表示する呼び出し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 、アーティクルのプロパティを再読み込みします。  
  
8.  すべての接続を閉じます。  
  
#### マージ パブリケーションのプル サブスクリプションのプロパティを表示または変更するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションがサーバー上に存在していません。  
  
6.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.MergePullSubscription> プロパティを設定でき、まず、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドです。  
  
7.  (省略可能)新しい設定を表示する呼び出し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 、アーティクルのプロパティを再読み込みします。  
  
8.  すべての接続を閉じます。  
  
## 参照  
 [情報を表示し、サブスクリプションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  