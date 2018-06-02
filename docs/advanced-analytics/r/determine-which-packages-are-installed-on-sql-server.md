---
title: SQL Server の Machine Learning の R、Python のパッケージ情報の取得 |Microsoft ドキュメント
description: R、Python のパッケージ バージョンを確認するのインストールを確認し、SQL Server R Services または Machine Learning のサービスにインストールされたパッケージの一覧を取得します。
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 85ea4658ca8b60fc24d7e4f7849de1655eab6082
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707890"
---
#  <a name="get-r-and-python-package-information"></a>R、Python のパッケージ情報を取得します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

場合によって複数の環境または R または Python のインストールを扱う場合は、確認する必要を実行しているコードが使用している、予期される環境の Python または正しいワークスペース R.例では、機械学習を介してコンポーネントをアップグレードした場合、[バインディング](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)、既定値とは異なるフォルダー内の R ライブラリへのパスがあります。 また、R クライアントまたはスタンドアロン サーバーのインスタンスをインストールする場合は、コンピューターに複数の R ライブラリがあります。

この記事で R と Python スクリプトの例では、SQL Server で使用されるパッケージのバージョンとパスを取得する方法を示します。

## <a name="get-the-r-library-location"></a>R ライブラリの場所を取得します。

すべての SQL Server のバージョンでは、ことを確認するには、次のステートメントを実行、[既定 R パッケージ ライブラリ](installing-and-managing-r-packages.md)現在のインスタンス。

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

必要に応じて、使用することができます[rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)新しいバージョンの SQL Server 2017 Machine Learning services RevoScaleR または[でに R Services できます R 最低 RevoScaleR 9.0.1](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。 このストアド プロシージャは、インスタンスのライブラリのパスと SQL Server で使用される RevoScaleR のバージョンを返します。

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
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)関数は、ローカル コンピューター上でのみ実行できます。 関数は、リモート接続のライブラリ パスを返すことはできません。

**結果**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Python ライブラリの場所を取得します。

**Python** SQL Server の 2017 で現在のインスタンスの既定のライブラリを確認する次のステートメントを実行します。 この例には、Python に含まれるフォルダーの一覧が返されます`sys.path`変数。 一覧には、現在のディレクトリ、および標準ライブラリ パスが含まれています。

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

変数の詳細については`sys.path`モジュールの検索パスのインタープリターの設定を使用する方法を参照してくださいおよび、 [Python ドキュメント。](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>すべてのパッケージを一覧表示します。

現在インストールされているパッケージの完全な一覧を取得できる複数の方法はあります。 Sp_execute_external_script からパッケージ一覧のコマンドを実行している 1 つの利点は、インスタンス ライブラリにインストールされているパッケージを取得する保証されていることです。

### <a name="r"></a>R

次の例は、R 関数を使用して`installed.packages()`で、 [!INCLUDE [tsql](..\..\includes\tsql-md.md)]ストアド プロシージャ、R_SERVICES のライブラリで現在のインスタンスにインストールされているパッケージの行列を取得します。 このスクリプトは、DESCRIPTION ファイル内のパッケージの名前とバージョンのフィールドを返します、名だけが返されます。

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

詳細と、R パッケージの説明フィールドの既定のフィールドに関する省略可能な詳細については、次を参照してください。 [ https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)です。

### <a name="python"></a>Python

`pip`モジュールが既定では、インストールされているし、標準的な Python でサポートされるだけでなく、インストールされている一覧のパッケージの多くの操作をサポートしています。 実行することができます`pip`Python からもちろん、コマンド プロンプトが呼び出すことができますもいくつかの pip 関数から`sp_execute_external_script`です。

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

実行しているときに`pip`コマンド ラインからは、その他の多くの便利な関数があります:`pip list`がインストールされているすべてのパッケージを取得`pip freeze`によってインストールされているパッケージを一覧表示`pip`、し、それ自体を pip パッケージ一覧が表示されません。依存します。 使用することも`pip freeze`依存ファイルを生成します。

## <a name="find-a-single-package"></a>1 つのパッケージを検索します。

パッケージがインストール済みであること、特定の SQL Server インスタンスに使用できるかどうかを確認する場合、パッケージの読み込みし、メッセージのみを返すには、次のストアド プロシージャ呼び出しを実行することができます。

### <a name="r"></a>R

この例を検索し、使用可能な場合は、RevoScaleR ライブラリを読み込みます。

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ パッケージが見つかった場合、メッセージが返されます"コマンド正常に完了します。"。

+ テキストを含むエラーが発生した場合は、パッケージの配置または読み込まれることはできません、:「'MissingPackageName' と呼ばれるパッケージはありません」

### <a name="python"></a>Python

Python の同等のチェックを実行できる、Python からシェルを使用して`conda`または`pip`コマンド。 また、ストアド プロシージャでこのステートメントを実行します。

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

## <a name="get-package-information-in-r-and-python-tools"></a>R、Python tools でパッケージ情報を取得します。

すべての前の手順は、SQL Server Management Studio (SSMS) などのツールを使用するいると仮定します。 R、Python のツールを使用する場合は、次の手順は、R、Python またはコマンドラインからライブラリとパッケージの情報を取得する方法を説明します。

### <a name="r-commands"></a>R コマンド

R のインスタンスのライブラリは \Program Files\Microsoft SQL Server\MSSQL14 です。MSSQLSERVER\R_SERVICES\library です。

インスタンスのライブラリからパッケージを使用してこれらの場所から標準の R ツールを起動します。

+ \MSSQL14 です。R コマンド プロンプトの MSSQLSERVER\R_SERVICES\bin\R.exe
+ \MSSQL14 です。R コンソール アプリの MSSQLSERVER\R_SERVICES\bin\x64\Rgui.exe

標準的な R コマンドや RevoScaleR コマンドを使用すると、パッケージ情報を取得します。 RevoScaleR パッケージが自動的に読み込まれます。 

RevoScaleR パッケージ情報を返します。

    > print(Revo.version)

インストールされているすべてのパッケージの一覧が返されます。

    > installed.packages()

R: のバージョンを返す

    > packageDescription("base")

### <a name="python-commands"></a>Python コマンド

Python は、SQL Server 2017 のみサポートされます。 インスタンス用ライブラリ Python は、\Program Files\Microsoft SQL Server\MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\ です。

インスタンスのライブラリからのパッケージが使用されることを確認するには、この場所から Python コマンド ウィンドウを開きます。

+ \MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\Python.exe

対話型のヘルプを開くには。

    > help()

プロンプトで、ヘルプをパッケージの内容、バージョン、およびファイルの場所を取得するには、モジュール名を入力します。

    help> revoscalepy

<a name="pip-conda"></a>

### <a name="python-package-managers-pip-and-conda"></a>Python パッケージ マネージャー (Pip と Conda)

Anaconda には、パッケージを管理するための Python tools が含まれています。 既定のインスタンス、Pip、Conda、およびその他のツールはあります \Program Files\Microsoft SQL Server\MSSQL14 です。MSSQLSERVER\PYTHON_SERVICES\Scripts です。

SQL Server セットアップでは、Pip またはパスから不要な実行可能ファイルを保持する Conda をシステム パスと、実稼働 SQL Server インスタンスでは、ベスト プラクティスは追加されません。 ただし、開発およびテストの環境には、そのコマンドで任意の場所から Pip と Conda の両方を実行するシステムの PATH 環境変数に、Scripts フォルダーを追加します。

1. C:\Program files \microsoft SQL Server\MSSQL14 に移動します。MSSQLSERVER\PYTHON_SERVICES\Scripts

1. 右クリック**conda.exe** > **管理者として実行**、入力と`conda list`現在の環境にインストールされているパッケージの一覧を返します。

1. 同様を右クリックして**pip.exe** > **管理者として実行**、入力と`pip list`同じ情報を返します。 


## <a name="next-steps"></a>次のステップ

+ [新しい R パッケージのインストール](install-additional-r-packages-on-sql-server.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [チュートリアル、サンプル、ソリューション](../tutorials/machine-learning-services-tutorials.md)