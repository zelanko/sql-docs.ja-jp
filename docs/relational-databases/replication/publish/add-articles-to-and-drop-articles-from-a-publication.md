---
title: "パブリケーションでのアーティクルの追加または削除 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アーティクル [SQL Server レプリケーション]、ドロップ"
  - "アーティクルの削除"
  - "アーティクルのドロップ"
  - "アーティクルの追加"
  - "アーティクル [SQL Server レプリケーション]、追加"
ms.assetid: d5a3e536-62d2-4473-a178-877ba52f7d7f
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# パブリケーションでのアーティクルの追加または削除 (SQL Server Management Studio)
  パブリケーションの新規作成ウィザードでパブリケーションを作成する場合は、最初にアーティクルを追加します。 このウィザードの使用に関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md)します。  
  
 追加しにアーティクルを削除するパブリケーションを作成した後、 **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。 についての追加と削除に関する注意点は、次を参照してください。 [にアーティクルを追加し、既存のパブリケーションからアーティクルを削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)します。  
  
### パブリケーションの作成後にアーティクルを追加するには  
  
1.   **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** 、ダイアログ ボックスをオフ、 **ショー、リスト内のオブジェクトにのみチェック** チェック ボックスをオンします。 これにより、パブリケーション データベース内のパブリッシュされていないオブジェクトも表示されるようになります。  
  
2.  追加する各アーティクルの隣にあるチェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### アーティクルを削除するには  
  
1.   **記事** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、チェック ボックスをオフの横のチェック ボックスを削除する各アーティクルです。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## 参照  
 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  