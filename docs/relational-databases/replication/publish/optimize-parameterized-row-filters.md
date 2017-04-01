---
title: "パラメーター化された行フィルターの最適化 | Microsoft Docs"
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
  - "事前計算済みパーティション [SQL Server レプリケーション]"
  - "フィルター [SQL Server レプリケーション]、パラメーター化"
  - "マージ レプリケーション事前計算済みパーティション [SQL Server レプリケーション]、SQL Server Management Studio"
  - "パラメーター化されたフィルター [SQL Server レプリケーション]、最適化"
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# パラメーター化された行フィルターの最適化
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、パラメーター化された行フィルターを最適化する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **パラメーター化された行フィルターを最適化するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   パラメーター化されたフィルターを使用する場合、パブリケーションを作成する際に **@use_partition_groups** オプションまたは **@keep_partition_changes** オプションを指定して、マージ レプリケーションでのフィルターの処理方法を制御できます。 この 2 つのオプションを使用し、パブリケーション データベースに追加のメタデータを格納することで、アーティクルをフィルター選択し、パブリケーションの同期パフォーマンスを向上できます。 アーティクルを作成する際に **@partition_options** を設定することで、サブスクライバー間でデータを共有する方法を制御できます。 これらの要件の詳細については、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
     [!INCLUDE[ssEW](../../../includes/ssew-md.md)] SQL Server Compact サブスクライバーを使用して、keep_partition_changes を true に設定し、削除を正しく反映する必要があります。 false に設定すると、サブスクライバーに予想よりも多くの行が含まれる場合があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 次の設定を使用して、パラメーター化された行フィルターを最適化できます。  
  
 **[パーティションのオプション]**  
 このオプションを設定、 **プロパティ** のページ、 **アーティクルのプロパティ - \< 記事>** ダイアログ ボックスで、または、 **フィルターの追加** ] ダイアログ ボックス。 両方のダイアログ ボックスはパブリケーションの新規作成ウィザードで使用できる、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックスでは、このオプションでは使用できない追加の値を指定することができます、 **フィルターの追加** ] ダイアログ ボックス。  
  
 **[パーティションの事前計算]**  
 このオプションが設定されている **True** 既定では、パブリケーションのアーティクルが一連の要件を満たしている場合。 これらの要件の詳細については、次を参照してください。 [事前計算済みパーティションを持つパラメーター化されたフィルター パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)します。 このオプションを変更、 **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
 **[同期の最適化]**  
 このオプションを設定する必要があります **True** 場合にのみ、 **Precompute パーティション** に設定されている **False**します。 このオプションを設定、 **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
 パブリケーションの新規作成ウィザードを使用して、アクセスの詳細については、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスを参照してください [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### [フィルターの追加] または [フィルターの編集] ダイアログ ボックスでパーティションのオプションを設定するには  
  
1.   **テーブル行のフィルター** パブリケーションの新規作成ウィザードのページまたは **行のフィルター選択** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、をクリックして **追加**, 、順にクリック **フィルターの追加**します。  
  
2.  パラメーター化されたフィルターを作成します。 詳しくは、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
3.  複数のサブスクライバー間でのデータの共有方法に一致するオプションを選択します。  
  
    -   **[このテーブルの 1 行を複数のサブスクリプションに移動する]**  
  
    -   **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**  
  
     **[このテーブルの 1 行を 1 つのサブスクリプションのみに移動する]**を選択すると、マージ レプリケーションは、格納および処理するメタデータを減らすことにより、パフォーマンスを最適化できます。 ただし、データのパーティション分割によって、1 つの行が複数のサブスクライバーにレプリケートされないことを確認する必要があります。 詳細については、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」トピックの「[パーティションのオプション] の設定」をご覧ください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### アーティクルのプロパティ - [パーティションのオプションを設定する \< 記事> ] ダイアログ ボックス  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、テーブルを選択し、をクリックして **アーティクルのプロパティ**します。  
  
2.  **[反転表示されたテーブル アーティクルのプロパティを設定]** または **[すべてのテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **対象オブジェクト** のセクション、 **プロパティ** のタブ、 **アーティクルのプロパティ - \< 記事>** ] ダイアログ ボックスで、次の値のいずれかを指定 **パーティション オプション**:  
  
    -   **[重複する]**  
  
    -   **[重複する (パーティション外のデータ変更を禁止)]**  
  
    -   **[重複しない (単一のサブスクリプション)]**  
  
    -   **[重複しない (複数のサブスクリプションで共有)]**  
  
     これらのオプションの詳細、および **[フィルターの追加]** および **[フィルターの編集]** ダイアログ ボックスで使用できるオプションとこれらのオプションを関連付ける方法の詳細については、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」の「[パーティションのオプション] の設定」を参照してください。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  場合は、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスをクリックして **[ok]** を保存してダイアログ ボックスを閉じます。  
  
#### [パーティションの事前計算] を設定するには  
  
1.   **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでの値を選択、 **Precompute パーティション** オプション。 このプロパティは、以下の場合に読み取り専用になります。  
  
    -   パブリケーションが、事前計算済みパーティションの要件を満たさない場合。  
  
    -   スナップショットが、パブリケーションに対して生成されていない場合。 この場合、 **[スナップショットの作成時に自動的に設定する]**の値が表示されます。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### [同期の最適化] を設定するには  
  
1.   **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスの値を **True** の **同期の最適化** オプション。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 フィルタ オプションの定義については **@keep_partition_changes** と **@use_partition_groups**, を参照してください [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。  
  
#### 新しいパブリケーションを作成するときにマージ フィルターの最適化を指定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 **@publication** を指定し、次のいずれかのパラメーターに **true** を指定します。  
  
    -   **@use_partition_groups**:-アーティクルが事前計算済みパーティションの要件に準拠している指定された最高のパフォーマンスの最適化。 詳細については、次を参照してください。 [事前計算済みパーティションを持つパラメーター化されたフィルター パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)します。  
  
    -   **@keep_partition_changes** -事前計算済みパーティションを使用できない場合は、この最適化を使用します。  
  
2.  パブリケーション用のスナップショット ジョブを追加します。 詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), 、次のパラメーターを指定します。  
  
    -   **@publication** -手順 1. のパブリケーションの名前。  
  
    -   **@article** -アーティクルの名前  
  
    -   **@source_object** - パブリッシュされるデータベース オブジェクトです。  
  
    -   **@subset_filterclause** -アーティクルの水平方向にフィルター選択するために使用する省略可能なパラメーター化されたフィルター句。  
  
    -   **@partition_options** -フィルター選択されたアーティクルのパーティションのオプションです。  
  
4.  パブリケーションの各アーティクルに対し、手順 3. を実行します。  
  
5.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) を 2 つのアーティクル間の結合フィルターを定義します。 詳しくは、「 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
#### 既存のパブリケーションに対するマージ フィルターの動作を表示して変更するには  
  
1.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), を指定して **@publication**します。 値に注意してください **keep_partition_changes** と **use_partition_groups** 結果に設定します。  
  
2.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。 値を指定して **use_partition_groups** の **@property** 、 **true** または **false** の **@value**します。  
  
3.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)します。 値を指定して **keep_partition_changes** の **@property** 、 **true** または **false** の **@value**します。  
  
    > [!NOTE]  
    >  有効にすると **keep_partition_changes**, 、まず無効にする必要があります **use_partition_groups** の値を指定して **1** の **@force_reinit_subscription**します。  
  
4.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **partition_options** の **@property** と適切な値を **@value**します。 参照してください [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) これらの定義については、オプションをフィルター処理します。  
  
5.  (省略可) 必要に応じてスナップショット エージェントを開始し、スナップショットを再生成してください。 については、変更は、新しいスナップショットを生成するを必要とするについて、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
## 参照  
 [マージ アーティクルと #40; の間の結合フィルターのセットを自動的に生成します。SQL Server Management Studio と #41 です。](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md)   
 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [パラメーター化された行フィルター](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  