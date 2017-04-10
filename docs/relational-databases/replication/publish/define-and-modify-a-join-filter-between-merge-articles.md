---
title: "マージ アーティクル間の結合フィルターの定義および変更 | Microsoft Docs"
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
  - "filters [SQL Server replication], join"
  - "merge replication join filters [SQL Server replication]"
  - "modifying filters, join"
  - "結合フィルター"
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# マージ アーティクル間の結合フィルターの定義および変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクル間の結合フィルターを定義および変更する方法について説明します。 マージ レプリケーションでは結合フィルターがサポートされています。結合フィルターは、通常、テーブル分割を他の関連するテーブル アーティクルに拡張するために、パラメーター化されたフィルターと組み合わせて使用されます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
-   **マージ アーティクル間の結合フィルターを定義および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   結合フィルターを作成するには、パブリケーションに少なくとも 2 つの関連テーブルを含める必要があります。 結合フィルターは、行フィルターを拡張したものです。そのため、結合を使用して行フィルターを別のテーブルに拡張するには、先に 1 つのテーブルの行フィルターを定義する必要があります。 結合フィルターを 1 つ定義すると、パブリケーションに追加の関連テーブルが含まれている場合、この結合フィルターは別の結合フィルターを使用して拡張できます。  
  
-   パブリケーションに対するサブスクリプションが初期化された後に、結合フィルターを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。 プロパティの変更に対する要件の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   結合フィルターは、一連のテーブルに対して手動で作成できます。また、テーブルに定義された外部キーと主キーのリレーションシップに基づいて、レプリケーションによって自動的に生成することもできます。 一連の結合フィルターを自動的に生成する方法の詳細については、次を参照してください。 [自動的に生成する設定の結合フィルターの間でマージ アーティクルと #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 定義、変更、および結合フィルターを削除、 **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### 結合フィルターを定義するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>**, を既存の行フィルターを選択するか結合フィルター、 **フィルター選択されたテーブル** ウィンドウです。  
  
2.  **[追加]**をクリックし、 **[選択したフィルターを拡張するために結合を追加する]**をクリックします。  
  
3.  JOIN ステートメントを作成します。 **[ビルダーを使用してステートメントを作成する]** または **[JOIN ステートメントを手動で作成する]**を選択します。  
  
    -   ビルダーを使用して選択した場合は、グリッドの列を使用して (**組み合わせて**, 、**フィルター選択されたテーブルの列**, 、**演算子**, と **結合テーブルの列**) を join ステートメントを構築します。  
  
         グリッド内の各列には 2 つの列と演算子を選択し、ドロップダウン コンボ ボックスが含まれています (**=**, 、**<>**, 、**<=**, 、**\<**, 、**>=**, 、**>**, 、および **のような**)。 結果は **[プレビュー]** テキスト領域に表示されます。 結合には、列の 1 つ以上のペアが含まれている場合は、結合を選択 (とまたは OR) から、 **組み合わせて** ] 列で、2 列と演算子を入力します。  
  
    -   ステートメントを手動で作成する場合、 **[JOIN ステートメント]** テキスト領域に JOIN ステートメントを入力します。 **[フィルター選択されたテーブルの列]** ボックスと **[結合テーブルの列]** ボックスを使用して、 **[JOIN ステートメント]** テキスト領域に列をドラッグ アンド ドロップします。  
  
    -   完成した JOIN ステートメントは、次のように表示されます。  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         JOIN 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。  
  
4.  結合オプションを指定します。  
  
    -   フィルター選択されたテーブル (親テーブル) に参加する列が一意である場合は、選択 **一意キー**します。  
  
        > [!CAUTION]  
        >  このオプションを選択すると、結合フィルターにおける子テーブルと親テーブルのリレーションシップが一対一または一対多となるように指定されます。 子テーブル内で結合する列に制約があり、一意性が保証される場合にのみ、このオプションを選択します。 このオプションを適切に設定しなかった場合、データを収束できない可能性があります。  
  
    -   既定で、マージ レプリケーションでは同期中に行ごとに変化が処理されます。 関連する変更をフィルター選択されたテーブルとを単位として処理する結合テーブルの両方の行で、次のように選択します。 **論理レコード** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降のバージョンのみ)。 このオプションは、論理レコードを使用するために必要なアーティクルとパブリケーションの要件が満たされている場合にのみ使用できます。 詳細については「に関する考慮事項の論理レコードの使用」セクションを参照してください [論理レコードによる関連行へのグループの変更](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)します。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### 結合フィルターを変更するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>**, 、内のフィルターを選択して、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **編集**します。  
  
2.  **[結合の編集]** ダイアログ ボックスで、フィルターを変更します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### 結合フィルターを削除するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>**, 、内のフィルターを選択、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **削除**します。 削除する結合フィルター自体が他の結合によって拡張されている場合は、それらの結合も削除されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 この手順では、親アーティクルのパラメーター化されたフィルターと、親アーティクルと子アーティクルの結合フィルターを組み合わせて使用する方法について説明します。 結合フィルターは、レプリケーションのストアド プロシージャを使用してプログラムから定義したり変更したりできます。  
  
#### アーティクル フィルターをマージ パブリケーションの関連アーティクルに拡張する結合フィルターを定義するには  
  
1.  結合先アーティクル (親アーティクル) のフィルターを定義します。  
  
    -   パラメーター化された行フィルターを使ったアーティクルのフィルター選択については、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」を参照してください。  
  
    -   静的行フィルターを使ったアーティクルのフィルター選択については、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」を参照してください。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) 定義する 1 つ以上、関連アーティクル、パブリケーション用の子アーティクルとも呼ばれます。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergefilter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)します。 指定 **@publication**, 、フィルターの対象の一意の名前 **@filtername**, 、手順 2 で作成した子アーティクルの名前 **@article**, 、用に結合されている親アーティクルの名前 **@join_articlename**, 、次のいずれかの値 **@join_unique_key**:  
  
    -   **0** -親と子アーティクル間の多対一または多対多の結合を示します。  
  
    -   **1** -親と子アーティクル間の一対一または一対多の結合を示します。  
  
     これにより、2 つのアーティクル間の結合フィルターが定義されます。  
  
    > [!CAUTION]  
    >  設定のみ **@join_unique_key** に **1** 一意性を保証する親アーティクルの基になるテーブルに結合する列の制約がある場合。 場合 **@join_unique_key** に設定されている **1** 正しく、データの未集約が発生するされません。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、マージ パブリケーションのアーティクルを定義しています。 `SalesOrderDetail` テーブルのアーティクルが、 `SalesOrderHeader` テーブルと比較されてフィルター選択されます (このテーブル自体が静的行フィルターを使ってフィルター選択されています)。 詳しくは、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-join_1.sql)]  
  
 この例は、アーティクルが一連の結合フィルターのフィルター処理、マージ パブリケーションでアーティクルのグループを定義、 `Employee` 自体の値に対するパラメーター化された行フィルターを使ってフィルター選択されたテーブルには、 [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) で、 **LoginID** 列です。 詳しくは、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-join_2.sql)]  
  
## 参照  
 [結合フィルター](../../../relational-databases/replication/merge/join-filters.md)   
 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [マージ レプリケーション用にパブリッシュされたデータのフィルター選択](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)   
 [マージ アーティクル間の結合フィルターを定義および変更する方法 (SQL Server Management Studio)](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Define a Logical Record Relationship Between Merge Table Articles](../../../relational-databases/replication/publish/define-a-logical-record-relationship-between-merge-table-articles.md)   
 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  