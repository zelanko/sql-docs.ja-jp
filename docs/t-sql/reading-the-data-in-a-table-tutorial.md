---
title: "テーブルのデータの読み取り (チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "テーブル内のデータの読み取り"
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# テーブルのデータの読み取り (チュートリアル)
テーブルのデータを読み取るには、SELECT ステートメントを使用します。 SELECT ステートメントは最も重要な [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの 1 つで、構文には多くのバリエーションがあります。 このチュートリアルでは、5 つの単純なバージョンを使用します。  
  
### テーブルのデータを読み取るには  
  
1.  次のステートメントを入力して実行し、`Products` テーブルのデータを読み取ります。  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  アスタリスクを使用すると、テーブルの列をすべて選択できます。 これはアドホック クエリでよく使用されます。 永続的なコード内では列一覧を指定して、新しい列が後からテーブルに追加された場合でも、予測された列がステートメントによって返されるようにしてください。  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  返す必要のない列は省略できます。 列は、一覧内の順序で返されます。  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  ユーザーに返される行を制限するには、`WHERE` 句を使用します。  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  列内の値は、列が返されたときに操作できます。 次の例では、`Price` 列に対して数学的演算を実行します。 このようにして変更された列には、`AS` キーワードを使用して名前を指定しない限り、名前が付けられません。  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## SELECT ステートメント内で役に立つ関数  
SELECT ステートメント内のデータの操作に使用できる関数の詳細については、次のトピックを参照してください。  
  
|||  
|-|-|  
|[文字列関数 (Transact-SQL)](../t-sql/functions/string-functions-transact-sql.md)|[日付と時刻のデータ型および関数 (Transact-SQL)](../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)|  
|[数学関数 (Transact-SQL)](../t-sql/functions/mathematical-functions-transact-sql.md)|[テキスト関数とイメージ関数 (Transact-SQL)](../Topic/Text%20and%20Image%20Functions%20(Transact-SQL).md)|  
  
## このレッスンの次の作業  
[要約 : データベース オブジェクトの作成](../t-sql/summary-creating-database-objects.md)  
  
## 参照  
[SELECT &#40;Transact-SQL&#41;](../t-sql/queries/select-transact-sql.md)  
  
  
  
