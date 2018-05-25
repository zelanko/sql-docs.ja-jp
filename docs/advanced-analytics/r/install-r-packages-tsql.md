---
title: SQL Server の Machine Learning のサービスに R パッケージをインストールする T-SQL (外部ライブラリの作成) を使用して |Microsoft ドキュメント
description: SQL Server 2017 Machine Learning Services (In-database) に新しい R パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/20/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: bbc1adf4868cbfbd02afe5cae3a38fd6223e2d4d
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="use-t-sql-create-external-library-to-install-r-packages-on-sql-server-2017-machine-learning-services"></a>T-SQL (外部ライブラリの作成) を使用して、SQL Server 2017 Machine Learning サービスで R パッケージをインストールするには
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、機械学習が有効になっている SQL Server のインスタンスに新しい R パッケージをインストールする方法について説明します。 選択するための複数の方法があります。 この方法は最適な R. に精通しているサーバー管理者

**適用されます。**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)文では、特定のデータベースやインスタンスに R を実行しなくても、パッケージまたはパッケージのセットを追加すること、または Python コードを直接です。 ただし、このメソッドは、パッケージの準備と追加のデータベースのアクセス許可が必要です。

+ すべてのパッケージは、必要に応じて、インターネットからダウンロードではなく、ローカルの zip ファイルとして使用可能にする必要があります。

+ すべての依存関係の名前とバージョン、によって識別され、zip ファイルに含まれる必要があります。 必要なパッケージがない、ダウン ストリームのパッケージの依存関係を含む場合は、ステートメントが失敗します。 

+ データベースでは、必要なアクセス許可が必要です。 詳細については、「[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)です。

## <a name="download-packages-in-archive-format"></a>アーカイブ形式でパッケージをダウンロードします。

1 つのパッケージをインストールする場合は、zip 形式でパッケージをダウンロードします。

パッケージには、他のパッケージが必要とする場合は、必要なパッケージが利用できることを確認する必要があります。 MiniCRAN を使用して、対象パッケージを分析し、すべての依存関係を識別することができます。 使用することをお勧め[ **miniCRAN** ](create-a-local-package-repository-using-minicran.md)または[ **igraph** ](http://igraph.org/r/)パッケージの依存関係を分析するためです。 間違ったバージョンのパッケージまたはパッケージの依存関係をインストールすると、ステートメントが失敗することもあります。 

## <a name="copy-the-file-to-a-local-folder"></a>ファイルをローカル フォルダーにコピーします。

サーバー上のローカル フォルダーにすべてのパッケージを含む zip 形式のファイルをコピーします。 サーバー上のファイル システムへのアクセスがない、渡すこともできます完全なパッケージ変数としてバイナリ形式を使用します。 詳細については、次を参照してください。[外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)です。

## <a name="run-the-statement-to-upload-packages"></a>パッケージをアップロードするステートメントを実行します。

開く、**クエリ**ウィンドウで、管理者特権を持つアカウントを使用します。

T-SQL ステートメントを実行`CREATE EXTERNAL LIBRARY`zip 形式のパッケージのコレクションをデータベースにアップロードします。

    For example, the following statement names as the package source a miniCRAN repository containing the **randomForest** package, together with its dependencies. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    You cannot use an arbitrary name; the external library name must have the same name that you expect to use when loading or calling the package.

## <a name="verify-package-installation"></a>パッケージのインストールを確認します。

ライブラリが正常に作成する場合は、ストアド プロシージャ内で呼び出すことによって、SQL Server でパッケージを実行できます。
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

