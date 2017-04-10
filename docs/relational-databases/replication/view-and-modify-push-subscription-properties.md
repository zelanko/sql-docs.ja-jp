---
title: "プッシュ サブスクリプションのプロパティの表示または変更 | Microsoft Docs"
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
  - "viewing replication properties"
  - "push subscriptions [SQL Server replication], properties"
  - "subscriptions [SQL Server replication], push"
  - "push subscriptions [SQL Server replication], modifying"
  - "modifying replication properties, push subscriptions"
  - "サブスクリプションの変更, SQL Server Management Studio"
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# プッシュ サブスクリプションのプロパティの表示または変更
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プッシュ サブスクリプションのプロパティを表示および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **プッシュ サブスクリプションのプロパティを表示および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 プッシュ サブスクリプション プロパティを表示および変更するには、以下の方法があります。  
  
-    **サブスクリプションのプロパティ - \< Publisher>: \< PublicationDatabase>** ] ダイアログ ボックスから利用できる [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  
  
-   レプリケーション モニターの **[すべてのサブスクリプション]** タブ。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
#### Management Studio でプッシュ サブスクリプション プロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  適切なパブリケーションを展開し、サブスクリプションを右クリックしてをクリックし、 **プロパティ**します。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
#### レプリケーション モニターでプッシュ サブスクリプション プロパティを表示および変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  サブスクリプションの場合を右クリックし、をクリックし、 **プロパティ**します。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 プッシュ サブスクリプションのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更できます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのプッシュ サブスクリプションのプロパティを表示するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)します。 **@publication**と **@subscriber**を指定し、 **@article** に **all**を指定します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), を指定して **@subscriber**します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのプッシュ サブスクリプションのプロパティを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changesubscriber](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md), を指定して **@subscriber** および変更するサブスクライバーのプロパティのパラメーターです。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, 、**@destination_db**, の値 **すべて** の **@article**, 、変更対象のサブスクリプション プロパティ **@property**, 、し、新しい値として **@value**します。 これにより、プッシュ サブスクリプションのセキュリティ設定が変更されます。  
  
3.  (省略可能)サブスクリプションのデータ変換サービス (DTS) パッケージのプロパティを変更するには、実行 [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md) サブスクライバー側でサブスクリプション データベースです。 **@jobid** にディストリビューション エージェント ジョブの ID を指定し、さらに、次の DTS パッケージ プロパティを指定します。  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     これにより、サブスクリプションの DTS パッケージ プロパティが変更されます。  
  
    > [!NOTE]  
    >  ジョブを実行して ID を取得できる [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)します。  
  
#### マージ パブリケーションのプッシュ サブスクリプションのプロパティを表示するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)します。 **@publication** と **@subscriber**を指定します。  
  
2.  パブリッシャーで実行 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md), を指定して **@subscriber**します。  
  
#### マージ パブリケーションのプッシュ サブスクリプションのプロパティを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)します。 指定 **@publication**, 、**@subscriber**, 、**@subscriber_db**, 、変更対象のサブスクリプション プロパティ **@property**, 、し、新しい値として **@value**します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 プッシュ サブスクリプション プロパティの表示や変更に使用する RMO クラスは、プッシュ サブスクリプションをサブスクライブするパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションのプロパティを表示または変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> プロパティです。  
  
4.  設定、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティの設定です。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
6.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.TransSubscription> プロパティを設定でき、まず、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドです。  
  
7.  (省略可能)新しい設定を表示する呼び出し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドをサブスクリプションのプロパティを再読み込みします。  
  
#### マージ パブリケーションに対するプッシュ サブスクリプションのプロパティを表示または変更するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>, 、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> プロパティです。  
  
4.  設定、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> に手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティの設定です。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
6.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> プロパティを設定でき、まず、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドです。  
  
7.  (省略可能)新しい設定を表示する呼び出し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドをサブスクリプションのプロパティを再読み込みします。  
  
## 参照  
 [情報を表示し、サブスクリプションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  