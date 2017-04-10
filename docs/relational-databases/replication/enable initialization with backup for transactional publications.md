---
title: "トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "manual subscription initialization [SQL Server replication]"
  - "subscriptions [SQL Server replication], initializing"
  - "サブスクリプションの初期化 [SQL Server レプリケーション], スナップショットなし"
  - "トランザクション レプリケーション, バックアップと復元"
  - "バックアップ [SQL Server レプリケーション], トランザクション レプリケーション"
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする (SQL Server Management Studio)
  バックアップからトランザクション パブリケーションに対してサブスクリプションを初期化するには、パブリケーションを有効にしてバックアップからの初期化を許可し、サブスクリプションの作成時にバックアップ情報を指定します。  
  
-   パブリケーションを有効にする、 **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   ストアド プロシージャとバックアップの情報を指定 [sp_addsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)します。 必要なパラメーターの詳細については **sp_addsubscription**, を参照してください [バックアップ & #40; からトランザクション パブリケーションに対するサブスクリプションの初期化レプリケーション TRANSACT-SQL プログラミングと #41;](../../relational-databases/replication/initialize a transactional subscription from a backup.md)します。  
  
### バックアップを使用した初期化を有効にするには  
  
1.   **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ - \< パブリケーション>** ダイアログ ボックスの値を **True** の **バックアップ ファイルからの初期化を許可する** オプション。  
  
## 参照  
 [スナップショットを使用しないトランザクション サブスクリプションの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  