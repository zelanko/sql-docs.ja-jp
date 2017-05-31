---
title: "データベース スナップショットの表示 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c11dd41a0c6077ff1d34b6a1f2b348fed87d92e5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="view-a-database-snapshot-sql-server"></a>データベース スナップショットの表示 (SQL Server)
  このトピックでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベース スナップショットを表示する方法について説明します。  
  
> [!NOTE]  
>  データベース スナップショットの作成、復元、削除には、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用する必要があります。  
  
 **このトピックの内容**  
  
-   **データベース スナップショットの確認に使用するツール:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **データベース スナップショットを確認するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開します。  
  
3.  **[データベース スナップショット]**を展開し、表示するスナップショットを選択します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **データベース スナップショットを確認するには**  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスのデータベース スナップショットの一覧を表示するには、 **sys.databases** カタログ ビューの [source_database_id](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 列で NULL 以外の値に対してクエリを実行します。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベース スナップショットの作成 &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [データベースをデータベース スナップショットに戻す](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [データベース スナップショットの削除 &#40;Transact-SQL&#41;](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
