---
title: "スナップショットの形式の指定 (SQL Server Management Studio) | Microsoft Docs"
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
  - "スナップショット [SQL Server レプリケーション], 形式"
  - "スナップショット レプリケーション [SQL Server], 形式"
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# スナップショットの形式の指定 (SQL Server Management Studio)
  スナップショットの形式を指定する、 **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### スナップショットの形式を指定するには  
  
1.   **スナップショット** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、 **ネイティブ SQL Server - すべてのサブスクライバーは SQL Server を実行しているサーバーである必要があります** または **文字のかどうかパブリッシャーまたはサブスクライバーが実行されていない SQL Server は必須**します。  
  
    > [!NOTE]  
    >  このパブリケーションで [!INCLUDE[ssEW](../../../includes/ssew-md.md)] データベースまたは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のデータベースへのサブスクリプションをサポートする必要がある場合を除き、ネイティブ形式を選択することをお勧めします。  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## 参照  
 [スナップショットのプロパティと #40; 構成します。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [パブリケーションおよびアーティクルのプロパティの変更](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [スナップショットを使用したサブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  