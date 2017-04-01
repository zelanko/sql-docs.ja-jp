---
title: "テーブルの作成 (チュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テーブルの作成"
ms.assetid: 653f2dd3-36a2-4bd5-8703-71a57d244661
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# テーブルの作成 (チュートリアル)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

テーブルを作成するには、テーブルの名前と、テーブル内の各列の名前とデータ型を入力する必要があります。 また、各列でヌル値を許可するかどうかを指定することも推奨されます。 テーブルを作成するには、テーブルを追加するスキーマに対して `CREATE TABLE` アクセス許可と `ALTER SCHEMA` アクセス許可を持っている必要があります。 `db_ddladmin` 固定データベース ロールには、これらのアクセス許可があります。  
  
ほとんどのテーブルに、テーブルの 1 つ以上の列で構成された主キーがあります。 主キーは常に一意です。 [!INCLUDE[ssDE](../includes/ssde-md.md)]によって、主キーの値がテーブルで重複しないように制限されます。  
  
データ型のリストと、それぞれの説明のリンクについては、「[データ型 (Transact-SQL)](../t-sql/data-types/data-types-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
> [!INCLUDE[ssDE](../includes/ssde-md.md)]は、大文字と小文字を区別するか区別しないかを設定してインストールできます。 大文字と小文字を区別するように設定して[!INCLUDE[ssDE](../includes/ssde-md.md)]をインストールした場合は、オブジェクト名を常に大文字か小文字に統一する必要があります。 たとえば、OrderData という名前のテーブルと、ORDERDATA という名前のテーブルは別のテーブルです。 大文字と小文字を区別しないように設定して[!INCLUDE[ssDE](../includes/ssde-md.md)]をインストールした場合、この 2 つのテーブル名は同じテーブルと見なされるため、その名前は一度しか使用できません。  
  
### 新しいテーブルを含めるデータベースを作成するには  
  
-   クエリ エディター ウィンドウに次のコードを入力します。  
  
    ```  
    USE master;  
    GO  
  
    --Delete the TestData database if it exists.  
    IF EXISTS(SELECT * from sys.databases WHERE name='TestData')  
    BEGIN  
        DROP DATABASE TestData;  
    END  
  
    --Create a new database called TestData.  
    CREATE DATABASE TestData;  
    Press the F5 key to execute the code and create the database.  
    ```  
  
### クエリ エディター接続から TestData データベースへの切り替え  
  
-   接続を `TestData` データベースに変更するには、クエリ エディターのウィンドウで次のコードを入力して実行します。  
  
    ```  
    USE TestData  
    GO  
    ```  
  
### テーブルを作成するには  
  
-   クエリ エディターのウィンドウで、次のコードを入力して実行し、`Products` という名前の単純なテーブルを作成します。 テーブルの列は `ProductID`、`ProductName`、`Price`、`ProductDescription` という名前です。 `ProductID` 列がテーブルの主キーです。 `int`、`varchar(25)`、`money`、`text` は、すべてデータ型です。 行を挿入または変更するときにデータを入力しなくてもよい列は、`Price` と `ProductionDescription` のみです。 このステートメントには、スキーマというオプションの要素 (`dbo.`) が含まれています。 スキーマは、テーブルを所有するデータベース オブジェクトです。 管理者の場合は、`dbo` が既定のスキーマです。 `dbo` はデータベース所有者を表します。  
  
    ```  
    CREATE TABLE dbo.Products  
       (ProductID int PRIMARY KEY NOT NULL,  
        ProductName varchar(25) NOT NULL,  
        Price money NULL,  
        ProductDescription text NULL)  
    GO  
    ```  
  
## このレッスンの次の作業  
[テーブルのデータの挿入と更新 (チュートリアル)](../t-sql/inserting-and-updating-data-in-a-table-tutorial.md)  
  
## 参照  
[CREATE TABLE &#40;Transact-SQL&#41;](../t-sql/statements/create-table-transact-sql.md)  
  
  
  
