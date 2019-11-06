---
title: Python パッケージ情報の取得
description: SQL Server Machine Learning Services で、インストールされている Python パッケージのバージョンやインストール場所などの情報を取得する方法について説明します。
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1aa12da4a138ea8f292fa8b64db00456d3c35fe3
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000450"
---
# <a name="get-python-package-information"></a>Python パッケージ情報の取得

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、SQL Server Machine Learning Services で、インストールされている Python パッケージのバージョンやインストール場所などの情報を取得する方法について説明します。 Python スクリプトの例では、インストールパスやバージョンなどのパッケージ情報を一覧表示する方法を示しています。

## <a name="default-python-library-location"></a>既定の Python ライブラリの場所

SQL Server を使用して machine learning をインストールすると、インストールする言語ごとに1つのパッケージライブラリがインスタンスレベルで作成されます。 Windows では、インスタンスライブラリは SQL Server に登録されているセキュリティで保護されたフォルダーです。

SQL Server でデータベース内で実行されるすべてのスクリプトまたはコードは、インスタンスライブラリから関数を読み込む必要があります。 SQL Server は、他のライブラリにインストールされているパッケージにアクセスできません。 これはリモートクライアントにも当てはまります。サーバーコンピューティングコンテキストで実行されているすべての Python コードでは、インスタンスライブラリにインストールされているパッケージのみを使用できます。
サーバー資産を保護するために、既定のインスタンスライブラリは、コンピューターの管理者のみが変更できます。

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Python のバイナリの既定のパスは次のとおりです。

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Python のバイナリの既定のパスは次のとおりです。

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

既定の SQL インスタンス MSSQLSERVER が想定されます。 SQL Server がユーザー定義の名前付きインスタンスとしてインストールされている場合は、その名前が代わりに使用されます。

現在のインスタンスの既定のライブラリを確認するには、次のステートメントを実行します。 この例では、Python `sys.path`変数に含まれるフォルダーの一覧を返します。 一覧には、現在のディレクトリと標準ライブラリパスが含まれています。

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

変数の詳細と、その`sys.path`変数を使用してモジュールのインタープリターの検索パスを設定する方法については、[モジュールの検索パス](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)に関する説明を参照してください。

## <a name="default-python-packages"></a>既定の Python パッケージ

セットアップ中に Python 機能を選択すると、次の Python パッケージが SQL Server Machine Learning Services と共にインストールされます。

| パッケージ | バージョン |  説明 |
| ---------|---------|--------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | リモートの計算コンテキスト、ストリーミング、データのインポートと変換、モデリング、視覚化、および分析のための rx 関数の並列実行に使用されます。 |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Python で機械学習アルゴリズムを追加します。 |

### <a name="component-upgrades"></a>コンポーネントのアップグレード

既定では、Python パッケージは、サービスパックと累積更新プログラムによって更新されます。 コア Python コンポーネントの追加パッケージと完全バージョンアップグレードは、製品のアップグレードを通じて、または Python サポートを Microsoft Machine Learning Server にバインドすることによってのみ可能です。

詳細については、「 [SQL Server での R および Python コンポーネントのアップグレード](../install/upgrade-r-and-python.md)」を参照してください。

## <a name="default-open-source-python-packages"></a>既定のオープンソースの Python パッケージ

セットアップ中に [Python 言語] オプションを選択すると、Anaconda 4.2 distribution (Python 3.5 経由) がインストールされます。 Python コードライブラリに加えて、標準インストールには、サンプルデータ、単体テスト、およびサンプルスクリプトが含まれています。

> [!IMPORTANT]
> 新しいバージョンの web で SQL Server セットアップによってインストールされた Python のバージョンを手動で上書きすることは避けてください。 Microsoft Python パッケージは、Anaconda の特定のバージョンに基づいています。 インストールを変更すると、それが不安定になる可能性があります。

## <a name="list-all-installed-python-packages"></a>インストールされているすべての Python パッケージの一覧表示

次のスクリプトの例では、インストールされているパッケージとそのバージョンの一覧を表示します。

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
import pkg_resources
import pandas as pd
installed_packages = pkg_resources.working_set
installed_packages_list = sorted(["%s==%s" % (i.key, i.version) for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
  '
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

## <a name="find-a-single-python-package"></a>1つの Python パッケージを検索する

Python パッケージをインストールし、特定の SQL Server インスタンスで使用できるようにするには、ストアドプロシージャを実行してパッケージを読み込み、メッセージを返すことができます。

たとえば、次のコードではパッケージが`scikit-learn`検索されます。
パッケージが見つかった場合、コードは "Package scikit-learn-学習がインストールされています" というメッセージを返します。

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import pkg_resources
pckg_name = "scikit-learn"
pckgs = pandas.DataFrame([(i.key) for i in pkg_resources.working_set], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
  '
```

<a name="get-package-vers"></a>

次の例では、revoscalepy パッケージと Python のバージョンが返されます。

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

+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [R パッケージ情報の取得](r-package-information.md)
+ [新しい R パッケージのインストール](../r/install-additional-r-packages-on-sql-server.md)
+ [R と Python のチュートリアル](../tutorials/machine-learning-services-tutorials.md)
