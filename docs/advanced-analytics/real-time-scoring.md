---
title: "リアルタイムのスコアリング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/03/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9136aee11d5104fd0723521a3466361f06ce26d6
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="realtime-scoring"></a>リアルタイムのスコアリング

このトピックでは、SQL Server 2016 とほぼリアルタイムで機械学習モデルのスコア付けをサポートする SQL Server 2017 で利用できる機能について説明します。

> [!TIP]
> ネイティブのスコア付けは、スコアリングをリアルタイムの特殊な実装は非常に高速スコアリングのため、ネイティブの T-SQL で予測関数を使用して、SQL Server 2017 でのみ使用できます。 詳細については、次を参照してください。[ネイティブ スコアリング](sql-native-scoring.md)です。

## <a name="how-realtime-scoring-works"></a>リアルタイムのスコア付けの動作方法

リアルタイムのスコアリングでがサポートされる SQL Server 2017 と SQL Server 2016 の両方サポート RevoScaleR または MicrosoftML アルゴリズムを使用して作成される特定のモデルの種類。 機械学習モデルの特別なバイナリ形式で格納するのにユーザー入力に基づいてスコアを生成するのにネイティブの C++ ライブラリを使用します。

トレーニング済みモデルは、外部の言語ランタイムを呼び出さずにスコア付けに使用されることができます、ために、複数のプロセスのオーバーヘッドが削減されます。 これは、実稼働のシナリオをスコア付けの予測のパフォーマンスを向上させる多くをサポートします。 データは、SQL Server を離れるはありません、ため結果は生成され、R と SQL の間でデータ変換されることがなく、新しいテーブルに挿入します。

リアルタイムのスコアリングは、複数のステップ プロセスです。

1. スコア付けを行うストアド プロシージャは、データベースごとに有効にする必要があります。
2. バイナリ形式で事前トレーニング済みモデルを読み込みます。
3. 新しい入力データを表形式または 1 つの行は、モデルへの入力として提供します。
4. スコアを生成するには、sp_rxPredict ストアド プロシージャを呼び出します。

## <a name="get-started"></a>作業を開始します。

コード例と手順については、次を参照してください。[ネイティブ スコアリングまたはリアルタイムのスコアリングを実行する方法](r/how-to-do-realtime-scoring.md)です。

RxPredict する方法の例は、スコア付けの使用を参照してください[エンド ツー エンド ローン ChargeOff 予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> R コードでのみ作業する場合は、使用することも、 [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)高速のスコア付け関数。

## <a name="requirements"></a>必要条件

これらのプラットフォームでは、リアルタイムのスコア付けがサポートされています。

+ SQL Server 2017 Machine Learning サービス
+ SQL Server R Services 2016、Microsoft R Server 9.1.0 に R Services のインスタンスのアップグレードまたはそれ以降
+ Machine Learning Server (スタンドアロン)

SQL Server の機能を事前にスコア付けリアルタイムを有効にする必要があります。 これは、機能には、SQL Server に ライブラリの CLR ベースのインストールが必要とするためです。

リアルタイムに関する情報、Microsoft R Server に基づく分散環境でスコアリングを参照してください、 [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)関数で使用できる、 [mrsDeploy パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)、サポートします。R Server で実行されている web サービスを新しいスコアリング リアルタイムのモデルを公開します。

### <a name="restrictions"></a>制限

+ 事前に、サポートされているのいずれかを使用して、モデルをトレーニングする必要があります**rx**アルゴリズムです。 詳細については、「[アルゴリズムがサポートされている](#bkmk_rt_supported_algos)です。 スコアリング リアルタイム`sp_rxPredict`RevoScaleR と MicrosoftML の両方のアルゴリズムをサポートしています。

+ 新しいシリアル化関数を使用して、モデルを保存する必要があります: [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) r、および[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) Python のためです。 これらのシリアル化の関数は、高速のスコア付けをサポートするために最適化されています。

+ リアルタイムのスコアリングは、インタープリター インタープリター; を使用しません。そのため、インタープリターが必要となる機能をすべては、スコア付けの手順ではサポートされません。  たとえば、次のようなものがあります。

  + 使用してモデル化、`rxGlm`または`rxNaiveBayes`アルゴリズムは現在サポートされていません

  + R 変換関数の場合は、またはように、変換を含む数式を使用するモデルの RevoScaleR<code>A ~ log(B)</code>リアルタイムのスコアリングでサポートされていません。 この種類のモデルを使用することをお勧めで変換を実行し、リアルタイムのスコア付けするデータを渡す前にデータを入力します。

+ リアルタイムのスコアリングは現在、いくつかの行から何百もの行の数千個に至るまで、データのサイズの小さいセットでの予測の高速に最適化されています。 使用して、非常に大きなデータセット[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)処理が速くなる場合があります。

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-realtime-scoring"></a><a name="bkmk_rt_supported_algos">リアルタイムのスコア付けをサポートするアルゴリズム

+ RevoScaleR モデル

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)\*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)\*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)\*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)\*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)\*
  
  マークされたモデル\*ネイティブ スコアリング、PREDICT 関数もサポートします。

+ MicrosoftML モデル

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ MicrosoftML によって提供される変換

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [カテゴリ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>サポートされていないモデルの種類

次の種類のモデルがサポートされていません。

+ サポートされていない、他の種類の R の変換を含むモデル
+ 使用してモデル化、`rxGlm`または`rxNaiveBayes`RevoScaleR 内のアルゴリズム
+ PMML モデル
+ CRAN または他のリポジトリから他の R ライブラリを使用して作成されたモデル
+ 含むその他の種類は、ここに記載されている以外の R 変換のモデル

### <a name="known-issues"></a>既知の問題

+ `sp_rxPredict`モデルと NULL 値が渡されるときに不正確なメッセージが返されます。"System.Data.SqlTypes.SqlNullValueException:Data で Null"です。

## <a name="next-steps"></a>次の手順

[リアルタイムのスコア付けを行う方法](r/how-to-do-realtime-scoring.md)
