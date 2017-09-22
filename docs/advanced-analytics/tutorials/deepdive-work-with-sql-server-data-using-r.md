---
title: "R を使用する SQL Server データの操作 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 0a3d7ba0-4113-4cde-9645-debba45cae8f
caps.latest.revision: 20
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 6aa23c7a8f2daefcf0b138bb39926eb2e377c22b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/21/2017

---
# <a name="work-with-sql-server-data-using-r"></a>R を使用する SQL Server データを操作します。

このレッスンでは、モデルのトレーニングに必要な環境を設定してデータを追加し、データのクイック サマリーを実行します。 このプロセスでは次のタスクを実行します。
  
- 2 つの R モデルのトレーニングとスコアリングに使用するデータを格納するための新しいデータベースを作成します。
  
- ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターの間の通信に使用するアカウント (Windows ユーザーまたは SQL ログイン) を作成します。
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータとデータベース オブジェクトを操作するためのデータ ソースを R で作成します。
  
- R のデータ ソースを使用してデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に読み込みます。
  
- R を使用して変数のリストを取得し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルのメタデータを変更します。
  
- 計算コンテキストを作成して、R コードのリモート実行を有効にします。
  
- リモート計算コンテキストでトレースを有効にする方法について説明します。
  
## <a name="create-the-database-and-user"></a>データベースとユーザーを作成する

このチュートリアルでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で新しいデータベースを作成し、データの読み取りと書き込みおよび R スクリプトの実行のアクセス許可を持つ SQL ログインを追加します。

> [!NOTE]
> データを読み取るだけ場合 R スクリプトを実行するアカウントに SELECT 権限のみが必要です (**db_datareader**ロール) で指定されたデータベースです。 ただし、このチュートリアルでは、データベースを準備し、スコアリング結果を保存するテーブルを作成するために、DDL 管理者特権が必要になります。
> 
> さらに、データベースの所有者でない場合は、アクセス許可、EXECUTE ANY EXTERNAL SCRIPT、R スクリプトを実行できるようにする必要があります。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を有効にするインスタンスを選択し、 **[データベース]**を右クリックして、 **[新しいデータベース]**を選択します。
  
2. 新しいデータベースの名前を入力します。 任意の名前を使用できます。すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトと R スクリプトをそれに合わせて編集してください。
  
    > [!TIP]
    > 更新されたデータベース名を表示するには、 **[データベース]** を右クリックして **[更新]** を選択します。
  
3. **[新しいクエリ]**をクリックして、データベース コンテキストを master データベースに変更します。
  
4. 新しい **[クエリ]** ウィンドウで、次のコマンドを実行してユーザー アカウントを作成し、このチュートリアルで使用するデータベースに割り当てます。 必要に応じてデータベースの名前を変更します。
  
**Windows ユーザー**
  
```SQL
 -- Create server user based on Windows account
USE master
GO
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[DeepDive]

 --Add the new user to tutorial database
USE [DeepDive]
GO
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]
```

**SQL ログイン**

```SQL
-- Create new SQL login
USE master
GO
CREATE LOGIN DDUser01 WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;

-- Add the new SQL login to tutorial database
USE [DeepDive]
GO
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]
```

5. ユーザーが作成されたことを確認するには、新しいデータベースを選択し、 **[セキュリティ]**、 **[ユーザー]**の順に展開します。

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、データベースを設定する過程で発生する可能性がある一般的な問題を示します。

- **データベースの接続と SQL クエリを確認するにはどうすればよいですか。**
  
    サーバーを使用して R コードを実行する前に、R の開発環境からデータベースにアクセスできることを確認したい場合があります。 [Visual Studio のサーバー エクスプローラー](https://msdn.microsoft.com/library/x603htbk.aspx) と [SQL Server Management Studio](/sql-docs/docs/ssms/download-sql-server-management-studio-ssms) はどちらも、強力なデータベース接続と管理機能を持つ無償のツールです。
  
    新しいデータベース管理ツールをインストールしたくない場合は、コントロール パネルの [ODBC データ ソース アドミニストレーター](https://msdn.microsoft.com/library/ms714024.aspx) を使用して、SQL Server インスタンスへのテスト接続を作成できます。 データベースが正しく構成されていて、正しいユーザー名とパスワードを入力した場合は、先に作成したデータベースを表示し、既定のデータベースとして選択することができます。
  
    データベースに接続できない場合は、サーバーでリモート接続が有効になっていること、および名前付きパイプ プロトコルが有効になっていることを確認します。 その他のトラブルシューティングのヒントについては、 [こちらの記事](http://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)を参照してください。
  
- **テーブル名に datareader というプレフィックスが付くのはなぜですか。**
  
    このユーザーの既定のスキーマを **db_datareader**と指定すると、このユーザーが作成するすべてのテーブルとその他の新しいオブジェクトの名前の前には、この " *スキーマ*" が付加されます。 スキーマは、オブジェクトを整理するためにデータベースに追加できるフォルダーのようなものです。 スキーマでは、データベース内でのユーザーの権限も定義されています。
  
    スキーマが 1 つの特定のユーザー名に関連付けられている場合は、そのユーザーはスキーマの所有者と呼ばれます。 オブジェクトを作成するときは、別のスキーマに作成することを明示的に要求しない限り、常に自分用のスキーマに作成されます。
  
    たとえば、*TestData* という名前のテーブルを作成し、既定のスキーマが **db_datareader** である場合、テーブルは "*<データベース名>.db_datareader.TestData*" という名前で作成されます。
  
    このため、テーブルが異なるスキーマに属していれば、1 つのデータベースに同じ名前の複数のテーブルを含めることができます。
   
    テーブルを検索するときにスキーマを指定しないと、データベース サーバーはユーザーが所有するスキーマを探します。 そのため、自分のログインに関連付けられているスキーマ内のテーブルにアクセスするときは、スキーマ名を指定する必要はありません。
  
- **DDL 特権を持っていません。それでもチュートリアルを実行できますか。**
  
    はい。ただし、他のユーザーにデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに事前に読み込んでもらう必要があります。そうすれば、新しいテーブルを作成するセクションを省略できます。 DDL 特権が必要な関数は一般にチュートリアルで呼び出されます。

    また、管理者に依頼して EXECUTE ANY EXTERNAL SCRIPT、アクセス許可を付与します。 リモートかどうか、またはを使用して、R スクリプトを実行する必要がある`sp_execute_external_script`です。

## <a name="next-step"></a>次の手順

[RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)

## <a name="overview"></a>概要

[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)




