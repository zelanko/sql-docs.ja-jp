---
title: 'クイック スタート: SQL Operations Studio (プレビュー) を使用して Azure SQL Database に接続して照会する |Microsoft ドキュメント'
description: このクイック スタートは、SQL Operations Studio (プレビュー) を使用して SQL データベースに接続し、クエリを実行する方法を示しています。
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
ms.openlocfilehash: 5470e19da9d8641a1337f0f8162fe0a1789820dd
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982264"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>クイック スタート: [!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用して Azure SQL Database に接続して照会する

このクイック スタートでは、*[!INCLUDE[name-sos](../includes/name-sos-short.md)]* を使用して Azure SQL database に接続し、TRANSACT-SQL (T-SQL) ステートメントを使用して [!INCLUDE[name-sos](../includes/name-sos-short.md)] チュートリアルで使用される *TutorialDB* を作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了させるためには、[!INCLUDE[name-sos](../includes/name-sos-short.md)] および Azure SQL サーバーが必要です。

- [[!INCLUDE[name-sos](../includes/name-sos-short.md)] のインストール](download.md)

まだ Azure SQL サーバーを持っていないという場合は、次のいずれかの Azure SQL Database のクイック スタートを完了させてください (そのときにサーバー名とログイン資格情報を覚えておくようにしてください)。

- [DB の作成 - ポータル](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [DB の作成 - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [DB の作成 - PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Azure SQL Database サーバーに接続する

[!INCLUDE[name-sos](../includes/name-sos-short.md)]を使用して Azure SQL データベース サーバーへの接続を確立します。

1. [!INCLUDE[name-sos](../includes/name-sos-short.md)] の初回実行時には **[接続]** ページが開きます。 **[接続]** ページが表示されない場合は、**[接続の追加]**、または **[サーバー]** サイドバーの **[新しい接続]** アイコンをクリックします。
   
   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-icon.png)

2. この記事では*SQL ログイン*を使用しますが、*Windows 認証*もサポートされています。 Azure SQL サーバーのサーバー名、ユーザー名およびパスワードを使用して *、* 次のようにフィールドに入力します。

   | 設定       | 提案される値 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前は、このようなものでなければなりません: **servername.database.windows.net** |
   | **[認証]** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **データベース名** | *空白のままに* | 接続するデータベースの名前。 |
   | **サーバー グループ** | 選択します <Default> | サーバー グループを作成する場合は、特定のサーバー グループに設定できます。 | 

   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-screen.png)  

3. サーバーに SQL Operations Studio の接続を許可するファイアウォール規則が設定されていない場合、**[新しいファイアウォール規則の作成]** フォームが開きます。 フォームを完成させて新しいファイアウォール規則を作成します。 詳細については、[ファイアウォール規則](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)を参照してください。

   ![新しいファイアウォール規則](media/quickstart-sql-database/firewall.png)  

4. サーバーの接続が正常に開いたら、*サーバー*サイドバーです。

## <a name="create-the-tutorial-database"></a>チュートリアルのデータベースを作成します。

次のセクションでは、作成、 *TutorialDB*でいくつか使用されているデータベース[!INCLUDE[name-sos](../includes/name-sos-short.md)]チュートリアル。

1. サーバー サイド バーで、Azure SQL サーバーを右クリックし、選択**新しいクエリ。**

1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

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

クエリ エディターの接続状態を*マスター*でテーブルを作成するデータベースが、 *TutorialDB*データベース。 

1. 接続コンテキストを変更する**TutorialDB**:

   ![コンテキストの変更](media/quickstart-sql-database/change-context.png)



1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

   > [!NOTE]
   > これには、追加したり、エディターで上記のクエリを上書きできます。 クリックする**実行**が選択されている、クエリを実行します。 何も選択されている場合は、クリックして**実行**エディター内のすべてのクエリを実行します。

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

- クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

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


## <a name="view-the-result"></a>結果を表示します
1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます。

   ![結果を選択します。](media/quickstart-sql-database/select-results.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップします。

このコレクション内の他の記事では、このクイック スタートに基づいて構築します。 引き続きクイック スタートで作業する場合は、このクイック スタートで作成したリソースをクリーンアップしないでください。 続行する予定がない場合、次の手順を使用して、Azure portal でこのクイック スタートで作成したリソースを削除します。
不要になったリソース グループを削除することによって、リソースをクリーンアップします。 詳細については、次を参照してください。[リソースをクリーンアップする](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources)します。

## <a name="next-steps"></a>次の手順

これで、Azure SQL database に正常に接続したクエリを実行して、試し、[コード エディターのチュートリアル](tutorial-sql-editor.md)します。
