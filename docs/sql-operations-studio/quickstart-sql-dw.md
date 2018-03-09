---
title: "クイック スタート: は接続し、クエリの SQL 操作 Studio (プレビュー) を使用して Azure SQL Data Warehouse |Microsoft ドキュメント"
description: "このクイック スタートは、SQL 操作 Studio (プレビュー) を使用して SQL データベースに接続し、クエリを実行する方法を示しています。"
ms.custom: tools|sos
ms.date: 03/08/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d4ed7d25abb2780c719c5b8201ecae54e8e86bf
ms.sourcegitcommit: 6c06267f3eeeb3f0d6fc4c57e1387621720ca8bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2018
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>クイック スタート: を使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]接続し、Azure SQL Data Warehouse のデータの照会

このクイック スタートを使用する方法を示しています[!INCLUDE[name-sos](../includes/name-sos-short.md)]に Azure SQL データ ウェアハウスに接続し、TRANSACT-SQL ステートメントを使用して、作成、挿入、およびデータを選択します。 

## <a name="prerequisites"></a>前提条件
このクイック スタートを完了する必要があります[!INCLUDE[name-sos](../includes/name-sos-short.md)]、および Azure SQL データ ウェアハウスです。

- [インストール[!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)です。

SQL データ ウェアハウスがない場合は、次を参照してください。 [SQL データ ウェアハウスを作成](https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision)です。

サーバー名、およびログイン資格情報に注意してください。


## <a name="connect-to-your-data-warehouse"></a>データ ウェアハウスに接続します。

使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]Azure SQL Data Warehouse サーバーへの接続を確立します。

1. 初めて実行する[!INCLUDE[name-sos](../includes/name-sos-short.md)]、**接続**ページを開く必要があります。 表示されない場合、**接続**] ページで [**接続の追加**、または**新しい接続**のアイコン、**サーバー**サイドバー。
   
   ![新しい接続のアイコン](media/quickstart-sql-dw/new-connection-icon.png)

2. この記事では*SQL ログイン*が*Windows 認証*もサポートされています。 次のようにサーバー名、ユーザー名およびパスワードを使用して、フィールドに入力*、* Azure SQL server:

   | 設定       | 提案される値 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前には、次のようにする必要があります: **sqldwsample.database.windows.net** |
   | **[認証]** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **データベース名** | *空白のままに* | 接続先となるデータベースの名前。 |
   | **サーバー グループ** | 選択します。 <Default> | サーバー グループを作成する場合は、特定のサーバー グループを設定できます。 | 

   ![新しい接続のアイコン](media/quickstart-sql-dw/new-connection-screen.png) 

3. サーバーに接続する、SQL 操作 Studio を許可するファイアウォール規則を持っていない場合、**新しいファイアウォール ルールを作成**フォームが開きます。 新しいファイアウォール ルールを作成するフォームを完了します。 詳細については、「[のファイアウォール ルール](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)です。

   ![新しいファイアウォール規則](media/quickstart-sql-dw/firewall.png)  

4. サーバーへの接続が開いた後、*サーバー*サイドバーです。

## <a name="create-the-tutorial-data-warehouse"></a>チュートリアルのデータ ウェアハウスを作成します。
1. オブジェクト エクスプ ローラーで、サーバーを右クリックし、選択**新しいクエリ。**

1. 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

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


## <a name="create-a-table"></a>テーブルの作成

クエリ エディター接続が失われて、*マスター*にテーブルを作成するデータベースですが、 *TutorialDB*データベース。 

1. 接続コンテキストを変更する**TutorialDB**:

   ![変更のコンテキスト](media/quickstart-sql-database/change-context.png)


1. 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

   > [!NOTE]
   > これを追加したり、エディターでは、前のクエリを上書きできます。 クリックすると**実行**が選択されているクエリのみを実行します。 何も選択されている場合にクリックすると**実行**エディター内のすべてのクエリを実行します。

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


## <a name="insert-rows"></a>行を挿入します。

1. 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>結果を表示します。
1. 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます。

   ![Select の結果](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップします。

このコレクション内の他の記事は、このクイック スタートに基づいて構築します。 後続のクイック スタートの操作を続行する場合は、このクイック スタートで作成されたリソースをクリーンアップしないでください。 続行する予定がない場合は、Azure ポータルでこのクイック スタートで作成されたリソースを削除する、次の手順を使用します。
不要になったリソース グループを削除することによって、リソースをクリーンアップします。 詳細については、「[リソースをクリーンアップ](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#clean-up-resources)です。


## <a name="next-steps"></a>次の手順

わかったらした Azure SQL データ ウェアハウスに正常に接続してクエリを実行すること、[コード エディターのチュートリアル](tutorial-sql-editor.md)です。