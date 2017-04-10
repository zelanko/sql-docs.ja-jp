---
title: "マージ アーティクルのパラメーター化された行フィルターの定義および変更 | Microsoft Docs"
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
  - "パラメーター化されたフィルター [SQL Server レプリケーション]、定義"
  - "パラメーター化されたフィルター [SQL Server レプリケーション]、変更"
  - "マージ レプリケーション [SQL Server レプリケーション]、動的フィルター"
  - "マージ レプリケーションのパラメーター化されたフィルター [SQL Server レプリケーション]"
  - "フィルター [SQL Server レプリケーション]、パラメーター化"
  - "フィルター変更、 パラメーター化された行"
  - "動的フィルター [SQL Server レプリケーション]"
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# マージ アーティクルのパラメーター化された行フィルターの定義および変更
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、パラメーター化された行フィルターを定義および変更する方法について説明します。  
  
 テーブル アーティクルを作成する際には、パラメーター化された行フィルターを使用できます。 これらのフィルターを使用して、 [、](../../../t-sql/queries/where-transact-sql.md) 句を公開する適切なデータを選択します。 (静的行フィルターと同様) 句でリテラル値の指定ではなく、次のシステム関数の一方または両方を指定する: [SUSER_SNAME](../../../t-sql/functions/suser-sname-transact-sql.md) と [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md)します。 詳しくは、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **パラメーター化された行フィルターを定義または変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションに対するサブスクリプションが初期化された後に、パラメーター化された行フィルターを追加、変更、または削除した場合は、変更を行った後で、新しいスナップショットを生成し、すべてのサブスクリプションを再初期化する必要があります。 プロパティの変更に対する要件の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   パラメーター化された行フィルター句では列名に関数を適用しないことをお勧めします。これは、`LEFT([MyColumn]) = SUSER_SNAME()` のように指定すると、パフォーマンスに問題が生じるためです。 フィルター句で HOST_NAME を使用していて、HOST_NAME 値を上書きする場合は、CONVERT を使用するデータ型の変換が必要になる可能性があります。 この場合のベスト プラクティスについての詳細については、」の「HOST_NAME() 値のオーバーライド」セクションを参照してください。 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 定義、変更、およびパラメーター化された行フィルターの削除、 **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### パラメーター化された行フィルターを定義するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>**, 、] をクリックして **追加**, 、] をクリックし、 **フィルターの追加**します。  
  
2.   **フィルターの追加** ] ダイアログ ボックスでドロップダウン リスト ボックスからフィルター処理するテーブルを選択します。  
  
3.  **[フィルター ステートメント]** テキスト ボックスで、フィルター ステートメントを作成します。 テキスト領域に直接入力することも、 **[列]** ボックスから列をドラッグ アンド ドロップすることもできます。  
  
    -   **[フィルター ステートメント]** テキスト領域には、次の形式の既定のテキストが表示されます。  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   既定のテキストは変更できません。標準の SQL 構文を使用して WHERE キーワードの後にフィルター句を入力してください。 パラメーター化されたフィルターには、システム関数の呼び出しが含まれています。 **HOST_NAME()** や **SUSER_SNAME()**, 、あるいはこれらの関数の一方または両方を参照するユーザー定義関数です。 パラメーター化された行フィルターの完全なフィルター句の例を次に示します。  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         WHERE 句には、2 つの部分で構成されている名前を使用する必要があります。3 つまたは 4 つの部分で構成されている名前の使用はサポートされていません。  
  
4.  複数のサブスクライバー間でのデータの共有方法に一致するオプションを選択します。  
  
    -   **[このテーブルの 1 行を複数のサブスクリプションに移動する]**  
  
    -   **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**  
  
     **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**を選択すると、マージ レプリケーションは、格納および処理するメタデータを減らすことにより、パフォーマンスを最適化できます。 ただし、データのパーティション分割によって、1 つの行が複数のサブスクライバーにレプリケートされないことを確認する必要があります。 詳細については、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」トピックの「[パーティションのオプション] の設定」をご覧ください。  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### パラメーター化された行フィルターを変更するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>**, 、内のフィルターを選択して、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **編集**します。  
  
2.  **[フィルターの編集]** ダイアログ ボックスで、フィルターを変更します。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### パラメーター化された行フィルターを削除するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>**, 、内のフィルターを選択、 **フィルター選択されたテーブル** ] ウィンドウで、クリックして **削除**します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パラメーター化された行フィルターは、レプリケーション ストアド プロシージャを使用してプログラムから作成し、変更できます。  
  
#### マージ パブリケーション内のアーティクルにパラメーター化された行フィルターを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 指定 **@publication**, 、アーティクルの名前 **@article**, 、パブリッシュ対象のテーブル **@source_object**, 、WHERE 句のパラメーター化されたフィルターを定義する **@subset_filterclause** (を含まない `WHERE`)、次のいずれかの値 **@partition_options**, がパラメーター化された行フィルターから発生するパーティション分割の種類を説明します。  
  
    -   **0** - が静的か、各パーティション (「重複する」のパーティション) のデータの一意なサブセットを作成しませんアーティクルのフィルター選択します。  
  
    -   **1** - 生成されるパーティションが重複していると、サブスクライバーで行われた更新は、行が属するパーティションを変更できません。  
  
    -   **2** - 重複しないパーティションは、アーティクルのフィルター処理が生成されますが、複数のサブスクライバーが同じパーティションを受け取ることができます。  
  
    -   **3** - サブスクリプションごとに一意である記事生成重複しないパーティションのフィルター選択します。  
  
#### マージ パブリケーション内のアーティクルに適用するパラメーター化された行フィルターを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 指定 **@publication**, 、**@article**, の値 **subset_filterclause** の **@property**, のパラメーター化されたフィルターを定義する式 **@value** (を含まない `WHERE`) の値との **1** 両方の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
2.  この変更によりパーティション分割は異なる動作をする場合、実行 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) 再度します。 指定 **@publication**, 、**@article**, の値 **partition_options** の **@property**, 、および最も適切なパーティション分割オプションを **@value**, 、次のいずれかを指定することができます。  
  
    -   **0** - が静的か、各パーティション (「重複する」のパーティション) のデータの一意なサブセットを作成しませんアーティクルのフィルター選択します。  
  
    -   **1** - 生成されるパーティションが重複していると、サブスクライバーで行われた更新は、行が属するパーティションを変更できません。  
  
    -   **2** - 重複しないパーティションは、アーティクルのフィルター処理が生成されますが、複数のサブスクライバーが同じパーティションを受け取ることができます。  
  
    -   **3** - サブスクリプションごとに一意である記事生成重複しないパーティションのフィルター選択します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例は、アーティクルが一連の結合フィルターのフィルター処理、マージ パブリケーションでアーティクルのグループを定義、 `Employee` 自体に対するパラメーター化された行フィルターを使ってフィルター選択されたテーブルには、 **LoginID** 列です。 戻り値の同期中に、 [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) 関数をオーバーライドします。 詳細については、トピックの「HOST_NAME() 値オーバーライドを参照してください [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)します。  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-para_1.sql)]  
  
## 参照  
 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [結合フィルター](../../../relational-databases/replication/merge/join-filters.md)   
 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  