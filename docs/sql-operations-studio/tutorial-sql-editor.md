---
title: "チュートリアル: SQL 操作 Studio (プレビュー) により、TRANSACT-SQL エディターを使用してデータベース オブジェクトを作成 |Microsoft ドキュメント"
description: "このチュートリアルでは、SQL 操作 Studio (プレビュー) で T-SQL を使用して簡略化する主要な機能について説明します。"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2754a998963be5a25d00aa58dcb9b4105bb8f37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>チュートリアル: TRANSACT-SQL エディターを使用してデータベース オブジェクトを作成するには[!INCLUDE[name-sos](../includes/name-sos-short.md)]

を作成し、クエリを実行するストアド プロシージャやスクリプトなどは、データベース担当者の中核となるタスクです。 このチュートリアルでは、データベース オブジェクトを作成する T-SQL エディターで、主要な機能を示します。

このチュートリアルで使用する方法を学びます[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]に。
> [!div class="checklist"]
> * データベース オブジェクトの検索
> * テーブル データを編集します。 
> * スニペットを使用してすばやく T-SQL を記述するには
> * 使用してデータベース オブジェクトの詳細の表示*ピークの定義*と*定義へ移動*


## <a name="prerequisites"></a>Prerequisites

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>すぐにデータベース オブジェクトを見つけるし、一般的なタスクを実行

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]データベース オブジェクトをすばやく検索する検索ウィジェットを提供します。 結果一覧は、コンテキスト メニューの選択したオブジェクトに関連する一般的なタスクなど*データの編集*テーブル。

1. サーバー サイド バーを開く (**Ctrl + G**)、展開**データベース**を選択して**TutorialDB**です。 

1. 開く、 *TutorialDB ダッシュ ボード*を選択して**管理**コンテキスト メニュー。

   ![コンテキスト メニュー - 管理](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. 検索、*顧客*」と入力してテーブル*カスタム*ウィジェットで、検索します。
1. 右クリック**dbo します。顧客**選択**データを編集**です。

   ![クイック検索のウィジェット](./media/tutorial-sql-editor/quick-search-widget.png)

1. 編集、**電子メール**最初の行では、型の列 *orlando0@adventure-works.com*とキーを押します**Enter**して変更を保存します。

   ![データを編集します。](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-a-stored-procedure"></a>ストアド プロシージャを作成する T-SQL でスニペットを使用します。

### <a name="use-snippets-in-includename-sos-shortincludesname-sos-shortmd"></a>スニペットを使用します。[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]

1. キーを押して新しいクエリ エディターを開く**Ctrl + N**です。

2. 型**sql**エディターでは、下にある矢印**sqlCreateStoredProcedure**、キーを押すと、  *タブ*キーを新しいストアド プロシージャのスニペットを読み込めません。

   ![スニペットの一覧](./media/tutorial-sql-editor/snippet-list.png)

3. 型*getCustomer*すべてと*StoredProcedureName*エントリを変更する*getCustomer*です。 

   ![スニペット](./media/tutorial-sql-editor/snippet.png)

4. ストアド プロシージャの残りの部分を T-SQL は、以下に置き換えます。

    ```sql
    -- Create a new stored procedure called 'getCustomer' in schema 'dbo'
    -- Drop the stored procedure if it already exists
    IF EXISTS (
    SELECT *
    FROM INFORMATION_SCHEMA.ROUTINES
    WHERE SPECIFIC_SCHEMA = N'dbo'
    AND SPECIFIC_NAME = N'getCustomer'
    )
    DROP PROCEDURE dbo.getCustomer
    GO
    -- Create the stored procedure in the specified schema
    CREATE PROCEDURE dbo.getCustomer
    @ID int
    -- add more stored procedure parameters here
    AS
    -- body of the stored procedure
    SELECT  c.CustomerID, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerID = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. ストアド プロシージャを作成し、テストの実行を設定にキーを押して**f5 キーを押して**です。

## <a name="use-peek-definition-and-go-to-definition"></a>ピークの定義を使用して定義へ移動 

1. キーを押して新しいエディターを開きます**Ctrl + N**です。 

2. 入力し、 **sqlCreateStoredProcedure**スニペットの候補リストからです。 入力**setCustomer**の**StoredProcedureName**と**dbo**の**SchemaName**

3. 置換、@param行を次のパラメーター定義。

   ```sql
       @json_val nvarchar(max)
   ```

4. 次のストアド プロシージャの本体に置き換えます。
   ```sql
   -- body of the stored procedure
   INSERT INTO dbo.Customers
   ```

5. 右クリック**dbo します。顧客**選択**ピークの定義**です。

   ![ピークの定義](./media/tutorial-sql-editor/peek-definition.png)

6. テーブルの定義を使用すると、次の insert ステートメントを完了します。

   ```sql
   INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
   ```
7. 最後のステートメントがあります。

   ```sql
   -- Create a new stored procedure called 'setCustomer' in schema 'dbo'
   -- Drop the stored procedure if it already exists
   IF EXISTS (
   SELECT *
       FROM INFORMATION_SCHEMA.ROUTINES
       WHERE SPECIFIC_SCHEMA = N'dbo'
       AND SPECIFIC_NAME = N'setCustomer'
   )
   DROP PROCEDURE dbo.setCustomer
   GO
   -- Create the stored procedure in the specified schema
   CREATE PROCEDURE dbo.setCustomer
       @json_val nvarchar(max) 
   AS
       -- body of the stored procedure
       INSERT INTO dbo.Customers (CustomerID, Name, Location, Email)
       SELECT CustomerID, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerID int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. スクリプトを実行するには、キーを押して**f5 キーを押して**です。

## <a name="use-save-query-results-as-json-to-test-our-stored-procedure"></a>使用して、ストアド プロシージャをテストする JSON としてクエリ結果を保存します。

1. **上位 1000 行**から、 *dbo します。顧客*テーブル。

2. 結果ビューで最初の行を選択し**JSON として保存**です。  
3. をクリックして**保存**、され強調表示された行の JSON 形式で起動します。

   ![JSON として保存します。](./media/tutorial-sql-editor/save-as-json.png)

4. JSON データを選択し、それをコピーします。

5. 新しいクエリを開く*TutorialDB*し、JSON データを使用して、前の手順をテンプレートとして次のテスト スクリプトを完了します。 値を変更*CustomerID*、*名前*、*場所*、および*電子メール*です。

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerID": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. キーを押してスクリプトを実行**f5 キーを押して**です。 スクリプトは、新しい顧客を挿入し、JSON 形式で、新しい顧客の情報を返します。 書式設定されたビューを開く結果をクリックします。

   ![テスト結果](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>次の手順
このチュートリアルで学習した方法。
> [!div class="checklist"]
> * スキーマ オブジェクトのクイック検索
> * テーブル データを編集します。 
> * スニペットを使用する T-SQL スクリプトの記述
> * ピークの定義を使用してデータベース オブジェクトの詳細について説明し、定義へ移動


有効にする方法については、 **5 速度が遅かったクエリ**インサイトをサンプルを次のチュートリアルを完了します。

> [!div class="nextstepaction"]
> [低速のクエリ サンプル insight ウィジェットを有効にします。](tutorial-qds-sql-server.md)
