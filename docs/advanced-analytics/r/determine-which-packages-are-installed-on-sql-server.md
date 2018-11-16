---
title: SQL Server Machine Learning で R と Python のパッケージ情報を取得 |Microsoft Docs
description: R と Python のパッケージ バージョンを確認するのインストールを確認し、SQL Server R Services または Machine Learning サービスでインストールされているパッケージの一覧を取得します。
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 96cda599e260982b26e6c565bd38c5097fc01763
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291538"
---
#  <a name="get-r-and-python-package-information"></a>R と Python のパッケージ情報を取得します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

場合によって複数の環境または R または Python のインストールを扱う場合は、必要があります R 向けの Python、または適切なワークスペースを実行しているコードは、予想される環境を使って確認するには例では、機械学習によってコンポーネントをアップグレードした場合、[バインド](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)、既定値は異なるフォルダーで、R ライブラリへのパスがあります。 また、R クライアントまたはスタンドアロン サーバーのインスタンスをインストールする場合は、コンピューターに複数の R ライブラリがあります。

この記事では R と Python スクリプトの例では、SQL Server で使用されるパッケージのバージョンとパスを取得する方法を示します。

## <a name="get-the-r-library-location"></a>R ライブラリの場所を取得します。

SQL Server の任意のバージョンを確認する次のステートメントを実行、[既定の R パッケージ ライブラリ](installing-and-managing-r-packages.md)の現在のインスタンス。

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

必要に応じて、使用[rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) RevoScaleR SQL Server 2017 Machine Learning Services での新しいバージョンでまたは[R Services は、R を少なくともアップグレード RevoScaleR 9.0.1](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。 このストアド プロシージャには、インスタンスのライブラリのパスと SQL Server で使用される RevoScaleR のバージョンが返されます。

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)関数をローカル コンピューター上でのみ実行できます。 関数は、リモート接続のライブラリ パスを返すことはできません。

**結果**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Python ライブラリの場所を取得します。

**Python**で SQL Server 2017 では、現在のインスタンスの既定のライブラリを確認する次のステートメントを実行します。 この例は、Python に含まれるフォルダーの一覧を返します`sys.path`変数。 一覧には、現在のディレクトリと標準ライブラリのパスが含まれています。

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**結果**

```text
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

変数の詳細については`sys.path`とモジュールのインタープリターの検索パスを設定するために、方法を参照してください、 [Python のドキュメント](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>すべてのパッケージを一覧表示します。

現在インストールされているパッケージの完全な一覧を取得する複数の方法はあります。 Sp_execute_external_script からパッケージ一覧のコマンドを実行する利点の 1 つは、あるインスタンス ライブラリにインストールされているパッケージを取得することが保証されます。

### <a name="r"></a>R

次の例では、R 関数を使用して`installed.packages()`で、 [!INCLUDE [tsql](..\..\includes\tsql-md.md)]ストアド プロシージャを現在のインスタンスの R_SERVICES ライブラリにインストールされているパッケージの行列を取得します。 このスクリプトは、DESCRIPTION ファイル内のパッケージの名前とバージョンのフィールドを返します、名だけが返されます。

```SQL
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

詳細と、R パッケージの説明フィールドの既定のフィールド オプションについては、次を参照してください。 [ https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)します。

### <a name="python"></a>Python

`pip`モジュールが既定では、インストールされているし、標準的な Python でサポートされているものに加えて、一覧がインストールされているパッケージの多くの操作をサポートしています。 実行することができます`pip`、Python からコマンド プロンプト、もちろんですが、呼び出すこともできますから一部の pip 関数`sp_execute_external_script`します。

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
  import pip
  import pandas as pd
  installed_packages = pip.get_installed_distributions()
  installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
  df = pd.DataFrame(installed_packages_list)
  OutputDataSet = df'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

実行しているときに`pip`、コマンドラインからは、その他の多数の役立つ機能があります:`pip list`がインストールされているすべてのパッケージを取得`pip freeze`によってインストールされるパッケージを一覧表示`pip`、および自体の pip パッケージを一覧表示しません依存します。 使用することも`pip freeze`依存関係ファイルを生成します。

## <a name="find-a-single-package"></a>1 つのパッケージを検索します。

パッケージがインストールされている特定の SQL Server インスタンスに使用可能なであるかどうかを確認する場合、パッケージの読み込みし、メッセージのみを返すには、次のストアド プロシージャ呼び出しを実行できます。

### <a name="r"></a>R

この例では、検索され、使用可能な場合は、RevoScaleR ライブラリを読み込みます。

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ メッセージが返されます、パッケージが見つかった場合:「コマンドの完了しました」。

+ テキストを含むエラーが発生した場合は、パッケージの配置または読み込まれることはできません、:「'MissingPackageName' という名前のパッケージはありません」

### <a name="python"></a>Python

Python の同等のチェックを実行するには、Python からシェルを使用して`conda`または`pip`コマンド。 または、ストアド プロシージャでこのステートメントを実行します。

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
  import pip
  import pkg_resources
  pckg_name = "revoscalepy"
  pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
  installed_pckg = pckgs.query(''key == @pckg_name'')
  print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

<a name="get-package-vers"></a>

## <a name="get-package-version"></a>パッケージのバージョンを取得します。

すれば、R と Python package Management Studio を使用してバージョン情報。

### <a name="r-package-version"></a>R パッケージのバージョン

このステートメントは、RevoScaleR パッケージのバージョンと基本の R のバージョンを返します。

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("RevoScaleR"))
print(packageDescription("base"))
'
```

### <a name="python-package-version"></a>Python パッケージのバージョン

このステートメントは、revoscalepy パッケージのバージョンと Python のバージョンを返します。

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import revoscalepy
import sys
print(revoscalepy.__version__)
print(sys.version)
'
```

## <a name="next-steps"></a>次の手順

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)