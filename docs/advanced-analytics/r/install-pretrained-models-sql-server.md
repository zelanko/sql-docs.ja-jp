---
title: "事前トレーニング済みの機械学習モデルを SQL Server のインストール |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21456462-e58a-44c3-9d3a-68b4263575d7
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: b52fcc1e4ac77df2968a4ea6cbd6e546ff1b74ac
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="install-pretrained-machine-learning-models-on-sql-server"></a>事前トレーニング済みの機械学習の SQL Server 上のモデルをインストールします。

このトピックでは、事前トレーニング済みモデルを SQL Server のインスタンスに追加済みの R Services または Machine Learning のサービスのインストール方法について説明します。

事前トレーニング済みモデルは、Microsoft R Server (または Microsoft Machine Learning のサーバーに更新プログラム) に、更新プログラムで提供されます。 インスタンスをアップグレードおよび Microsoft R の最新バージョンを取得する方法については、次を参照してください。 [R Services のインスタンスで R コンポーネントをアップグレード](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)です。

R Server の Windows ベースの独立したインストーラーを実行しているだけでは、これらのモデルをインストールできます。
ただし、これには、モデルを SQL Server にインストールするときに使用する追加の手順があります。 このトピックでは、プロセスについて説明します。

## <a name="benefits-of-using-pretrained-models"></a>事前トレーニング済みモデルを使用する利点

事前トレーニング済みモデルがの特性付け、画像のまたはセンチメント分析などのタスクを実行する必要がありますが、大規模なデータセットを取得するか、複雑なモデルをトレーニングするリソースがない顧客をサポートするために使用可能な行われました。 事前トレーニング済みモデルを使用するには、テキストおよびイメージ最も効率的に処理を開始することができます。

現在使用できるモデルは深層ニューラル ネットワーク (DNN) センチメント分析とイメージ分類モデルです。 4 つすべての事前トレーニング済みモデルは、CNTK に対してトレーニングされました。 各ネットワークの構成が次の参照の実装に基づいています。

+ ResNet 18
+ ResNet 50
+ ResNet 101
+ AlexNet

深層残存ネットワークおよび CNTK を使用して実装する方法の詳細については、次の記事を参照してください。

+ [Microsoft の調査担当者のアルゴリズム ImageNet チャレンジ マイルス トーンを設定します。](https://www.microsoft.com/research/blog/microsoft-researchers-algorithm-sets-imagenet-challenge-milestone/)

+ [Microsoft 計算ネットワーク Toolkit には、計算パフォーマンスを学習、最も効率的な分散深いが提供しています](https://www.microsoft.com/research/blog/microsoft-computational-network-toolkit-offers-most-efficient-distributed-deep-learning-computational-performance/)

## <a name="how-to-install-the-models-on-sql-server"></a>SQL Server にモデルをインストールする方法

   > [!NOTE]
   > 
   > Microsoft R Server をインストールするか、SQL Server のインスタンスをアップグレードする個別の Windows ベースのインストーラーを使用する場合、事前トレーニング済みモデルはインストーラーから入手できます。 参照してください[インストール R Server for Windows](https://docs.microsoft.com/en-us/r-server/install/r-server-install-windows)です。
   > 
   > 追加の手順は、Microsoft R Server で、モデルを使用する必要があります。 詳細については、次を参照してください[事前トレーニング済み MicrosoftML の機械学習モデルをインストールおよび展開する方法。](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models)

1. 既定では、SQL Server をインストールするときに事前トレーニング済みモデルはインストールされません。SQL Server セットアップが完了したら、コマンド ライン セットアップ ユーティリティを実行して、それらを追加する必要があります。

2. 管理者特権でコマンド プロンプトを開くし、Microsoft R インストーラーが含まれる SQL Server のセットアップ ブートス トラップ フォルダーに移動します。

    SQL Server 2017 年 1 RC 1 の既定のインスタンスにこれは、次のようになります。
    
    `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\SQL2017RC1\x64\`

3. をインストールするコンポーネントと、次の引数を使用して、事前トレーニング済みモデルを追加する必要がありますフォルダーを指定します。

  + 使用したモデルを使用する**R_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\R_SERVICES`

    たとえば、SQL Server 2017 の既定のインスタンスに R を使用する事前トレーニング済みモデルの使用を有効にするには、このステートメントを実行しました。

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES"`

  + 使用したモデルを使用する**PYTHON_SERVICES**

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir <SQL_DB_instance_folder>\PYTHON_SERVICES`

    たとえばの既定のインスタンスの SQL Server の 2017、Python を使用して事前トレーニング済みモデルの使用を有効にするには、このステートメントを実行します。

    `RSetup.exe /install /component MLM /version 9.2.0.22 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES"`

4. バージョン パラメーターには、次の値がサポートされています。

    + リリース候補 0:**されていた 9.1.0.0**
    + リリース候補 1: **9.2.0.22**
    + 最終バージョン番号 (リリースではありません): **9.2.0.100**

5. 次のモデルを R に追加する必要がありますのインストールが成功した場合は、\_SERVICES または PYTHON\_SERVICES フォルダー。

    - AlexNet_Updated.model
    - ImageNet1K_mean.xml
    - pretrained.model
    - ResNet_101_Updated.model
    - ResNet_18_Updated.model
    - ResNet_50_Updated.model

## <a name="examples"></a>使用例

モデルをインストールした後は、R コードから呼び出すことによって、モデルを使用できます。

### <a name="image-featurization-example"></a>イメージの特性付けの例

イメージの事前トレーニング済みモデルを指定するイメージの特性付けがサポートされています。 使用するには、モデルを呼び出す、 **featurizeImage**を変換します。

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
> 
> 読み取り、または事前トレーニング済みモデル自体を変更することはできません。 この特定のモデルに基づいている[CNTK](https://docs.microsoft.com/cognitive-toolkit/)モデルが、パフォーマンス向上のためのネイティブ形式を使用して圧縮されました。

### <a name="text-analysis-example"></a>テキスト分析の例

このサンプルでは、分類の事前トレーニング済みモデルの使用を示します。

[テキスト フィーチャライザーを使用してセンチメント分析](https://github.com/Microsoft/microsoft-r/tree/master/microsoft-ml/Samples/101/BinaryClassification/SimpleSentimentAnalysis)

