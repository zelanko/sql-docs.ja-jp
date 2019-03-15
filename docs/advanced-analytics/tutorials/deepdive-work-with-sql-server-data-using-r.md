---
title: RevoScaleR のチュートリアル - SQL Server Machine Learning のデータベースとアクセス許可を作成します。
description: R のチュートリアルについては、SQL Server データベースを作成する方法のチュートリアル.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: af64387490de8af43d29742e7b388ab1755896b7
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976342"
---
# <a name="create-a-database-and-permissions-sql-server-and-revoscaler-tutorial"></a>データベースとアクセス許可 (SQL Server と RevoScaleR チュートリアルを) 作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

レッスン 1 では、このチュートリアルを完了するために必要な SQL Server データベースとアクセス許可を設定する方法についてはします。 使用[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)または別のクエリ エディターで、次のタスクを完了します。

> [!div class="checklist"]
> * トレーニングと 2 つの R モデルをスコア付けのデータを格納する新しいデータベースを作成します。
> * 作成およびデータベース オブジェクトを使用するためのアクセス許可を持つデータベース ユーザー ログインを作成します。
  
## <a name="create-the-database"></a>データベースの作成

このチュートリアルでは、データやコードを格納するため、データベースが必要です。 管理者でない場合は、データベースとログインを作成する、データベース管理者に問い合わせてください。 アクセス許可を記述し、データの読み取り、および R スクリプトを実行する必要があります。

1. SQL Server Management studio では、R が有効なデータベース インスタンスに接続します。

2. 右クリック**データベース**、選び**新しいデータベース**します。
  
2. 新しいデータベースの名前を入力します。RevoDeepDive します。
  

## <a name="create-a-login"></a>ログインを作成します
  
1. **[新しいクエリ]** をクリックして、データベース コンテキストを master データベースに変更します。
  
2. 新しい **[クエリ]** ウィンドウで、次のコマンドを実行してユーザー アカウントを作成し、このチュートリアルで使用するデータベースに割り当てます。 必要に応じてデータベースの名前を変更します。

3. ログインを確認する新しいデータベースを選択、展開**セキュリティ**、展開と**ユーザー**します。
  
**Windows ユーザー**
  
```sql
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[RevoDeepDive]

 --Add the new user to tutorial database
USE [RevoDeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**SQL ログイン**

```sql
-- Create new SQL login
USE master
GO
CREATE LOGIN [DDUser01] WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE RevoDeepDive
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

## <a name="assign-permissions"></a>アクセス許可を割り当てる

このチュートリアルでは、R スクリプトなどを作成してテーブルおよびストアド プロシージャを削除し、SQL Server の外部プロセスに R スクリプトを実行して DDL 操作を示します。 この手順では、これらのタスクを許可するアクセス許可を割り当てます。

この例では SQL ログイン (DDUser01) が、Windows ログインを作成した場合は、代わりに使用します。

```sql
USE RevoDeepDive
GO

EXEC sp_addrolemember 'db_owner', 'DDUser01'
GRANT EXECUTE ANY EXTERNAL SCRIPT TO DDUser01
GO
```

## <a name="troubleshoot-connections"></a>接続をトラブルシューティングします。

このセクションでは、データベースを設定する過程で発生する可能性がある一般的な問題を示します。

- **データベースの接続と SQL クエリを確認するにはどうすればよいですか。**
  
    サーバーを使用して R コードを実行する前に、R の開発環境からデータベースにアクセスできることを確認したい場合があります。 [Visual Studio のサーバー エクスプローラー](https://docs.microsoft.com/previous-versions/x603htbk(v=vs.140)) と [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) はどちらも、強力なデータベース接続と管理機能を持つ無償のツールです。
  
    新しいデータベース管理ツールをインストールしたくない場合は、コントロール パネルの [ODBC データ ソース アドミニストレーター](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator?view=sql-server-2017) を使用して、SQL Server インスタンスへのテスト接続を作成できます。 データベースが正しく構成されていて、正しいユーザー名とパスワードを入力した場合は、先に作成したデータベースを表示し、既定のデータベースとして選択することができます。
  
    接続エラーの一般的な理由は、リモート サーバーの接続が有効でないと、名前付きパイプ プロトコルが有効になっていません。 この記事ではその他のトラブルシューティングのヒントをご覧ください。[SQL Server データベース エンジンへの接続のトラブルシューティングを行う](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine)します。
  
- **テーブル名に datareader というプレフィックスが付くのはなぜですか。**
  
    このユーザーとしての既定のスキーマを指定すると**db_datareader**、すべてのテーブルとその他の新しいオブジェクトがこのユーザーによって作成されたプレフィックスが付きます、*スキーマ*名。 スキーマは、オブジェクトを整理するためにデータベースに追加できるフォルダーのようなものです。 スキーマでは、データベース内でのユーザーの権限も定義されています。
  
    スキーマは、1 つの特定のユーザー名に関連付けられたが、ユーザーに対して、_スキーマの所有者_します。 オブジェクトを作成するときは、別のスキーマに作成することを明示的に要求しない限り、常に自分用のスキーマに作成されます。
  
    名前のテーブルを作成する場合など**TestData**、既定のスキーマは、 **db_datareader**、名前のテーブルが作成された`<database_name>.db_datareader.TestData`。
  
    このため、テーブルが異なるスキーマに属していれば、1 つのデータベースに同じ名前の複数のテーブルを含めることができます。
   
    テーブルを検索し、スキーマを指定しない場合、データベース サーバーを所有するスキーマを探します。 そのため、自分のログインに関連付けられているスキーマ内のテーブルにアクセスするときは、スキーマ名を指定する必要はありません。
  
- **DDL 特権を持っていません。それでもチュートリアルを実行できますか。**
  
    [はい] に、他のユーザーにデータの事前読み込みを要求する必要が、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル、および次のレッスンに進んでをスキップします。 DDL 特権を必要とする関数は、可能であれば、チュートリアルでは呼び出されます。

    また、EXECUTE ANY EXTERNAL SCRIPT、アクセス許可を付与する管理者を依頼します。 リモートかどうか、またはを使用して R スクリプトの実行に必要な`sp_execute_external_script`します。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)