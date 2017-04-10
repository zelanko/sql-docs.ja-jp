---
title: "アーティクルのプロパティの表示および変更 | Microsoft Docs"
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
  - "sp_changearticle"
  - "sp_helparticle"
  - "レプリケーション プロパティの表示"
  - "sp_changemergearticle"
  - "sp_helpmergearticle"
  - "レプリケーション プロパティの変更、アーティクル"
  - "アーティクル [SQL Server レプリケーション]、変更"
  - "アーティクル [SQL Server レプリケーション]、プロパティ"
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# アーティクルのプロパティの表示および変更
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルのプロパティを表示および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
-   **アーティクルのプロパティを表示および変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションの作成後には変更できないプロパティや、パブリケーションへのサブスクリプションがある場合には変更できないプロパティもあります。 変更できないプロパティは、読み取り専用として表示されます。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   パブリケーションの作成後、プロパティの変更によっては新しいスナップショットが必要となります。 パブリケーションにサブスクリプションが含まれている場合、変更によっては、すべてのサブスクリプションを再初期化する必要もあります。 詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) と [にアーティクルを追加し、既存のパブリケーションからアーティクルを削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)します。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 表示および変更のアーティクルのプロパティ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスで使用可能な [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] およびレプリケーション モニターします。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
-   **[全般]** ページ。パブリケーションの名前と説明、データベースの名前、パブリケーションの種類、およびサブスクリプションの有効期限の設定が含まれています。  
  
-   **[アーティクル]** ページ。パブリケーションの新規作成ウィザードの **[アーティクル]** ページに相当します。 このページでは、アーティクルの追加や削除、およびアーティクルのプロパティや列のフィルター選択の変更を行うことができます。  
  
-   **[行のフィルター選択]** ページ。パブリケーションの新規作成ウィザードの **[テーブル行のフィルター選択]** ページに相当します。 このページでは、すべての種類のパブリケーションの静的行フィルターや、マージ パブリケーションのパラメーター化された行フィルターと結合フィルターを追加、編集、および削除できます。  
  
-   **[スナップショット]** ページ。このページでは、スナップショットの形式と場所、スナップショットを圧縮するかどうか、およびスナップショットの適用の前後に実行するスクリプトを指定できます。  
  
-    **FTP スナップショット** ] ページ (スナップショット レプリケーションおよびトランザクション パブリケーション、および SQL Server 2005 より前のバージョンを実行しているパブリッシャーのマージ パブリケーション) 用では、サブスクライバーがスナップショット ファイルのファイル転送プロトコル (FTP) を介してをダウンロードできるかどうかを指定することができます。  
  
-    **FTP スナップショットとインターネット** (SQL Server 2005 以降を実行しているパブリッシャーからのマージ パブリケーション) 用のページでは、サブスクライバーが ftp でスナップショット ファイルをダウンロードするかどうかと、サブスクライバーが HTTPS でサブスクリプションを同期するかどうかを指定することができます。  
  
-   **[サブスクリプション オプション]** ページ。このページでは、すべてのサブスクリプションに適用されるさまざまなオプションを設定できます。 利用できるオプションは、パブリケーションの種類によって異なります。  
  
-   **[パブリケーション アクセス リスト]** ページ。このページでは、パブリケーションにアクセスできるログインやグループを指定できます。  
  
-   **[エージェント セキュリティ]** ページ。このページでは、エージェントの実行やレプリケーション トポロジ内のコンピューターへの接続に使用されるアカウントの設定にアクセスできます。この設定を使用するエージェントは、すべてのパブリケーションのスナップショット エージェント、すべてのトランザクション パブリケーションのログ リーダー エージェント、およびキュー更新サブスクリプションを許可するトランザクション パブリケーションのキュー リーダー エージェントです。  
  
-    **データ パーティション** (SQL Server 2005 以降を実行しているパブリッシャーからのマージ パブリケーション) 用のページでは、いずれかが使用できない場合、パラメーター化されたフィルターを使用してパブリケーションに対するサブスクライバーがスナップショットを要求できるかどうかを指定することができます。 また、1 つ以上のパーティションのスナップショットを 1 回生成したり、スケジュールによって定期的に生成したりすることもできます。  
  
#### アーティクルのプロパティを表示および変更するには  
  
1.   **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでは、アーティクルを選択し、をクリックし、 **アーティクルのプロパティ**します。  
  
2.  プロパティの変更を適用するアーティクルを選択します。  
  
    -   をクリックして **設定のプロパティの強調表示されている \< ObjectType> 記事** を起動する、 **アーティクルのプロパティ - \< ObjectName>** ] ダイアログ ボックス。 プロパティのオブジェクト ペインで強調表示されているオブジェクトだけにこのダイアログ ボックスで行われた変更が適用される、 **記事** ページです。  
  
    -   をクリックして **プロパティをすべての設定 \< ObjectType> 記事**, を起動するには、 **すべてのプロパティ \< ObjectType> 記事** ] ダイアログ ボックス。 プロパティこのダイアログ ボックスで行った変更は、オブジェクト] ペインで、その種類のすべてのオブジェクトに適用されます、 **記事** ] ページで、パブリケーション用に選択されていないものなどです。  
  
        > [!NOTE]  
        >  行われたプロパティの変更、 **すべてプロパティ \< ObjectType> 記事** ダイアログ ボックスの上書きで以前に行われた、 **アーティクルのプロパティ - \< ObjectName>** ] ダイアログ ボックス。 たとえば、あるオブジェクトの種類のすべてのアーティクルに対して複数の既定を設定し、かつそれぞれのオブジェクトに対してプロパティを設定する場合には、最初にすべてのアーティクルに対する既定を設定します。 次に、それぞれのオブジェクトに対してプロパティを設定します。  
  
3.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
4.  をクリックして **OK** 上、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 アーティクルのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更および取得できます。 使用するストアド プロシージャは、アーティクルが属するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに属するアーティクルのプロパティを表示するには  
  
1.  実行 [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md), 、パブリケーションの名前を指定する、 **@publication** パラメーターとのアーティクルの名前、 **@article** パラメーター。 **@article**を指定しない場合、パブリケーションのすべてのアーティクルに関する情報が返されます。  
  
2.  実行 [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) ベース テーブルで使用できるすべての列を一覧表示するテーブル アーティクルに対してです。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに属するアーティクルのプロパティを変更するには  
  
1.  実行 [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md), で変更されているアーティクルのプロパティを指定する、 **@property** パラメーターとでは、このプロパティの新しい値、 **@value** パラメーター。  
  
    > [!NOTE]  
    >  変更は、新しいスナップショットの生成を必要とする場合は、値も指定する必要があります **1** の **@force_invalidate_snapshot**, の値を指定する、変更は、サブスクライバーを再初期化する必要がある場合もする必要があります **1** の **@force_reinit_subscription**します。 詳細プロパティについて、変更されると、新しいスナップショット パブリケーションまたは再初期化を参照してください。 を必要と [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
#### マージ パブリケーションに属するアーティクルのプロパティを表示するには  
  
1.  実行 [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md), 、パブリケーションの名前を指定する、 **@publication** パラメーターとのアーティクルの名前、 **@article** パラメーター。 これらのパラメーターを指定しない場合、パブリケーションまたはパブリッシャーのすべてのアーティクルに関する情報が返されます。  
  
2.  実行 [sp_helpmergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql.md) ベース テーブルで使用できるすべての列を一覧表示するテーブル アーティクルに対してです。  
  
#### マージ パブリケーションに属するアーティクルのプロパティを変更するには  
  
1.  実行 [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), で変更されているアーティクルのプロパティを指定する、 **@property** パラメーターとでは、このプロパティの新しい値、 **@value** パラメーター。  
  
    > [!NOTE]  
    >  変更は、新しいスナップショットの生成を必要とする場合は、値も指定する必要があります **1** の **@force_invalidate_snapshot**, の値を指定する、変更は、サブスクライバーを再初期化する必要がある場合もする必要があります **1** の **@force_reinit_subscription**します。 詳細プロパティについて、変更されると、新しいスナップショット パブリケーションまたは再初期化を参照してください。 を必要と [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 パブリッシュされたアーティクルのプロパティを取得するトランザクション レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_1.sql)]  
  
 パブリッシュされたアーティクルのスキーマ オプションを変更するトランザクション レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_2.sql)]  
  
 パブリッシュされたアーティクルのプロパティを取得するマージ レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_3.sql)]  
  
 パブリッシュされたアーティクルの競合検出の設定を変更するマージ レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_4.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 アーティクルのプロパティは、レプリケーション管理オブジェクト (RMO) を使用してプログラムから変更できます。 アーティクルのプロパティを表示または変更する際に使用する RMO のクラスは、アーティクルが属しているパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションに属しているアーティクルのプロパティを表示または変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransArticle> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。  
  
6.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.TransArticle> プロパティを設定できます。  
  
7.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
#### マージ パブリケーションに属しているアーティクルのプロパティを表示または変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeArticle> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。  
  
6.  (省略可能)プロパティを変更するには、いずれかの新しい値を設定、 <xref:Microsoft.SqlServer.Replication.MergeArticle> プロパティを設定できます。  
  
7.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、マージ アーティクルに変更を加え、アーティクル用のビジネス ロジック ハンドラーを指定しています。  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## 参照  
 [マージ アーティクルのビジネス ロジック ハンドラーの実装](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [マージ レプリケーションの競合検出および解決の詳細](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  