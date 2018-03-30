---
Title: 'Tutorial: Connect and Query SQL Server using SQL Server Management Studio'
description: SQL Server Management Studio を使用して SQL Server に接続し、基本的な T-SQL クエリを実行する方法についてのチュートリアルです。
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: 6f4110a0ae1b4ca349cc9b990cc9a32f7d41764d
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-connect-and-query-sql-server-using-sql-server-management-studio"></a>チュートリアル: SQL Server Management Studio を使用して SQL Server に接続しクエリを行う
このチュートリアルでは、SQL Server Management Studio (SSMS) を使って SQL Server インスタンスに接続し、いくつかの基本的な Transact-SQL (T-SQL) コマンドを実行する方法を説明します。 この記事では、以下のことを行う方法を示します。

> [!div class="checklist"]
> * [SQL Server に接続する](#connect-to-a-sql-server)
> * [新しいデータベース (**TutorialDB**) を作成する](#create-a-database)
> * [新しいデータベースにテーブル (**Customers**) を作成する](#create-a-table)
> * [新しい **Customers** テーブルに行を挿入する](#insert-rows)
> * [**Customers** テーブルのクエリを行って結果を表示する](#view-query-results)
> * [クエリ ウィンドウのテーブルを使用して接続のプロパティを確認する](#verify-your-query-window-connection-properties)
> * [クエリ ウィンドウが接続するサーバーを変更する](#change-server-connection-within-query-window)


## <a name="prerequisites"></a>Prerequisites
このチュートリアルを実行するには、SQL Server Management Studio と SQL Server へのアクセスが必要です。 

- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms) をインストールする。

アクセスできる SQL Server がない場合は、次のリンクからお使いのプラットフォームを選んでください (SQL 認証を選ぶ場合は、SQL ログインとパスワードを憶えておいてください)。
- [Windows - SQL Server 2017 Developer Edition をダウンロードする](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS - Docker で SQL Server 2017 をダウンロードする](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)


## <a name="connect-to-a-sql-server"></a>SQL Server に接続する

1. SQL Server Management Studio (SSMS) を起動します。
1. SSMS を初めて実行すると、**[サーバーへの接続]** ダイアログ ボックスが開きます。 
      - **[サーバーへの接続]** ダイアログが開かない場合は、**[オブジェクト エクスプローラー]** > **[接続]** (またはその横にあるアイコン) > **[データベース エンジン]** から手動で開くことができます。

        ![オブジェクト エクスプローラーで接続する](media/connect-query-sql-server/connectobjexp.png)

1. **[サーバーへの接続]** ダイアログ ボックスで、接続のオプションを入力します。 

    - **[サーバーの種類]**: データベース エンジン (通常は既定で選ばれています)
    - **[認証]**: Windows 認証 (この記事では Windows 認証を使いますが、SQL ログインもサポートされており、選ぶとユーザー名/パスワードの入力を求められます)

      ![接続](media/connect-query-sql-server/connection.png)

        **[オプション]** ボタンをクリックすると、他の接続オプション (接続先データベース、接続タイムアウト値、ネットワーク プロトコルなど) も変更できます。 この記事では、すべてを既定値のままにしました。 

1. フィールドを設定した後、**[接続]** をクリックします。 

1. **オブジェクト エクスプローラー**でオブジェクトを調べることにより、SQL Server への接続が成功したことを確認できます。 

   ![成功した接続](media/connect-query-sql-server/successfulconnection.png)


## <a name="create-a-database"></a>データベースの作成
次の手順では、TutorialDB という名前のデータベースを作成します。 

1. **オブジェクト エクスプローラー**でサーバーを右クリックし、**[新しいクエリ]** を選択します。

   ![新しいクエリ](media/connect-query-sql-server/newquery.png)
   
1. クエリ ウィンドウに次の T-SQL コード スニペットを貼り付けます。 
   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO
   ```
2. クエリを実行するには、**[実行]** をクリックします (または、キーボードの F5 キーを押します)。 

   ![クエリの実行](media/connect-query-sql-server/execute.png)
  
 
クエリが完了すると、**オブジェクト エクスプローラー**のデータベースの一覧に新しい **TutorialDB** が表示されます。 表示されない場合は、[データベース] ノードを右クリックして **[更新]** を選択します。  


## <a name="create-a-table"></a>テーブルを作成する
以下の手順では、新しく作成した **TutorialDB** データベースにテーブルを作成します。 ただし、クエリ エディターはまだ *master* データベースのコンテキストになっており、テーブルを作成したいのは *TutorialDB* データベースです。 

1. データベースのドロップダウンから目的のデータベースを選んで、クエリの接続コンテキストを master データベースから **TutorialDB** に変更します。 

   ![データベースの変更](media/connect-query-sql-server/changedb.png)

1. 次の T-SQL コード スニペットをクエリ ウィンドウに貼り付け、強調表示にして、**[実行]** をクリックします (または、キーボードの F5 キーを押します)。 
    - クエリ ウィンドウの既存のテキストを置き換えても、末尾に追加してもかまいません。 クエリ ウィンドウ内のすべてを実行する場合は、**[実行]** をクリックします。 テキストの一部を実行する場合は、その部分を強調表示にしてから、**[実行]** をクリックします。  
  
   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```
クエリが完了すると、**オブジェクト エクスプローラー**のテーブルの一覧に新しい **Customers** テーブルが表示されます。 テーブルが表示されない場合は、**オブジェクト エクスプローラー**で **[TutorialDB] > [テーブル]** ノードを右クリックし、**[更新]** を選択します。

## <a name="insert-rows"></a>行を挿入する
次の手順では、前に作成した **Customers** テーブルにいくつかの行を挿入します。 

クエリ ウィンドウに次の T-SQL コード スニペットを貼り付けて、**[実行]** をクリックします。 


   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```

## <a name="view-query-results"></a>クエリ結果を表示する
クエリの結果は、クエリ テキスト ウィンドウの下で見ることができます。 次の手順では、**Customers** テーブルのクエリを行って、前に挿入した行を表示できます。  

1. クエリ ウィンドウに次の T-SQL コード スニペットを貼り付けて、**[実行]** をクリックします。 

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```
1. クエリの結果は、テキストを入力した領域の下に表示されます。 

   ![クエリ結果](media/connect-query-sql-server/queryresults.png)


1.  以下のオプションのいずれかを選択して、結果の表示方法を変更できます。

     ![結果 (results)](media/connect-query-sql-server/results.png)

    - 既定では、結果は**グリッド ビュー**になります。これは中央のボタンで指定し、表形式で結果が表示されます。 
    - 1 番目のボタンを選ぶと、結果は**テキスト ビュー**で表示されます。次のセクションの図はこの表示方法です。
    - 3 番目のボタンを選ぶと、結果をファイルに保存できます。既定のファイル拡張子は *.rpt です。

## <a name="verify-your-query-window-connection-properties"></a>クエリ ウィンドウの接続プロパティを確認する
接続プロパティに関する情報は、クエリの結果の下で確認できます。 
- 前の手順で示したクエリを実行した後、クエリ ウィンドウの下端にある接続プロパティを確認します。
    - 接続先のサーバーとデータベース、およびログインに使っているユーザーがわかります。
    - クエリの実行時間と、前に実行したクエリによって返された行数も確認できます。
    
    ![接続プロパティ](media/connect-query-sql-server/connectionproperties.png)  
    この画像では、結果は**テキスト ビュー**で表示されています。  

## <a name="change-server-connection-within-query-window"></a>クエリ ウィンドウでサーバーの接続を変更する
次の手順で、現在のクエリ ウィンドウに接続されているサーバーを変更できます。
1. クエリ ウィンドウ内を右クリックして、[接続] > [接続の変更] の順に選択します。
2. **[サーバーへの接続]** ダイアログ ボックスが再び開き、クエリの接続先のサーバーを変更できます。 
 
   ![[接続の変更]](media/connect-query-sql-server/changeconnection.png)
   - これを行っても**オブジェクト エクスプローラー**が接続しているサーバーは変更されないことに注意してください。変更されるのは現在のクエリ ウィンドウだけです。 



