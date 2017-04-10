---
title: "トランザクション レプリケーションの待機時間の計測および接続の検証 | Microsoft Docs"
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
  - "Replication Monitor, performance"
  - "tracer tokens [SQL Server replication]"
  - "latency [SQL Server replication]"
  - "transactional replication, tracer tokens"
  - "パフォーマンスの監視 [SQL Server レプリケーション], トレーサー トークン"
ms.assetid: 4addd426-7523-4067-8d7d-ca6bae4c9e34
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# トランザクション レプリケーションの待機時間の計測および接続の検証
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] でレプリケーション モニター、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用し、トランザクション レプリケーションの待機時間を計測して接続を検証する方法について説明します。 トランザクション レプリケーションには、トレーサー トークン機能が用意されており、これによって簡単にトランザクション レプリケーション トポロジにおける待機時間を計測したり、パブリッシャー、ディストリビューター、およびサブスクライバーの間の接続を検証したりすることができます。 トークン (小さなデータ) は、通常のレプリケートされたトランザクションのようにマークが付けられてパブリケーション データベースのトランザクション ログに書き込まれ、システムを介して送信されることで、次の計算が可能になります。  
  
-   パブリッシャーでコミットされるトランザクションと、ディストリビューターでディストリビューション データベース内に挿入される対応するコマンドの間での経過時間。  
  
-   ディストリビューション データベース内に挿入されるコマンドと、サブスクライバーでコミットされる対応するトランザクションの間での経過時間。  
  
 これらの計算結果から、以下のようなさまざまな内容を特定できます。  
  
-   変更内容をパブリッシャーから受信するのに最も時間がかかるのはどのサブスクライバーか。  
  
-   トレース トークンを受信することになっているサブスクライバーのうち、受信していないサブスクライバーがあるか。あるとすればどのサブスクライバーか。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **接続の待機時間を計測して検証するために使用するもの:**  
  
     [SQL Server レプリケーション モニター](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 トレーサー トークンは、システムを停止する場合にも役立ちます。このとき、すべての処理を停止して、すべてのノードがすべての未処理の変更を受信したかどうかを検証します。 詳細については、次を参照してください。 [休止レプリケーション トポロジと #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)します。  
  
 トレーサー トークンを使用するには、特定のバージョンの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を使用する必要があります。  
  
-   ディストリビューターは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降である必要があります。  
  
-   パブリッシャーは [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降であるか、Oracle パブリッシャーである必要があります。  
  
-   プッシュ サブスクリプションでは、サブスクライバーが [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 以降である場合に、トレーサー トークン統計がパブリッシャー、ディストリビューター、およびサブスクライバーから収集されます。  
  
-   プル サブスクリプションでは、サブスクライバーが [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降である場合にのみ、トレーサー トークン統計がサブスクライバーから収集されます。 サブスクライバーが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 7.0 または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]である場合は、統計はパブリッシャーおよびディストリビューターからのみ収集されます。  
  
 その他にも、次のような問題点と制限事項について注意する必要があります。  
  
-   トレーサー トークンを受信するには、サブスクリプションをアクティブにする必要があります。 サブスクリプションは、初期化されている場合はアクティブです。  
  
-   再初期化を行うと、関連するサブスクリプションに対する保留中のトレーサー トークンがすべて削除されます。  
  
-   サブスクライバーは、初期同期の完了後に作成されたトレーサー トークンのみを受信します。  
  
-   レーサ トークンは、再パブリッシュ サブスクライバーからは転送されません。  
  
-   セカンダリにフェールオーバーした後、レプリケーション モニターは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のパブリッシング インスタンスの名前を調整できません。引き続き、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の元のプライマリ インスタンスの名前を使ってレプリケーション情報を表示します。 フェールオーバー後は、トレーサー トークンはレプリケーション モニターを使用して入力できませんが、新しいパブリッシャーで [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して入力されたトレース トークンがレプリケーション モニターに表示されます。  
  
##  <a name="SSMSProcedure"></a> SQL Server レプリケーション モニターの使用  
 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
#### トレーサー トークンを挿入してトークンの情報を表示するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[トレーサー トークン]** タブをクリックします。  
  
3.  **[トレーサーの挿入]**をクリックします。  
  
4.  **[パブリッシャーからディストリビューターまで]**列、 **[ディストリビューターからサブスクライバーまで]**列、および **[合計待機時間]**列で、トレーサー トークンの経過時間を表示します。 **[保留中]** と表示された場合は、トークンが特定のポイントに到達していないことを示します。  
  
#### 以前に挿入したトレーサー トークンの情報を表示するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[トレーサー トークン]** タブをクリックします。  
  
3.  時間を選択、 **挿入時刻** ボックスの一覧です。  
  
4.  **[パブリッシャーからディストリビューターまで]**列、 **[ディストリビューターからサブスクライバーまで]**列、および **[合計待機時間]**列で、トレーサー トークンの経過時間を表示します。 **[保留中]** と表示された場合は、トークンが特定のポイントに到達していないことを示します。  
  
    > [!NOTE]  
    >  トレーサー トークン情報は、ディストリビューション データベースの履歴保持期間の制約を受けるその他の履歴データと同じ期間保持されます。 ディストリビューション データベースのプロパティを変更する方法の詳細については、次を参照してください。 [表示と変更のディストリビューターとパブリッシャーのプロパティ](../../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### トレーサー トークンをトランザクション パブリケーションに通知するには  
  
1.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helppublication & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)します。 パブリケーションが存在すること、および状態がアクティブであることを確認します。  
  
2.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpsubscription & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)します。 サブスクリプションが存在すること、および状態がアクティブであることを確認します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_posttracertoken & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-posttracertoken-transact-sql.md), を指定して **@publication**します。 値に注意してください、 **@tracer_token_id** 出力パラメーターです。  
  
#### 待機時間を決定し、トランザクション パブリケーションの接続を確認するには  
  
1.  上述の手順を使用して、トレーサー トークンをパブリケーションに通知します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helptracertokens & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md), を指定して **@publication**します。 パブリケーションに通知されたすべてのトレーサー トークンのリストが返されます。 目的 **tracer_id** 結果に設定します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helptracertokenhistory & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md), を指定して **@publication** と手順 2. のトレーサー トークン ID **@tracer_id**します。 選択したトレーサー トークンの待機情報が返されます。  
  
#### トレーサー トークンを削除するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helptracertokens & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md), を指定して **@publication**します。 パブリケーションに通知されたすべてのトレーサー トークンのリストが返されます。 注、 **tracer_id** 、結果を削除するトレーサー トークンを設定します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_deletetracertokenhistory & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md), を指定して **@publication** と手順 2. を削除するトレーサーの ID **@tracer_id**します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、トレーサー トークン レコードを通知し、返された通知済みトレーサー トークンの ID を使用して待機時間情報を表示します。  
  
 [!code-sql[HowTo#sp_tracertokens](../../../relational-databases/replication/codesnippet/tsql/measure-latency-and-vali_1.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
#### トレーサー トークンをトランザクション パブリケーションに通知するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 3. でパブリケーション プロパティの定義が正しくなかったか、パブリケーションが存在していません。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.TransPublication.PostTracerToken%2A> メソッドです。 このメソッドは、トレーサー トークンをパブリケーションのトランザクション ログに挿入します。  
  
#### 待機時間を決定し、トランザクション パブリケーションの接続を確認するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> プロパティ、およびセット、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 3. でパブリケーション モニター プロパティの定義が正しくなかったか、パブリケーションが存在していません。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> メソッドです。 返されたキャスト <xref:System.Collections.ArrayList> オブジェクトの配列を <xref:Microsoft.SqlServer.Replication.TracerToken> オブジェクトです。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokenHistory%2A> メソッドです。 値を渡す <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 手順 5. のトレーサー トークンのです。 として選択したトレーサー トークンの待機時間の情報が返されます、 <xref:System.Data.DataSet> オブジェクトです。 すべてのトレーサー トークン情報が返された場合、パブリッシャーとディストリビューターとの接続、およびディストリビューターとサブスクライバーの接続が両方とも存在し、レプリケーション トポロジは機能しています。  
  
#### トレーサー トークンを削除するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.DistributionDBName%2A>, 、<xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublisherName%2A>, 、および <xref:Microsoft.SqlServer.Replication.PublicationMonitor.PublicationDBName%2A> プロパティ、およびセット、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 3. でパブリケーション モニター プロパティの定義が正しくなかったか、パブリケーションが存在していません。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.EnumTracerTokens%2A> メソッドです。 返されたキャスト <xref:System.Collections.ArrayList> オブジェクトの配列を <xref:Microsoft.SqlServer.Replication.TracerToken> オブジェクトです。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.PublicationMonitor.CleanUpTracerTokenHistory%2A> メソッドです。 次の値のいずれかを渡します。  
  
    -    <xref:Microsoft.SqlServer.Replication.TracerToken.TracerTokenId%2A> 手順 5. のトレーサー トークンのです。 これにより、選択したトークンの情報が削除されます。  
  
    -   A <xref:System.DateTime> オブジェクトです。 これにより、指定した日時より古いすべてのトークンの情報が削除されます。  
  
  