---
title: "レプリケーションのデータベースの有効化 (SQL Server Management Studio) | Microsoft Docs"
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
  - "データベース [SQL Server レプリケーション]"
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# レプリケーションのデータベースの有効化 (SQL Server Management Studio)
  固定サーバー ロール **sysadmin** のメンバーがパブリケーションの新規作成ウィザードでパブリケーションを作成すると、レプリケーションのデータベースが暗黙的に有効になります。 メンバー、 **sysadmin** 固定サーバー ロールも有効にできますレプリケーション用のデータベース、明示的にようにのメンバー、 **db_owner** 固定データベース ロールは、そのデータベースの 1 つまたは複数のパブリケーションを作成できます。 データベースを明示的に有効にするには、 **パブリケーション データベース** のページ、 **パブリッシャーのプロパティ - \< Publisher>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
### レプリケーションのデータベースを有効化するには  
  
1.   **パブリケーション データベース** のページ、 **パブリッシャーのプロパティ - \< Publisher>** ダイアログ ボックスで、 **トランザクション** や **マージ** をレプリケートする各データベースのチェック ボックスです。 スナップショット レプリケーションのデータベースを有効にするには、 **[トランザクション]** を選択します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  