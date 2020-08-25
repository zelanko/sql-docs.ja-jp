---
title: Azure SQL Data Warehouse への接続とクエリの実行
description: このクイック スタートでは、Azure Data Studio を使用して Azure SQL Data Warehouse に接続し、クエリを実行する方法を示します
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.reviewer: alayu, maghan, sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: e9c0ba08445eb1f9712b00b84cc07ac7eae310f1
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766371"
---
# <a name="quickstart-use-azure-data-studio-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>クイック スタート:Azure Data Studio を使用して、Azure SQL Data Warehouse のデータに接続してクエリを実行する

このクイック スタートでは、Azure Data Studio を使用して Azure SQL Data Warehouse に接続し、Transact-SQL ステートメントを使用してデータを作成、挿入、選択する方法について説明します。 

## <a name="prerequisites"></a>前提条件
このクイック スタートを完了するには、Azure Data Studio と Azure SQL Data Warehouse が必要です。

- [Azure Data Studio をインストールする](./download-azure-data-studio.md?view=sql-server-ver15)。

SQL Data Warehouse がまだない場合は、[SQL Data Warehouse の作成](/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision)に関するページを参照してください。

サーバー名とログイン資格情報を覚えておいてください。


## <a name="connect-to-your-data-warehouse"></a>データ ウェアハウスに接続する

Azure Data Studio を使用して、Azure SQL Data Warehouse サーバーへの接続を確立します。

1. 最初に Azure Data Studio を実行すると、 **[接続]** ページが開きます。 **[接続]** ページが表示されない場合は、 **[接続の追加]** をクリックするか、 **[サーバー]** サイドバーの **[新しい接続]** アイコンをクリックします。
   
   ![新しい接続アイコン](media/quickstart-sql-dw/new-connection-icon.png)

2. この記事では、*SQL ログイン*を使用しますが、*Windows 認証*もサポートされています。 *ご利用の* Azure SQL サーバーのサーバー名、ユーザー名、パスワードを使用して、次のようにフィールドに入力します。

   | 設定       | 推奨値 | 説明 |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前は次のようになります: **sqldwsample.database.windows.net** |
   | **認証** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **データベース名** | *空白のままにする* | 接続先となるデータベースの名前。 |
   | **サーバー グループ** | <Default> を選択 | サーバー グループを作成した場合は、特定のサーバー グループに設定できます。 | 

   ![新しい接続アイコン](media/quickstart-sql-dw/new-connection-screen.png) 

3. サーバーに Azure Data Studio の接続を許可するファイアウォール規則がない場合は、 **[新しいファイアウォール規則の作成]** フォームが開きます。 フォームに入力して、新しいファイアウォール規則を作成します。 詳細については、[ファイアウォール規則](/azure/sql-database/sql-database-firewall-configure)に関するページを参照してください。

   ![新しいファイアウォール規則](media/quickstart-sql-dw/firewall.png)  

4. ご利用のサーバーに接続が正常に行われると、 *[サーバー]* サイドバーに表示されます。

## <a name="create-the-tutorial-data-warehouse"></a>チュートリアル データ ウェアハウスを作成する
1. オブジェクト エクスプローラーでご利用のサーバーを右クリックし、 **[新しいクエリ]** を選択します。

1. クエリ エディターに次のスニペットを貼り付けて、 **[実行]** をクリックします。

   ```sql
    IF NOT EXISTS (
       SELECT name
       FROM sys.databases
       WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB] (EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');
    GO  
    
    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
   ```


## <a name="create-a-table"></a>テーブルを作成する

クエリ エディターはまだ *master* データベースに接続されていますが、*TutorialDB* データベースにテーブルを作成する必要があります。 

1. 接続コンテキストを **TutorialDB** に変更します。

   ![変更コンテキスト](media/quickstart-sql-database/change-context.png)


1. クエリ エディターに次のスニペットを貼り付けて、 **[実行]** をクリックします。

   > [!NOTE]
   > これを追加したり、エディターで前のクエリを上書きしたりすることができます。 **[実行]** をクリックすると、選択されているクエリのみが実行されることに注意してください。 何も選択されていない場合、 **[実行]** をクリックすると、エディター内のすべてのクエリが実行されます。

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>行を挿入する

1. クエリ エディターに次のスニペットを貼り付けて、 **[実行]** をクリックします。

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>結果を表示する
1. クエリ エディターに次のスニペットを貼り付けて、 **[実行]** をクリックします。

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます:

   ![結果の選択](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップする

このコレクションの他の記事は、このクイック スタートに基づいています。 後続のクイック スタートで作業を続ける場合は、このクイック スタートで作成したリソースをクリーンアップしないでください。 続行する予定がない場合は、次の手順を使用して、このクイック スタートで作成したリソースを Azure portal で削除します。
不要になったリソース グループを削除することで、リソースをクリーンアップします。 詳細については、「[リソースのクリーンアップ](/azure/sql-database/sql-database-get-started-portal#clean-up-resources)」を参照してください。


## <a name="next-steps"></a>次のステップ

Azure SQL Data Warehouse に正常に接続してクエリを実行したので、[コード エディターのチュートリアル](tutorial-sql-editor.md)をお試しください。