---
title: "キュー更新の競合解決オプションの設定 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "競合解決 [SQL Server レプリケーション], キュー更新サブスクリプション"
  - "キュー更新サブスクリプション [SQL Server レプリケーション]"
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# キュー更新の競合解決オプションの設定 (SQL Server Management Studio)
  競合のキューで、更新サブスクリプションをサポートするパブリケーションの解決オプションを設定、 **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### キュー更新の競合解決オプションを設定するには  
  
1.   **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスで、次のいずれかの値、 **競合解決ポリシー** オプション。  
  
    -   **[パブリッシャーの変更を保持します]**  
  
    -   **[サブスクライバーの変更を保持します]**  
  
    -   **[サブスクリプションを再初期化します]**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## 参照  
 [Enable Updating Subscriptions for Transactional Publications](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [キュー更新における競合の検出と解決](../../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md)  
  
  