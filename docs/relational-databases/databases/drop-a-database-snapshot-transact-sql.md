---
title: データベース スナップショットの削除 (Transact-SQL) | Microsoft Docs
description: Transact-SQL を使用してデータベース スナップショットを削除する方法について説明します。これにより、SQL Server のスナップショットとスナップショットで使用されるスパース ファイルが削除されます。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ae40c8d9b4a93ff1f035953207caae5addb56b2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756163"
---
# <a name="drop-a-database-snapshot-transact-sql"></a>データベース スナップショットの削除 (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  データベース スナップショットを削除すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータベース スナップショットが削除され、そのスナップショットで使用されていたスパース ファイルが削除されます。 データベース スナップショットを削除すると、そのデータベース スナップショットに対するすべてのユーザー接続が終了します。  
  
## <a name="security"></a>セキュリティ  
  
###  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 DROP DATABASE 権限を持つすべてのユーザーが、データベース スナップショットを削除できます。  
  
##  <a name="how-to-drop-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> データベース スナップショットを削除する方法 (Transact-SQL の使用)  
 **データベース スナップショットを削除するには**  
  
1.  削除するデータベース スナップショットを特定します。 データベース内のスナップショットは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で参照できます。 詳細については、「 [データベース スナップショットの表示 &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)で参照できます。  
  
2.  削除するデータベース スナップショットの名前を指定して [DROP DATABASE](../../t-sql/statements/drop-database-transact-sql.md) ステートメントを実行します。 構文は次のとおりです。  
  
     DROP DATABASE *database_snapshot_name* [ **,** ...*n* ]  
  
     ここで、 *database_snapshot_name* は、削除するデータベース スナップショットの名前です。  
  
####  <a name="example-transact-sql"></a><a name="TsqlExample"></a> 例 (Transact-SQL)  
 この例では、データベース スナップショット SalesSnapshot0600 を削除します。これは元のデータベースには影響しません。  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 SalesSnapshot0600 へのユーザー接続がすべて終了し、スナップショットで使用される NTFS ファイル システムのスパース ファイルがすべて削除されます。  
  
> [!NOTE]  
>  データベース スナップショットによるスパース ファイルの使用の詳細については、「 [データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)で参照できます。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [データベース スナップショットの作成 &#40;Transact-SQL&#41;](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [データベース スナップショットの表示 &#40;SQL Server&#41;](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [データベースをデータベース スナップショットに戻す](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
  
## <a name="see-also"></a>参照  
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  
