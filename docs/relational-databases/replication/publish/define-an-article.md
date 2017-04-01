---
title: "アーティクルの定義 | Microsoft Docs"
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
  - "articles [SQL Server replication], defining"
  - "sp_addmergearticle"
  - "adding articles"
  - "sp_addarticle"
  - "アーティクル [SQL Server レプリケーション]、追加"
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# アーティクルの定義
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルを定義する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **アーティクルを定義するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   アーティクルの名前には % , * , [ , ] , | , : , " , ? を使用できません。 , ' , \ , / , \< , >. データベース内のオブジェクトにこれらの文字が使用されているときに、そのオブジェクトをレプリケートする場合、そのオブジェクト名とは異なる名前をアーティクルに指定する必要があります。  
  
##  <a name="Security"></a> セキュリティ  
 可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 資格情報を保存する必要がある場合は、 [Windows .NET&amp;amp;#xA0;Framework に用意されている](http://go.microsoft.com/fwlink/?LinkId=34733) 暗号化サービス [!INCLUDE[msCoName](../../../includes/msconame-md.md)] を使用します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 パブリケーションの新規作成ウィザードにより、パブリケーションを作成し、アーティクルを定義します。 表示し、[パブリケーションのプロパティを変更、パブリケーションを作成した後、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 Oracle データベースからパブリケーションを作成する方法の詳細については、次を参照してください。 [Oracle データベースからパブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)します。  
  
#### パブリケーションを作成し、アーティクルを定義するには  
  
1.   [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  展開、 **レプリケーション** フォルダー、および右クリック、 **ローカル パブリケーション** フォルダーです。  
  
3.  **[新しいパブリケーション]**をクリックします。  
  
4.  パブリケーションの新規作成ウィザードのページに従い、以下の操作を実行します。  
  
    -   サーバーでディストリビューションが構成されていない場合は、ディストリビューターを指定します。 ディストリビューションの構成の詳細については、次を参照してください。 [パブリッシングとディストリビューション](../../../relational-databases/replication/configure-publishing-and-distribution.md)します。  
  
         指定する場合、 **ディストリビューター** 発行元のサーバーは独自のディストリビューター (ローカル ディストリビューター) として機能し、サーバーが構成されていない、ディストリビューター、パブリケーションの新規作成ウィザードは、サーバーを構成するページです。 **[スナップショット フォルダー]** ページで、ディストリビューターの既定のスナップショット フォルダーを指定します。 スナップショット フォルダーは、共有として指定したディレクトリです。このフォルダーの読み取りと書き込みをするエージェントには、このフォルダーへのアクセスを可能にする十分な権限が必要です。 詳細については、フォルダーを適切にセキュリティで保護する、次を参照してください。 [スナップショット フォルダーをセキュリティで保護された](../../../relational-databases/replication/security/secure-the-snapshot-folder.md)します。  
  
         別のサーバーがディストリビューターとして機能するように指定する場合は、パブリッシャーからディストリビューターへの接続のため、 **[管理パスワード]** ページでパスワードを入力する必要があります。 このパスワードは、リモート ディストリビューターでパブリッシャーを有効にしたときに指定したパスワードと一致する必要があります。  
  
         詳細については、次を参照してください。 [ディストリビューションの構成](../../../relational-databases/replication/configure-distribution.md)します。  
  
    -   パブリケーション データベースを選択します。  
  
    -   パブリケーションの種類を選択します。 詳細については、次を参照してください。 [の種類のレプリケーション](../../../relational-databases/replication/types-of-replication.md)します。  
  
    -   パブリッシュするデータおよびデータベース オブジェクトを指定します。必要に応じて、テーブル アーティクルから列をフィルター選択し、アーティクルのプロパティを設定します。  
  
    -   必要に応じて、テーブル アーティクルから行をフィルター選択します。 詳細については、次を参照してください。 [パブリッシュされたデータのフィルター](../../../relational-databases/replication/publish/filter-published-data.md)します。  
  
    -   スナップショット エージェントのスケジュールを設定します。  
  
    -   以下のレプリケーション エージェントの実行および接続に使用される資格情報を指定します。  
  
         \- すべてのパブリケーションのスナップショット エージェント。  
  
         \- ログ リーダー エージェントは、すべてのトランザクション パブリケーション用にします。  
  
         \- キュー リーダー エージェントは、更新サブスクリプションを許可するトランザクション パブリケーション用にします。  
  
         詳細については、「 [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) 」および「 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)」を参照してください。  
  
    -   必要に応じて、パブリケーションのスクリプトを作成します。 詳しくは、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」をご覧ください。  
  
    -   パブリケーションの名前を指定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリケーションが作成された後、プログラムでレプリケーション ストアド プロシージャを使用してアーティクルを作成できます。 アーティクルの作成に使用するストアド プロシージャは、定義するアーティクルのパブリケーションの種類によって決まります。 詳しくは、「 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 アーティクルが属しているパブリケーションの名前を指定 **@publication**, 、アーティクルの名前 **@article**, 用にパブリッシュされるデータベース オブジェクトを使用して **@source_object**, 、その他の省略可能なパラメーターです。 使用 **@source_owner** 以外の場合、オブジェクトのスキーマの所有権を指定する **dbo**します。 アーティクルがログベース テーブル アーティクルでない場合は、指定のアーティクルの種類を **@type**。 詳細については、を参照してください [アーティクルの種類の指定 (&) #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md)します。  
  
2.  水平方向にテーブル内の行をフィルター処理またはアーティクルを表示する、 [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) フィルター句を定義します。 詳しくは、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
3.  垂直方向にテーブル内の列をフィルター処理またはアーティクルを表示する、 [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)します。 詳しくは、「 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)」をご覧ください。  
  
4.  実行 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 場合は、アーティクルがフィルター選択します。  
  
5.  パブリケーションに既存のサブスクリプションがある場合と [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) の値を返します **0** で、 **immediate_sync** ] 列で、呼び出す必要があります [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) 既存の各サブスクリプションにアーティクルを追加します。  
  
6.  パブリケーションの既存のプル サブスクリプションがある、実行 [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) パブリッシャーに新しいアーティクルのみを含む既存のプル サブスクリプションの新しいスナップショットを作成します。  
  
    > [!NOTE]  
    >  サブスクリプションのスナップショットを使用して初期化されていない場合は実行する必要はありません [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) によってこの手順が実行される [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。  
  
#### マージ パブリケーションのアーティクルを定義するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 パブリケーションの名前を指定 **@publication**, 、アーティクルの名前の名前 **@article**, 、およびパブリッシュ対象のオブジェクト **@source_object**します。 値を指定するテーブルの行を水平方向にフィルターするには、 **@subset_filterclause**します。 詳細については、「 [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) 」および「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」を参照してください。 アーティクルがテーブル アーティクルでない場合、 **@type**にアーティクルの種類を指定します。 詳細については、次を参照してください。 [アーティクルの種類の指定 (&) #40 です。レプリケーション TRANSACT-SQL プログラミングと #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md)します。  
  
2.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) を 2 つのアーティクル間の結合フィルターを定義します。 詳しくは、「 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)」をご覧ください。  
  
3.  (省略可能)パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) フィルター テーブルの列にします。 詳しくは、「 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)」をご覧ください。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、 `Product` テーブルに基づいてトランザクション パブリケーションにアーティクルを定義します。アーティクルは行方向および列方向にフィルター選択されます。  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_1.sql)]  
  
 この例では、マージ パブリケーションのアーティクルを定義します。 `SalesOrderHeader` アーティクルは **SalesPersonID**に基づいて静的にフィルター選択され、 `SalesOrderDetail` アーティクルは `SalesOrderHeader`に基づいて結合フィルターが適用されます。  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってアーティクルを定義できます。 アーティクルの定義に使用する RMO クラスは、アーティクルを定義するパブリケーションの種類によって決まります。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、行フィルターと列フィルターを含むアーティクルをトランザクション パブリケーションに追加します。  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 次の例では、マージ パブリケーションに 3 つのアーティクルを追加します。 このアーティクルには列フィルターがあり、2 つの結合フィルターを使用してパラメーター化された行フィルターを他のアーティクルに反映します。  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## 参照  
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [既存のパブリケーションでのアーティクルの追加および削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [パブリッシュされたデータのフィルター選択](../../../relational-databases/replication/publish/filter-published-data.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  