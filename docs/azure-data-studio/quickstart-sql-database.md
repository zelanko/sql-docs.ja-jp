---
title: 'クイック スタート: 接続し、Azure SQL database のクエリ'
titleSuffix: Azure Data Studio
description: このクイック スタートは、Azure Data Studio を使用して SQL database に接続し、クエリを実行する方法を示しています。
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: efff2a0ac451afb869451735545be6cc50ad15f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778292"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-azure-sql-database"></a>クイック スタート: 使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]に接続して Azure SQL database のクエリ

このクイック スタートで使用する[!INCLUDE[name-sos](../includes/name-sos-short.md)]Azure SQL Database サーバーに接続します。 TRANSACT-SQL (T-SQL) ステートメントを作成し、その他で使用されている TutorialDB データベースのクエリを実行しする[!INCLUDE[name-sos](../includes/name-sos-short.md)]チュートリアル。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了する必要があります[!INCLUDE[name-sos](../includes/name-sos-short.md)]、および Azure SQL Database サーバー。

- [インストールします。 [!INCLUDE[name-sos](../includes/name-sos-short.md)]](download.md)

Azure SQL サーバーを持っていない場合は、次の Azure SQL Database のクイック スタートのいずれかを完了します。 完全修飾サーバー名を覚えてし、後の手順で資格情報でサインインします。

- [DB の作成 - ポータル](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal)
- [DB の作成 - CLI](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-cli)
- [DB の作成 - PowerShell](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-powershell)


## <a name="connect-to-your-azure-sql-database-server"></a>Azure SQL Database サーバーに接続する

[!INCLUDE[name-sos](../includes/name-sos-short.md)]を使用して Azure SQL データベース サーバーへの接続を確立します。

1. 初めて実行する[!INCLUDE[name-sos](../includes/name-sos-short.md)]、**ようこそ**ページを開く必要があります。 表示されない場合、**ようこそ**] ページで、[**ヘルプ** > **ようこそ**。 選択**新しい接続**を開く、**接続**ウィンドウ。
   
   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-icon.png)

2. この記事では、サインインの SQL を使用してが Windows 認証もサポートします。 Azure SQL サーバーのサーバー名、ユーザー名、およびパスワードを使用して、次のフィールドに入力します。

   | 設定       | 提案される値 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 次のように: **servername.database.windows.net**します。 |
   | **[認証]** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバー管理者アカウントのユーザー名 | サーバーの作成に使用するアカウントからユーザー名。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | サーバーの作成に使用するアカウントのパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 選択**はい**たびに、パスワードを入力しない場合。 |
   | **データベース名** | *空白のままに* | ここでサーバーに接続しているだけです。 |
   | **サーバー グループ** | 選択します <Default> | 作成した特定のサーバー グループには、このフィールドを設定できます。 | 

   ![新しい接続のアイコン](media/quickstart-sql-database/new-connection-screen.png)  

3. **[接続]** を選択します。

4. サーバーが接続には、Azure Data Studio を許可するファイアウォール規則を持っていない場合、**新しいファイアウォール ルールの作成**フォームが開きます。 フォームを完成させて新しいファイアウォール規則を作成します。 詳細については、[ファイアウォール規則](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)を参照してください。

   ![新しいファイアウォール規則](media/quickstart-sql-database/firewall.png)  

正常に接続した後、サーバーを開きます、**サーバー**サイドバーです。

## <a name="create-the-tutorial-database"></a>チュートリアルのデータベースを作成します。

次のセクションでは、他のために使用される TutorialDB データベースを作成する[!INCLUDE[name-sos](../includes/name-sos-short.md)]チュートリアル。

1. Azure SQL サーバーを右クリックし、**サーバー**サイド バーと選択**新しいクエリ**します。

1. この SQL クエリ エディターに貼り付けます。

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

1. ツールバーで、次のように選択します。**実行**します。 通知に表示されます、**メッセージ**ウィンドウがクエリの進行状況を表示します。

## <a name="create-a-table"></a>テーブルの作成

クエリ エディターの接続、**マスター**でテーブルを作成するデータベースが、 **TutorialDB**データベース。 

1. 接続、 **TutorialDB**データベース。

   ![コンテキストの変更](media/quickstart-sql-database/change-context2.png)



1. 作成、`Customers`テーブル。 

   クエリ エディターで上記のクエリを置き換えてこのいずれかを選択**実行**します。

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


## <a name="insert-rows-into-the-table"></a>テーブルに行を挿入します。

前のクエリを置き換えてこのいずれかを選択**実行**します。

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

前のクエリを置き換えてこのいずれかを選択**実行**します。

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

クエリの結果を表示します。

   ![結果を選択します。](media/quickstart-sql-database/select-results2.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップする

それ以降のクイック スタートの記事では、ここで作成されたリソースに基づいて構築します。 これらの記事を使用する場合は、必ずこれらのリソースを削除します。 それ以外の場合、Azure portal のでは、不要になったリソースを削除します。 詳細については、次を参照してください。[リソースをクリーンアップする](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources)します。

## <a name="next-steps"></a>次の手順

これで、Azure SQL database とクエリの実行を正常に接続した、[コード エディターのチュートリアル](tutorial-sql-editor.md)します。
