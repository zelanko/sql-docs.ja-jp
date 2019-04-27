---
title: T-SQL (CREATE EXTERNAL LIBRARY) を使用して、SQL Server Machine Learning Services の R パッケージをインストールするには
description: SQL Server 2016 R Services または SQL Server 2017 の Machine Learning Services (In-database) するには、新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: b59f15ace1dc96af537486336e76a209f1c85da7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62507028"
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server"></a>T-SQL (CREATE EXTERNAL LIBRARY) を使用して、SQL Server に R パッケージをインストールするには
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。 選択できる複数の方法はあります。 サーバー管理者が R. に慣れていない T-SQL を使用して最適します。

**適用対象します。**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

[CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)ステートメントでは、R を実行することがなく、インスタンスまたは特定のデータベースにパッケージまたはパッケージのセットを追加する、Python コードを直接またはします。 ただし、このメソッドは、パッケージの準備と追加のデータベースのアクセス許可が必要です。

+ すべてのパッケージには、インターネットからオンデマンドでダウンロードしたのではなく、ローカルの zip ファイルとして利用可能なをする必要があります。

+ すべての依存関係の名前とバージョンで識別され、zip ファイルに含まれる必要があります。 パッケージが使用可能なダウン ストリームのパッケージの依存関係を含む必要な場合、ステートメントが失敗します。 

+ 必要があります**db_owner**またはデータベース ロールの外部ライブラリの作成の権限があります。 詳細については、次を参照してください。 [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)します。

## <a name="download-packages-in-archive-format"></a>アーカイブ形式でパッケージをダウンロードします。

1 つのパッケージをインストールする場合は、zip 形式でパッケージをダウンロードします。

パッケージの依存関係のための複数のパッケージをインストールする方が一般的です。 パッケージには、他のパッケージが必要とする場合は、それらのすべてがインストール時に互いにアクセス可能であることを確認する必要があります。 お勧め[ローカル リポジトリを作成する](create-a-local-package-repository-using-minicran.md)を使用して[miniCRAN](https://andrie.github.io/miniCRAN/) 、パッケージの完全なコレクションをアセンブルするだけでなく[igraph](https://igraph.org/r/)パッケージの依存関係を分析するためです。 間違ったバージョンのパッケージをインストールまたはパッケージの依存関係を省略するには、CREATE EXTERNAL LIBRARY ステートメントが失敗する可能性があります。 

## <a name="copy-the-file-to-a-local-folder"></a>ファイルをローカル フォルダーにコピーします。

サーバー上のローカル フォルダーにすべてのパッケージを含む zip 形式のファイルをコピーします。 サーバー上のファイル システムへのアクセスがない、渡すこともできます完全なパッケージ変数としてバイナリ形式を使用します。 詳細については、次を参照してください。 [CREATE EXTERNAL LIBRARY](../../t-sql/statements/create-external-library-transact-sql.md)します。

## <a name="run-the-statement-to-upload-packages"></a>パッケージをアップロードするステートメントを実行します。

開く、**クエリ**ウィンドウで、管理者特権を持つアカウントを使用します。

T-SQL ステートメントを実行して`CREATE EXTERNAL LIBRARY`圧縮されたパッケージのコレクションをデータベースにアップロードします。

たとえば、次のステートメント名、パッケージ ソースとして、miniCRAN リポジトリを含む、 **randomForest**パッケージ、その依存関係とします。 

```sql
CREATE EXTERNAL LIBRARY randomForest
FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
WITH (LANGUAGE = 'R');
```

任意の名前を使用することはできません。外部ライブラリ名の読み込みや、パッケージを呼び出すときに使用すると思われる同じ名前が必要です。

## <a name="verify-package-installation"></a>パッケージのインストールを確認します。

ライブラリが正常に作成すると場合、は、ストアド プロシージャ内で呼び出して、SQL Server でパッケージを実行できます。
    
```sql
EXEC sp_execute_external_script
@language =N'R',
@script=N'library(randomForest)'
```

## <a name="see-also"></a>関連項目

+ [パッケージ情報の取得](determine-which-packages-are-installed-on-sql-server.md)
+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)
+ [操作方法ガイド](sql-server-machine-learning-tasks.md)