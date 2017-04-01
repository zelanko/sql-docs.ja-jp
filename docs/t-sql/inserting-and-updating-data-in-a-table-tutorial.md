---
title: "テーブルのデータの挿入と更新 (チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
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
  - "データの挿入と更新"
ms.assetid: 514dc87a-b829-43b5-8fc8-1a400a260284
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# テーブルのデータの挿入と更新 (チュートリアル)
**Products** テーブルを作成したので、INSERT ステートメントを使用してデータをテーブルに挿入する準備ができました。 データを挿入した後は、UPDATE ステートメントを使用して行の内容を変更します。 更新を 1 つの行に制限するには、UPDATE ステートメントの WHERE 句を使用します。 4 つのステートメントによって、次のデータが入力されます。  
  
|ProductID|ProductName|Price|ProductDescription|  
|-------------|---------------|---------|----------------------|  
|1|Clamp|12.48|Workbench clamp|  
|50|Screwdriver|3.17|Flat head|  
|75|Tire Bar||Tool for changing tires|  
|3000|3mm Bracket|.52||  
  
基本的な構文は、INSERT、テーブル名、列一覧、VALUES、および挿入する値の一覧です。 行の先頭にある 2 つのハイフンは、その行がコメントであることを示します。この行のテキストはコンパイラによって無視されます。 この場合、コメントは構文に許可されているバリエーションを記述します。  
  
### データをテーブルに挿入するには  
  
1.  次のステートメントを実行し、前のタスクで作成した `Products` テーブルに行を挿入します。 これは基本構文です。  
  
    ```  
    -- Standard syntax  
    INSERT dbo.Products (ProductID, ProductName, Price, ProductDescription)  
        VALUES (1, 'Clamp', 12.48, 'Workbench clamp')  
    GO  
  
    ```  
  
2.  次のステートメントは、フィールド一覧 (かっこ内) と値一覧の両方にある `ProductID` と `ProductName` の配置を交換することで、パラメーターの順序を変更する方法を示しています。  
  
    ```  
    -- Changing the order of the columns  
    INSERT dbo.Products (ProductName, ProductID, Price, ProductDescription)  
        VALUES ('Screwdriver', 50, 3.17, 'Flat head')  
    GO  
  
    ```  
  
3.  次のステートメントは、値が正しい順序で示されている限り、列の名前はオプションであることを示しています。 この構文は一般的ですが、他のユーザーがコードを理解しにくいため、推奨されません。 `NULL` が `Price` 列に指定されているのは、この製品の価格が不明ためです。  
  
    ```  
    -- Skipping the column list, but keeping the values in order  
    INSERT dbo.Products  
        VALUES (75, 'Tire Bar', NULL, 'Tool for changing tires.')  
    GO  
  
    ```  
  
4.  スキーマ名は、既定のスキーマ内のテーブルにアクセスし、変更している場合にはオプションです。 `ProductDescription` 列では NULL 値が許可されており、値が提供されていないため、`ProductDescription` 列の名前と値はステートメントから完全に省略できます。  
  
    ```  
    -- Dropping the optional dbo and dropping the ProductDescription column  
    INSERT Products (ProductID, ProductName, Price)  
        VALUES (3000, '3mm Bracket', .52)  
    GO  
    ```  
  
### Products テーブルを更新するには  
  
1.  次の `UPDATE` ステートメントを入力して実行し、2 番目の製品の `ProductName` を `Screwdriver` から `Flat Head Screwdriver` に変更します。  
  
    ```  
    UPDATE dbo.Products  
        SET ProductName = 'Flat Head Screwdriver'  
        WHERE ProductID = 50  
    GO  
    ```  
  
## このレッスンの次の作業  
[テーブルのデータの読み取り (チュートリアル)](../t-sql/reading-the-data-in-a-table-tutorial.md)  
  
## 参照  
[INSERT &#40;Transact-SQL&#41;](../t-sql/statements/insert-transact-sql.md)  
[UPDATE &#40;Transact-SQL&#41;](../t-sql/queries/update-transact-sql.md)  
  
  
  
