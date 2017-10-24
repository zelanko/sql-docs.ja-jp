---
title: "データベース オブジェクトの削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bcd4f3254cfd6b648411ae6fb9c364fa7017913
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-3-1---deleting-database-objects"></a>レッスン 3-1-データベース オブジェクトの削除
このチュートリアルのすべてのトレースを削除するには、データベースを削除します。 ただし、このトピックでは、チュートリアルを進みながら実行したすべての操作を元に戻す手順を実行します。  
  
### <a name="removing-permissions-and-objects"></a>権限とオブジェクトの削除  
  
1.  オブジェクトを削除する前に、適切なデータベースで作業していることを確認します。  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  ストアド プロシージャに対する `REVOKE` の実行権限を削除するには、 `Mary` ステートメントを使用します。  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  `DROP` データベースに対する `Mary` のアクセス権限を削除するには、 `TestData` ステートメントを使用します。  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  `DROP` が `Mary` のこのインスタンスにアクセスする権限を削除するには、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]ステートメントを使用します。  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  ストアド プロシージャ `DROP` を削除するには、 `pr_Names`ステートメントを使用します。  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  ビュー `DROP` を削除するには、 `vw_Names`ステートメントを使用します。  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  `DELETE` テーブルからすべての行を削除するには、 `Products` ステートメントを使用します。  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  `DROP` テーブルを削除するには、 `Products` ステートメントを使用します。  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. データベースでの作業中は、 `TestData` データベースを削除できません。したがって、まずコンテキストを他のデータベースに切り替えてから、 `DROP` ステートメントを使用して `TestData` データベースを削除します。  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
これで、「 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの記述」のチュートリアルを終了します。 このチュートリアルは概要であり、使用できるステートメントのすべてのオプションが記載されているわけではありません。 効率のよいデータベース構造を設計して作成し、セキュリティ保護されたデータ アクセスを構成するには、このチュートリアルで示したデータベースよりも複雑なデータベースが必要です。  
  
## <a name="return-to-sql-server-tools-portal"></a>SQL Server ツールのポータルに戻る  
[チュートリアル : Transact-SQL ステートメントの作成](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>参照  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
[DROP USER (Transact-SQL)](../t-sql/statements/drop-user-transact-sql.md)  
[DROP LOGIN (Transact-SQL)](../t-sql/statements/drop-login-transact-sql.md)  
[DROP PROCEDURE &#40;Transact-SQL&#41;](../t-sql/statements/drop-procedure-transact-sql.md)  
[DROP VIEW (Transact-SQL)](../t-sql/statements/drop-view-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../t-sql/statements/delete-transact-sql.md)  
[DROP TABLE (Transact-SQL)](../t-sql/statements/drop-table-transact-sql.md)  
[DROP DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/drop-database-transact-sql.md)  
  
  
  

