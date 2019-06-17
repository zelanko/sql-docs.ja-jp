---
title: アーティクルの種類の指定 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- stored procedures [SQL Server replication], publishing
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b90fb6d2a85d30179e630d292f8fc11250958344
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261770"
---
# <a name="specify-article-types-replication-transact-sql-programming"></a>アーティクルの種類の指定 (レプリケーション Transact-SQL プログラミング)
  レプリケーションにおける既定の種類のアーティクルはテーブル アーティクルですが、ビュー、ストアド プロシージャ、ユーザー定義関数、ストアド プロシージャ実行など、他のデータベース オブジェクトもパブリッシュできます。 レプリケーション ストアド プロシージャを使用することで、アーティクルの定義時にプログラムでアーティクルの種類を指定できます。 使用するストアド プロシージャは、レプリケーションの種類とアーティクルの種類に応じて異なります。  
  
> [!NOTE]  
>  テーブル、ビュー、ストアド プロシージャのアーティクルを定義する際にスキーマのみを指定すると、そのオブジェクトの定義のみをレプリケートするように指定されます。  
  
### <a name="to-publish-a-table-article-in-a-transactional-or-snapshot-publication"></a>トランザクション パブリケーションまたはスナップショット パブリケーションでテーブル アーティクルをパブリッシュするには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。 **@type** に次のいずれかの値を指定して、アーティクルの種類を定義します。  
  
    -   **logbased** - ログベース テーブル アーティクル。トランザクション レプリケーションとスナップショット レプリケーションの既定の設定です。 レプリケーションでは、行方向のフィルター選択に使用されるストアド プロシージャと、列方向にフィルター選択されるアーティクルを定義するビューが自動的に生成されます。  
  
    -   **logbased manualfilter** - ログベースの、行方向にフィルター選択されるアーティクル。行方向のフィルター選択に使用されるストアド プロシージャは、ユーザーが手動で作成して定義し、 **@filter** を実行します。 詳細については、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
    -   **logbased manualview** - ログベースの、列方向にフィルター選択されるアーティクル。列方向にフィルター選択されるアーティクルを定義するビューは、ユーザーが作成して定義し、 **@sync_object** を実行します。 詳細については、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) 」および「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」を参照してください。  
  
    -   **logbased manualboth** - ログベースの、行方向と列方向にフィルター選択されるアーティクル。行方向のフィルター選択に使用されるストアド プロシージャと、列方向にフィルター選択されるアーティクルを定義するビューは、どちらもユーザーが作成して定義し、それぞれ **@filter** 」および「 **@sync_object** に指定します。 詳細については、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) 」および「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」を参照してください。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳細については、「 [Define an Article](define-an-article.md)」を参照してください。  
  
2.  **logbased manualboth** および **logbased manualfilter** のアーティクルの場合、 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を実行して、行方向にフィルター選択されるアーティクル用のフィルター選択ストアド プロシージャを生成します。 詳しくは、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
3.  **logbased manualboth**、 **logbased manualview**、および **logbased manualfilter** のアーティクルの場合、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) を実行して、列方向にフィルター選択されるアーティクルを定義するビューを生成します。 詳細については、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」をご覧ください。  
  
### <a name="to-publish-a-view-or-indexed-view-article-in-a-transactional-or-snapshot-publication"></a>トランザクション パブリケーションまたはスナップショット パブリケーションでビュー アーティクルまたはインデックス付きビュー アーティクルをパブリッシュするには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。 **@type** に次のいずれかの値を指定して、アーティクルの種類を定義します。  
  
    -   **indexed view logbased** - ログベースのインデックス付きビュー アーティクル。 レプリケーションでは、行方向のフィルター選択に使用されるストアド プロシージャと、列方向にフィルター選択されるアーティクルを定義するビューが自動的に生成されます。  
  
    -   **view schema only** - スキーマのみのビュー アーティクル。 ベース テーブルもレプリケートする必要があります。  
  
    -   **indexed view schema only** - スキーマのみのインデックス付きビュー アーティクル。 ベース テーブルもレプリケートする必要があります。  
  
    -   **indexed view logbased manualfilter** - ログベースの、行方向にフィルター選択されるインデックス付きビュー アーティクル。行方向のフィルター選択に使用されるストアド プロシージャは、ユーザーが手動で作成して定義し、 **@filter** を実行します。 詳しくは、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
    -   **indexed view logbased manualview** - ログベースのフィルター選択されるインデックス付きビュー アーティクル。列方向にフィルター選択されるアーティクルを定義するビューは、ユーザーが作成して定義し、 **@sync_object** を実行します。 詳細については、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) 」および「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」を参照してください。  
  
    -   **indexed view logbased manualboth** - ログベースの、フィルター選択されるインデックス付きビュー アーティクル。行方向のフィルター選択に使用されるストアド プロシージャと、列方向にフィルター選択されるアーティクルを定義するビューは、どちらもユーザーが作成して定義し、それぞれ **@filter** 」および「 **@sync_object** に指定します。 詳細については、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) 」および「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」を参照してください。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳細については、「 [Define an Article](define-an-article.md)」を参照してください。  
  
2.  **logbased manualboth** および **logbased manualfilter** のアーティクルの場合、 [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) を実行して、行方向にフィルター選択されるアーティクル用のフィルター選択ストアド プロシージャを生成します。 詳しくは、「 [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md)」をご覧ください。  
  
3.  **logbased manualboth**、 **logbased manualview**、および **logbased manualfilter** のアーティクルの場合、 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) を実行して、列方向にフィルター選択されるアーティクルを定義するビューを生成します。 詳細については、「 [Define and Modify a Column Filter](define-and-modify-a-column-filter.md)」をご覧ください。  
  
### <a name="to-publish-a-stored-procedure-stored-procedure-execution-or-user-defined-function-article-in-a-transactional-or-snapshot-publication"></a>トランザクション パブリケーションまたはスナップショット パブリケーションでストアド プロシージャ、ストアド プロシージャ実行、またはユーザー定義関数のアーティクルをパブリッシュするには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)を実行します。 **@type** に次のいずれかの値を指定して、アーティクルの種類を定義します。  
  
    -   **proc schema only** - スキーマのみのストアド プロシージャ アーティクル。  
  
    -   **proc exec** - アーティクルのすべてのサブスクライバーにストアド プロシージャの実行をレプリケートします。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」をご覧ください。  
  
    -   **serializable proc exec** - シリアル化可能なトランザクションのコンテキスト内で実行される場合にのみ、ストアド プロシージャの実行をレプリケートします。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」をご覧ください。  
  
    -   **func schema only** - スキーマのみのユーザー定義関数アーティクル。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
### <a name="to-publish-a-table-or-view-article-in-a-merge-publication"></a>マージ パブリケーションでテーブル アーティクルまたはビュー アーティクルをパブリッシュするには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。 **@type** に次のいずれかの値を指定して、アーティクルの種類を定義します。  
  
    -   **table** - テーブル アーティクル。  
  
    -   **indexed view schema only** - スキーマのみのインデックス付きビュー アーティクル。  
  
    -   **view schema only** - スキーマのみのビュー アーティクル。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
### <a name="to-publish-a-stored-procedure-or-user-defined-function-article-in-a-merge-publication"></a>マージ パブリケーションにストアド プロシージャまたはユーザー定義関数のアーティクルをパブリッシュするには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)を実行します。 **@type** に次のいずれかの値を指定して、アーティクルの種類を定義します。  
  
    -   **func schema only** - スキーマのみのユーザー定義関数アーティクル。  
  
    -   **proc schema only** - スキーマのみのストアド プロシージャ アーティクル。  
  
     これにより、パブリケーションに新しいアーティクルが定義されます。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [データとデータベース オブジェクトのパブリッシュ](publish-data-and-database-objects.md)  
  
  
