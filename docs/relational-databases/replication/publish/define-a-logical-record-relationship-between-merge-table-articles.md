---
title: "マージ テーブル アーティクル間に論理レコード リレーションシップを定義する | Microsoft Docs"
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
  - "merge replication logical records [SQL Server replication]"
  - "articles [SQL Server replication], logical records"
  - "論理レコード [SQL Server レプリケーション]"
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# マージ テーブル アーティクル間に論理レコード リレーションシップを定義する
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、マージ テーブル アーティクル間に論理レコード リレーションシップを定義する方法について説明します。  
  
 マージ レプリケーションでは、さまざまなテーブルの関連する行の間にリレーションシップを定義できます。 これらの行は、同期の際にトランザクション単位として処理できます。 論理レコードは、2 つのアーティクルの間に定義できます。結合フィルター リレーションシップの有無は関係ありません。 詳細については、次を参照してください。 [論理レコードによる関連行へのグループの変更](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **マージ テーブル アーティクル間に論理レコード リレーションシップを定義するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションに対するサブスクリプションが初期化された後に、論理レコードを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。 プロパティの変更に対する要件の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 論理レコードの定義、 **結合を追加** パブリケーションの新規作成ウィザードで使用可能なダイアログ ボックスおよび **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
 **[結合の追加]** ダイアログ ボックスで論理レコードを定義できるのは、マージ パブリケーションの結合フィルターに論理レコードが適用されている場合だけです。また、パブリケーションが、事前計算済みパーティションを使用するための要件を満たしている必要もあります。 結合フィルターに適用されていない論理レコードを定義して、論理レコード レベルでの競合の検出と解決を設定するには、ストアド プロシージャを使用する必要があります。  
  
#### 論理レコード リレーションシップを定義するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスで、選択内の行フィルター、 **フィルター選択されたテーブル** ウィンドウです。  
  
     論理レコード リレーションシップは、行フィルターを拡張する結合フィルターに関連付けられます。 したがって、先に行フィルターが定義されていないと、行フィルターを結合で拡張して論理レコード リレーションシップを適用することはできません。 1 つの結合フィルターが定義されると、この結合フィルターを別の結合フィルターを使用して拡張できます。 結合フィルターの定義の詳細については、「 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」を参照してください。  
  
2.  **[追加]**をクリックし、 **[選択したフィルターを拡張するために結合を追加する]**をクリックします。  
  
3.  **[結合の追加]** ダイアログ ボックスで結合フィルターを定義してから、 **[論理レコード]**チェック ボックスをオンにします。  
  
4.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### 論理レコード リレーションシップを削除するには  
  
-   論理レコード リレーションシップのみを削除するか、または論理レコード リレーションシップとそれに関連付けられている結合フィルターを削除します。  
  
     論理レコード リレーションシップのみを削除するには  
  
    1.   **行のフィルター選択** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスで、選択の論理レコード リレーションシップに関連付けられている結合フィルター、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **編集**します。  
  
    2.  **[結合の編集]** ダイアログ ボックスで、 **[論理レコード]**チェック ボックスをオフにします。  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     論理レコード リレーションシップとそれに関連付けられている結合フィルターを削除するには  
  
    -    **行のフィルター選択** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックス内のフィルター選択、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **削除**します。 削除する結合フィルター自体が他の結合によって拡張されている場合は、それらの結合も削除されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 プログラムでレプリケーション ストアド プロシージャを使用して、アーティクル間に論理レコード リレーションシップを指定できます。  
  
#### 関連する結合フィルターを使用せずに論理レコード リレーションシップを定義するには  
  
1.  パブリケーションにフィルター処理されている任意のアーティクルが含まれている場合は、実行 [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), の値をメモ **use_partition_groups** 結果セットにします。  
  
    -   値が **1**の場合、事前計算済みパーティションが既に使用されています。  
  
    -   値の場合 **0**, 、実行し、 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **use_partition_groups** の **@property** の **true** の **@value**します。  
  
        > [!NOTE]  
        >  パブリケーションで事前計算済みパーティションがサポートされない場合、論理レコードは使用できません。 詳細については、トピックで使用する事前計算済みパーティションの要件を参照してください。 [事前計算済みパーティションを持つパラメーター化されたフィルター パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)します。  
  
    -   この値が NULL の場合、パブリケーションの初期スナップショットを生成するためにスナップショット エージェントを実行する必要があります。  
  
2.  論理レコードを構成するアーティクルが存在しない場合、実行 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 論理レコードの競合の検出と解決に関するオプションを次の中から 1 つ指定します。  
  
    -   検出し、論理レコードに関連付けられている行で発生する競合を解決するには、指定の値 **true** の **@logical_record_level_conflict_detection** と **@logical_record_level_conflict_resolution**します。  
  
    -   標準的な行または列レベルの競合の検出と解決を使用するには、値を指定 **false** の **@logical_record_level_conflict_detection** と **@logical_record_level_conflict_resolution**, 、既定であります。  
  
3.  論理レコードを構成する各アーティクルに対して、手順 2. を実行します。 論理レコード内の各アーティクルに使用する競合の検出および解決のオプションは、すべて同じである必要があります。 詳しくは、「 [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md)」をご覧ください。  
  
4.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)します。 指定 **@publication**, との関係の 1 つのアーティクルの名前 **@article**, の 2 つ目のアーティクルの名前 **@join_articlename**, のリレーションシップの名前 **@filtername**, の記事の 2 つのリレーションシップを定義する句 **@join_filterclause**, の結合の種類 **@join_unique_key** し、次のいずれかの値を **@filter_type**:  
  
    -   **2** -論理リレーションシップを定義します。  
  
    -   **3** -結合フィルターを使用して論理リレーションシップを定義します。  
  
    > [!NOTE]  
    >  結合フィルターを使用しない場合、2 つのアーティクル間のリレーションシップの方向はあまり重要でなくなります。  
  
5.  パブリケーションの他の論理レコード リレーションシップについても、手順 2. をそれぞれ実行します。  
  
#### 論理レコードにおける競合の検出と解決の方法を変更するには  
  
1.  論理レコードの関連する行で発生する競合を検出し、解決するには、次の手順を実行します。  
  
    -   パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **logical_record_level_conflict_detection** の **@property** の **true** の **@value**します。 値を指定して **1** の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
    -   パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **logical_record_level_conflict_resolution** の **@property** の **true** の **@value**します。 値を指定して **1** の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
2.  標準の行レベルまたは列レベルの競合の検出と解決を使用するには、次の手順を実行します。  
  
    -   パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **logical_record_level_conflict_detection** の **@property** の **false** の **@value**します。 値を指定して **1** の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
    -   パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **logical_record_level_conflict_resolution** の **@property** の **false** の **@value**します。 値を指定して **1** の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
#### 論理レコード リレーションシップを削除するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して次のクエリを実行し、指定されたパブリケーションに対して定義されているすべての論理レコード リレーションシップに関する情報を返します。  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_1.sql)]  
  
     結果セット内の **filtername** 列で削除されている論理レコード リレーションシップの名前を確認します。  
  
    > [!NOTE]  
    >  このクエリと同じ情報を返します [sp_helpmergefilter](../../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)。 ただし、このシステムにストアド プロシージャがあるだけで結合フィルターでも、論理レコード リレーションシップに関する情報を返します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_dropmergefilter](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)します。 **@publication**を指定し、リレーションシップ内の 1 つのアーティクルの名前を **@article**に、手順 1. のリレーションシップの名前を **@filtername**に指定します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、既存のパブリケーションで事前計算済みパーティションを有効にし、 `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルの 2 つの新しいアーティクルを含む論理レコードを作成しています。  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
> [!NOTE]  
>  マージ レプリケーションを使用して、論理レコード レベルで追跡および解決する競合を指定できますが、これらのオプションは RMO を使用して設定できません。  
  
#### 関連する結合フィルターを使用せずに論理レコード リレーションシップを定義するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  場合、 <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> にプロパティが設定されている <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, に設定 <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>します。  
  
5.  論理レコードを構成しようとするアーティクルが存在しない場合は、インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeArticle> クラスし、次のプロパティを設定します。  
  
    -   アーティクルの名前 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>します。  
  
    -   (省略可能)アーティクルが行方向にフィルター選択される場合に行フィルター句を指定、 <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> プロパティです。 このプロパティを使用して、静的行フィルターまたはパラメーター化された行フィルターを指定します。 詳しくは、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
     詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Article.Create%2A> メソッドです。  
  
7.  論理レコードを構成するアーティクルごとに、手順 5. と 6. を繰り返します。  
  
8.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> アーティクル間の論理レコード リレーションシップを定義するクラス。 その後、次のプロパティを設定します。  
  
    -   論理レコード リレーションシップの子アーティクルの名前、 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> プロパティです。  
  
    -   論理レコードのリレーションシップでは、既存の親アーティクルの名前、 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> プロパティです。  
  
    -   論理レコード リレーションシップの名前、 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> プロパティです。  
  
    -   式のリレーションシップを定義する、 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> プロパティです。  
  
    -   値 <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> の <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> プロパティです。 論理レコードのリレーションシップが結合フィルターでもある場合は、値を指定 <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> このプロパティのです。 詳細については、次を参照してください。 [論理レコードによる関連行へのグループの変更](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)します。  
  
9. 呼び出す、 <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> リレーションシップの子アーティクルを表すオブジェクトのメソッドです。 渡す、 <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> 、手順 8 リレーションシップを定義するオブジェクト。  
  
10. パブリケーションの他の論理レコード リレーションシップについても、手順 8. と 9. をそれぞれ実行します。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 この例では、 `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルの 2 つの新しいアーティクルを含む論理レコードを作成しています。  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## 参照  
 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [論理レコードによる関連行への変更のグループ化](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)   
 [論理レコードによる関連行への変更のグループ化](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)  
  
  