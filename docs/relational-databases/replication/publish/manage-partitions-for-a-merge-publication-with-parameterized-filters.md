---
title: "パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理 | Microsoft Docs"
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
  - "パーティション [SQL Server レプリケーション]"
  - "マージ レプリケーションのパーティション [SQL Server レプリケーション]、SQL Server Management Studio"
  - "パラメーター化されたフィルター [SQL Server レプリケーション]、パーティション管理"
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# パラメーター化されたフィルターによるマージ パブリケーションのパーティションの管理
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パラメーター化されたフィルターを利用し、マージ パブリケーションのパーティションを管理する方法ついて説明します。 パラメーター化された行フィルターを使用して、重複しないパーティションを生成できます。 パーティションを制限することで、特定のパーティションを 1 つのサブスクリプションだけが受け取るようにできます。 このような場合、サブスクリプションの数が多いと多数のパーティションが生成されるため、それと同数のパーティション スナップショットが必要になります。 詳しくは、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **パラメーター化されたフィルターによるマージ パブリケーションのパーティションを管理するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   レプリケーション トポロジをスクリプト化する場合 (推奨)、パブリケーション スクリプトには、データ パーティションを作成するためのストアド プロシージャの呼び出しが含まれます。 このスクリプトによって、作成されたパーティションの参照、および必要に応じて 1 つ以上のパーティションを再作成する方法を利用できます。 詳しくは、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
-   パブリケーションが、重複しないパーティションを含むサブスクリプションを返すパラメーター化されたフィルターを持つ場合に、特定のサブスクリプションが失われて再作成が必要になったときは、サブスクライブされたパーティションを削除し、サブスクリプションを再作成してから、パーティションを再作成する必要があります。 詳しくは、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。 パブリケーション作成スクリプトが生成されると、レプリケーションによって既存のサブスクライバー パーティション用の作成スクリプトが生成されます。 詳しくは、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パーティションを管理、 **データ パーティション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。 このページでは、パーティションを作成および削除する、サブスクライバーがスナップショットの生成および配信を開始できるようにする、1 つ以上のパーティションのスナップショットを生成する、スナップショットをクリーンアップするなどの操作を行うことができます。  
  
#### パーティションを作成するには  
  
1.   **データ パーティション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、をクリックして **追加**します。  
  
2.   **データ パーティションの追加** ] ダイアログ ボックスで、値を入力、 **HOST_NAME()** や **SUSER_SNAME()** を作成するパーティションに関連付けられた値。  
  
3.  オプションでスナップショットの更新スケジュールを指定します。  
  
    1.  選択 **スケジュールのスケジュールで実行するには、このパーティションのスナップショット エージェント**  
  
    2.  スナップショットの既定の更新スケジュールをそのまま使用するか、または **[変更]** をクリックして別のスケジュールを指定します。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### パーティションを削除するには  
  
1.  **[データ パーティション]** ページのグリッドでパーティションを選択します。  
  
2.  **[削除]**をクリックします。  
  
#### サブスクライバーにスナップショットの生成と配信を許可するには  
  
1.  **[データ パーティション]** ページで、 **[新規サブスクライバーで同期を行うとき、パーティションを自動的に定義し、必要に応じてスナップショットを生成する]**を選択します。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### パーティションのスナップショットを生成するには  
  
1.  **[データ パーティション]** ページのグリッドでパーティションを選択します。  
  
2.  **[今すぐ選択したスナップショットを生成する]**をクリックします。  
  
#### パーティションのスナップショットをクリーンアップするには  
  
1.  **[データ パーティション]** ページのグリッドでパーティションを選択します。  
  
2.  **[既存のスナップショットをクリーンアップする]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パラメーター化されたフィルターを使ってパブリケーションをより詳細に管理するために、プログラムからレプリケーション ストアド プロシージャを使用して既存のパーティションを列挙できます。 既存のパーティションの作成と削除も行えます。 既存パーティションに関する次の情報も取得できます。  
  
-   パーティションをフィルター処理する方法 (を使用して [SUSER_SNAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/suser-sname-transact-sql.md) または [HOST_NAME & #40 です。Transact-SQL と #41;](../../../t-sql/functions/host-name-transact-sql.md))。  
  
-   パーティション スナップショットを生成するジョブの名前  
  
-   パーティション スナップショット ジョブが最後に実行された時刻  
  
 新しいサブスクリプションが初期化されたときに、2 つの部分から構成されるスナップショットの 2 番目の部分は要求時に生成できますが、下記の手順を実行することで、このスナップショットの生成方法を制御し、都合のよいときにこのスナップショットをあらかじめ生成できます。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
#### 既存のパーティションに関する情報を表示するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergepartition & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md)します。 パブリケーションの名前を **@publication**に指定します。 (省略可能)指定 **@suser_sname** または **@host_name** を 1 つのフィルター選択条件に基づく情報のみを返します。  
  
#### 新しいパーティションを定義して、新しいパーティション スナップショットを生成するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepartition & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)します。 **@publication**にパブリケーションの名前を指定し、次のいずれかのパラメーターに、パーティションを定義するパラメーター値を指定します。  
  
    -   **@suser_sname** によって返される値でパラメーター化されたフィルターを定義するときに [SUSER_SNAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/suser-sname-transact-sql.md)します。  
  
    -   **@host_name** によって返される値でパラメーター化されたフィルターを定義するときに [HOST_NAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/host-name-transact-sql.md)します。  
  
2.  この新しいパーティションのパラメーター化スナップショットを作成し、初期化します。 詳しくは、「 [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。  
  
#### パーティションを削除するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_dropmergepartition & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)します。 **@publication** にパブリケーションの名前を指定し、次のいずれかのパラメーターに、パーティションを定義するパラメーター値を指定します。  
  
    -   **@suser_sname** によって返される値でパラメーター化されたフィルターを定義するときに [SUSER_SNAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/suser-sname-transact-sql.md)します。  
  
    -   **@host_name** によって返される値でパラメーター化されたフィルターを定義するときに [HOST_NAME & #40 です。Transact SQL と #41;](../../../t-sql/functions/host-name-transact-sql.md)します。  
  
     これにより、そのパーティションのスナップショット ジョブおよびすべてのスナップショット ファイルも削除されます。  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 パラメーター化されたフィルターを使ってパブリケーションをより適切に管理するために、レプリケーション管理オブジェクト (RMO) を使用して、新しいサブスクライバー パーティションの作成、既存のサブスクライバー パーティションの列挙、およびサブスクライバーの削除をプログラムで行うことができます。 サブスクライバー パーティションを作成する方法の詳細については、「 [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」を参照してください。 既存のパーティションに関する次の情報を取得できます。  
  
-   パーティションの基になる値およびフィルター関数。  
  
-   サブスクライバーのパラメーター化されたスナップショットを生成するジョブの名前。  
  
-   パラメーター化されたスナップショット ジョブが最後に実行された日時。  
  
#### 既存のパーティションに関する情報を表示するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> メソッド、型の配列を結果を渡すと <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトです。  
  
5.  各 <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトの配列で、必要なプロパティを取得します。  
  
#### 既存のパーティションを削除するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> クラスです。 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. で作成します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> メソッド、型の配列を結果を渡すと <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトです。  
  
5.  各 <xref:Microsoft.SqlServer.Replication.MergePartition> オブジェクトの配列で、パーティションを削除するかどうかを判断します。 この決定は通常の値に基づいて、 <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> プロパティまたは <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> プロパティです。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> メソッドを <xref:Microsoft.SqlServer.Replication.MergePublication> 手順 2 のオブジェクト。 渡す、 <xref:Microsoft.SqlServer.Replication.MergePartition> 手順 5. のオブジェクト。  
  
7.  削除する各パーティションに対して手順 6. を繰り返します。  
  
## 参照  
 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [パラメーター化されたフィルターを使用したマージ パブリケーションのスナップショット](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  