---
title: 新しい Python 言語のパッケージの SQL Server Machine Learning のインストールします。
description: SQL Server 2017 の Machine Learning Services (In-database)、および Machine Learning Server (スタンドアロン) するには、新しい Python パッケージを追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: fc038f94fc24b8c0f795efc18c62acc1656877a7
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432315"
---
# <a name="install-new-python-packages-on-sql-server"></a>SQL Server に新しい Python パッケージをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server 2017 Machine Learning Services のインスタンスに新しい Python パッケージをインストールする方法について説明します。 一般に、新しいパッケージをインストールするプロセスは、標準的な Python 環境のと似ています。 ただし、サーバーには、インターネット接続がない場合は、追加の手順が必要です。

パッケージの場所とインストール パスの詳細については、次を参照してください。[パッケージ情報を取得する R または Python](../r/determine-which-packages-are-installed-on-sql-server.md)します。

## <a name="prerequisites"></a>前提条件

+ [SQL Server 2017 の Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md) Python 言語のオプションを使用します。 

+ パッケージには、Windows での Python 3.5 対応で、実行をする必要があります。 

+ パッケージをインストールするサーバーへの管理アクセスが必要です。

## <a name="considerations"></a>考慮事項

パッケージを追加する前に、パッケージに、SQL Server 環境に適していますがかどうかを検討してください。 通常、データベース サーバーは、複数のワークロードを考慮に入れるため共有資産です。 計算が多すぎる負荷をサーバーに配置するパッケージを追加すると、パフォーマンスが低下します。 

さらに、(Flask) などのいくつかの一般的な Python パッケージは、スタンドアロン環境に適している web 開発などのタスクを実行します。 単に、データベース クエリを実行するタスクではなく、machine learning など、データベース エンジンとの緊密な統合から利点を得られるタスクには、データベース内に Python を使用することをお勧めします。

データベース サーバーは、ダウン頻繁にロックされます。 多くの場合、インターネットへのアクセスを完全にブロックします。 依存関係の長い一覧でのパッケージを事前にこれらの依存関係を特定し、それぞれを手動でインストールする必要があります。

## <a name="add-a-new-python-package"></a>新しい Python パッケージを追加します。

この例では、SQL Server コンピューター上で直接新しいパッケージをインストールすると仮定します。

パッケージのインストールは、インスタンスごとです。 Machine Learning サービスの複数のインスタンスがある場合は、それぞれにパッケージを追加する必要があります。

この例ではインストールされているパッケージは[CNTK](https://docs.microsoft.com/cognitive-toolkit/)、トレーニング、およびニューラル ネットワークのさまざまな種類の共有で、カスタマイズをサポートするマイクロソフトのディープ ラーニング フレームワークです。

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>手順 1. Windows のバージョンの Python パッケージをダウンロードします。

+ インターネットにアクセスできないと、サーバー上の Python パッケージをインストールする場合は、WHL ファイルを別のコンピューターにダウンロードし、サーバーにコピーする必要があります。

    たとえば、別のコンピューターにダウンロードできます WHL ファイルこのサイトから[ https://cntk.ai/PythonWheel/CPU-Only ](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl)、ファイルをコピー `cntk-2.1-cp35-cp35m-win_amd64.whl` SQL Server コンピューター上のローカル フォルダーにします。

+ SQL Server 2017 では、Python 3.5 を使用します。 

> [!IMPORTANT]
> パッケージの Windows バージョンを取得できることを確認します。 .Gz のファイルが終了した場合、適切なバージョンではない可能性があります。

このページには、複数のプラットフォームおよび複数の Python バージョンのダウンロードが含まれています。[CNTK をセットアップします。](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>手順 2. Python のコマンド プロンプトを開く

SQL Server で使用される既定 Python ライブラリの場所を見つけます。 複数のインスタンスをインストールした場合は、パッケージを追加するインスタンスの PYTHON_SERVICE フォルダーを探します。

たとえば場合は、既定値を使用して Machine Learning サービスがインストールされており、既定のインスタンスで機械学習を有効に、パスはようになります。

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

インスタンスに関連付けられている Python のコマンド プロンプトを開きます。

> [!TIP]
> 将来的では、デバッグとテスト、インスタンスのライブラリに固有の Python 環境を設定する可能性があります。

### <a name="step-3-install-the-package-using-pip"></a>手順 3. Pip を使用してパッケージをインストールします。

+ Python のコマンドラインを使用する場合は、新しいパッケージをインストールする PIP.exe を使用します。 検索することができます、 **pip**内のインストーラー、`Scripts`サブフォルダーです。 

  SQL Server セットアップでは、スクリプトはシステム パスに追加されません。 エラーが発生する場合`pip`Scripts フォルダーを追加するには Windows で PATH 変数に、内部または外部コマンドとして認識されていません。

  完全なパス、**スクリプト**既定のインストール フォルダーを次に示します。

    C:\Program files \microsoft SQL Server\MSSQL14 します。MSSQLSERVER\PYTHON_SERVICES\Scripts

+ Python 拡張機能を Visual Studio 2017 または Visual Studio 2015 を使用する場合は実行できます`pip install`から、 **Python 環境**ウィンドウ。 クリックして**パッケージ**、テキスト ボックスで、名前またはインストールするパッケージの場所を提供します。 入力する必要はありません`pip install`; が自動的に入力できます。 

    - コンピューターにインターネットへのアクセスがある場合は、パッケージの名前または特定のパッケージとバージョンの URL を提供します。 
    
    たとえば、Windows、および Python 3.5 のサポートされている CNTK のバージョンをインストールするには、ダウンロード URL を指定します。 `https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - コンピューターがインターネットへのアクセスを持たない場合は、インストールを開始する前に WHL ファイルをダウンロードする必要があります。 次に、ローカル ファイル パスと名前を指定します。 たとえば、次のパスと、サイトからダウンロードした WHL ファイルをインストールするファイルを貼り付けます。 `"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

インストールを完了するアクセス許可を昇格するように促さ可能性があります。

インストールの進行状況に応じて、コマンド プロンプト ウィンドウにステータス メッセージを確認できます。

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```


### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>手順 4. スクリプトの一部として、パッケージまたはその関数を読み込む

インストールが完了したら、次の手順で説明したようにパッケージを使用してすぐに開始できます。

CNTK を使用したディープ ラーニングの例については、これらのチュートリアルを参照してください。[CNTK は Python API](https://cntk.ai/pythondocs/tutorials.html)

パッケージから関数をスクリプトを使用する挿入の標準`import <package_name>`スクリプトの最初の行のステートメント。

```python
import numpy as np
import cntk as cntk
cntk._version_
```

## <a name="list-installed-packages-using-conda"></a>Conda を使用して、インストールされているパッケージを一覧表示します。

インストールされているパッケージの一覧を取得する別の方法はあります。 インストールされているパッケージを表示するなど、 **Python 環境**Visual Studio のウィンドウ。

Python のコマンドラインを使用している場合は、いずれかを使用**Pip**または**conda**パッケージ マネージャー、SQL Server セットアップによって追加された Anaconda Python 環境に含まれています。

1. C:\Program files \microsoft SQL Server\MSSQL14 に移動します。MSSQLSERVER\PYTHON_SERVICES\Scripts

1. 右クリック**conda.exe** > **管理者として実行**、入力と`conda list`を現在の環境にインストールされているパッケージの一覧を返します。

1. 同様に、右クリック**pip.exe** > **管理者として実行**、入力と`pip list`同じ情報を返します。 

詳細については**conda**の作成し複数の Python 環境の管理、参照を使用する方法と[conda 環境を管理する](https://conda.io/docs/user-guide/tasks/manage-environments.html)します。

> [!Note]
> SQL Server セットアップでは、Pip または Conda をシステム パスと、実稼働 SQL Server インスタンスが、パスから不要な実行可能ファイルを維持することがベスト プラクティスは追加されません。 ただし、開発およびテスト環境で、任意の場所から、コマンドで Pip と Conda の両方を実行するシステムの PATH 環境変数を Scripts フォルダーを追加できます。
