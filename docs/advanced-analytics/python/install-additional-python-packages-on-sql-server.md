---
title: "SQL Server に新しい Python パッケージをインストール |Microsoft ドキュメント"
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 78a76403f3212c7619afbf02577075161699fbd6
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="install-new-python-packages-on-sql-server"></a>SQL Server に新しい Python パッケージをインストールします。

この記事では、SQL Server 2017 のインスタンスに新しい Python パッケージをインストールする方法について説明します。

現在の環境にインストールされているパッケージを一覧表示する方法についても説明します。

## <a name="prerequisites"></a>Prerequisites

新しいパッケージをインストールするためのプロセスでは、ほとんどを標準の Python 環境でこのような。 ただし、サーバーには、インターネット接続がない場合は、追加の手順が必要です。

+ Python 言語オプションと Machine Learning Services (In-database) をインストールする必要があります。 手順については、次を参照してください。 [Python Machine Learning のサービス設定](setup-python-machine-learning-services.md)です。

+ 各サーバー インスタンスには、パッケージの個別のコピーをインストールする必要があります。 パッケージは、インスタンス間で共有することはできません。

+ Python 3.5 とは、Windows 環境で使用するパッケージは機能するかどうかを決定します。 

    一般に、インポートして SQL Server 環境で使用したパッケージのほとんどの制限がありません。 考えられる問題は、サーバーまたはファイアウォールによってブロックされているネットワークの機能を使用するパッケージまたは Windows コンピューターにインストールすることはできませんの依存関係を持つパッケージを含めます。

+ パッケージをインストールするには、サーバーへの管理アクセスが必要です。

## <a name="add-a-new-python-package"></a>新しい Python パッケージを追加します。

この例では、SQL Server コンピューター上で直接新しいパッケージをインストールする想定しています。

この例ではインストールされているパッケージが[CNTK](https://docs.microsoft.com/cognitive-toolkit/)、トレーニング、およびニューラル ネットワークのさまざまな種類の共有、カスタマイズをサポートしている Microsoft から深層学習するためのフレームワークです。

> [!TIP]
> ヘルプ、Python のツールを構成する必要がありますか。 これらのブログを参照してください。
> 
> [Machine Learning のサーバーを使用する Python Web サービスの概要](https://blogs.msdn.microsoft.com/mlserver/2017/12/13/getting-started-with-python-web-services-using-machine-learning-server/)
> 
> [David 肘: Microsoft 認知 Toolkit + VS Code](http://dacrook.com/cntk-vs-code-awesome/)

### <a name="step-1-download-the-windows-version-of-the-python-package"></a>手順 1. Python パッケージの Windows バージョンをダウンロードします。

+ Python パッケージをインターネットにアクセスできないと、サーバーをインストールする場合は、別のコンピューターに WHL ファイルをダウンロードし、それをサーバーにコピーする必要があります。

    たとえば、別のコンピューターにダウンロードできます WHL ファイルこのサイトから[https://cntk.ai/PythonWheel/CPU-Only](https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl)、ファイル コピー `cntk-2.1-cp35-cp35m-win_amd64.whl` SQL Server コンピューターのローカル フォルダーにします。

+ SQL Server 2017 は、Python 3.5 を使用します。 Windows のバージョンのパッケージ、および Python 3.5 と互換性があるバージョンを取得することを確認します。

このページには、複数のプラットフォームおよび複数の Python バージョンのダウンロードが含まれています: [CNTK 設定](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine)

### <a name="step-2-open-a-python-command-prompt"></a>手順 2. Python コマンド プロンプトを開きます

SQL Server で使用される既定 Python ライブラリの場所を見つけます。 複数のインスタンスをインストールした場合は、パッケージを追加するインスタンスの PYTHON_SERVICE フォルダーに移動することを確認します。

たとえば、マシン学習サービスがインストールされている既定値を使用して、機械学習が既定のインスタンスで有効になっている場合は、パスはようになります。

    `C:\Program Files\Microsoft SQL  Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`

インスタンスに関連付けられている Python コマンド プロンプトを開きます。

> [!TIP]
> Machine Learning Server または SQL Server に固有に Python 環境をセットアップする設定をお勧めします。

### <a name="step-3-install-the-package-using-pip"></a>手順 3. Pip を使用してパッケージをインストールします。

+ Python のコマンドラインを使用することに慣れている場合は、PIP.exe を使用して、新しいパッケージをインストールします。 検索することができます、 **pip**内のインストーラー、`Scripts`サブフォルダーです。 

    エラーが表示された場合**pip** Python 実行可能ファイルと、Python スクリプト フォルダーのパスを追加するには Windows での PATH 変数に、内部または外部コマンドとして認識されていません。

    完全なパス、**スクリプト**既定のインストール フォルダーは、次のようにします。

    `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Scripts`

+ Python の拡張子を持つ Visual Studio 2017 年 1、または Visual Studio 2015 を使用している場合は、実行`pip install`から、 **Python Environments**ウィンドウです。 をクリックして**パッケージ**、テキスト ボックスに名前またはインストールするパッケージの場所を指定します。 入力する必要はありません`pip install`; これが自動的に入力します。 

    - コンピューターがインターネットにアクセスしている、パッケージの名前または特定のパッケージとバージョンの URL を提供します。 たとえば、Windows および Python 3.5 がサポートされている CNTK のバージョンをインストールするダウンロード URL を指定します。`https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl`

    - コンピューターがインターネットにアクセスできる、する必要がありますがファイルをダウンロードした WHL 事前にします。 次に、ローカル ファイル パスと名前を指定します。 たとえば、次のパスと、サイトからダウンロードした WHL ファイルをインストールするファイルを貼り付けます。`"C:\Downloads\CNTK\cntk-2.1-cp35-cp35m-win_amd64.whl"`

インストールを完了するアクセス許可を引き上げるようにを求められます可能性があります。

インストールの進行状況に応じて、コマンド プロンプト ウィンドウで、ステータス メッセージを確認できます。

```python
pip install https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
Collecting cntk==2.1 from https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl
  Downloading https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp35-cp35m-win_amd64.whl (34.1MB)
    100% |################################| 34.1MB 13kB/s
...
Installing collected packages: cntk
Successfully installed cntk-2.1
```



### <a name="step-4-load-the-package-or-its-functions-as-part-of-your-script"></a>手順 4. スクリプトの一部として、パッケージまたはその機能を読み込む

インストールが完了したら、次の手順で説明したようにパッケージを使用してすぐに開始できます。

CNTK を使用して、深層学習の例については、これらのチュートリアルを参照してください: [CNTK 用 Python API](https://cntk.ai/pythondocs/tutorials.html)

使用するには、パッケージから関数、スクリプトで挿入、標準`import <package_name>`行は、スクリプトの最初のステートメント。

```python
import numpy as np
import cntk as cntk
cntk._version_
```

##  <a name="how-to-view-installed-packages-using-conda"></a>Conda を使用してインストールされているパッケージを表示する方法

インストールされているパッケージの一覧を取得できるさまざまな方法はあります。 たとえばにインストールされているパッケージを表示することができます、 **Python Environments** Visual Studio のウィンドウ。

使用することができます、Python のコマンドラインを使用している場合、 **conda**は SQL Server セットアップによって追加された Anaconda Python 環境に含まれているパッケージ マネージャーです。

現在の環境にインストールされている Python パッケージを表示するには、するには、コマンド プロンプト ウィンドウからこのコマンドを実行します。

```python
conda list
```

詳細については**conda**を作成し、複数の Python 環境の管理を参照してくださいを使用する方法と[conda で環境を管理する](https://conda.io/docs/user-guide/tasks/manage-environments.html)です。
