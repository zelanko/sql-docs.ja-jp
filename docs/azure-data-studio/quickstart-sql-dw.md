---
title: 'クイック スタート: 接続し、Azure SQL Data Warehouse に対するクエリ'
titleSuffix: Azure Data Studio
description: このクイック スタートは、Azure Data Studio を使用して Azure SQL Data Warehouse に接続し、クエリを実行する方法を示しています。
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: f98f6be4502254910b5c144f08a95181ccf1b2a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800264"
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>クイック スタート: 使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]に接続して、Azure SQL Data Warehouse のデータの照会

このクイック スタートでは、[!INCLUDE[name-sos](../includes/name-sos-short.md)] を使用して、Azure SQL データ ウェアハウスに接続し、TRANSACT-SQL ステートメントを使用して、データを作成、挿入、および選択する方法を説明します。 

## <a name="prerequisites"></a>前提条件
このクイック スタートを完了させるためには、[!INCLUDE[name-sos](../includes/name-sos-short.md)]、および Azure SQL データ ウェアハウス が必要です。

- [[!INCLUDE[name-sos](../includes/name-sos-short.md)]のインストール](download.md)。

SQL データ ウェアハウスをもっていない場合は [SQL データ ウェアハウスを作成](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision) を参照してください。

サーバー名、およびログイン資格情報を覚えておくようにしてください。


## <a name="connect-to-your-data-warehouse"></a>データ ウェアハウスに接続します。

[!INCLUDE[name-sos](../includes/name-sos-short.md)]を使用して、Azure SQL Data Warehouse に接続しデータを照会する

1. [!INCLUDE[name-sos](../includes/name-sos-short.md)] の初回実行時には **[接続]** ページが開きます。 **[接続]** ページが表示されない場合は、 **[接続の追加]** 、または **[サーバー]** サイドバーの **[新しい接続]** アイコンをクリックします。
   
   ![新しい接続のアイコン](media/quickstart-sql-dw/new-connection-icon.png)

2. この記事では*SQL ログイン*を使用しますが、*Windows 認証*もサポートされています。 Azure SQL サーバーのサーバー名、ユーザー名およびパスワードを使用して *、* 次のようにフィールドに入力します。

   | 設定       | 提案される値 | Description |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | 完全修飾サーバー名 | 名前は、このようなものでなければなりません: **sqldwsample.database.windows.net** |
   | **[認証]** | SQL ログイン| このチュートリアルでは、SQL 認証を使用します。 |
   | **ユーザー名** | サーバー管理者アカウント | これはサーバーを作成したときに指定したアカウントです。 |
   | **パスワード (SQL ログイン)** | サーバー管理者アカウントのパスワード | これはサーバーを作成したときに指定したパスワードです。 |
   | **パスワードを保存しますか?** | はい、いいえ | 毎回パスワードを入力したくない場合は、[はい] を選択します。 |
   | **データベース名** | *空白のままに* | 接続先となるデータベースの名前。 |
   | **サーバー グループ** | 選択します <Default> | サーバー グループを作成する場合は、特定のサーバー グループに設定できます。 | 

   ![新しい接続のアイコン](media/quickstart-sql-dw/new-connection-screen.png) 

3. サーバーが接続には、Azure Data Studio を許可するファイアウォール規則を持っていない場合、**新しいファイアウォール ルールの作成**フォームが開きます。 フォームを完成させて新しいファイアウォール規則を作成します。 詳細については、[ファイアウォール規則](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)を参照してください。

   ![新しいファイアウォール規則](media/quickstart-sql-dw/firewall.png)  

4. サーバーの接続が正常に開いたら、*サーバー*サイドバーです。

## <a name="create-the-tutorial-data-warehouse"></a>チュートリアルの data warehouse を作成します。
1. オブジェクト エクスプ ローラーで、サーバーを右クリックし、選択**新しいクエリ。**

1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

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
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```


## <a name="insert-rows"></a>行を挿入する

1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```


## <a name="view-the-result"></a>結果を表示します
1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. クエリの結果が表示されます。

   ![結果を選択します。](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>リソースをクリーンアップする

このコレクション内の他の記事では、このクイック スタートに基づいて構築します。 引き続きクイック スタートで作業する場合は、このクイック スタートで作成したリソースをクリーンアップしないでください。 続行する予定がない場合、次の手順を使用して、Azure portal でこのクイック スタートで作成したリソースを削除します。
不要になったリソース グループを削除することによって、リソースをクリーンアップします。 詳細については、次を参照してください。[リソースをクリーンアップする](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal#clean-up-resources)します。


## <a name="next-steps"></a>次の手順

これで、Azure SQL data warehouse に正常に接続したクエリを実行して、試し、[コード エディターのチュートリアル](tutorial-sql-editor.md)します。
