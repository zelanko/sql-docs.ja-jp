---
title: "静的行フィルターの定義および変更 | Microsoft Docs"
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
  - "modifying filters, static row"
  - "static row filters"
  - "フィルター [SQL Server レプリケーション], 静的行"
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# 静的行フィルターの定義および変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、静的行フィルターを定義および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
-   **静的行フィルターを定義または変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションに対するサブスクリプションが初期化された後に、静的行フィルターを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。 プロパティの変更に対する要件の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
-   パブリケーションでピア ツー ピア トランザクション レプリケーションが有効な場合、テーブルはフィルター選択できません。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   フィルターが静的であるため、すべてのサブスクライバーは同じデータのサブセットを受け取ることになります。 マージ パブリケーションに属しているテーブルのアーティクルから行を動的にフィルター選択して、各サブスクライバーが異なるデータ パーティションを受け取るようにする場合は、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」を参照してください。 マージ レプリケーションでは、既存の行フィルターに基づいて、関連する行をフィルター選択することもできます。 詳細については、「 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご参照ください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 定義、変更、および静的行フィルターを削除、 **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### 静的行フィルターを定義するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、行う操作は、パブリケーションの種類に依存します。  
  
    -   スナップショット パブリケーションまたはトランザクション パブリケーションの場合は、 **[追加]**をクリックします。  
  
    -   マージ パブリケーションの場合は、 **[追加]**をクリックしてから **[フィルターの追加]**をクリックします。  
  
2.   **フィルターの追加** ] ダイアログ ボックスでドロップダウン リスト ボックスからフィルター処理するテーブルを選択します。  
  
3.  **[フィルター ステートメント]** テキスト領域で、フィルター ステートメントを作成します。 テキスト領域に直接入力することも、 **[列]** ボックスから列をドラッグ アンド ドロップすることもできます。  
  
    > [!NOTE]  
    >  WHERE 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。 パブリケーションが Oracle パブリッシャーからのものである場合、WHERE 句は Oracle の構文に準拠する必要があります。  
  
    -   **[フィルター ステートメント]** テキスト領域には、次の形式の既定のテキストが表示されます。  
  
        ```tsql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   既定のテキストは変更できません。標準の SQL 構文を使用して WHERE キーワードの後にフィルター句を入力してください。 完成したフィルター句は、次のように表示されます。  
  
        ```tsql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   静的行フィルターには、ユーザー定義関数を含めることができます。 ユーザー定義関数を指定して完成した静的行フィルターのフィルター句は、次のように表示されます。  
  
        ```tsql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### 静的行フィルターを変更するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックス内のフィルター選択、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **編集**します。  
  
2.  **[フィルターの編集]** ダイアログ ボックスで、フィルターを変更します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### 静的行フィルターを削除するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックス内のフィルター選択、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **削除**します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 テーブルのアーティクルを作成するとき、WHERE 句を定義することで、アーティクルから特定の行をフィルター選択できます。 いったん行フィルターを定義した後で、そのフィルターを変更することもできます。 静的行フィルターは、レプリケーションのストアド プロシージャを使用してプログラムから作成したり変更したりできます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションの静的行フィルターを定義するには  
  
1.  フィルターを適用するアーティクルを定義します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articlefilter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)します。 アーティクルの名前を指定 **@article**, のパブリケーションの名前 **@publication**, のフィルターの名前 **@filter_name**, 、およびフィルター句 **@filter_clause** (を含まない `WHERE`)。  
  
3.  列フィルターも定義する必要がある場合は、「 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)」を参照してください。 それ以外の場合、実行 [sp_articleview & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。 パブリケーション名を指定 **@publication**, 、フィルター選択されたアーティクルの名前 **@article**, 、および手順 2 で指定されたフィルタ句 **@filter_clause**します。 これにより、フィルターを適用するアーティクルの同期オブジェクトが作成されます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションの静的行フィルターを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articlefilter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)します。 アーティクルの名前を指定 **@article**, のパブリケーションの名前 **@publication**, 、新しいフィルターの名前 **@filter_name**, 、および新しいフィルター句 **@filter_clause** (を含まない `WHERE`)。 この変更には、既存のサブスクリプション内のデータが無効になりますので、値を指定して **1** の **@force_reinit_subscription**します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articleview & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。 パブリケーション名を指定 **@publication**, 、フィルター選択されたアーティクルの名前 **@article**, 、および手順 1. で指定されたフィルタ句 **@filter_clause**します。 この結果、フィルター選択の対象アーティクルを定義するビューが再作成されます。  
  
3.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」をご参照ください。  
  
4.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションの静的行フィルターを削除するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articlefilter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)します。 アーティクルの名前を指定 **@article**, のパブリケーションの名前 **@publication**, の NULL 値 **@filter_name**, 、値の場合は NULL を **@filter_clause**します。 この変更には、既存のサブスクリプション内のデータが無効になりますので、値を指定して **1** の **@force_reinit_subscription**します。  
  
2.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」をご参照ください。  
  
3.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### マージ パブリケーションの静的行フィルターを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 フィルター句を指定 **@subset_filterclause** (を含まない `WHERE`)。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.  列フィルターも定義する必要がある場合は、「 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)」を参照してください。  
  
#### マージ パブリケーションの静的行フィルターを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 パブリケーション名を指定 **@publication**, 、フィルター選択されたアーティクルの名前 **@article**, の値 **subset_filterclause** の **@property**, 、および新しいフィルター句 **@value** (を含まない `WHERE`)。 この変更には、既存のサブスクリプション内のデータが無効になりますのでの 1 の値を指定します。 **@force_reinit_subscription**します。  
  
2.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」をご参照ください。  
  
3.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次のトランザクション レプリケーションの例では、アーティクルを行方向でフィルター選択し、製造停止になった製品をすべて除外します。  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_1.sql)]  
  
 次のマージ レプリケーションの例では、アーティクルを行方向でフィルター選択して、指定した営業担当者に属する行だけを取得します。 結合フィルターも使用されます。 詳しくは、「 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_2.sql)]  
  
## 参照  
 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [パブリッシュされたデータのフィルター選択](../../../relational-databases/replication/publish/filter-published-data.md)   
 [マージ レプリケーション用にパブリッシュされたデータのフィルター選択](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  