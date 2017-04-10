---
title: "プログラムによるレプリケーションの監視 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_replmonitorhelppublisher"
  - "sp_replmonitorhelpmergesessiondetail"
  - "monitoring performance [SQL Server replication], publication status"
  - "sp_replmonitorhelpmergesession"
  - "sp_replmonitorhelppublicationthresholds"
  - "monitoring performance [SQL Server replication], subscription status"
  - "monitoring performance [SQL Server replication], Transact-SQL programming"
  - "sp_replmonitorsubscriptionpendingcmds"
  - "sp_replmonitorchangepublicationthreshold"
  - "transactional replication, monitoring"
  - "sp_replmonitorhelppublication"
  - "sp_replmonitorhelpsubscription"
  - "monitoring performance [SQL Server replication], thresholds and warnings"
  - "merge replication monitoring [SQL Server replication]"
  - "スナップショット レプリケーション [SQL Server], 監視"
ms.assetid: e8bf8850-8da5-4a4f-a399-64232b4e476d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# プログラムによるレプリケーションの監視
  レプリケーション モニターは、レプリケーション トポロジを監視するためのグラフィカル ツールです。 [!INCLUDE[tsql](../../../includes/tsql-md.md)] レプリケーション ストアド プロシージャまたはレプリケーション管理オブジェクト (RMO) を使用すると、同じ監視データにプログラムからアクセスできます。 このオブジェクトにより、次のタスクをプログラムできます。  
  
-   パブリッシャー、パブリケーション、およびサブスクリプションの状態を監視する。  
  
-   1 つ以上のサブスクライバーにおけるマージ エージェント セッションを監視する。  
  
-   1 つ以上のサブスクライバーで適用を待機しているトランザクション コマンドを監視する。  
  
-   パブリケーションにユーザーの介入が必要となるしきい値の基準を定義する。  
  
-   トレーサー トークンのステータスを監視する。  
  
 **このトピックの内容:**  
  
 [Transact-SQL](#Tsql)  
  
 [レプリケーション管理オブジェクト (RMO)](#RMO)  
  
##  <a name="Tsql"></a> Transact-SQL  
  
#### ディストリビューターからパブリッシャー、パブリケーション、サブスクリプションを監視するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorhelppublisher](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublisher-transact-sql.md)します。 これにより、このディストリビューターを利用している全パブリッシャーの監視情報が返されます。 結果セットを 1 つのパブリッシャーに限定するには、 **@publisher**を指定します。  
  
2.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorhelppublication](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublication-transact-sql.md)です。 これにより、このディストリビューターを利用している全パブリケーションの監視情報が返されます。 1 つのパブリッシャー、パブリケーション、またはパブリッシュされたデータベースに結果セットを制限するには、次のように指定します。 **@publisher**, 、**@publication**, 、または **@publisher_db**, 、それぞれします。  
  
3.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorhelpsubscription](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpsubscription-transact-sql.md)します。 これにより、このディストリビューターを利用しているすべてのサブスクリプションの監視情報が返されます。 パブリケーション、またはパブリッシュされたデータベースを指定する 1 つのパブリッシャーに属するサブスクリプションに結果セットを制限するには、 **@publisher**, 、**@publication**, 、または **@publisher_db**, 、それぞれします。  
  
#### サブスクライバーで適用を待機しているトランザクション コマンドを監視するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorsubscriptionpendingcmds](../../../relational-databases/system-stored-procedures/sp-replmonitorsubscriptionpendingcmds-transact-sql.md)します。 これにより、このディストリビューターを利用しているすべてのサブスクリプションの、待機中の全コマンドに関する監視情報が返されます。 結果セットを 1 つのパブリッシャーに属するサブスクリプションの保留中のコマンドを制限するサブスクライバー、パブリケーション、またはパブリッシュされたデータベースが指定 **@publisher**, 、**@subscriber**, 、**@publication**, 、または **@publisher_db**, 、それぞれします。  
  
#### アップロードまたはダウンロードされるのを待機しているマージ変更を監視するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md)します。 返される結果セットには、サブスクライバーへのレプリケートを待機している変更に関する情報が示されます。 結果セットを 1 つのパブリケーションまたはアーティクルに属する変更に限定するには、それぞれ **@publication** または **@article**を指定します。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_showpendingchanges](../../../relational-databases/system-stored-procedures/sp-showpendingchanges-transact-sql.md)します。 返される結果セットには、パブリッシャーへのレプリケートを待機している変更に関する情報が示されます。 結果セットを 1 つのパブリケーションまたはアーティクルに属する変更に限定するには、それぞれ **@publication** または **@article**を指定します。  
  
#### マージ エージェント セッションを監視するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md)します。 監視情報が返されますなど **Session_id**, 、このディストリビューターを使用しているすべてのサブスクリプションのすべてのマージ エージェント セッションに関するします。 取得することも **Session_id** クエリを実行して、 [MSmerge_sessions](../../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) システム テーブルです。  
  
2.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md)します。 指定する **Session_id** 手順 1. の値 **@session_id**です。 これにより、セッションに関する詳細な監視情報が表示されます。  
  
3.  目的の各セッションについて、手順 2. を実行します。  
  
#### サブスクライバーからのプル サブスクリプションのマージ エージェント セッションを監視するには  
  
1.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_replmonitorhelpmergesession](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesession-transact-sql.md)です。 指定したサブスクリプションの次のように指定します。 **@publisher**, 、**@publication**, 、パブリケーション データベースの名前と **@publisher_db**します。 これにより、このサブスクリプションの過去 5 回のマージ エージェント セッションに関する監視情報が返されます。 値に注意してください **Session_id** 結果に目的のセッションを設定します。  
  
2.  サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_replmonitorhelpmergesessiondetail](../../../relational-databases/system-stored-procedures/sp-replmonitorhelpmergesessiondetail-transact-sql.md)します。 指定する **Session_id** 手順 1. の値 **@session_id**です。 これにより、セッションに関する詳細な監視情報が表示されます。  
  
3.  目的の各セッションについて、手順 2. を実行します。  
  
#### パブリケーションのしきい値を表示して変更するには  
  
1.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorhelppublicationthresholds](../../../relational-databases/system-stored-procedures/sp-replmonitorhelppublicationthresholds-transact-sql.md)します。 これにより、このディストリビューターを利用している全パブリケーションの監視しきい値が返されます。 結果セットを 1 つのパブリッシャー、パブリッシュされたデータベースまたは 1 つのパブリケーションに属しているパブリケーションのしきい値の監視を制限する指定 **@publisher**, 、**@publisher_db**, 、または **@publication**, 、それぞれします。 値に注意してください **Metric_id** 変更する必要があるしきい値にします。 詳細については、次を参照してください。 [しきい値の設定とレプリケーション モニターで警告](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)します。  
  
2.  ディストリビューター、ディストリビューション データベースで、次のように実行します。 [sp_replmonitorchangepublicationthreshold](../../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md)します。 必要に応じて、次の値を指定します。  
  
    -    **Metric_id** 手順 1. で取得した値 **@metric_id**します。  
  
    -   監視しきい値の新しい値を **@value**に指定します。  
  
    -   このしきい値に到達したときに警告をログに記録するには、 **@shouldalert** に **1** を指定します。警告が不要な場合には、 **0** を指定します。  
  
    -   監視しきい値を有効にするには **@mode** に **1** を指定し、無効にするには **2** を指定します。  
  
##  <a name="RMO"></a> レプリケーション管理オブジェクト (RMO)  
  
#### サブスクライバーでマージ パブリケーションのサブスクリプションを監視するには  
  
1.  使用してサブスクライバーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor> クラス、 <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publisher%2A>, 、<xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.Publication%2A>, 、<xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.PublisherDB%2A>, 、<xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.SubscriberDB%2A> 、サブスクリプション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。  
  
3.  次のいずれかのメソッドを呼び出して、このサブスクリプションのマージ エージェント セッションの情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> -の配列を返します <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> 最大で過去 5 回のマージ エージェント セッション情報をオブジェクトです。 注、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> 関心のある任意のセッションの値。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummary%2A> -の配列を返します <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> として渡された時間数の過去の中に発生したマージ エージェント セッションに関する情報を持つオブジェクト、 *時間* (最大 5 セッション) のパラメーターです。 注、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> 関心のある任意のセッションの値。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummary%2A> -返します、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> 、最後のマージ エージェント セッションに関する情報を含むオブジェクト。 注、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary.SessionId%2A> このセッションの値。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionsSummaryDataSet%2A> -返します、 <xref:System.Data.DataSet> 行ごとに 1 つずつ最後の 5 つのマージ エージェント セッションの最大のオブジェクトの情報を使用します。 値に注意してください、 **Session_id** 関心のあるすべてのセッションについての列です。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetLastSessionSummaryDataRow%2A> -返します、 <xref:System.Data.DataRow> 最後のマージ エージェント セッションに関する情報を含むオブジェクト。 値に注意してください、 **Session_id** このセッションの列です。  
  
4.  (省略可能)呼び出す <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> データを更新、 <xref:Microsoft.SqlServer.Replication.MergeSessionSummary> として渡されるオブジェクト *mss、* 呼び出したり <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.RefreshSessionSummary%2A> でデータを更新する、 <xref:System.Data.DataRow> として渡されるオブジェクト *drRefresh*します。  
  
5.  手順 3. で取得したセッション ID を使用して次のいずれかのメソッドを呼び出し、特定のセッションの詳細情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetails%2A> -の配列を返します <xref:Microsoft.SqlServer.Replication.MergeSessionDetail> 指定されたオブジェクト *SessionId*します。  
  
    -   <xref:Microsoft.SqlServer.Replication.MergeSubscriberMonitor.GetSessionDetailsDataSet%2A> -返します、 <xref:System.Data.DataSet> オブジェクトには、指定された情報 *SessionId*します。  
  
#### ディストリビューターですべてのパブリケーションについてレプリケーション プロパティを監視するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。  
  
5.  次の 1 つまたは複数のメソッドを実行して、このディストリビューターを使用している、すべてのパブリッシャーのレプリケーション情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumDistributionAgents%2A> -返します、 <xref:System.Data.DataSet> このディストリビューターのすべてのディストリビューション エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumErrorRecords%2A> -返します、 <xref:System.Data.DataSet> ディストリビューターで保存されているエラーに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumLogReaderAgents%2A> -返します、 <xref:System.Data.DataSet> 、ディストリビューターのすべてのログ リーダー エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMergeAgents%2A> -返します、 <xref:System.Data.DataSet> 、ディストリビューターのすべてのマージ エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumMiscellaneousAgents%2A> -返します、 <xref:System.Data.DataSet> 、ディストリビューター側でその他のすべてのレプリケーション エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers%2A> -返します、 <xref:System.Data.DataSet> このディストリビューターのすべてのパブリッシャーに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumPublishers2%2A> -返します、 <xref:System.Data.DataSet> このディストリビューターを使用しているパブリッシャーから返されるオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgents%2A> -返します、 <xref:System.Data.DataSet> 、ディストリビューターのすべてのキュー リーダー エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessionDetails%2A> -返します、 <xref:System.Data.DataSet> 指定されたキュー リーダー エージェントおよびセッションに関する詳細を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumQueueReaderAgentSessions%2A> -返します、 <xref:System.Data.DataSet> に関する指定されたキュー リーダー エージェント セッション情報を格納しているオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.EnumSnapshotAgents%2A> -返します、 <xref:System.Data.DataSet> 、ディストリビューターのすべてのスナップショット エージェントに関する情報を格納しているオブジェクト。  
  
#### ディストリビューターで特定のパブリッシャーのパブリケーション プロパティを監視するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  取得、 <xref:Microsoft.SqlServer.Replication.PublisherMonitor> 以下の方法の 1 つのオブジェクト。  
  
    -   インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.PublisherMonitor> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.PublisherMonitor.Name%2A> 発行元、および一連のプロパティ、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。 呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、パブリッシャー名が正しく定義されていないか、パブリケーションが存在していません。  
  
    -    <xref:Microsoft.SqlServer.Replication.PublisherMonitorCollection> のアクセス、 <xref:Microsoft.SqlServer.Replication.ReplicationMonitor.PublisherMonitors%2A> 、既存のプロパティ <xref:Microsoft.SqlServer.Replication.ReplicationMonitor> オブジェクトです。  
  
3.  次の 1 つまたは複数のメソッドを実行して、このパブリッシャーに属している、すべてのパブリケーションのレプリケーション情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessionDetails%2A> -返します、 <xref:System.Data.DataSet> 指定されたディストリビューション エージェントおよびセッションに関する詳細を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumDistributionAgentSessions%2A> -返します、 <xref:System.Data.DataSet> 指定されたディストリビューション エージェントのセッション情報を格納しているオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumErrorRecords%2A> -返します、 <xref:System.Data.DataSet> を指定したエラーに関する情報を記録するエラーを含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessionDetails%2A> -返します、 <xref:System.Data.DataSet> 指定のログ リーダー エージェントおよびセッションの詳細を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumLogReaderAgentSessions%2A> -返します、 <xref:System.Data.DataSet> 指定のログ リーダー エージェントのセッション情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails%2A> -返します、 <xref:System.Data.DataSet> 指定されたマージ エージェントおよびセッションに関する詳細を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessionDetails2%2A> -返します、 <xref:System.Data.DataSet> 指定されたマージ エージェントおよびセッションに関する追加情報を格納しているオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions%2A> -返します、 <xref:System.Data.DataSet> の指定されたマージ エージェント セッション情報を格納しているオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumMergeAgentSessions2%2A> -返します、 <xref:System.Data.DataSet> 指定されたマージ エージェントの追加のセッション情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications%2A> -返します、 <xref:System.Data.DataSet> このディストリビューターのすべてのパブリケーションに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumPublications2%2A> -返します、 <xref:System.Data.DataSet> このディストリビューターのすべてのパブリケーションに関する追加情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessionDetails%2A> -返します、 <xref:System.Data.DataSet> 指定されたスナップショット エージェントおよびセッションに関する詳細を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSnapshotAgentSessions%2A> -返します、 <xref:System.Data.DataSet> 指定したスナップショット エージェントのセッション情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublisherMonitor.EnumSubscriptions%2A> -返します、 <xref:System.Data.DataSet> このディストリビューターのパブリケーションに対するすべてのサブスクリプションに関する情報を含むオブジェクト。  
  
#### ディストリビューターで特定のパブリッシャーのプロパティを監視するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  取得、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 以下の方法の 1 つのオブジェクト。  
  
    -   インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。 呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、パブリケーションのプロパティが正しく定義されていないか、パブリケーションが存在していません。  
  
    -    <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> のアクセス、 <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> 、既存のプロパティ <xref:Microsoft.SqlServer.Replication.PublisherMonitor> オブジェクトです。  
  
3.  次の 1 つまたは複数のメソッドを実行して、このパブリケーションに関する情報を取得します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumErrorRecords%2A> -返します、 <xref:System.Data.DataSet> を指定したエラーのエラー レコードを含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumLogReaderAgent%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションのログ リーダー エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションに対して監視警告のしきい値に関する情報を含むオブジェクトを設定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumQueueReaderAgent%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションで使用されるキュー リーダー エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSnapshotAgent%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションのスナップショット エージェントに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.Publication.EnumSubscriptions%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションに対するサブスクリプションに関する情報を含むオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumSubscriptions2%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションに対するサブスクリプションに関する追加情報を格納しているオブジェクトに基づいて、指定された <xref:Microsoft.SqlServer.Replication.SubscriptionResultOption>します。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> -返します、 <xref:System.Data.DataSet> 指定されたトレーサー トークンの待機時間情報を格納しているオブジェクト。  
  
    -   <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> -返します、 <xref:System.Data.DataSet> このパブリケーションに挿入されたすべてのトレーサー トークンに関する情報を含むオブジェクト。  
  
#### サブスクライバーで適用待ち状態になっているトランザクション コマンドを監視するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  取得、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 以下の方法の 1 つのオブジェクト。  
  
    -   インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。 呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、パブリケーションのプロパティが正しく定義されていないか、パブリケーションが存在していません。  
  
    -    <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> のアクセス、 <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> 、既存のプロパティ <xref:Microsoft.SqlServer.Replication.PublisherMonitor> オブジェクトです。  
  
3.  実行、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.TransPendingCommandInfo%2A> を返すメソッド、 <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> オブジェクトです。  
  
4.  このプロパティを使用して <xref:Microsoft.SqlServer.Replication.PendingCommandInfo> オブジェクトを保留中のコマンドの推定数とこれらのコマンドの配信を完了するための所要時間の長さを決定します。  
  
#### パブリケーションに対して監視警告のしきい値を設定するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  取得、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> 以下の方法の 1 つのオブジェクト。  
  
    -   インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。 呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、パブリケーションのプロパティが正しく定義されていないか、パブリケーションが存在していません。  
  
    -    <xref:Microsoft.SqlServer.Replication.PublicationMonitorCollection> のアクセス、 <xref:Microsoft.SqlServer.Replication.PublisherMonitor.PublicationMonitors%2A> 、既存のプロパティ <xref:Microsoft.SqlServer.Replication.PublisherMonitor> オブジェクトです。  
  
3.  実行、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumMonitorThresholds%2A> メソッドです。 つまり、返される現在のしきい値の設定に注意してください <xref:System.Collections.ArrayList> の <xref:Microsoft.SqlServer.Replication.MonitorThreshold> オブジェクトです。  
  
4.  実行、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.ChangeMonitorThreshold%2A> メソッドです。 次のパラメーターを指定します。  
  
    -   *metricID* - <xref:System.Int32> を次の表の監視のしきい値を表す値。  
  
        |値|説明|  
        |-----------|-----------------|  
        |1|**有効期限** -トランザクション パブリケーションに対するサブスクリプションの有効期限が近づいているを監視します。|  
        |2|**待機時間** -トランザクション パブリケーションに対するサブスクリプションのパフォーマンスを監視します。|  
        |4|**mergeexpiration** -マージ パブリケーションへのサブスクリプションに期限が迫っていないかを監視します。|  
        |5|**mergeslowrunduration** -低帯域 (ダイヤルアップ) 接続でのマージ同期の期間を監視します。|  
        |6|**mergefastrunduration** -高帯域 (LAN) 接続でのマージ同期の期間を監視します。|  
        |7|**mergefastrunspeed** -高帯域 (LAN) 接続でのマージ同期の同期率を監視します。|  
        |8|**mergeslowrunspeed** -低帯域 (ダイヤルアップ) 接続でのマージ同期の同期率を監視します。|  
  
    -   *有効にする* - <xref:System.Boolean> をパブリケーションのメトリックが有効になっているかどうかを示す値。  
  
    -   *%thresholdvalue* -しきい値を設定する整数値。  
  
    -   *shouldAlert* -このしきい値がアラートを生成するかどうかを示す整数です。  
  
  