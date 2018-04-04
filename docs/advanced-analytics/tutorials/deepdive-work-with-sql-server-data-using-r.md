---
title: R (SQL と R deep dive) を使用する SQL Server データの操作 |Microsoft ドキュメント
ms.date: 12/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 5cd152ac5da350b216eaf3f517d5da2d1c415a4d
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="work-with-sql-server-data-using-r-sql-and-r-deep-dive"></a>R (SQL と R deep dive) を使用する SQL Server データの操作します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

このレッスンでは、モデルのトレーニングに必要なデータを追加し、データのいくつかの概要を実行環境を設定します。 プロセスの一環として、これらのタスクを完了する必要があります。
  
- 2 つの R モデルのトレーニングとスコアリングに使用するデータを格納するための新しいデータベースを作成します。
  
- ワークステーションと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターの間の通信に使用するアカウント (Windows ユーザーまたは SQL ログイン) を作成します。
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータとデータベース オブジェクトを操作するためのデータ ソースを R で作成します。
  
- R のデータ ソースを使用してデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に読み込みます。
  
- R を使用して変数のリストを取得し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルのメタデータを変更します。
  
- 計算コンテキストを作成して、R コードのリモート実行を有効にします。
  
- (省略可能)リモート計算コンテキストのトレースを有効にします。
  
## <a name="create-the-database-and-user"></a>データベースおよびユーザーを作成します。

このチュートリアルでは、新しいデータベースを作成[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、し、データの読み取りし、書き込みをして、R スクリプトを実行するアクセス許可を持つ SQL ログインを追加します。

> [!NOTE]
> データを読み取るだけ場合、R スクリプトを実行するアカウントに SELECT 権限が必要です (**db_datareader**ロール) で指定されたデータベースです。 ただし、このチュートリアルでは権限が必要 DDL 管理者、データベースを準備して、スコア付けの結果を保存するためのテーブルを作成します。
> 
> さらに、データベースの所有者でない場合は、アクセス許可、EXECUTE ANY EXTERNAL SCRIPT、R スクリプトを実行するために必要があります。

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
  
    サーバーを使用して R コードを実行する前に、R の開発環境からデータベースにアクセスできることを確認したい場合があります。 [Visual Studio のサーバー エクスプローラー](https://msdn.microsoft.com/library/x603htbk.aspx) と [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) はどちらも、強力なデータベース接続と管理機能を持つ無償のツールです。
  
    新しいデータベース管理ツールをインストールしたくない場合は、コントロール パネルの [ODBC データ ソース アドミニストレーター](https://msdn.microsoft.com/library/ms714024.aspx) を使用して、SQL Server インスタンスへのテスト接続を作成できます。 データベースが正しく構成されていて、正しいユーザー名とパスワードを入力した場合は、先に作成したデータベースを表示し、既定のデータベースとして選択することができます。
  
    データベースに接続できない場合は、サーバーでリモート接続が有効になっていること、および名前付きパイプ プロトコルが有効になっていることを確認します。 この記事で説明が追加のトラブルシューティングのヒント: [、SQL Server データベース エンジンへの接続のトラブルシューティングを行う](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine)です。
  
- **テーブル名に datareader というプレフィックスが付くのはなぜですか。**
  
    このユーザーの既定のスキーマを指定すると**db_datareader**、すべてのテーブルと、このユーザーが作成された新しいオブジェクトを他のプレフィックスが付きます、*スキーマ*名。 スキーマは、オブジェクトを整理するためにデータベースに追加できるフォルダーのようなものです。 スキーマでは、データベース内でのユーザーの権限も定義されています。
  
    スキーマは、1 つの特定のユーザー名に関連付けられた、ユーザーが、_スキーマの所有者_です。 オブジェクトを作成するときは、別のスキーマに作成することを明示的に要求しない限り、常に自分用のスキーマに作成されます。
  
    たとえば、名前のテーブルを作成する`*`TestData`, and your default schema is **db\_datareader**, the table is created with the name `< database_name > .db_datareader です。TestData' です。
  
    このため、テーブルが異なるスキーマに属していれば、1 つのデータベースに同じ名前の複数のテーブルを含めることができます。
   
    テーブルを探しているし、スキーマを指定して、自分が所有するスキーマのデータベース サーバーが検索されます。 そのため、自分のログインに関連付けられているスキーマ内のテーブルにアクセスするときは、スキーマ名を指定する必要はありません。
  
- **DDL 特権を持っていません。それでもチュートリアルを実行できますか。**
  
    はい。ただし、他のユーザーにデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに事前に読み込んでもらう必要があります。そうすれば、新しいテーブルを作成するセクションを省略できます。 DDL の特権が必要な関数は、可能な限り、このチュートリアルで呼び出されます。

    また、管理者に依頼して EXECUTE ANY EXTERNAL SCRIPT、アクセス許可を付与します。 リモートかどうか、またはを使用して、R スクリプトを実行する必要がある`sp_execute_external_script`です。

## <a name="next-step"></a>次の手順

[RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)

## <a name="overview"></a>概要

[データ サイエンスの詳細: RevoScaleR パッケージの使用](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)



