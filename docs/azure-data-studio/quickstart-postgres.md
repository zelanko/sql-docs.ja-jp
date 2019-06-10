---
title: 'クイック スタート: 接続し、PostgreSQL の照会'
titleSuffix: Azure Data Studio
description: このクイック スタートは、Azure Data Studio を使用して PostgreSQL に接続し、クエリを実行する方法を示しています。
ms.custom: seodec18
ms.date: 03/19/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: rachel-msft
ms.author: raagyema
manager: jroth
ms.openlocfilehash: be8683ae563e4e0676f53203cb40386cf8aa4840
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778332"
---
# <a name="quickstart-connect-and-query-postgresql-using-includename-sosincludesname-sos-shortmd"></a>クイック スタート: 接続し、PostgreSQL を使用したクエリ [!INCLUDE[name-sos](../includes/name-sos-short.md)]
このクイック スタートは、使用する方法を示しています。 [!INCLUDE[name-sos](../includes/name-sos-short.md)] Postgres、に接続し、データベースを作成する SQL ステートメントを使用する*tutorialdb*しクエリを実行します。

## <a name="prerequisites"></a>前提条件

このクイック スタートを完了する必要があります[!INCLUDE[name-sos](../includes/name-sos-short.md)]、用の PostgreSQL 拡張機能 [!含める[名前 sos](../includes/name-sos-short.md)、および PostgreSQL サーバーへのアクセス。

- [[!INCLUDE[name-sos](../includes/name-sos-short.md)] のインストール](download.md)
- [Azure Data Studio 用の PostgreSQL 拡張機能のインストール](postgres-extension.md)します。
- [PostgreSQL のインストール](https://www.postgresql.org/download/)します。 (クラウドを使用して、Postgres データベースを作成する代わりに、[を az postgres](https://docs.microsoft.com/azure/postgresql/quickstart-create-server-up-azure-cli))。 

## <a name="connect-to-postgresql"></a>PostgreSQL に接続します。

1. **[!INCLUDE[name-sos](../includes/name-sos-short.md)]** を実行します。

2. 初めて起動する[!INCLUDE[name-sos](../includes/name-sos-short.md)]、**接続**ダイアログ ボックスが開きます。 **[接続]** ダイアログが開かない場合、 **[サーバー]** ページの **[新しい接続]** アイコンをクリックしてください。

   ![新しい接続のアイコン](media/quickstart-postgresql/new-connection-icon.png)

3. ポップアップ表示されるフォームに移動します。**接続の種類**選択**PostgreSQL**ドロップダウン リストから。


4. PostgreSQL サーバーのサーバー名、ユーザー名、およびパスワードを使用して、残りのフィールドを入力します。 

   ![新しい接続 画面](media/quickstart-postgresql/new-connection-screen.png)  

   | 設定       | 値の例 | 説明 |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **サーバー名** | localhost | 完全修飾サーバー名 |
   | **ユーザー名** | postgres | ログインに使用するユーザー名。 |
   | **パスワード (SQL ログイン)** | *password* | ログインに使用するアカウントのパスワード。 |
   | **Password** | *[確認]* | 接続するたびにパスワードを入力しない場合は、このチェック ボックスをオンにします。 |
   | **データベース名** | \<[Default]\> | データベースを指定する接続を使用する場合は、これを入力します。 |
   | **[サーバー グループ]** | \<[Default]\> | このオプションには、この接続を作成した特定のサーバー グループに割り当てることができます。 | 
   | **名前 (省略可能)** | *空白のままに* | このオプションを使用して、サーバーのフレンドリ名を指定できます。 | 

5. **[接続]** を選択します。 

正常に接続した後、サーバーを開きます、**サーバー**サイドバーです。


## <a name="create-a-database"></a>データベースの作成

次の手順は、という名前のデータベースを作成**tutorialdb**:

1. PostgreSQL のサーバーを右クリックし、**サーバー**サイド バーと選択**新しいクエリ**します。

2. この SQL ステートメントが開いたら、クエリ エディターに貼り付けます。

   ```sql
   CREATE DATABASE tutorialdb;
   ```

3. ツールバーから選択**実行**クエリを実行します。 通知に表示されます、**メッセージ**クエリの進行状況を表示するウィンドウ。

>[!TIP]
> 使用することができます**F5** 、キーボードを使用する代わりにステートメントを実行する**実行**します。

右クリックし、クエリが完了すると、**データベース**選択**更新**を参照してください**tutorialdb**下の一覧で、**データベース**ノード.


## <a name="create-a-table"></a>テーブルの作成

 次の手順でテーブルを作成する、 **tutorialdb**:

1. 接続コンテキストを変更する**tutorialdb**クエリ エディターで、ドロップダウン リストを使用します。 

   ![コンテキストの変更](media/quickstart-postgresql/change-context.png)

2. クエリ エディターに次の SQL ステートメントを貼り付けて、をクリックして**実行**します。 

   > [!NOTE]
   > これを追加するか、エディターで、既存のクエリを上書きします。 クリックすると**実行**強調表示されているクエリのみを実行します。 場合は、何が強調表示をクリックすると**実行**エディター内のすべてのクエリを実行します。

   ```sql
   -- Drop the table if it already exists
   DROP TABLE IF EXISTS customers;
   -- Create a new table called 'customers'
   CREATE TABLE customers(
       customer_id SERIAL PRIMARY KEY,
       name VARCHAR (50) NOT NULL,
       location VARCHAR (50) NOT NULL,
       email VARCHAR (50) NOT NULL
   );
   ```

## <a name="insert-rows"></a>行を挿入する

クエリ ウィンドウに次のスニペットを貼り付けて、をクリックして**実行**:

   ```sql
   -- Insert rows into table 'customers'
   INSERT INTO customers
       (customer_id, name, location, email)
    VALUES
      ( 1, 'Orlando', 'Australia', ''),
      ( 2, 'Keith', 'India', 'keith0@adventure-works.com'),
      ( 3, 'Donna', 'Germany', 'donna0@adventure-works.com'),
      ( 4, 'Janet', 'United States','janet1@adventure-works.com');
   ```

## <a name="query-the-data"></a>データのクエリ

1. クエリ エディターに次のスニペットを貼り付けて、をクリックして**実行**:
   
   ```sql
   -- Select rows from table 'customers'
   SELECT * FROM customers; 
   ```

2. クエリの結果が表示されます。

   ![結果を表示します。](media/quickstart-postgresql/view-results.png)

## <a name="next-steps"></a>次の手順

については、 [Postgres Azure Data Studio で使用可能なシナリオ](postgres-extension.md)します。 