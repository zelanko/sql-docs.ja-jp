---
title: "事前トレーニング済みの機械学習モデルを SQL Server のインストール |Microsoft ドキュメント"
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 5d9f60684cc749c35674233fbdaaa222953396d9
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>事前トレーニング済みの機械学習の SQL Server 上のモデルをインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、事前トレーニング済みモデルを SQL Server のインスタンスに追加済みの R Services または Machine Learning のサービスのインストール方法について説明します。

事前トレーニング済みモデルをインストールするオプションは、Microsoft R Server や Machine Learning のサーバーに個別の Windows インストーラーを使用する場合に使用できます。 このインストーラーを使用するを事前トレーニング済みモデルだけを取得またはクエリを使用することができます[コンピューターをアップグレードするコンポーネントを学習](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)SQL Server 2016 または SQL Server 2017 のインスタンスにします。

インストーラーを実行して、事前トレーニング済みモデルをダウンロードしたら、SQL Server を使用するためのモデルを構成する追加の手順があります。 この記事では、プロセスについて説明します。

SQL Server のデータを事前トレーニング済みモデルを使用する方法の例は、SQL Server の Machine Learning チームによってこのブログを参照してください。 

+ [SQL Server の Machine Learning のサービスでの Python のセンチメント分析](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

## <a name="benefits-of-using-pretrained-models"></a>事前トレーニング済みモデルを使用する利点

これらの事前トレーニング済みモデルは、センチメント分析またはイメージの特性付けなどのタスクを実行する必要があり、大規模なデータセットを取得するか、複雑なモデルをトレーニングするためのリソースは持っていないユーザーを支援する作成されました。 事前トレーニング済みモデルを使用するには、テキストおよびイメージ効率的に処理を開始することができます。

現在使用できるモデルは深層ニューラル ネットワーク (DNN) センチメント分析とイメージ分類モデルです。 Microsoft を使用してすべての事前トレーニング済みモデル トレーニングを受けた[計算ネットワーク Toolkit](https://cntk.ai/Features/Index.html)、または**CNTK**です。

各ネットワークの構成が次の参照の実装に基づいています。

+ ResNet-18
+ ResNet-50
+ ResNet-101
+ AlexNet

これらのモデルの詳細については、次を参照してください[事前トレーニング済みの機械学習のセンチメント分析とイメージ検出モデル。](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)

ネットワークの詳細な学習および CNTK を使用してその実装の詳細については、次の記事を参照してください。

+ [Microsoft の調査担当者のアルゴリズム ImageNet チャレンジ マイルス トーンを設定します。](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft 計算ネットワーク Toolkit には、計算パフォーマンスを学習、最も効率的な分散深いが提供しています](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>SQL Server にモデルをインストールする方法

1. Machine Learning のサーバーの Windows ベースの独立したインストーラーを実行します。 ダウンロードの場所を参照してください。

    + [機械学習の windows Server をインストールします。](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
    + [R Server 9.1 を Windows をインストールします。](https://docs.microsoft.com/r-server/install/r-server-install-windows)

2. インストールする機能の選択内容は、のモデルを取得するか、インストーラーを使用して他の更新を実行するかによって異なります。
 
    + これは、Machine Learning のサーバーの新規インストールと、R、Python またはコンポーネントにその他の変更を加えるたくない場合**のみ**事前トレーニング済みモデル オプション。 使用許諾契約書を含む、他のすべてのメッセージをそのまま使用します。

    + 同時に、R または Python コンポーネントをアップグレードするに更新するには使用する言語 (R、Python、またはその両方) を選択し、事前トレーニング済みモデル オプションを選択します。 これらの変更を適用する 1 つまたは複数のインスタンスを選択します。

    + 前のすべての選択のままにして以前に Machine Learning のサーバーをインストールおよび更新されたバインド オプションを使用して R または Python のコンポーネントが場合、**は**、事前トレーニング済みモデルのオプションを選択します。 以前に選択したオプションです。 選択を解除できません。これを行う場合、インストーラーは、コンポーネントを削除します。

3. インストールが完了したら、Windows コマンド プロンプトを開き**管理者として**、し、Microsoft R インストーラーが含まれる SQL Server のセットアップ ブートス トラップ フォルダーに移動します。 SQL Server 2017 の既定のインスタンスで、フォルダーになります。
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017\x64\`

4. RSetup.exe を実行し、インストールするコンポーネント、バージョン、およびこれらの例に示すようにコマンドライン引数を使用して、モデルのソース ファイルを含むフォルダーを指定します。

    + 使用したモデルを使用する**R_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    たとえば、SQL Server の 2017 の既定のインスタンスでの R の事前トレーニング済みモデルの最新バージョンの使用を有効にするには、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    名前付きインスタンスのコマンドは、ようになります次のような

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\R_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + 事前トレーニング済みモデルを使用して、R Server (スタンドアロン) または Machine Learning Server (スタンドアロン).

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "~\R_SERVER\library\MicrosoftML\mxLibs\x64"`

    たとえばを SQL Server 2016 での R Server の既定のインストールでの R の事前トレーニング済みモデルの最新バージョンの使用を有効にするには、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir ‘C:\Program Files\Microsoft SQL Server\130\R_SERVER\library\MicrosoftML\mxLibs\"`
    
    + 事前トレーニング済みモデルを使用する**PYTHON_SERVICES**:

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<SQL_DB_instance_folder>\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    たとえば、事前トレーニング済みモデルの最新バージョンの SQL Server の 2017 の既定のインスタンスでの Python のために使用するには、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    名前付きインスタンスのコマンドは、ようになります次のような

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Python を使用するには、Machine Learning Server (スタンドアロン) を持つモデルに事前トレーニング済み。

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    たとえば、2017 年 1 SQL Server セットアップを使用してマシン ラーニング Server (スタンドアロン) の既定のインストールと仮定した場合、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. バージョン パラメーターは、次の値がサポートされています。

    + リリース候補 0:**されていた 9.1.0.0**
    + リリース候補 1: **9.2.0.22**
    + RTM: **9.2.0.100**
    + 累積更新プログラム 1: **9.2.0.24**

6. 次のモデルを R に追加する必要がありますのインストールが成功した場合は、\_SERVICES または PYTHON\_SERVICES フォルダー。

    - AlexNet\_Updated.model
    - ImageNet1K\_mean.xml
    - pretrained.model
    - ResNet\_101\_Updated.model
    - ResNet\_18\_Updated.model
    - ResNet\_50\_Updated.model


> [!NOTE]
> 
> モデル ファイルへのパスが長い場合は、Python コードから、モデル ファイルを呼び出すときにエラーが表示する可能性があります。 これは、現在の Python 実装の制限によるものです。 この問題は、次のサービス リリースで修正されます。

## <a name="examples"></a>使用例

モデルをインストールした後は、コードから呼び出すことによって、モデルを使用できます。

### <a name="image-featurization-example"></a>イメージの特性付けの例

イメージの事前トレーニング済みモデルを指定するイメージの特性付けがサポートされています。 使用してこの特定のモデルのトレーニングが行われた[CNTK](https://docs.microsoft.com/cognitive-toolkit/)です。 

使用するには、モデルを呼び出す、 **featurizeImage**を変換します。

+ [featurizeImage: Machine Learning イメージの特性付けの変換](https://docs.microsoft.com/r-server/r-reference/microsoftml/featurizeimage)

この例では、2 つ目のコード ブロックを参照してください。 イメージが読み込まれた、サイズ変更、および事前トレーニング済みの convolutional DNN モデルでの特徴です。 DNN featurizer の出力はイメージ分類の線形のモデルのトレーニングに使用されます。

トレーニング済みモデルの要件を満たすため、イメージのサイズを変更する必要があります: トレーニングに使用されるイメージが 224 x 224 px します。 AlexNet モデルを使用していた 227 x 227 に画像をサイズ変更は px します。

```R
 model <- rxFastLinear(
     Label ~ Features,
     data = train,
     mlTransforms = list(
         loadImage(vars = list(Features = "Path")),
         resizeImage(vars = "Features", width = 224, height = 224), 
         extractPixels(vars = "Features"),
         featurizeImage(var = "Features")
         ),
     mlTransformVars = "Path")
```

> [!NOTE]
> パフォーマンスを向上させるために、ネイティブ形式を使用して圧縮されているために、読み取り、または事前トレーニング済みのモデルを変更することはありません。

### <a name="text-analysis-example"></a>テキスト分析の例

事前トレーニング済みのテキストの特性付けのモデルを使用してテキスト分類する方法の例については、次の例を参照してください。

[テキスト フィーチャライザーを使用してセンチメント分析](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)
