---
title: "パブリケーション プロパティの表示および変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レプリケーション プロパティの表示"
  - "レプリケーション プロパティの変更、アーティクル"
  - "アーティクル [SQL Server レプリケーション]、変更"
  - "パブリケーション [SQL Server レプリケーション]、プロパティ"
  - "アーティクル [SQL Server レプリケーション]、プロパティ"
  - "レプリケーション プロパティの変更、パブリケーション"
  - "パブリケーション [SQL Server レプリケーション]、変更"
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# パブリケーション プロパティの表示および変更
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリケーションのプロパティを表示および変更する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
-   **パブリケーションのプロパティを表示または変更するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   パブリケーションの作成後には変更できないプロパティや、パブリケーションへのサブスクリプションがある場合には変更できないプロパティもあります。 変更できないプロパティは、読み取り専用として表示されます。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   パブリケーションの作成後、プロパティの変更によっては新しいスナップショットが必要となります。 パブリケーションにサブスクリプションが含まれている場合、変更によっては、すべてのサブスクリプションを再初期化する必要もあります。 詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) と [にアーティクルを追加し、既存のパブリケーションからアーティクルを削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 [パブリケーションのプロパティの変更を表示および、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスで使用可能な [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] およびレプリケーション モニターします。 レプリケーション モニターの起動方法については、次を参照してください。 [レプリケーション モニターを起動](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)します。  
  
  **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスには、次のページが含まれています。  
  
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
  
#### Management Studio でパブリケーションのプロパティを表示および変更するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  パブリケーションを右クリックし、をクリックして **プロパティ**です。  
  
4.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
#### レプリケーション モニターでパブリケーションのプロパティを表示および変更するには  
  
1.  レプリケーション モニターの左ペインでパブリッシャー グループを展開し、パブリッシャーを展開します。  
  
2.  パブリケーションを右クリックし、をクリックして **プロパティ**です。  
  
3.  必要に応じてプロパティを変更し、 **[OK]**をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリケーションのプロパティは、レプリケーションのストアド プロシージャを使用して、プログラムから変更および取得できます。 どのストアド プロシージャを使用するかは、パブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのプロパティを表示するには  
  
1.  実行 [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), 、パブリケーションの名前を指定する、 **@publication** パラメーター。 このパラメーターを指定しなかった場合、パブリッシャーのすべてのパブリケーションの情報が返されます。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのプロパティを変更するには  
  
1.  実行 [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), に変更するパブリケーションのプロパティを指定する、 **@property** パラメーターとでは、このプロパティの新しい値、 **@value** パラメーター。  
  
    > [!NOTE]  
    >  値を指定する、変更には、新しいスナップショットの生成が必要とする場合もする必要があります **1** の **@force_invalidate_snapshot**, 、変更は、サブスクライバーを再初期化する必要がある場合は、値を指定する必要があります **1** の **@force_reinit_subscription**します。 詳細については、プロパティ、変更されると、必要に新しいスナップショットや、再初期化を参照してください [変更パブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)です。  
  
#### マージ パブリケーションのプロパティを表示するには  
  
1.  実行 [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), 、パブリケーションの名前を指定する、 **@publication** パラメーター。 このパラメーターを指定しなかった場合、パブリッシャーのすべてのパブリケーションの情報が返されます。  
  
#### マージ パブリケーションのプロパティを変更するには  
  
1.  実行 [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), で変更されているパブリケーションのプロパティを指定する、 **@property** パラメーターとでは、このプロパティの新しい値、 **@value** パラメーター。  
  
    > [!NOTE]  
    >  値を指定する、変更には、新しいスナップショットの生成が必要とする場合もする必要があります **1** の **@force_invalidate_snapshot**, 、変更は、サブスクライバーを再初期化する必要がある場合は、値を指定する必要があります **1** の **@force_reinit_subscription** プロパティについて、変更されると、新しいスナップショット パブリケーションまたは再初期化を参照してください。 を必要と [を変更するパブリケーションとアーティクルのプロパティ](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
#### スナップショットのプロパティを表示するには  
  
1.  実行 [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), 、パブリケーションの名前を指定する、 **@publication** パラメーター。  
  
#### スナップショットのプロパティを変更するには  
  
1.  実行 [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), 、適切なスナップショットのパラメーターの新しいスナップショットのプロパティの 1 つ以上を指定します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 パブリケーションのプロパティを取得するトランザクション レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 パブリケーションのスキーマ レプリケーションを無効化するトランザクション レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 パブリケーションのプロパティを取得するマージ レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 パブリケーションのスキーマ レプリケーションを無効化するマージ レプリケーションの例を、次に示します。  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用して、パブリケーションの変更とそのプロパティへのアクセスをプログラムから実行できます。 パブリケーション プロパティの表示と変更に使用する RMO クラスは、パブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのプロパティを表示または変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransPublication> 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  (省略可) プロパティを変更するには、設定可能なプロパティに新しい値を設定します。 論理 AND 演算子を使用して (**&** Microsoft Visual C# の場合と **と** Microsoft Visual Basic で) かどうかを指定された <xref:Microsoft.SqlServer.Replication.PublicationAttributes> の値を設定、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティです。 包括的論理和演算子を使用して (**|** Visual C# の場合と **または** Visual Basic で) と排他的論理和演算子 (**^** Visual C# の場合と **Xor** Visual Basic で) を変更する、 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> の値、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティです。  
  
5.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
#### マージ パブリケーションのプロパティを表示または変更するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergePublication> 設定、 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> と <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 、パブリケーション、およびセット プロパティを <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成された接続。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドが **false**を返す場合、手順 2. でパブリケーション プロパティを不適切に設定したか、パブリケーションが存在していません。  
  
4.  (省略可) プロパティを変更するには、設定可能なプロパティに新しい値を設定します。 論理 AND 演算子を使用して (**&** Visual C# の場合と **と** Visual Basic で) かどうかを指定された <xref:Microsoft.SqlServer.Replication.PublicationAttributes> の値を設定、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティです。 包括的論理和演算子を使用して (**|** Visual C# の場合と **または** Visual Basic で) と排他的論理和演算子 (**^** Visual C# の場合と **Xor** Visual Basic で) を変更する、 <xref:Microsoft.SqlServer.Replication.PublicationAttributes> の値、 <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> プロパティです。  
  
5.  (省略可能)値を指定した場合 **true** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, を呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドは、サーバーに変更をコミットします。 値を指定した場合 **false** の <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (既定値) の変更をサーバーには直ちに送信されます。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションにパブリケーション属性を設定します。 変更は明示的にサーバーに送られるまでキャッシュされます。  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 次の例では、マージ パブリケーションの DDL レプリケーションを無効にします。  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## 参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [パブリケーション データベースでのスキーマの変更](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [パブリケーションと #40; からの追加およびドロップ記事SQL Server Management Studio と #41 です。](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)   
 [情報を表示し、パブリケーションと #40; のタスクを実行レプリケーション モニターと #41 です。](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [アーティクルのプロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  