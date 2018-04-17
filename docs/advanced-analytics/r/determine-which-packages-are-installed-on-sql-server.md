---
title: R の表示または SQL Server にインストールされている Python パッケージ |Microsoft ドキュメント
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 227da5cd4ba9ae91019556cc9bac00aee770a525
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="viewing-r-or-python-packages-installed-on-sql-server"></a>R の表示または SQL Server にインストールされている Python パッケージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python の複数の環境をインストールした複数の R ツールを使用するかは、簡単に間違ったライブラリまたは環境にパッケージをインストールして、後で検索することできません。 

この記事では、いくつかのクエリを現在のバージョンを決定し、現在の SQL Server 環境にインストールされているパッケージを一覧表示を行うこともできますを提供します。

## <a name="verify-the-current-default-library"></a>現在の既定のライブラリを確認してください。

**R** SQL Server の現在のインスタンスの既定のライブラリを確認する次のステートメントを実行します。

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

**Python** SQL Server の現在のインスタンスの既定のライブラリを確認する次のステートメントを実行します。

```sql
EXEC sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

## <a name="generate-a-package-list-using-a-stored-procedure"></a>ストアド プロシージャを使用して、パッケージ リストを生成します。

現在インストールされているパッケージの完全な一覧を取得できる複数の方法はあります。 Sp_execute_external_script からパッケージ一覧のコマンドを実行している 1 つの利点は、インスタンス ライブラリにインストールされているパッケージを取得する保証されていることです。

### <a name="r"></a>R

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

詳細と、R パッケージの説明フィールドの既定のフィールドに関する省略可能な詳細については、次を参照してください。 [ https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)です。

### <a name="python"></a>Python

`pip`モジュールが既定では、インストールされているし、標準的な Python でサポートされるだけでなく、インストールされている一覧のパッケージの多くの操作をサポートしています。 実行することができます`pip`Python からもちろん、コマンド プロンプトが呼び出すことができますもいくつかの pip 関数から`sp_execute_external_script`です。

```sql
execute sp_execute_external_script 
@language = N'Python', 
@script = N'
import pip
import pandas as pd
installed_packages = pip.get_installed_distributions()
installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

実行しているときに`pip`コマンド ラインからは、その他の多くの便利な関数があります:`pip list`がインストールされているすべてのパッケージを取得`pip freeze`によってインストールされているパッケージを一覧表示`pip`、し、それ自体を pip パッケージ一覧が表示されません。依存します。 使用することも`pip freeze`依存ファイルを生成します。

## <a name="verify-whether-a-package-is-installed-with-an-instance"></a>インスタンスにパッケージがインストールされているかどうかを確認してください。

パッケージがインストール済みであること、特定の SQL Server インスタンスに使用できるかどうかを確認する場合、パッケージの読み込みし、メッセージのみを返すには、次のストアド プロシージャ呼び出しを実行することができます。

### <a name="r"></a>R

この例を検索し、使用可能な場合は、RevoScaleR ライブラリを読み込みます。

```sql
EXEC sp_execute_external_script  @language =N'R',
@script=N'require("RevoScaleR")'
GO
```

+ パッケージが見つかった場合、メッセージが返されます"コマンド正常に完了します。"。

+ テキストを含むエラーが発生した場合は、パッケージの配置または読み込まれることはできません、:「'MissingPackageName' と呼ばれるパッケージはありません」

### <a name="python"></a>Python

Python の同等のチェックを実行できる、Python からシェルを使用して`conda`または`pip`コマンド。 また、ストアド プロシージャでこのステートメントを実行します。

```sql
exec sp_execute_external_script
       @language = N'Python'
       , @script = N'
import pip
import pkg_resources
pckg_name = "revoscalepy"
pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
```

## <a name="view-installed-packages-using-a-utility-or-ide"></a>ユーティリティまたは IDE を使用してインストールされているパッケージを表示します。

ほとんどの開発ツールは、オブジェクト ブラウザーでは、またはインストールされているか、現在のワークスペースまたは環境に読み込まれてパッケージの一覧を提供します。 このセクションでは、一般的な R または Python のツールを使用するための短いヒントを示します。

### <a name="r-tools"></a>R のツール

R ユーティリティを使用してインストールまたは読み込み済みのパッケージの一覧を取得する複数の方法はあります。 

+ ローカルの R ユーティリティでは、ベースの R 関数をなど使用`installed.packages()`に含まれている、`utils`パッケージです。 インスタンスの正確な一覧を取得するには、ライブラリ パスを明示的に指定かインスタンス ライブラリに関連付けられた R のツールを使用する必要があります。

### <a name="python-tools"></a>Python tools

Visual Studio 用 Python の拡張機能しやすい非常に現在の環境で、または IDE で表示されている他の仮想環境でインストールされているパッケージを表示します。 複数の環境を構成して、一覧から環境を選択し、パッケージを表示するか、またはその環境に新しいパッケージをインストールできます。

+ [Python environments](https://docs.microsoft.com/visualstudio/python/managing-python-environments-in-visual-studio)

Visual Studio のコードは、使用可能ないくつかの Python linters で Python をサポートする無料エディターです。 VS Code から Visual Studio でのようなパッケージ ブラウザーできませんが、構成して、複数の環境間の切り替えをサポートします。

+ [Visual Studio のコードでの Python](https://code.visualstudio.com/docs/languages/python)

追加の構成を実行する必要があります**revoscalepy**リモート クライアントからのコマンド。

+ [Windows では、カスタムの Python パッケージおよびインタープリターをローカルにインストールします。](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)

このブログを使用する、PyCharm を含む、他の Python 環境の構成に役立つヒントを提供する**revoscalepy**です。

+ [Machine Learning のサーバーを使用する Python Web サービスの概要します。](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)

## <a name="use-functions-from-machine-learning-server"></a>Machine Learning のサーバーから機能を使用します。

リモート クライアントからのコードのサポートを実行する SQL Server に使用される、ライブラリを含むパッケージを調べるにはこれらの関数を使用できるため、リモート環境でインストールされます。

### <a name="revoscaler"></a>RevoScaleR

リモート クライアントで作業しているし、サーバーへのアクセス権がない場合は、RevoScaleR 関数を使用して、SQL Server にインストールされているパッケージの一覧を引き続き取得できます。 SQL Server を指定するには、サーバーに接続する権限が必要ですが、コンピューティング コンテキストとして。 

+ [rxFindPackage](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxfindpackage)リモート計算コンテキストでパッケージのパスを検索します。

+ [rxInstalledPackages](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxinstalledpackages)コンピューティング コンテキストでインストールされているパッケージに関する情報を取得します。

たとえば、指定した SQL Server のコンピューティング コンテキストで使用可能なパッケージの一覧を取得する次の R コードを実行します。

```R
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```

次の例では、RevoScaleR のローカル コンピューティング コンテキストでパッケージのバージョンのライブラリの場所を取得します。

```R
rxFindPackage(RevoScaleR, "local")
packageVersion("RevoScaleR")
```

### <a name="revoscalepy"></a>revoscalepy

この時点では、RevoScaleR のものに類似した関数を使用できません。 以降のバージョンのファイルの場所に**revoscalepy**です。

## <a name="get-library-location-and-version"></a>ライブラリの場所とバージョンを取得します。

場合によって複数の環境または R または Python のインストールを扱う場合は、する必要がありますを実行しているコードによって R. の Python、または正しいワークスペースの適切な環境が使用していることを確認するには

たとえば、機械学習のバインディングを使用してコンポーネントをアップグレードした場合、R ライブラリへのパス可能性があります、既定とは異なるフォルダー。 また、R クライアントまたはスタンドアロン サーバーのインスタンスをインストールする場合は、コンピューターに複数の R ライブラリがあります。

これらの例では、SQL Server で使用されているライブラリのバージョンとパスを取得する方法を示します。

### <a name="r"></a>R

このストアド プロシージャは、インスタンス ライブラリのパスと SQL Server で使用される、RevoScaleR パッケージのバージョンを返します。

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)関数は、ターゲット コンピューター上でのみ実行できます。 関数は、リモート接続のライブラリ パスを返すことはできません。

**結果**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.2.1'
```

### <a name="python"></a>Python

この例には、Python に含まれるフォルダーの一覧が返されます`sys.path`変数。 一覧には、現在のディレクトリ、および標準ライブラリ パスが含まれています。

```sql
EXEC sp_execute_external_script
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

