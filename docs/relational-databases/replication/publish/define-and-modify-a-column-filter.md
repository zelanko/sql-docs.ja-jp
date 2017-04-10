---
title: "列フィルターの定義および変更 | Microsoft Docs"
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
  - "filters [SQL Server replication], column"
  - "modifying filters, column"
  - "modifying filters"
  - "列フィルター [SQL Server レプリケーション]"
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# 列フィルターの定義および変更
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、列フィルターを定義および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
-   **列フィルターを定義または変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   いくつかの列をフィルター処理できません。詳細については、次を参照してください。 [パブリッシュされたデータのフィルター](../../../relational-databases/replication/publish/filter-published-data.md)します。 サブスクリプションを初期化した後で列フィルターを変更する場合には、列フィルターの変更後、新規スナップショットを生成してすべてのサブスクリプションを再初期化する必要があります。 プロパティの変更に対する要件の詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードの **[アーティクル]** ページで列フィルターを定義します。 詳細については、パブリケーションの新規作成ウィザードを使用して、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。  
  
 定義し、列フィルターを変更、 **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 パブリケーションとアーティクルのプロパティの詳細については、次を参照してください。 [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### 列フィルターを定義するには  
  
1.  パブリケーションの新規作成ウィザードの **[アーティクル]** ページにある **[パブリッシュするオブジェクト]** ペインで、フィルター選択するテーブルを展開します。  
  
2.  フィルター選択する列の隣にあるチェック ボックスをオフにします。  
  
#### 列フィルターを変更するには  
  
1.   **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスで、フィルター選択されるテーブルを展開し、 **パブリッシュするオブジェクト** ウィンドウです。  
  
2.  フィルター選択する列の隣にあるチェック ボックスをオフにして、アーティクルに含める列のチェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 テーブル アーティクルを作成するときに、アーティクルにどの列を含めるかを定義したり、アーティクルを定義した後で列を変更したりできます。 レプリケーション ストアド プロシージャを使用して、フィルターが適用された列をプログラムで作成および変更できます。  
  
> [!NOTE]  
>  次の手順は、基になるテーブルが変更されていないことが前提となっています。 パブリッシュされたテーブルに対するデータ定義言語 (DDL) の変更をレプリケートする方法については、次を参照してください。 [パブリケーション データベースでスキーマ変更を行う](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされたアーティクルの列フィルターを定義するには  
  
1.  フィルターを適用するアーティクルを定義します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)します。 これにより、アーティクルに含める列、またはアーティクルから削除する列を定義します。  
  
    -   多くの列を含むテーブルからのいくつか列のみをパブリッシュする場合は、実行 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) 追加する各列に対して 1 回です。 **@column** に列名を指定し、 **@operation** に **add**を指定します。  
  
    -   列のほとんどを多くの列を含むテーブルをパブリッシュする場合は、実行 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), の値を指定する **null** の **@column** の値との **追加** の **@operation** すべての列を追加します。 実行し、 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), 除外する各列の値を指定するとしたら、 **ドロップ** の **@operation** と除外する列名を **@column**します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。 **@publication** にパブリケーション名を指定し、 **@article**にフィルターを適用するアーティクルの名前を指定します。 これにより、フィルターを適用するアーティクルの同期オブジェクトが作成されます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされたアーティクルに対して、追加列を含めるための列フィルターを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) 追加する各列に対して 1 回です。 **@column** に列名を指定し、 **@operation** に **add**を指定します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。 **@publication** にパブリケーション名を指定し、 **@article**にフィルターを適用するアーティクルの名前を指定します。 パブリケーションに既存のサブスクリプションがある場合は、値を指定 **1** の **@change_active**します。 これにより、フィルターを適用するアーティクルの同期オブジェクトが再作成されます。  
  
3.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。  
  
4.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションでパブリッシュされたアーティクルに対して、列を削除するための列フィルターを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) 削除する各列に対して 1 回です。 **@column** に列名を指定し、 **@operation** に **drop**を指定します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)します。 **@publication** にパブリケーション名を指定し、 **@article**にフィルターを適用するアーティクルの名前を指定します。 パブリケーションに既存のサブスクリプションがある場合は、値を指定 **1** の **@change_active**します。 これにより、フィルターを適用するアーティクルの同期オブジェクトが再作成されます。  
  
3.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。  
  
4.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### スナップショットまたはマージ パブリケーションでパブリッシュされたアーティクルの列フィルターを定義するには  
  
1.  フィルターを適用するアーティクルを定義します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md)します。 これにより、アーティクルに含める列、またはアーティクルから削除する列を定義します。  
  
    -   多くの列を含むテーブルからのいくつか列のみをパブリッシュする場合は、実行 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) 追加する各列に対して 1 回です。 **@column** に列名を指定し、 **@operation** に **add**を指定します。  
  
    -   列のほとんどを多くの列を含むテーブルをパブリッシュする場合は、実行 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), の値を指定する **null** の **@column** の値との **追加** の **@operation** すべての列を追加します。 実行し、 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), 除外する各列の値を指定するとしたら、 **ドロップ** の **@operation** と除外する列名を **@column**します。  
  
#### マージ パブリケーションでパブリッシュされたアーティクルに対して、追加列を含めるための列フィルターを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) 追加する各列に対して 1 回です。 列名を指定 **@column**, の値 **追加** の **@operation** の値との **1** 両方の **@force_invalidate_snapshot** と **@force_reinit_subscription**します。  
  
2.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。  
  
3.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
#### マージ パブリケーションでパブリッシュされたアーティクルに対して、列を削除するための列フィルターを変更するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) 削除する各列に対して 1 回です。 列名を指定 **@column**, の値 **ドロップ** の **@operation** の **1** 両方の **@force_invalidate_snapshot** と **@force_reinit_subscription**です。  
  
2.  パブリケーションに対してスナップショット エージェント ジョブを再実行し、更新済みスナップショットを生成します。  
  
3.  サブスクリプションを再初期化します。 詳細については、次を参照してください。 [サブスクリプションの再初期化](../../../relational-databases/replication/reinitialize-subscriptions.md)します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次のトランザクション レプリケーション例では、 `DaysToManufacture` テーブルに基づく `Product` 列がアーティクルから削除されます。  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_1.sql)]  
  
 次のマージ レプリケーション例では、 `CreditCardApprovalCode` テーブルに基づく `SalesOrderHeader` 列がアーティクルから削除されます。  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_2.sql)]  
  
## 参照  
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [パブリッシュされたデータのフィルター選択](../../../relational-databases/replication/publish/filter-published-data.md)   
 [マージ レプリケーション用にパブリッシュされたデータのフィルター選択](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  