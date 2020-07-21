---
title: プッシュ サブスクリプションのプロパティの表示または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1506d4f83fcfb94d62efd01c4d6447048fecfd6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063689"
---
# <a name="view-and-modify-push-subscription-properties"></a>プッシュ サブスクリプションのプロパティの表示または変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、プッシュ サブスクリプションのプロパティを表示および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **プッシュ サブスクリプションのプロパティを表示および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 プッシュ サブスクリプション プロパティを表示および変更するには、以下の方法があります。  
  
-   [**サブスクリプションのプロパティ \<Publisher> - \<PublicationDatabase> :** ] ダイアログボックス。から使用でき [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ます。  
  
-   レプリケーション モニターの **[すべてのサブスクリプション]** タブ。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a>Management Studio でプッシュ サブスクリプション プロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  適切なパブリケーションを展開し、サブスクリプションを右クリックして、 **[プロパティ]** をクリックします。  
  
4.  必要に応じてプロパティを変更し、 **[OK]** をクリックします。  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a>レプリケーション モニターでプッシュ サブスクリプション プロパティを表示および変更するには  
  
1.  レプリケーション モニターの左ペインのパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックします。  
  
3.  サブスクリプションを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  必要に応じてプロパティを変更し、 **[OK]** をクリックします。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
 プッシュ サブスクリプションのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更できます。 使用するストアド プロシージャは、サブスクリプションが属するパブリケーションの種類によって異なります。  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションのプッシュ サブスクリプションのプロパティを表示するには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)を実行します。 には **@publication** 、、 **@subscriber** 、および**すべて**の値を指定し **@article** ます。  
  
2.  パブリッシャーのパブリケーション データベースで [@subscriber](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)を指定して **@subscriber**ダイアログ ボックス。  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションのプッシュ サブスクリプションのプロパティを変更するには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_changesubscriber](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)を指定して **@subscriber** を指定し、さらに、変更対象とするサブスクライバー プロパティのパラメーターをすべて指定します。  
  
2.  パブリッシャーのパブリケーション データベースで [sp_changesubscription](/sql/relational-databases/system-stored-procedures/sp-changesubscription-transact-sql)を実行します。 、、を指定し、に all を、に変更するサブスクリプションプロパティを、に新しい値を指定し **@publication** **@subscriber** **@destination_db** **all** **@article** **@property** **@value** ます。 これにより、プッシュ サブスクリプションのセキュリティ設定が変更されます。  
  
3.  (省略可) サブスクリプションのデータ変換サービス (DTS) パッケージのプロパティを変更するには、サブスクライバーのサブスクリプション データベースで [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql) を実行します。 にディストリビューションエージェントジョブの ID を指定 **@jobid** し、次の DTS パッケージのプロパティを指定します。  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     これにより、サブスクリプションの DTS パッケージ プロパティが変更されます。  
  
    > [!NOTE]  
    >  ジョブ ID は、 [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql)を実行することで取得できます。  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a>マージ パブリケーションのプッシュ サブスクリプションのプロパティを表示するには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql)を実行します。 およびを指定し **@publication** **@subscriber** ます。  
  
2.  パブリッシャーで、 [@subscriber](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)を指定して **@subscriber**から表示できます。  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a>マージ パブリケーションのプッシュ サブスクリプションのプロパティを変更するには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_changemergesubscription](/sql/relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql)を実行します。 **@publication**、、 **@subscriber** **@subscriber_db** 、変更するサブスクリプションプロパティを、 **@property** および新しい値として指定し **@value** ます。  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> 例 (Transact-SQL)  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 プッシュ サブスクリプション プロパティの表示や変更に使用する RMO クラスは、プッシュ サブスクリプションをサブスクライブするパブリケーションの種類によって異なります。  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションに対するプッシュ サブスクリプションのプロパティを表示または変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.TransSubscription> クラスのインスタンスを作成します。  
  
3.  <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> の各プロパティを設定します。  
  
4.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティ設定に、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> を設定します。  
  
5.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから `false` が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
6.  (省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.TransSubscription> の設定可能なプロパティに新しい値を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。  
  
7.  (省略可) 新しい設定を表示するには、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドを呼び出して、サブスクリプションのプロパティを再読み込みします。  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a>マージ パブリケーションに対するプッシュ サブスクリプションのプロパティを表示または変更するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、サブスクライバーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.MergeSubscription> クラスのインスタンスを作成します。  
  
3.  <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A>、 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> の各プロパティを設定します。  
  
4.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティ設定に、手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> を設定します。  
  
5.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、オブジェクトのプロパティを取得します。 このメソッドから `false` が返された場合、手順 3. で指定したサブスクリプションのプロパティが正しく定義されていないか、サブスクリプションが存在していません。  
  
6.  (省略可) プロパティを変更するには、 <xref:Microsoft.SqlServer.Replication.MergeSubscription> の設定可能なプロパティに新しい値を設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。  
  
7.  (省略可) 新しい設定を表示するには、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> メソッドを呼び出して、サブスクリプションのプロパティを再読み込みします。  
  
## <a name="see-also"></a>参照  
 [レプリケーションモニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [レプリケーションのセキュリティに関するベストプラクティス](security/replication-security-best-practices.md)   
 [Subscribe to Publications](subscribe-to-publications.md)  
  
  
