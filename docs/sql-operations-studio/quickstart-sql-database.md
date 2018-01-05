---
title: "クイック スタート: 接続し、SQL 操作 Studio (プレビュー) を使用して Azure SQL データベースを照会 |Microsoft ドキュメント"
description: "このクイック スタートは、SQL 操作 Studio (プレビュー) を使用して SQL データベースに接続し、クエリを実行する方法を示しています。"
ms.custom: tools|sos
ms.date: 11/15/2017
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
ms.openlocfilehash: d0e2d48ed411f883a904decce5d836dde7aaa41b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>クイック スタート: を使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]接続し、Azure SQL データベースを照会するには

このクイック スタートを使用する方法を示しています *[!INCLUDE[name-sos](../includes/name-sos-short.md)]*  、Azure SQL database に接続し、TRANSACT-SQL (T-SQL) ステートメントを使用して、作成、 *TutorialDB*で使用される[!INCLUDE[name-sos](../includes/name-sos-short.md)]チュートリアルです。

## <a name="prerequisites"></a>Prerequisites

このクイック スタートを完了する必要があります[!INCLUDE[name-sos](../includes/name-sos-short.md)]、および Azure SQL サーバー。

- [インストール[!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)です。

Azure SQL サーバーがない場合は、次の Azure SQL Database のクイック スタート (サーバー名、およびログイン資格情報を注意してください)。 のいずれかを完了します。

- [DB - ポータルを作成します。](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [DB - CLI を作成します。](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [作成 DB - PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Azure SQL データベース サーバーへの接続します。

使用して[!INCLUDE[name-sos](../includes/name-sos-short.md)]Azure SQL データベース サーバーへの接続を確立します。

1. 初めて実行する[!INCLUDE[name-sos](../includes/name-sos-short.md)]、**接続**ページを開く必要があります。 場合、**接続**ページが開かないをクリックして、**新しい接続**のアイコン、**サーバー**サイドバー。
   
   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-icon.png)

2. この記事では*SQL ログイン*が*Windows 認証*もサポートされています。 次のように、フィールドに入力します。

   | 設定       | 提案される値 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前には、次のようにする必要があります: **servername.database.windows.net** |
   | **[認証]** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **User name** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **データベース名** | *空白のままに* | 接続するデータベースの名前。 |
   | **サーバー グループ** | 選択します。<Default> | サーバー グループを作成する場合は、特定のサーバー グループを設定できます。 | 

   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-screen.png)  

3. ファイアウォールに関するエラーが発生した場合は、ファイアウォール規則を作成する必要があります。 ファイアウォール規則を作成するを参照してください。[のファイアウォール ルールを](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)です。

4. 表示されます、サーバーへの接続後、*サーバー*サイドバーです。

## <a name="create-the-tutorial-database"></a>チュートリアルのデータベースを作成します。

*TutorialDB*いくつかのデータベースが使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]チュートリアルです。

1. サーバー サイド バー内の Azure SQL サーバーを右クリックし、選択**新しいクエリ。**

1. クエリ エディターに次のスニペットを貼り付けます。

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

1. クエリを実行する をクリックして**実行**です。


## <a name="create-a-table"></a>テーブルの作成

クエリ エディター接続が失われて、*マスター*にテーブルを作成するデータベースですが、 *TutorialDB*データベース。 

1. 接続コンテキストを変更する**TutorialDB**:

   ![変更のコンテキスト](media/quickstart-sql-database/change-context.png)



1. クエリ エディターに次のスニペットを貼り付けます。

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
1. クエリを実行する をクリックして**実行**です。

## <a name="insert-rows"></a>行を挿入します。

1. 次のスニペットをクエリ エディターに貼り付けます。
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

1. クエリを実行する をクリックして**実行**です。

## <a name="view-the-result"></a>結果を表示します。
1. クエリ エディターに次のスニペットを貼り付けます。

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリを実行する をクリックして**実行**です。

   ![Select の結果](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップします。

このコレクション内の他の記事は、このクイック スタートに基づいて構築します。 後続のクイック スタートの操作を続行する場合は、このクイック スタートで作成されたリソースをクリーンアップしないでください。 続行する予定がない場合は、Azure ポータルでこのクイック スタートで作成されたリソースを削除する、次の手順を使用します。
不要になったリソース グループを削除することによって、リソースをクリーンアップします。 詳細については、「[リソースをクリーンアップ](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#clean-up-resources)です。

## <a name="next-steps"></a>次の手順

わかったら、Azure SQL データベースに正常に接続してクエリを実行すること、[コード エディターのチュートリアル](tutorial-sql-editor.md)です。
