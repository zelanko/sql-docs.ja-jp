---
title: 事前トレーニング済みの機械学習モデルの SQL Server Machine Learning のインストールします。
description: センチメントの分析とイメージの特性付けの事前トレーニング済みモデルを SQL Server 2017 Machine Learning サービス (R または Python) または SQL Server 2016 R Services を追加します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/18/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: fdfb322699045a46630b7aaed4b4811f20be945f
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579082"
---
# <a name="install-pre-trained-machine-learning-models-on-sql-server"></a>事前トレーニング済みの machine learning のモデルでは、SQL Server をインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、Powershell を使用して無料事前トレーニング済みの機械学習モデルを追加する方法を説明します*感情分析*と*イメージ特性付け*R または Python を持つ SQL Server データベース エンジン インスタンスに。統合します。 事前トレーニング済みモデルは、Microsoft とすぐに使用して作成された、インストール後のタスクとして、データベース エンジンのインスタンスに追加します。 これらのモデルの詳細については、次を参照してください。、[リソース](#bkmk_resources)この記事の「します。

インストールされると、事前トレーニング済みモデルは MicrosoftML (R) および microsoftml (Python) ライブラリの特定の機能を実装の詳細と見なされます。 できますに処理するカスタム コードでは独立したリソースとしてもしていない必要があります (ことはできません) を表示したり、カスタマイズ、したり、モデルの再トレーニングまたはその他の関数をペアになっています。 

事前トレーニング済みモデルを使用するには、次の表に示す関数を呼び出します。

| R 関数 (MicrosoftML) | Python 関数 (microsoftml) | 使用方法 |
|--------------------------|-------------------------------|-------|
| [getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | [get_sentiment](https://docs.microsoft.com//machine-learning-server/python-reference/microsoftml/get-sentiment) | テキスト入力には、正、負のセンチメント スコアを生成します。 [詳細については](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)します。|
| [featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | [featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | イメージ ファイルの入力からのテキスト情報を抽出します。 [詳細については](https://blogs.msdn.microsoft.com/mlserver/2017/04/12/image-featurization-with-a-pre-trained-deep-neural-network-model/)します。 |

## <a name="prerequisites"></a>前提条件

機械学習アルゴリズムでは、コンピューターに負荷ができません。 低から中レベルのワークロードでは、すべてのサンプル データを使用したチュートリアルのチュートリアルの完了を含む 16 GB の RAM をお勧めします。

事前トレーニング済みモデルを追加するコンピューターと SQL Server の管理者権限が必要です。

外部スクリプトを有効にする必要があり、SQL Server スタート パッド サービスを実行する必要があります。 インストール手順については、有効にして、これらの機能を確認するための手順を提供します。 

[MicrosoftML の R パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)または[microsoftml Python パッケージ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)事前トレーニング済みモデルが含まれています。

+ [SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md)操作を行わなくてもユーザー側でこの前提条件を満たすために、machine learning ライブラリの両方の言語バージョンが含まれています。 ライブラリが存在するので、これらのライブラリに事前トレーニング済みモデルを追加するのにこの記事で説明する PowerShell スクリプトを使用できます。

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md)、のみ、R は含まない[MicrosoftML パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)すぐします。 MicrosoftML を追加することを実行する必要があります、[コンポーネントのアップグレード](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)します。 コンポーネントのアップグレードの利点の 1 つは、同時に追加できる事前トレーニング済みのモデルでは、これにより、不要な PowerShell スクリプトを実行します。 ただし、既にアップグレードが、事前トレーニング済みモデルを追加するには、初回使用時に実行されなかった、この記事の説明に従って PowerShell スクリプトを実行できます。 SQL Server の両方のバージョンで動作します。 実行する前に、C:\Program files \microsoft SQL Server\MSSQL13 に MicrosoftML ライブラリが存在することを確認します。MSSQLSERVER\R_SERVICES\library します。


<a name="file-location"></a>

## <a name="check-whether-pre-trained-models-are-installed"></a>事前トレーニング済みモデルがインストールされているかどうかを確認します。

R および Python のモデルのインストール パスは次のとおりです。

+ R: の `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library\MicrosoftML\mxLibs\x64`

+ Python: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\Lib\site-packages\microsoftml\mxLibs`

モデル ファイル名は、以下に示します。

+ AlexNet\_Updated.model
+ ImageNet1K\_mean.xml
+ pretrained.model
+ ResNet\_101\_Updated.model
+ ResNet\_18\_Updated.model
+ ResNet\_50\_Updated.model

モデルが既にインストールされている場合に進んで、[検証ステップ](#verify)可用性を確認します。

## <a name="download-the-installation-script"></a>インストール スクリプトをダウンロードします。

クリックして[ https://aka.ms/mlm4sql ](https://aka.ms/mlm4sql)ファイルをダウンロードする**インストール MLModels.ps1**します。

## <a name="execute-with-elevated-privileges"></a>昇格した特権で実行します。

1. PowerShell を起動します。 タスク バーでは、PowerShell のプログラム アイコンを右クリックして**管理者として実行**します。
2. インストールのスクリプト ファイルに完全修飾パスを入力し、インスタンス名を含めます。 ダウンロード フォルダーと既定のインスタンスと仮定すると、このようコマンドになります。

   ```powershell
   PS C:\WINDOWS\system32> C:\Users\<user-name>\Downloads\Install-MLModels.ps1 MSSQLSERVER
   ```

**出力**

インターネットに接続された SQL Server 2017 の Machine Learning 既定インスタンス上で R と Python、次のようなメッセージが表示されます。

   ```powershell
   MSSQL14.MSSQLSERVER
        Verifying R models [9.2.0.24]
        Downloading R models [C:\Users\<user-name>\AppData\Local\Temp]
        Installing R models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\]
        Verifying Python models [9.2.0.24]
        Installing Python models [C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\]
   PS C:\WINDOWS\system32>
   ```

<a name="verify"> </a>

## <a name="verify-installation"></a>インストールの確認

最初に、新しいファイルの確認、 [mxlibs フォルダー](#file-location)します。 次に、モデルが機能していることを確認するデモ コードを実行します。 

### <a name="r-verification-steps"></a>R の検証手順

1. 開始**RGUI します。EXE** C:\Program files \microsoft SQL Server\MSSQL14 にします。MSSQLSERVER\R_SERVICES\bin\x64 します。

2. コマンド プロンプトで次の R スクリプトを貼り付けます。

    ```R
    # Create the data
    CustomerReviews <- data.frame(Review = c(
    "I really did not like the taste of it",
    "It was surprisingly quite good!",
    "I will never ever ever go to that place again!!"),
    stringsAsFactors = FALSE)

    # Get the sentiment scores
    sentimentScores <- rxFeaturize(data = CustomerReviews, 
                                    mlTransforms = getSentiment(vars = list(SentimentScore = "Review")))

    # Let's translate the score to something more meaningful
    sentimentScores$PredictedRating <- ifelse(sentimentScores$SentimentScore > 0.6, 
                                            "AWESOMENESS", "BLAH")

    # Let's look at the results
    sentimentScores
    ```

3. センチメント スコアを表示するには Enter キーを押します。 出力は次のようにする必要があります。

    ```R
    > sentimentScores
                                            Review SentimentScore
    1           I really did not like the taste of it      0.4617899
    2                 It was surprisingly quite good!      0.9601924
    3 I will never ever ever go to that place again!!      0.3103435
    PredictedRating
    1            BLAH
    2     AWESOMENESS
    3            BLAH
    ```

### <a name="python-verification-steps"></a>Python の検証手順

1. 開始**Python.exe** C:\Program files \microsoft SQL Server\MSSQL14 にします。MSSQLSERVER\PYTHON_SERVICES します。

2. コマンド プロンプトで次の Python スクリプトを貼り付けます

    ```python
    import numpy
    import pandas
    from microsoftml import rx_logistic_regression, rx_featurize, rx_predict, get_sentiment

    # Create the data
    customer_reviews = pandas.DataFrame(data=dict(review=[
                "I really did not like the taste of it",
                "It was surprisingly quite good!",
                "I will never ever ever go to that place again!!"]))
                
    # Get the sentiment scores
    sentiment_scores = rx_featurize(
        data=customer_reviews,
        ml_transforms=[get_sentiment(cols=dict(scores="review"))])
        
    # Let's translate the score to something more meaningful
    sentiment_scores["eval"] = sentiment_scores.scores.apply(
                lambda score: "AWESOMENESS" if score > 0.6 else "BLAH")
    print(sentiment_scores)
    ```

3. スコアを印刷するには Enter キーを押します。 出力は次のようにする必要があります。

    ```python
    >>> print(sentiment_scores)
                                                review    scores         eval
    0            I really did not like the taste of it  0.461790         BLAH
    1                  It was surprisingly quite good!  0.960192  AWESOMENESS
    2  I will never ever ever go to that place again!!  0.310344         BLAH
    >>>
    ```

> [!NOTE]
> デモ スクリプトが失敗した場合は、まず、ファイルの場所を確認します。 システムで、SQL Server の複数のインスタンスを持つまたはのインスタンスを実行する - サイド スタンドアロン バージョンと、ミスは環境を読み取るし、誤った場所にファイルを配置するインストール スクリプトのことができます。 通常は、正しい mxlib フォルダーにファイルを手動でコピーの問題を解決します。

## <a name="examples-using-pre-trained-models"></a>事前トレーニング済みモデルの使用例

次のリンクには、事前トレーニング済みモデルを呼び出すことのチュートリアルおよびサンプルのコードが含まれます。

+ [SQL Server Machine Learning Services での Python の感情分析](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/11/01/sentiment-analysis-with-python-in-sql-server-machine-learning-services/)

+ [事前トレーニング済みのディープ ニューラル ネットワーク モデルでのイメージの特性付け](https://blogs.msdn.microsoft.com/mlserver/2017/04/12/image-featurization-with-a-pre-trained-deep-neural-network-model/)

  イメージの事前トレーニング済みモデルでは、指定したイメージの特徴の生成をサポートします。 モデルを使用して、呼び出す、 **featurizeImage**変換します。 イメージが読み込まれるサイズ変更、トレーニング済みモデルを特徴とします。 DNN featurizer の出力は画像の分類の線形モデルのトレーニングに使用されます。 このモデルを使用するには、トレーニング済みモデルの要件を満たすすべてのイメージのサイズを変更する必要があります。 たとえば、AlexNet モデルを使用する場合、イメージ必要がありますを変更する場合 227 x 227 ピクセルです。

+ [コード サンプル:テキストの特徴抽出器を使った感情分析](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

<a name="bkmk_resources"></a> 

## <a name="research-and-resources"></a>調査とリソース

現在利用できるモデルは、センチメント分析とイメージの分類のためのディープ ニューラル ネットワーク (DNN) モデルをします。 Microsoft を使用してすべての事前トレーニング済みモデル トレーニングを受けた[計算 Network Toolkit](https://cntk.ai/Features/Index.html)、または**CNTK**します。

各ネットワークの構成は、次の参照実装に基づくされました。

+ ResNet-18
+ Resnet-50
+ ResNet 101
+ AlexNet

これらのディープ ラーニング モデルの実装方法で使用されるアルゴリズムの詳細については、CNTK を使用してトレーニングすると、次の記事を参照してください。

+ [Microsoft の研究者のアルゴリズム ImageNet チャレンジ マイルス トーンを設定します。](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft Computational Network Toolkit は、最も効率的なの分散深層に優れたコンピューティング性能を学習を提供しています](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="see-also"></a>関連項目

+ [SQL Server 2016 R Services](sql-r-services-windows-install.md)
+ [SQL Server 2017 の Machine Learning サービス](sql-machine-learning-services-windows-install.md)
+ [SQL Server インスタンスで R と Python のコンポーネントをアップグレードします。](../r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
+ [R 用の MicrosoftML パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)
+ [Python 用の microsoftml パッケージ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)
