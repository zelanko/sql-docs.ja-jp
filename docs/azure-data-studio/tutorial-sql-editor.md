---
title: チュートリアル:TRANSACT-SQL エディターを使用して、データベース オブジェクトを作成するには
titleSuffix: Azure Data Studio
description: このチュートリアルでは、T-SQL での作業を簡略化する Azure Data Studio の主な機能について説明します。
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: b4778d54fe3853f2560159a83dae42c4fd8e55e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959010"
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>チュートリアル:TRANSACT-SQL エディターを使用して、データベースのオブジェクトを作成するには [!INCLUDE[name-sos](../includes/name-sos-short.md)]

クエリやストアドプロシージャ、スクリプトなどを作成し、実行することは、データベース担当者の中核となるタスクです。 このチュートリアルでは、T-SQL エディターの主要な機能を使用してデータベースオブジェクトを作成する方法を説明します。

このチュートリアルでは、以下の操作を [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] で行う方法を示しています:
> [!div class="checklist"]
> * データベース オブジェクトの検索
> * テーブル データの編集 
> * スニペットを使用してすばやく T-SQL を記述する
> * 使用してデータベース オブジェクトの詳細の表示*ピークの定義*と*定義へ移動*


## <a name="prerequisites"></a>前提条件

このチュートリアルでは、SQL Server または Azure SQL Database に *TutorialDB* が必要です。 *TutorialDB* データベースを作成するには、次のクイック スタートのいずれかを行います。

- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、SQL Server に接続し、クエリを実行する](quickstart-sql-server.md)
- [[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] を使用して、Azure SQL Database に接続し、クエリを実行する](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>すぐにデータベース オブジェクトを見つけて、一般的なタスクを実行

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] はデータベース オブジェクトをすばやく検索する検索ウィジェットを提供します。 結果一覧には、選択したオブジェクトに関連する、例えばテーブルの*データ編集*のような一般的なタスクのためのコンテキスト メニューが提供されます。

1. [サーバー] サイド バーを開き (**Ctrl + G**)、 **[データベース]** を展開して、 **[TutorialDB]** を選択します。 

1. **[TutorialDB]** を右クリックして、コンテキスト メニューの **[管理]** を選択し、*TutorialDB ダッシュボード*を開きます。

   ![コンテキスト メニュー - 管理](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. ダッシュ ボードの右クリックして**dbo します。顧客**(検索のウィジェット) で選択および**データの編集**します。
   
   > [!TIP]
   > 多くのオブジェクトをデータベースの検索ウィジェットを使用して、テーブル、ビュー、探しているなどをすばやく検索します。

   ![クイック検索ウィジェット](./media/tutorial-sql-editor/quick-search-widget.png)

1. 編集、**電子メール**最初の行では、型の列 *orlando0@adventure-works.com* 、キーを押します **Enter** の変更を保存します。

   ![データを編集します。](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>T-SQL のスニペットを使用してストアド プロシージャを作成するには

[!INCLUDE[name-sos](../includes/name-sos-short.md)] ステートメントをすばやく作成するためには、多くの組み込み TSQL スニペットを提供します。


1. キーを押して、新しいクエリ エディターを開く**Ctrl + N**します。

2. 型**sql**エディターで、下にある矢印**sqlCreateStoredProcedure**、キーを押すと、*タブ*キー (または *」と入力*) に格納されている作成を読み込むプロシージャのスニペットです。

   ![snippet-list](./media/tutorial-sql-editor/snippet-list.png)

3. 作成するストアド プロシージャのスニペットがクイック編集を設定する 2 つのフィールド*StoredProcedureName*と*SchemaName*します。 選択*StoredProcedureName*、右クリックし、**変更箇所をすべて**します。 ここで「 *getCustomer*すべてと*StoredProcedureName*エントリを変更する*getCustomer*します。

   ![スニペット](./media/tutorial-sql-editor/snippet.png)

5. 出現箇所をすべて*SchemaName*に*dbo*します。 
6. スニペットには、プレース ホルダー パラメーターと更新が必要な本文が含まれています。 *EXECUTE*手順には、パラメーターの数を認識していないためにステートメントがプレース ホルダー テキストにも含まれます。 このチュートリアルは、スニペットを更新のためようになります次のコード。

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
    SELECT  c.CustomerId, 
    c.Name, 
    c.Location, 
    c.Email
    FROM dbo.Customers c
    WHERE c.CustomerId = @ID
    FOR JSON PATH

    GO
    -- example to execute the stored procedure we just created
    EXECUTE dbo.getCustomer 1
    GO
    ```
    
5. ストアド プロシージャを作成し、テストの実行を試して、キーを押して**F5**します。

ストアド プロシージャが作成されましたが、および**結果**ペインには、JSON で返された顧客が表示されます。 書式設定された JSON を表示するには、返されるレコードをクリックします。 


## <a name="use-peek-definition"></a>ピークの定義を使用 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] ピークの定義機能を使用して、オブジェクト定義を表示する機能を提供します。 このセクションでは、2 番目のストアド プロシージャを作成し、ピークの定義が使用すると、どのような列は、テーブル、ストアド プロシージャの本体をすばやく作成します。

1. キーを押して新しいエディターを開く**Ctrl + N**します。 

2. 型*sql*エディターで、下にある矢印*sqlCreateStoredProcedure*、キーを押すと、*タブ*キー (または *」と入力*) に格納されている作成を読み込むプロシージャのスニペットです。
3. 入力*setCustomer*の*StoredProcedureName*と*dbo*の*SchemaName*

3. 置換、@paramプレース ホルダーを次のパラメーターの定義。

   ```sql
   @json_val nvarchar(max)
   ```

4. ストアド プロシージャの本体を次のコードに置き換えます。
   ```sql
   INSERT INTO dbo.Customers
   ```

5. *挿入*行が追加された、右クリックして**dbo します。顧客**選択**ピークの定義**します。

   ![ピークの定義](./media/tutorial-sql-editor/peek-definition.png)

6. テーブルの定義は、簡単にわかるようには、テーブル内の列が表示されます。 ストアド プロシージャのステートメントを簡単に完了する列の一覧を参照してください。 ストアド プロシージャの本体を完了し、ピークの定義ウィンドウを閉じる前に追加した INSERT ステートメントの作成を完了するには。

   ```sql
   INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
    )
   ```
7. 削除 (またはコメント アウト)、 *EXECUTE*クエリの下部にあるコマンド。
8. ステートメント全体は、次のコードのようになります。

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
       INSERT INTO dbo.Customers (CustomerId, Name, Location, Email)
       SELECT CustomerId, Name, Location, Email
       FROM OPENJSON (@json_val)
       WITH(   CustomerId int, 
               Name nvarchar(50), 
               Location nvarchar(50), 
               Email nvarchar(50)
       )
   GO
   ```

8. 作成する、 *setCustomer*ストアド プロシージャ、キーを押して**F5**します。

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>使用は、setCustomer ストアド プロシージャをテストする JSON としてクエリ結果を保存します。

*SetCustomer*前のセクションで作成したストアド プロシージャは、JSON を必要がありますに渡すデータ、 *@json_val* パラメーター。 このセクションでは、ストアド プロシージャをテストできるように、パラメーターに渡す JSON の正しく書式設定されたビットを取得する方法を示します。

1. **サーバー**サイド バーを右クリックし、 *dbo します。顧客*テーブルし、クリックして**上位 1000 行**します。

2. 結果ビューで最初の行を選択します。 行全体が選択されているかどうかを確認してください (クリックで一番左の列番号 1)、選択と**JSON として保存**。  
3. 後 (例のデスクトップ) のファイルを削除し、をクリックしてできるようにわかりやすい場所にフォルダーを変更**保存**します。 JSON の形式でファイルを開く。

   ![JSON として保存します。](./media/tutorial-sql-editor/save-as-json.png)

4. エディターで JSON データを選択し、それをコピーします。
5. キーを押して新しいエディターを開く**Ctrl + N**します。
6. 前の手順を表示する呼び出しを完了する適切な形式のデータを簡単に取得する方法、 *setCustomer*プロシージャ。 次のコードは、テストできるように新しい顧客の詳細と同じ JSON 形式を使用を参照してください、 *setCustomer*プロシージャ。 ステートメントには、パラメーターを宣言し、新しい get を実行してプロシージャを設定するための構文が含まれています。 前のセクションからコピーしたデータを貼り付けるため、これは、次の例と同じ編集または、次のステートメントをクエリ エディターに貼り付けるだけです。

   ```sql
   -- example to execute the stored procedure we just created
   declare @json nvarchar(max) =
   N'[
       {
           "CustomerId": 5,
           "Name": "Lucy",
           "Location": "Canada",
           "Email": "lucy0@adventure-works.com"
       }
   ]'

   EXECUTE dbo.setCustomer @json_val = @json
   GO

   EXECUTE dbo.getCustomer @ID = 5
   ```

7. 押してスクリプトを実行する**F5**します。 スクリプトでは、新しい顧客を挿入し、JSON 形式で、新しい顧客の情報を返します。 結果を書式設定されたビューを開く をクリックします。

   ![テスト結果](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>次の手順
このチュートリアルでは、以下の使用方法を学習しました:
> [!div class="checklist"]
> * クイック検索スキーマ オブジェクト
> * テーブル データの編集 
> * スニペットを使用して T-SQL スクリプトの記述
> * 定義を使用してデータベース オブジェクトの詳細について説明しますと、定義へ移動


有効にする方法については、 **5 つの最も低速なクエリ**ウィジェットで、次のチュートリアルを完了します。

> [!div class="nextstepaction"]
> [低速のクエリ サンプル洞察のウィジェットを有効にします。](tutorial-qds-sql-server.md)
