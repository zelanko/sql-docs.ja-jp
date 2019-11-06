---
title: R パッケージ情報の取得
description: SQL Server Machine Learning Services と SQL Server R Services にインストールされている R パッケージに関する情報を取得する方法について説明します。
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 8c3cf3c1debc03c169c585521b8b46dd8b1365c5
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69641159"
---
# <a name="get-r-package-information"></a>R パッケージ情報の取得

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、SQL Server Machine Learning Services と SQL Server R Services にインストールされている R パッケージに関する情報を取得する方法について説明します。 R スクリプトの例では、インストールパスやバージョンなどのパッケージ情報を一覧表示する方法を示しています。

## <a name="default-r-library-location"></a>既定の R ライブラリの場所

SQL Server を使用して machine learning をインストールすると、インストールする言語ごとに1つのパッケージライブラリがインスタンスレベルで作成されます。 Windows では、インスタンスライブラリは SQL Server に登録されているセキュリティで保護されたフォルダーです。

SQL Server でデータベース内で実行されるすべてのスクリプトは、インスタンスライブラリから関数を読み込む必要があります。 SQL Server は、他のライブラリにインストールされているパッケージにアクセスできません。 これはリモートクライアントにも当てはまります。サーバーコンピューティングコンテキストで実行されている R スクリプトでは、インスタンスライブラリにインストールされているパッケージのみを使用できます。
サーバー資産を保護するために、既定のインスタンスライブラリは、コンピューターの管理者のみが変更できます。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
R のバイナリの既定のパスは次のとおりです。

`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
R のバイナリの既定のパスは次のとおりです。

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
R のバイナリの既定のパスは次のとおりです。

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

既定の SQL インスタンス MSSQLSERVER が想定されます。 SQL Server がユーザー定義の名前付きインスタンスとしてインストールされている場合は、その名前が代わりに使用されます。

<!-- I don't think this note is necessary. If you have these other products installed, you'd already know about them.
> [!NOTE]
> If you find other folders having similar subfolder names and files, you probably have a standalone installation of  Microsoft R Server or Machine Learning Server. These server products have different installers and paths: C:\Program Files\Microsoft\R Server\R_SERVER or C:\Program Files\Microsoft\ML SERVER\R_SERVER. For more information, see [Install R Server 9.1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) or [Install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).
-->

現在のインスタンスの既定の R パッケージライブラリを確認するには、次のステートメントを実行します。

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

次のステートメントでは、 [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)を使用して、インスタンスライブラリのパスと、SQL Server によって使用される RevoScaleR のバージョンを返します。

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
> [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)関数は、ローカルコンピューター上でのみ実行できます。 関数は、リモート接続のライブラリパスを返すことはできません。

## <a name="default-r-packages"></a>既定の R パッケージ

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

次の R パッケージは、SQL Server R Services と共にインストールされます。

|パッケージ | バージョン | 説明 |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | リモートの計算コンテキスト、ストリーミング、データのインポートと変換、モデリング、視覚化、および分析のための rx 関数の並列実行に使用されます。 |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | ストアドプロシージャに R スクリプトを含めるために使用されます。 |

::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"

セットアップ中に R 機能を選択すると、次の R パッケージが SQL Server Machine Learning Services と共にインストールされます。

|パッケージ | バージョン | 説明 |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 9.2 | リモートの計算コンテキスト、ストリーミング、データのインポートと変換、モデリング、視覚化、および分析のための rx 関数の並列実行に使用されます。 |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 9.2 | ストアドプロシージャに R スクリプトを含めるために使用されます。 |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| 9.2 | R に機械学習アルゴリズムを追加します。 | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 9.2 | R で MDX ステートメントを記述するために使用されます。 |

::: moniker-end

### <a name="component-upgrades"></a>コンポーネントのアップグレード

既定では、R パッケージはサービスパックと累積更新プログラムによって更新されます。 追加のパッケージとコア R コンポーネントの完全バージョンアップグレードは、製品のアップグレードを通じて、または Microsoft Machine Learning Server に R サポートをバインドすることによってのみ可能です。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
また、コンポーネントのアップグレードを通じて、Microsoft Ml および olapR パッケージを SQL Server インスタンスに追加することもできます。
::: moniker-end

詳細については、「 [SQL Server での R および Python コンポーネントのアップグレード](../install/upgrade-r-and-python.md)」を参照してください。

## <a name="default-open-source-r-packages"></a>既定のオープンソース R パッケージ

R サポートにはオープンソースが含まれているので、base R 関数を呼び出して、追加のオープンソースおよびサードパーティパッケージをインストールできます。 R 言語サポートには、**ベース**、**統計**、**ユーティリティ**などのコア機能が含まれています。 R の基本インストールには、多くのサンプルデータセットと、 **Rgui** (軽量対話型エディター) や**Rgui** (R コマンドプロンプト) などの標準の R ツールも含まれています。

インストールに含まれるオープンソース R のディストリビューションは、 [Microsoft R open (MRO)](https://mran.microsoft.com/open)です。 MRO は、 [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library)などの追加のオープンソースパッケージを含めることによって、base R に値を追加します。

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
SQL Server R Services セットアップを使用して MRO によって提供される R のバージョンは3.2.2 です。
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
SQL Server Machine Learning Services セットアップを使用して MRO によって提供される R のバージョンは3.3.3 です。
::: moniker-end

> [!IMPORTANT]
> 新しいバージョンの web で SQL Server セットアップによってインストールされた R のバージョンを手動で上書きすることは避けてください。 Microsoft R パッケージは、R の特定のバージョンに基づいています。インストールを変更すると、それが不安定になる可能性があります。

## <a name="list-all-installed-r-packages"></a>インストールされているすべての R パッケージの一覧表示

次の例では、 `installed.packages()` [!INCLUDE[tsql](../../includes/tsql-md.md)]ストアドプロシージャで r 関数を使用して、現在の SQL インスタンスの R_SERVICES ライブラリにインストールされている r パッケージの一覧を表示します。 このスクリプトでは、説明ファイルのパッケージ名とバージョンフィールドが返されます。

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);',
@input_data_1 = N'
  '
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

[R パッケージの説明] フィールドのオプションフィールドおよび既定フィールドの詳細につい[https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)ては、「」を参照してください。

## <a name="find-a-single-r-package"></a>1つの R パッケージを検索する

R パッケージをインストールし、特定の SQL Server インスタンスで使用できるようにする場合は、ストアドプロシージャを実行してパッケージを読み込み、メッセージを返すことができます。

たとえば、次のステートメントは、使用可能な場合、[glue](https://cran.r-project.org/web/packages/glue/) パッケージを検索して読み込みます。
パッケージが見つからないか、または読み込めない場合は、"'glue' という名前のパッケージはありません" というテキストを含むエラーが表示されます。

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("glue")'
GO
```

パッケージの詳細については`packageDescription`、「」を参照してください。
次のステートメントは、**glue** パッケージの情報を返します。

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("glue"))
  '
```

## <a name="next-steps"></a>次の手順

+ [新しい R パッケージのインストール](../r/install-additional-r-packages-on-sql-server.md)
+ [Python パッケージ情報の取得](python-package-information.md)
+ [新しい Python パッケージのインストール](../python/install-additional-python-packages-on-sql-server.md)
+ [R と Python のチュートリアル](../tutorials/machine-learning-services-tutorials.md)
