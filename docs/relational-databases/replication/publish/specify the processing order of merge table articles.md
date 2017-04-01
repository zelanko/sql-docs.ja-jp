---
title: "マージ テーブル アーティクルの処理順序の指定 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "アーティクル [SQL Server レプリケーション], 処理順序"
  - "マージ レプリケーション [SQL Server レプリケーション], アーティクルの処理順序"
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ テーブル アーティクルの処理順序の指定 (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションでは、同期処理中にアーティクルをマージ エージェントで処理する順序を指定できます。 この順序は、レプリケーションのストアド プロシージャを使用して、アーティクル作成時に各アーティクルに対してプログラムから割り当てることができます。 アーティクルは、最も小さい値から最も大きい値の順序で処理されます。 2 つのアーティクルの値が同じ場合、それらは同時に処理されます。 詳細については、次を参照してください。 [アーティクルを指定して、処理順序のマージ](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)します。  
  
### 新しいマージ アーティクルの処理順序を指定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 アーティクルの処理順序を表す整数値を指定して **@processing_order**します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
    > [!NOTE]  
    >  処理順序を指定してアーティクルを作成する場合は、アーティクルの順序を表す値の間に、ある程度の間隔を設けるようにしてください。 こうすることで、後で、新しい値を設定するときに作業が楽になります。 たとえば、処理順序を指定する必要がある 3 つのアーティクルがあれば、設定の値 **@processing_order** 10、20、および 30 ではなく 1、2、および 3 にそれぞれします。  
  
### マージ アーティクルの処理順序を変更するには  
  
1.  アーティクルの処理順序を確認するのには、実行 [sp_helpmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) 値をメモ **processing_order** 結果に設定します。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **processing_order** の **@property** の処理順序を表す整数値と **@value**します。  
  
## 参照  
 [マージ アーティクルの処理順序の指定](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  