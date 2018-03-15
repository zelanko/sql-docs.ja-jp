---
title: "チュートリアル: SQL 操作 Studio (プレビュー) により、TRANSACT-SQL エディターを使用してデータベース オブジェクトを作成 |Microsoft ドキュメント"
description: "このチュートリアルでは、SQL 操作 Studio (プレビュー) で T-SQL を使用して簡略化する主要な機能について説明します。"
ms.custom: tools|sos
ms.date: 03/13/2018
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
ms.openlocfilehash: db9cc8185742980b649f9fcc11eced5687201464
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="tutorial-use-the-transact-sql-editor-to-create-database-objects---includename-sosincludesname-sos-shortmd"></a>チュートリアル: TRANSACT-SQL エディターを使用してデータベース オブジェクトを作成するには [!INCLUDE[name-sos](../includes/name-sos-short.md)]

を作成し、クエリを実行するストアド プロシージャやスクリプトなどは、データベース担当者の中核となるタスクです。 このチュートリアルでは、データベース オブジェクトを作成する T-SQL エディターで、主要な機能を示します。

このチュートリアルで使用する方法を学びます[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]に。
> [!div class="checklist"]
> * データベース オブジェクトの検索
> * テーブル データを編集します。 
> * スニペットを使用してすばやく T-SQL を記述するには
> * 使用してデータベース オブジェクトの詳細の表示*ピークの定義*と*定義へ移動*


## <a name="prerequisites"></a>前提条件

このチュートリアルは、SQL Server または Azure SQL データベースが必要です。 *TutorialDB*です。 作成する、 *TutorialDB*データベースで、次のクイック スタートのいずれかを行います。

- [接続してクエリを使用して SQL サーバー [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [接続してクエリを使用して Azure SQL データベース [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="quickly-locate-a-database-object-and-perform-a-common-task"></a>すぐにデータベース オブジェクトを見つけるし、一般的なタスクを実行

[!INCLUDE[name-sos-short](../includes/name-sos-short.md)] データベース オブジェクトをすばやく検索する検索ウィジェットを提供します。 結果一覧は、コンテキスト メニューの選択したオブジェクトに関連する一般的なタスクなど*データの編集*テーブル。

1. サーバー サイド バーを開く (**Ctrl + G**)、展開**データベース**を選択して**TutorialDB**です。 

1. 開く、 *TutorialDB ダッシュ ボード*を右クリックして**TutorialDB**を選択して**管理**コンテキスト メニュー。

   ![コンテキスト メニュー - 管理](./media/tutorial-sql-editor/insight-open-dashboard.png)

1. ダッシュ ボードを右クリックして**dbo します。顧客**(検索のウィジェット) で選択および**データの編集**です。
   
   > [!TIP]
   > データベースで多くのオブジェクトを使用して検索ウィジェットをすばやく検索できるテーブル、ビュー、探しているなどです。

   ![クイック検索のウィジェット](./media/tutorial-sql-editor/quick-search-widget.png)

1. 編集、**電子メール**最初の行では、型の列 *orlando0@adventure-works.com*とキーを押します**Enter**して変更を保存します。

   ![データを編集します。](./media/tutorial-sql-editor/edit-data.png)

## <a name="use-t-sql-snippets-to-create-stored-procedures"></a>T-SQL スニペットを使用してストアド プロシージャを作成するには

SQL 操作 Studio は、ステートメントをすばやく作成するため、多くの組み込みの T-SQL でスニペットを提供します。


1. キーを押して新しいクエリ エディターを開く**Ctrl + N**です。

2. 型**sql**エディターでは、下にある矢印**sqlCreateStoredProcedure**とキーを押します、*タブ*キー (または*Enter*) を格納されている作成を読み込むプロシージャ スニペット。

   ![snippet-list](./media/tutorial-sql-editor/snippet-list.png)

3. 作成するストアド プロシージャのスニペットが 2 つのフィールドをすばやくの編集用にセットアップ*StoredProcedureName*と*SchemaName*です。 選択*StoredProcedureName*、右クリックし、**出現するすべての変更**です。 ここで「 *getCustomer* ] および [すべて*StoredProcedureName*エントリを変更する*getCustomer*です。

   ![スニペット](./media/tutorial-sql-editor/snippet.png)

5. すべて置換*SchemaName*に*dbo*です。 
6. スニペットには、プレース ホルダー パラメーターと更新が必要な本文が含まれています。 *EXECUTE*手順には、パラメーターの数を認識していないためにステートメントがプレース ホルダー テキストにも含まれます。 このチュートリアルは、スニペットを更新ためようになります次のコード。

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
    
5. ストアド プロシージャを作成し、テストの実行を設定にキーを押して**f5 キーを押して**です。

ストアド プロシージャが作成されましたが、および**結果**ウィンドウには、JSON で返される顧客が表示されます。 書式設定された JSON を表示するには、返されたレコードをクリックします。 


## <a name="use-peek-definition"></a>ピークの定義を使用 

SQL 操作 Studio には、ピークの定義機能を使用して、オブジェクト定義を表示する機能が用意されています。 このセクションでは、2 番目のストアド プロシージャを作成し、ピークの定義が使用すると、どのような列は、テーブル、ストアド プロシージャの本体をすばやく作成します。

1. キーを押して新しいエディターを開きます**Ctrl + N**です。 

2. 型*sql*エディターでは、下にある矢印*sqlCreateStoredProcedure*とキーを押します、*タブ*キー (または*Enter*) を格納されている作成を読み込むプロシージャ スニペット。
3. 入力*setCustomer*の*StoredProcedureName*と*dbo*の*SchemaName*

3. 置換、@paramプレース ホルダーを次のパラメーターの定義で。

   ```sql
   @json_val nvarchar(max)
   ```

4. ストアド プロシージャの本体を次のコードに置き換えます。
   ```sql
   INSERT INTO dbo.Customers
   ```

5. *挿入*だけ追加を右クリックして行**dbo します。顧客**選択**ピークの定義**です。

   ![ピークの定義](./media/tutorial-sql-editor/peek-definition.png)

6. テーブルの定義は、簡単にわかるようには、テーブル内の列が表示されます。 ストアド プロシージャのステートメントを簡単に実行する列リストを参照してください。 ストアド プロシージャの本体を完了して、ピークの定義 ウィンドウを閉じる前に追加した INSERT ステートメントの作成を完了します。

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
7. 削除 (コメント アウト)、 *EXECUTE*クエリの下部にあるコマンド。
8. 全体のステートメントは、次のコードのようになります。

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

8. 作成する、 *setCustomer*ストアド プロシージャ、キーを押して**f5 キーを押して**です。

## <a name="use-save-query-results-as-json-to-test-the-setcustomer-stored-procedure"></a>使用して、setCustomer ストアド プロシージャをテストする JSON としてクエリ結果を保存します。

*SetCustomer*前のセクションで作成したストアド プロシージャに必要と JSON データに渡す、  *@json_val* パラメーター。 このセクションでは、ストアド プロシージャをテストできるように、パラメーターに渡すための JSON の正しく書式設定されたビットを取得する方法を示します。

1. **サーバー**サイド バーを右クリックし、 *dbo します。顧客*テーブルし、クリックして**上位 1000 行**です。

2. 結果ビューに最初の行を選択し、全体の行が選択されていることを確認 (左端の列の番号 1) をクリックし、選択**JSON として保存**です。  
3. 後で (例デスクトップ) のファイルを削除し、をクリックしてできるようわかりやすい場所にフォルダーを変更**保存**です。 JSON の形式でファイルを開く。

   ![JSON として保存します。](./media/tutorial-sql-editor/save-as-json.png)

4. エディターで、JSON データを選択し、それをコピーします。
5. キーを押して新しいエディターを開きます**Ctrl + N**です。
6. 前の手順を表示する呼び出しを完了する、正しく書式設定されたデータを簡単に取得する方法、 *setCustomer*プロシージャです。 テストできるように、次のコードで新しい顧客の詳細と同じ JSON 形式が使用を参照してください、 *setCustomer*プロシージャです。 ステートメントには、構文、パラメーターを宣言し、新しい get を実行 set プロシージャが含まれています。 前のセクションからコピーしたデータを貼り付けると次の例と同じであるため、編集したりできますだけで、次のステートメントをクエリ エディターに貼り付けます。

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

7. キーを押してスクリプトを実行**f5 キーを押して**です。 スクリプトは、新しい顧客を挿入し、JSON 形式で、新しい顧客の情報を返します。 書式設定されたビューを開く結果をクリックします。

   ![テスト結果](./media/tutorial-sql-editor/test-result.png)

## <a name="next-steps"></a>次の手順
このチュートリアルで学習した方法。
> [!div class="checklist"]
> * スキーマ オブジェクトのクイック検索
> * テーブル データを編集します。 
> * スニペットを使用する T-SQL スクリプトの記述
> * ピークの定義を使用してデータベース オブジェクトの詳細について説明し、定義へ移動


有効にする方法については、 **5 速度が遅かったクエリ**ウィジェット、[次へ]、チュートリアルを完了します。

> [!div class="nextstepaction"]
> [低速のクエリ サンプル insight ウィジェットを有効にします。](tutorial-qds-sql-server.md)
