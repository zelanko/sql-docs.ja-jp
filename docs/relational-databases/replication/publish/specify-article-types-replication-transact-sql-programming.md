---
title: "アーティクルの種類の指定 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "パブリッシュ [SQL Server レプリケーション], ストアド プロシージャの実行"
  - "アーティクル [SQL Server レプリケーション]、トランザクション レプリケーション オプション"
  - "アーティクル [SQL Server レプリケーション]、マージ レプリケーション オプション"
  - "ストアド プロシージャ [SQL Server レプリケーション], パブリッシュ"
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# アーティクルの種類の指定 (レプリケーション Transact-SQL プログラミング)
  レプリケーションにおける既定の種類のアーティクルはテーブル アーティクルですが、ビュー、ストアド プロシージャ、ユーザー定義関数、ストアド プロシージャ実行など、他のデータベース オブジェクトもパブリッシュできます。 レプリケーション ストアド プロシージャを使用することで、アーティクルの定義時にプログラムでアーティクルの種類を指定できます。 使用するストアド プロシージャは、レプリケーションの種類とアーティクルの種類に応じて異なります。  
  
> [!NOTE]  
>  テーブル、ビュー、ストアド プロシージャのアーティクルを定義する際にスキーマのみを指定すると、そのオブジェクトの定義のみをレプリケートするように指定されます。  
  
### トランザクション パブリケーションまたはスナップショット パブリケーションでテーブル アーティクルをパブリッシュするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 次の値のいずれかを指定 **@type** のアーティクルの種類を定義します。  
  
    -   **logbased** -トランザクションおよびスナップショット レプリケーションの既定値は、テーブルのログベースのアーティクルです。 レプリケーションでは、行方向のフィルター選択に使用されるストアド プロシージャと、列方向にフィルター選択されるアーティクルを定義するビューが自動的に生成されます。  
  
    -   **logbased manualfilter** -ログベースの水平方向にフィルター選択された記事は、ここで水平方向のフィルター処理に使用するストアド プロシージャ手動で作成し、ユーザーによって定義されに指定された **@filter**します。 詳しくは、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
    -   **logbased manualview** -垂直方向にフィルター選択されたアーティクルを定義するビューを作成し、ユーザーによって定義およびに対して指定する、ログベースの垂直方向にフィルター選択された記事 **@sync_object**します。 詳細については、次を参照してください。 [静的行フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) と [列フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)します。  
  
    -   **logbased manualboth** -ログベースの水平方向および垂直方向にフィルター選択されるアーティクルの水平方向のフィルター処理や、垂直方向にフィルター選択されたアーティクルを定義するビュー、これ、両方のストアド プロシージャを作成し、ユーザーが定義されている場所と指定された **@filter** と **@sync_object**, 、それぞれします。 詳細については、次を参照してください。 [静的行フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) と [列フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)します。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.   **Logbased manualboth** と **logbased manualfilter** 記事、実行 [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) を水平方向にフィルター選択されたアーティクルのフィルター選択ストアド プロシージャを生成します。 詳しくは、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
3.   **Logbased manualboth**, 、**logbased manualview**, 、および **logbased manualfilter** 記事、実行 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 垂直方向にフィルター選択されたアーティクルを定義するビューを生成します。 詳しくは、「 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)」をご覧ください。  
  
### トランザクション パブリケーションまたはスナップショット パブリケーションでビュー アーティクルまたはインデックス付きビュー アーティクルをパブリッシュするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 次の値のいずれかを指定 **@type** のアーティクルの種類を定義します。  
  
    -   **ビュー 'logbased' をインデックス付き** -ログベースのインデックス付きビュー アーティクル。 レプリケーションでは、行方向のフィルター選択に使用されるストアド プロシージャと、列方向にフィルター選択されるアーティクルを定義するビューが自動的に生成されます。  
  
    -   **ビュー スキーマのみ** -スキーマのみのビュー アーティクル。 ベース テーブルもレプリケートする必要があります。  
  
    -   **インデックス付きビュー スキーマのみ** -スキーマのみのインデックス付きビュー アーティクル。 ベース テーブルもレプリケートする必要があります。  
  
    -   **logbased manualfilter のビューのインデックスを作成** -ログベースの水平方向にフィルター選択されたインデックス付きビューの記事、水平方向のフィルター処理に使用するストアド プロシージャ手動で作成し、ユーザーによって定義されに指定された **@filter**します。 詳しくは、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
    -   **インデックス ビュー logbased manualview** -垂直方向にフィルター選択されたアーティクルを定義するビューを作成し、ユーザーによって定義およびに対して指定する場所、ログベースのフィルター選択されたインデックス付きビュー アーティクル **@sync_object**します。 詳細については、次を参照してください。 [静的行フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) と [列フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)します。  
  
    -   **logbased manualboth のビューのインデックスを作成** -フィルタ リングの水平方向および垂直方向にフィルター選択されたアーティクルを定義するビューの使用両方、ストアド プロシージャを作成し、ユーザーによって定義し、に対して指定する場所、ログベースのフィルター選択されたインデックス付きビュー アーティクル **@filter** と **@sync_object**, 、それぞれします。 詳細については、次を参照してください。 [静的行フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md) と [列フィルター定義および変更](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)します。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
2.   **Logbased manualboth** と **logbased manualfilter** 記事、実行 [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) を水平方向にフィルター選択されたアーティクルのフィルター選択ストアド プロシージャを生成します。 詳しくは、「 [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
3.   **Logbased manualboth**, 、**logbased manualview**, 、および **logbased manualfilter** 記事、実行 [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) 垂直方向にフィルター選択されたアーティクルを定義するビューを生成します。 詳しくは、「 [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)」をご覧ください。  
  
### トランザクション パブリケーションまたはスナップショット パブリケーションでストアド プロシージャ、ストアド プロシージャ実行、またはユーザー定義関数のアーティクルをパブリッシュするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 次の値のいずれかを指定 **@type** のアーティクルの種類を定義します。  
  
    -   **proc スキーマのみ** -スキーマのみのストアド プロシージャ アーティクル。  
  
    -   **proc exec** -アーティクルのすべてのサブスクライバーにストアド プロシージャの実行をレプリケートします。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」を参照してください。  
  
    -   **serializable proc exec** のシリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、ストアド プロシージャの実行をレプリケートします。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」を参照してください。  
  
    -   **func スキーマのみ** -スキーマのみのユーザー定義関数アーティクル。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
### マージ パブリケーションでテーブル アーティクルまたはビュー アーティクルをパブリッシュするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 次の値のいずれかを指定 **@type** のアーティクルの種類を定義します。  
  
    -   **テーブル** -テーブル アーティクル。  
  
    -   **インデックス付きビュー スキーマのみ** -スキーマのみのインデックス付きビュー アーティクル。  
  
    -   **ビュー スキーマのみ** -スキーマのみのビュー アーティクル。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
### マージ パブリケーションにストアド プロシージャまたはユーザー定義関数のアーティクルをパブリッシュするには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 次の値のいずれかを指定 **@type** のアーティクルの種類を定義します。  
  
    -   **func スキーマのみ** -スキーマのみのユーザー定義関数アーティクル。  
  
    -   **proc スキーマのみ** -スキーマのみのストアド プロシージャ アーティクル。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
## 参照  
 [レプリケーション システム ストアド プロシージャの概念](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  