---
title: "アーティクルの削除 | Microsoft Docs"
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
  - "articles [SQL Server replication], dropping"
  - "sp_droparticle"
  - "sp_dropmergearticle"
  - "deleting articles"
  - "removing articles"
  - "アーティクルのドロップ"
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# アーティクルの削除
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[tsql](../../../includes/tsql-md.md)] またはレプリケーション管理オブジェクト (RMO) を使用して、アーティクルを削除する方法について説明します。 するアーティクルを削除して、新しいスナップショット パブリケーションまたはサブスクリプションの再初期化は、必要なアーティクルを削除するかどうかの条件については、次を参照してください。 [にアーティクルを追加し、既存のパブリケーションからアーティクルを削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)します。  
  
 **このトピックの内容**  
  
-   **アーティクルを削除するために使用するもの:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 アーティクルは、レプリケーション ストアド プロシージャを使用してプログラムで削除できます。 使用するストアド プロシージャは、アーティクルが属するパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションからアーティクルを削除するには  
  
1.  実行 [sp_droparticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md) 指定された、アーティクルを削除する **@article**, で指定されたパブリケーション **@publication**します。 値を指定して **1** の **@force_invalidate_snapshot**します。  
  
2.  (省略可) パブリッシュされたオブジェクトをデータベースから完全に削除するには、パブリッシャーのパブリケーション データベースに対して `DROP <objectname>` コマンドを実行します。  
  
#### アーティクルをマージ パブリケーションから削除するには  
  
1.  実行 [sp_dropmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md) 指定された、アーティクルを削除する **@article**, で指定されたパブリケーション **@publication**します。 必要に応じて、指定の値 **1** の **@force_invalidate_snapshot** の **1** の **@force_reinit_subscription**します。  
  
2.  (省略可) パブリッシュされたオブジェクトをデータベースから完全に削除するには、パブリッシャーのパブリケーション データベースに対して `DROP <objectname>` コマンドを実行します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、トランザクション パブリケーションからアーティクルを削除します。 この変更には、既存のスナップショットの値が無効になるため **1** が指定されて、 **@force_invalidate_snapshot** パラメーター。  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article AS sysname;  
SET @publication = N'AdvWorksProductTran';   
SET @article = N'Product';   
  
-- Drop the transactional article.  
USE [AdventureWorks]  
EXEC sp_droparticle   
  @publication = @publication,   
  @article = @article,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
 次の例では、マージ パブリケーションから 2 つのアーティクルを削除します。 これらの変更には、既存のスナップショットの値が無効になるため **1** が指定されて、 **@force_invalidate_snapshot** パラメーター。  
  
```  
DECLARE @publication AS sysname;  
DECLARE @article1 AS sysname;  
DECLARE @article2 AS sysname;  
SET @publication = N'AdvWorksSalesOrdersMerge';  
SET @article1 = N'SalesOrderDetail';   
SET @article2 = N'SalesOrderHeader';   
  
-- Remove articles from a merge publication.  
USE [AdventureWorks]  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article1,  
  @force_invalidate_snapshot = 1;  
EXEC sp_dropmergearticle   
  @publication = @publication,   
  @article = @article2,  
  @force_invalidate_snapshot = 1;  
GO  
```  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 アーティクルは、レプリケーション管理オブジェクト (RMO) を使用してプログラムから削除できます。 アーティクルを削除する際に使用する RMO のクラスは、アーティクルが属しているパブリケーションの種類によって異なります。  
  
#### スナップショット パブリケーションまたはトランザクション パブリケーションのアーティクルを削除するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.TransArticle> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをアーティクルが存在することを確認します。 このプロパティの値が **false**の場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> メソッドです。  
  
7.  すべての接続を閉じます。  
  
#### マージ パブリケーションのアーティクルを削除するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeArticle> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  チェック、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをアーティクルが存在することを確認します。 このプロパティの値が **false**の場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。  
  
6.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> メソッドです。  
  
7.  すべての接続を閉じます。  
  
## 参照  
 [既存のパブリケーションでのアーティクルの追加および削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  