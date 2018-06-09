---
title: SQL Server の Machine Learning のサービスに R パッケージをインストールする T-SQL (外部ライブラリの作成) を使用して |Microsoft ドキュメント
description: SQL Server 2017 Machine Learning Services (In-database) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7a5a0c394e9a26244661a4ae712d20583c1f1c99
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585484"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>T-SQL (外部ライブラリの作成) を使用して、SQL Server 2017 Machine Learning サービスで R パッケージをインストールするには
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。 選択するための複数の方法があります。 T-SQL を使用して最適 R. に精通しているサーバー管理者

**適用されます。**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)文では、特定のデータベースやインスタンスに R を実行しなくても、パッケージまたはパッケージのセットを追加すること、または Python コードを直接です。 ただし、このメソッドは、パッケージの準備と追加のデータベースのアクセス許可が必要です。

+ すべてのパッケージには、インターネットからオンデマンドでダウンロードしたではなく、ローカルの zip ファイルとして利用可能なをする必要があります。

+ すべての依存関係の名前とバージョン、によって識別され、zip ファイルに含まれる必要があります。 必要なパッケージがない、ダウン ストリームのパッケージの依存関係を含む場合は、ステートメントが失敗します。 

+ 必要があります**db_owner**データベース ロールの外部ライブラリの作成権限を持っているか。 詳細については、「[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。

## <a name="download-packages-in-archive-format"></a>アーカイブ形式でパッケージをダウンロードします。

1 つのパッケージをインストールする場合は、zip 形式でパッケージをダウンロードします。

これは、パッケージの依存関係のための複数のパッケージをインストールする方が一般的です。 パッケージは、他のパッケージを必要とするときにする必要があることを確認してそれらのすべてのインストール中に相互にアクセスできます。 お勧め[ローカル リポジトリを作成する](create-a-local-package-repository-using-minicran.md)を使用して[miniCRAN](http://andrie.github.io/miniCRAN/) 、パッケージの完全なコレクションをアセンブルするだけでなく[igraph](http://igraph.org/r/)パッケージの依存関係を分析するためです。 間違ったバージョンのパッケージをインストールするか、パッケージの依存関係を省略することで、外部ライブラリの作成ステートメントが失敗する可能性があります。 

## <a name="copy-the-file-to-a-local-folder"></a>ファイルをローカル フォルダーにコピーします。

サーバー上のローカル フォルダーにすべてのパッケージを含む zip 形式のファイルをコピーします。 サーバー上のファイル システムへのアクセスがない、渡すこともできます完全なパッケージ変数としてバイナリ形式を使用します。 詳細については、次を参照してください。[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)です。

## <a name="run-the-statement-to-upload-packages"></a>パッケージをアップロードするステートメントを実行します。

開く、**クエリ**ウィンドウで、管理者特権を持つアカウントを使用します。

T-SQL ステートメントを実行`CREATE EXTERNAL LIBRARY`zip 形式のパッケージのコレクションをデータベースにアップロードします。

たとえば、次のステートメントが名前にパッケージのソースとして、miniCRAN リポジトリ、 **randomForest**パッケージ、その依存関係とします。 

```SQL
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

任意の名前を使用することはできません。外部ライブラリ名の読み込みまたはパッケージを呼び出すときに使用するものと同じ名前が必要です。

## <a name="verify-package-installation"></a>パッケージのインストールを確認します。

ライブラリが正常に作成する場合は、ストアド プロシージャ内で呼び出すことによって、SQL Server でパッケージを実行できます。
    
```SQL
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>参照

+ [パッケージ情報の取得](determine-which-packages-are-installed-on-sql-server.md)
+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)
+ [操作方法ガイド](sql-server-machine-learning-tasks.md)