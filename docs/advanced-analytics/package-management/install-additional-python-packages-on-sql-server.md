---
title: Pip を使用して Python パッケージをインストールする
description: Python pip を使用して SQL Server Machine Learning Services のインスタンスに新しい Python パッケージをインストールする方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 2e3452a6aad04d0d524e4eb0e6bd473fd39a2bf7
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542152"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Sqlmlutils を使用して Python パッケージをインストールする

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この記事では、 [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils)パッケージの関数を使用して、SQL Server Machine Learning Services のインスタンスに新しい Python パッケージをインストールする方法について説明します。 インストールするパッケージは、 [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) t-sql ステートメントを使用して、データベース内で実行されている Python スクリプトで使用できます。

パッケージの場所とインストールパスの詳細については、「 [Python パッケージ情報の取得](../package-management/python-package-information.md)」を参照してください。

> [!NOTE]
> Python パッケージを SQL Server に追加する場合は、標準の Python `pip install` コマンドを使用しないことをお勧めします。 代わりに、この記事で説明されているように**sqlmlutils**を使用します。

## <a name="prerequisites"></a>[前提条件]

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)を Python 言語オプションと共にインストールする必要があります。

+ SQL Server に接続するために使用するクライアントコンピューターに[python](https://www.python.org/)をインストールします。 また、python の[拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-python.python)を使用した[Visual Studio Code](https://code.visualstudio.com/download)などの python 開発環境が必要になる場合もあります。 

+ SQL Server への接続に使用するクライアントコンピューターに、 [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is)または[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) をインストールします。 他のデータベース管理ツールまたはクエリツールを使用することもできますが、この記事では Azure Data Studio または SSMS を前提としています。

### <a name="other-considerations"></a>その他の考慮事項

+ パッケージは Python 3.5 に準拠し、Windows 上で実行する必要があります。

+ Python パッケージライブラリは SQL Server インスタンスの Program Files フォルダーにあります。既定では、このフォルダーにインストールするには管理者権限が必要です。 詳細については、「[パッケージライブラリの場所](../package-management/python-package-information.md#default-python-library-location)」を参照してください。

+ パッケージのインストールはインスタンス単位です。 Machine Learning Services のインスタンスが複数ある場合は、パッケージを各インスタンスに追加する必要があります。

+ パッケージを追加する前に、パッケージが SQL Server 環境に適しているかどうかを検討してください。

  + データベースをクエリするだけのタスクではなく、機械学習などのデータベースエンジンとの緊密な統合のメリットが得られるタスクには、データベース内の Python を使用することをお勧めします。

  + サーバーで計算の負荷が大きくなるパッケージを追加すると、パフォーマンスが低下します。

  + セキュリティが強化された SQL Server 環境では、次のことを避けることをお勧めします。
    + ネットワークアクセスを必要とするパッケージ
    + 管理者特権でのファイルシステムアクセスが必要なパッケージ
    + SQL Server 内部で実行しても効果のない web 開発などのタスクに使用されるパッケージ

## <a name="install-sqlmlutils-on-the-client-computer"></a>クライアントコンピューターに sqlmlutils をインストールする

**Sqlmlutils**を使用するには、最初に、SQL Server への接続に使用するクライアントコンピューターにインストールする必要があります。

1. 最新の**sqlmlutils** zip ファイルを https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist からクライアントコンピューターにダウンロードします。 ファイルを解凍しないでください。

1. **コマンドプロンプト**を開き、次のコマンドを実行して**sqlmlutils**パッケージをインストールします。 ダウンロードした**sqlmlutils** zip ファイルの完全なパスに置き換えます。この例では、ダウンロードしたファイルが `c:\temp\sqlmlutils_0.6.0.zip` であることを前提としています。

   ```console
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils_0.6.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>SQL Server に Python パッケージを追加する

次の例では、SQL Server に[テキストツール](https://pypi.org/project/text-tools/)パッケージを追加します。

### <a name="add-the-package-online"></a>パッケージをオンラインで追加する

SQL Server への接続に使用するクライアントコンピューターがインターネットにアクセスできる場合は、 **sqlmlutils**を使用して、インターネット経由で**テキストツール**パッケージと依存関係を検索し、そのパッケージを SQL Server インスタンスにリモートでインストールできます。

1. クライアントコンピューターで、 **python**または python 環境を開きます。

1. 次のコマンドを使用して、**テキストツール**パッケージをインストールします。 独自の SQL Server データベース接続情報を置き換えます (Windows 認証を使用しない場合は、`uid` パラメーターと `pwd` パラメーターを追加します)。

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>パッケージをオフラインで追加する

SQL Server への接続に使用するクライアントコンピューターにインターネット接続がない場合は、インターネットにアクセスできるコンピューターで**pip**を使用して、パッケージとその依存パッケージをローカルフォルダーにダウンロードできます。 次に、パッケージをオフラインでインストールできるクライアントコンピューターにフォルダーをコピーします。

#### <a name="on-a-computer-with-internet-access"></a>インターネットに接続されているコンピューター

1. **コマンドプロンプト**を開き、次のコマンドを実行して、**テキストツール**パッケージを含むローカルフォルダーを作成します。 この例では、`c:\temp\text-tools` フォルダーを作成します。

   ```console
   pip download text-tools -d c:\temp\text-tools
   ```

1. @No__t_0 フォルダーをクライアントコンピューターにコピーします。 次の例では、`c:\temp\packages\text-tools` にコピーしたことを前提としています。

#### <a name="on-the-client-computer"></a>クライアントコンピューターの場合

**Sqlmlutils**を使用して、 **pip**が作成したローカルフォルダーにある各パッケージ (whl ファイル) をインストールします。 どのような順序でパッケージをインストールするかは関係ありません。

この例では、**テキストツール**に依存関係がないため、`text-tools` フォルダーのファイルは1つしかインストールできません。 これに対して、 **scikit-learn**などのパッケージには11個の依存関係があるため、フォルダー ( **scikit-learn**パッケージと11の依存パッケージ) に12個のファイルがあり、それぞれをインストールします。

次の Python スクリプトを実行します。 パッケージの実際のファイルパスと名前、および独自の SQL Server データベースの接続情報に置き換えます (Windows 認証を使用しない場合は、`uid` パラメーターと `pwd` パラメーターを追加します)。 フォルダー内のパッケージファイルごとに `sqlmlutils.SQLPackageManager` ステートメントを繰り返します。

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase")
sqlmlutils.SQLPackageManager(connection).install("c:/temp/packages/text-tools/text_tools-1.0.0-py3-none-any.whl")
```

## <a name="use-the-package-in-sql-server"></a>SQL Server でパッケージを使用する

これで、SQL Server の Python スクリプトでパッケージを使用できるようになりました。 例 :

```python
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
from text_tools.finders import find_best_string
corpus = "Lorem Ipsum text"
query = "Ipsum"
first_match = find_best_string(query, corpus)
print(first_match)
  '
```

## <a name="remove-the-package-from-sql-server"></a>パッケージを SQL Server から削除します。

**テキストツール**パッケージを削除する場合は、前に定義したのと同じ接続変数を使用して、クライアントコンピューターで次の Python コマンドを使用します。

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>参照

+ SQL Server Machine Learning Services にインストールされている Python パッケージに関する情報を表示するには、「 [python パッケージ情報を取得](../package-management/python-package-information.md)する」を参照してください。

+ SQL Server Machine Learning Services での R パッケージのインストールの詳細については、「 [SQL Server に新しい r パッケージをインストール](../r/install-additional-r-packages-on-sql-server.md)する」を参照してください。
