---
title: 'クイック スタート: 接続し、クエリの SQL Operations Studio (プレビュー) を使用して SQL Server |Microsoft ドキュメント'
description: このクイック スタートは、SQL Operations Studio (preview) を使用して SQL Server に接続してクエリを実行する方法を示しています。
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
ms.openlocfilehash: 94a760c815b9933ff4d8d7da3dd24c292fcdc641
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235392"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>クイック スタート: [!INCLUDE[name-sos](../includes/name-sos-short.md)]を使用して SQL サーバーに接続してクエリを問い合わせる
このクイック スタートでは、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用して SQL Server に接続し、TRANSACT-SQL (T-SQL) ステートメントを使用して、[!INCLUDE[name-sos](../includes/name-sos-short.md)] チュートリアルで使用する *TutorialDB* を作成します。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了させるためには、[!INCLUDE[name-sos](../includes/name-sos-short.md)] および SQL Server へのアクセスが必要です。

- [[!INCLUDE[name-sos](../includes/name-sos-short.md)]のインストール](download.md)。

SQL Server へのアクセスを持っていない場合は、次のリンクからプラットフォームを選択してください (SQL ログインとパスワードを覚えておくようにしてください)。
- [Windows - SQL Server 2017 Developer Edition のダウンロード](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS - Docker で SQL Server 2017 をダウンロードする](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker)
- [Linux - SQL Server 2017 Developer Edition のダウンロード](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-overview#install) - *データを作成しクエリを問い合わせる* ための手順に従うだけです。


## <a name="connect-to-a-sql-server"></a>SQL Server に接続する

   
1. **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** を実行します。
1. 初めて*[!INCLUDE[name-sos](../includes/name-sos-short.md)]*を実行する場合、**接続**ダイアログ ボックスが開きます。 **接続**ダイアログが開かない場合、**サーバー**ページの**新しい接続**のアイコンをクリックしてください。
   
   ![新しい接続のアイコン](media/quickstart-sql-server/new-connection-icon.png)

1. この記事では*SQL ログイン*を使用しますが、*Windows 認証*はサポートされています。 次のように、フィールドに入力します。
 
    - **サーバー名:** localhost
    - **認証の種類:** SQL ログイン  
    - **ユーザー名:** SQL Server のユーザー名  
    - **パスワード:** SQL サーバーのパスワード  
    - **データベース名:** このフィールドは空白 
    - **サーバー グループ:** \<既定\>  

   ![新しい接続 画面](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>データベースの作成

次の手順で**TutorialDB**:という名前のデータベースを作成します。

1. サーバーを右クリックして**localhost**を選択して**新しいクエリ。**
1. クエリ ウィンドウに次のスニペットを貼り付けます。 

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

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```
1. クエリを実行する をクリックして**実行**です。

クエリが完了したら、新しい**TutorialDB**データベースの一覧に表示されます。 表示されない場合を右クリックし、**データベース**ノード**更新**です。


## <a name="create-a-table"></a>テーブルの作成

クエリ エディター接続が失われて、*マスター*にテーブルを作成するデータベースですが、 *TutorialDB*データベース。 

1. 接続コンテキストを変更する**TutorialDB**:

   ![変更のコンテキスト](media/quickstart-sql-server/change-context.png)



1. クエリ ウィンドウに次のスニペットを貼り付けるし、をクリックして**実行**:

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

クエリが完了したら、新しい**顧客**テーブルのテーブルの一覧に表示されます。 右クリックする必要があります、 **TutorialDB > テーブル**ノード**更新**です。

## <a name="insert-rows"></a>行を挿入する

- クエリ ウィンドウに次のスニペットを貼り付けるし、をクリックして**実行**:

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



## <a name="view-the-data-returned-by-a-query"></a>クエリによって返されるデータを表示します。
1. クエリ ウィンドウに次のスニペットを貼り付けるし、をクリックして**実行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます。

   ![Select の結果](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>次の手順
これで正常に接続した SQL Server とクエリの実行を試してみてから、[コード エディターのチュートリアル](tutorial-sql-editor.md)です。


