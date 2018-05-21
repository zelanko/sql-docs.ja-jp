---
title: 'クイック スタート: 接続し、SQL 操作 Studio (プレビュー) を使用して Azure SQL データベースを照会 |Microsoft ドキュメント'
description: このクイック スタートは、SQL 操作 Studio (プレビュー) を使用して SQL データベースに接続し、クエリを実行する方法を示しています。
ms.custom: tools|sos
ms.date: 03/08/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: c72e6d5b8e3e2770300e6b890b076bf77617849b
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>クイック スタート: を使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]接続し、Azure SQL データベースを照会するには

このクイック スタートでは、*[!INCLUDE[name-sos](../includes/name-sos-short.md)]* を使用して Azure SQL database に接続し、TRANSACT-SQL (T-SQL) ステートメントを使用して [!INCLUDE[name-sos](../includes/name-sos-short.md)] チュートリアルで使用される *TutorialDB* を作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了させるためには、[!INCLUDE[name-sos](../includes/name-sos-short.md)] および Azure SQL サーバーが必要です。

- [[!INCLUDE[name-sos](../includes/name-sos-short.md)] のインストール](download.md)

まだ Azure SQL サーバーを持っていないという場合は、次のいずれかの Azure SQL Database のクイック スタートを完了させてください (そのときにサーバー名とログイン資格情報を覚えておくようにしてください)。

- [DB の作成 - ポータル](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [DB の作成 - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [DB の作成 - PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Azure SQL データベース サーバーへの接続します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)]を使用して Azure SQL データベース サーバーへの接続を確立します。

1. 初めて実行する[!INCLUDE[name-sos](../includes/name-sos-short.md)]、**接続**ページを開く必要があります。 表示されない場合、**接続**] ページで [**接続の追加**、または**新しい接続**のアイコン、**サーバー**サイドバー。
   
   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-icon.png)

2. この記事では*SQL ログイン*が*Windows 認証*もサポートされています。 次のようにサーバー名、ユーザー名およびパスワードを使用して、フィールドに入力 *、* Azure SQL server:

   | 設定       | 提案される値 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前には、次のようにする必要があります: **servername.database.windows.net** |
   | **[認証]** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **データベース名** | *空白のままに* | 接続するデータベースの名前。 |
   | **サーバー グループ** | 選択します。 <Default> | サーバー グループを作成する場合は、特定のサーバー グループを設定できます。 | 

   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-screen.png)  

3. サーバーに接続する、SQL 操作 Studio を許可するファイアウォール規則を持っていない場合、**新しいファイアウォール ルールを作成**フォームが開きます。 新しいファイアウォール ルールを作成するフォームを完了します。 詳細については、「[のファイアウォール ルール](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)です。

   ![新しいファイアウォール規則](media/quickstart-sql-database/firewall.png)  

4. サーバーへの接続が開いた後、*サーバー*サイドバーです。

## <a name="create-the-tutorial-database"></a>チュートリアルのデータベースを作成します。

次のセクションでは、作成、 *TutorialDB*でいくつか使用されているデータベース[!INCLUDE[name-sos](../includes/name-sos-short.md)]チュートリアルです。

1. サーバー サイド バー内の Azure SQL サーバーを右クリックし、選択**新しいクエリ。**

1. 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

   ```sql
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
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
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>行を挿入する

- 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

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


## <a name="view-the-result"></a>結果を表示します。
1. 次のスニペットをクエリ エディターに貼り付け をクリックして**実行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます。

   ![Select の結果](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップします。

このコレクション内の他の記事は、このクイック スタートに基づいて構築します。 後続のクイック スタートの操作を続行する場合は、このクイック スタートで作成されたリソースをクリーンアップしないでください。 続行する予定がない場合は、Azure ポータルでこのクイック スタートで作成されたリソースを削除する、次の手順を使用します。
不要になったリソース グループを削除することによって、リソースをクリーンアップします。 詳細については、「[リソースをクリーンアップ](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#clean-up-resources)です。

## <a name="next-steps"></a>次の手順

わかったら、Azure SQL データベースに正常に接続してクエリを実行すること、[コード エディターのチュートリアル](tutorial-sql-editor.md)です。
