---
title: "SQL Server で R パッケージがインストールされている確認 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5db9405b6ef2e7c1423fa2affe6ad8bca58e5d68
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>SQL Server にインストールされている R パッケージを確認します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server で、R 言語オプションと機械学習をインストールするときに専用のインスタンスによって、R パッケージ ライブラリが作成されます。 サーバー上の各インスタンスには、独自のパッケージ ライブラリがあります。 インスタンスでは、パッケージ ライブラリを共有することはできません。

この記事では、特定の SQL Server インスタンスにインストールされている R パッケージを確認する方法について説明します。

## <a name="generate-r-package-list-using-a-stored-procedure"></a>ストアド プロシージャを使用して R パッケージの一覧を生成します。

次の例は、R 関数を使用して`installed.packages()`で、 [!INCLUDE [tsql](..\..\includes\tsql-md.md)]ストアド プロシージャ、R_SERVICES のライブラリで現在のインスタンスにインストールされているパッケージの行列を取得します。 DESCRIPTION ファイル内のフィールドが解析されないようにするために、名前のみが返されます。

```SQL
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
NameOnly <- packagematrix[,1];
OutputDataSet <- as.data.frame(NameOnly);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250) ))
```

詳細と、R パッケージの説明フィールドの既定のフィールドに関する省略可能な詳細については、次を参照してください。 [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)です。

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>インスタンスにパッケージがインストールされているかどうかを確認してください。

パッケージがインストール済みであること、特定の SQL Server インスタンスに使用できるかどうかを確認する場合、パッケージの読み込みし、メッセージのみを返すには、次のストアド プロシージャ呼び出しを実行することができます。 この例を検索し、使用可能な場合は、RevoScaleR ライブラリを読み込みます。

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

+ パッケージが見つかった場合、メッセージが返されます"コマンド正常に完了します。"。

+ テキストを含むエラーが発生した場合は、パッケージの配置または読み込まれることはできません、:「'MissingPackageName' と呼ばれるパッケージはありません」

## <a name="get-a-list-of-installed-packages-using-r"></a>R を使用するインストール済みのパッケージの一覧を取得します。

R ツールと R 関数を使用すると、複数の方法でインストールまたは読み込み済みのパッケージの一覧を取得できます。 多くの R 開発ツールでは、オブジェクト ブラウザーや、インストール済みパッケージまたは現在の R ワークスペースに読み込まれているパッケージの一覧が提供されます。 このセクションでは、R のコマンドラインからまたは sp で使用できるいくつかの短いコマンド\_実行\_外部\_スクリプト。

+ ローカルの R ユーティリティでは、ベースの R 関数をなど使用`installed.packages()`に含まれている、`utils`パッケージです。 インスタンスの正確な一覧を取得するには、ライブラリ パスを明示的に指定かインスタンス ライブラリに関連付けられた R のツールを使用する必要があります。

+ 特定のコンピューティング コンテキストでパッケージを確認するには、RevoScaleR パッケージから、次の機能を使用できます。 これらの関数を使用して、指定された計算コンテキストでパッケージを識別できます。

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)

たとえば、指定した SQL Server のコンピューティング コンテキストで使用可能なパッケージの一覧を取得する次の R コードを実行します。

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

## <a name="get-library-location-and-version"></a>ライブラリの場所とバージョンを取得します。

次の例では、RevoScaleR のローカル コンピューティング コンテキストでパッケージのバージョンのライブラリの場所を取得します。

```r
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

## <a name="determine-path-of-library-used-by-sql-server"></a>SQL Server で使用されるライブラリのパスを確認します。

機械学習のバインディングを使用してコンポーネントをアップグレードした場合、R ライブラリへのパスを変更する可能性があります。 この場合、R ツールを以前のショートカットは、以前のバージョンを参照場合があります。 確認するため、パスとパッケージのバージョンの SQL Server で使用される、次などのコマンドを実行できます。

```sql
EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    sql_r_path <- rxSqlLibPaths("local")
      print(sql_r_path)
    version_info <-packageVersion("RevoScaleR")
      print(version_info)'
```

**結果**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```
## <a name="see-also"></a>参照

[SQL Server に追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
