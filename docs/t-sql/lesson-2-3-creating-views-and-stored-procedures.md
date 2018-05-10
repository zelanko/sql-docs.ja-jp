---
title: ビューとストアド プロシージャの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- creating views and stored procedures
ms.assetid: 53a0426d-07d8-4b7c-aa21-22632753bad8
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9731a52a783239755b78ae4ae967fc8ba6e44f73
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-2-3---creating-views-and-stored-procedures"></a>レッスン 2-3 - ビューとストアド プロシージャの作成
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Mary が **TestData** データベースにアクセスできるようになったので、ビューやストアド プロシージャのようなデータベース オブジェクトを作成し、Mary にこれらのオブジェクトへのアクセス権を付与できます。 ビューは、格納された SELECT ステートメントで、ストアド プロシージャは、バッチとして実行される 1 つ以上の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントです。  
  
ビューに対しては、テーブルと同じようにクエリが実行されます。パラメーターは使用できません。 ストアド プロシージャは、ビューよりも複雑です。 ストアド プロシージャは、入力と出力のパラメーターを指定でき、IF ステートメントや WHILE ステートメントなどの、コードの流れを制御するステートメントを含めることができます。 データベース内でのすべての繰り返し操作には、ストアド プロシージャを使用することをお勧めします。  
  
この例では、CREATE VIEW を使用して、 **Products** テーブル内の 2 つの列だけを選択するビューを作成します。 次に、CREATE PROCEDURE を使用して、価格のパラメーターを受け入れ、指定されたパラメーター値よりも価格が安い製品のみを返すストアド プロシージャを作成します。  
  
### <a name="to-create-a-view"></a>ビューを作成するには  
  
1.  次のステートメントを実行して、SELECT ステートメントを実行する非常に単純なビューを作成し、製品の名前と価格をユーザーに返します。  
  
    ```  
    CREATE VIEW vw_Names  
       AS  
       SELECT ProductName, Price FROM Products;  
    GO  
  
    ```  
  
### <a name="test-the-view"></a>ビューのテスト  
  
1.  ビューはテーブルと同じように処理されます。 ビューにアクセスするには `SELECT` ステートメントを使用します。  
  
    ```  
    SELECT * FROM vw_Names;  
    GO  
  
    ```  
  
### <a name="to-create-a-stored-procedure"></a>ストアド プロシージャを作成するには  
  
1.  次のステートメントでは、 `pr_Names`という名前のストアド プロシージャを作成し、 `@VarPrice` という名前の、 `money`データ型の入力パラメーターを受け入れます。 このストアド プロシージャによって、 `Products less than` データ型から `money` 文字データ型に変更される入力パラメーターと連結されるステートメント `varchar(10)` が出力されます。 次に、ビューに対して `SELECT` ステートメントが実行され、 `WHERE` 句の一部として入力パラメーターが渡されます。 これによって、入力パラメーター値よりも価格が安い製品がすべて返されます。  
  
    ```  
    CREATE PROCEDURE pr_Names @VarPrice money  
       AS  
       BEGIN  
          -- The print statement returns text to the user  
          PRINT 'Products less than ' + CAST(@VarPrice AS varchar(10));  
          -- A second statement starts here  
          SELECT ProductName, Price FROM vw_Names  
                WHERE Price < @varPrice;  
       END  
    GO  
  
    ```  
  
### <a name="test-the-stored-procedure"></a>ストアド プロシージャのテスト  
  
1.  ストアド プロシージャをテストするには、次のステートメントを入力して実行します。 このプロシージャによって、レッスン 1 で `Products` テーブルに入力した、価格が `10.00`より安い 2 つの製品の名前が返されます。  
  
    ```  
    EXECUTE pr_Names 10.00;  
    GO  
  
    ```  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[データベース オブジェクトへのアクセス権の付与](../t-sql/lesson-2-4-granting-access-to-a-database-object.md)  
  
## <a name="see-also"></a>参照  
[CREATE VIEW &#40;Transact-SQL&#41;](../t-sql/statements/create-view-transact-sql.md)  
[CREATE PROCEDURE &#40;Transact-SQL&#41;](../t-sql/statements/create-procedure-transact-sql.md)  
  
  
  
