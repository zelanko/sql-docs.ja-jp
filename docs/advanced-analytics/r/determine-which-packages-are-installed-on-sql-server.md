---
title: "SQL Server で R パッケージがインストールされている確認 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/09/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c570f5643880b1111889e29e6de03bbff4b10e1d
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="determine-which-r-packages-are-installed-on-sql-server"></a>SQL Server にインストールされている R パッケージを確認します。

SQL Server で、R 言語オプションと機械学習をインストールするときに、セットアップには、インスタンスに関連付けられた R パッケージ ライブラリが作成されます。 各インスタンスには、個別のパッケージ ライブラリがあります。 パッケージのライブラリが**いない**インスタンス間で共有すると、実行できないことが別のインスタンスにインストールされている他のパッケージでします。

この記事では、特定のインスタンスにインストールされている R パッケージを確認する方法について説明します。

## <a name="generate-r-package-list-using-a-stored-procedure"></a>ストアド プロシージャを使用して R パッケージの一覧を生成します。

次の例は、R 関数を使用して`installed.packages()`で、 [!INCLUDE [tsql](..\..\includes\tsql-md.md)]ストアド プロシージャ、R_SERVICES のライブラリで現在のインスタンスにインストールされているパッケージの行列を取得します。 DESCRIPTION ファイル内のフィールドが解析されないようにするために、名前のみが返されます。

```SQL
EXECUTE sp_execute_external_script
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```

詳細と、R パッケージの説明ファイルの既定のフィールドは省略可能なに関する詳細については、次を参照してください。 [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)です。

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>インスタンスにパッケージがインストールされているかどうかを確認してください。

パッケージがインストール済みであること、特定の SQL Server インスタンスに使用できるかどうかを確認する場合、パッケージの読み込みし、メッセージのみを返すには、次のストアド プロシージャ呼び出しを実行することができます。

```SQL
EXEC sp_execute_external_script  @language =N'R',
@script=N'library("RevoScaleR")'
GO
```

この例では、検索され、RevoScaleR ライブラリを読み込みます。

+ パッケージが見つかった場合、返されたメッセージがありますのような"コマンド正常に完了します"

+ 次のようなエラーが発生した場合は、パッケージの配置または読み込まれることはできません、:"外部スクリプト エラーが発生しました: library("RevoScaleR") でエラー: RevoScaleR と呼ばれるパッケージはありません"

## <a name="get-a-list-of-installed-packages-using-r"></a>R を使用するインストール済みのパッケージの一覧を取得します。

R ツールと R 関数を使用すると、複数の方法でインストールまたは読み込み済みのパッケージの一覧を取得できます。 多くの R 開発ツールでは、オブジェクト ブラウザーや、インストール済みパッケージまたは現在の R ワークスペースに読み込まれているパッケージの一覧が提供されます。

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
## <a name="see-also"></a>参照

[SQL Server に追加の R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
