---
title: SQL Server machine learning でリアルタイム スコアリング |Microsoft Docs
description: Sp_rxPredict、SQL Server で R で記述された事前トレーニング済みモデルに対して dta 入力のスコアリングを使用して予測を生成します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: d5a3d0318f925918ef98ae18744e4287d6b81108
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2018
ms.locfileid: "40395135"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>リアルタイムのスコアリングでは、SQL Server machine learning で sp_rxPredict
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server のリレーショナル データに対してほぼリアルタイムの機能でスコア付けする方法、machine learning を使用してモデル化 R で記述について説明します 

> [!Note]
> ネイティブ スコアリングは、非常に高速のスコアリングのため、ネイティブの T-SQL の予測関数を使用するリアルタイム スコアリングの特別な実装です。 詳細と可用性は、次を参照してください。[ネイティブ スコアリング](sql-native-scoring.md)します。

## <a name="how-real-time-scoring-works"></a>リアルタイムのスコアリング動作

SQL Server 2017 と SQL Server 2016 の両方で RevoScaleR または MicrosoftML 関数をなどに基づいて特定のモデルの種類でのリアルタイム スコアリングはサポートされて[rxLinMod (RevoScaleR)](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)または[rxNeuralNet (MicrosoftML)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet). Machine learning の特別なバイナリ形式で格納されているモデルに提供されるユーザー入力に基づいてスコアを生成するのにネイティブの C++ ライブラリを使用します。

トレーニング済みモデルは、外部言語のランタイムを呼び出さずにスコア付けに使用できます、ため、複数のプロセスのオーバーヘッドが減少します。 運用環境のシナリオをスコア付け用の予測パフォーマンスを向上させる多くをサポートしています。 データが SQL Server を越える、ため、結果は生成され、R と SQL の間のデータ変換されることがなく新しいテーブルに挿入します。

複数の手順は、リアルタイム スコアリングします。

1. スコア付けを行うストアド プロシージャは、データベースごとに有効にする必要があります。
2. バイナリ形式で事前トレーニング済みモデルを読み込みます。
3. 新しい入力データを表形式または 1 つのいずれかの行は、モデルへの入力として提供します。
4. スコアを生成するには、sp_rxPredict ストアド プロシージャを呼び出します。

## <a name="get-started"></a>作業開始

コード例と手順については、次を参照してください。[ネイティブ スコアリングまたはリアルタイム スコアリングを実行する方法について](r/how-to-do-realtime-scoring.md)します。

RxPredict を使用して、スコア付け方法の例は、次を参照してください[エンド ツー エンド ローン償却予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス。](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

> [!TIP]
> 使用できますの R コード内だけで作業している場合、 [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)高速のスコア付け関数。

## <a name="requirements"></a>要件

これらのプラットフォームでは、リアルタイム スコアリングはサポートされています。

+ SQL Server 2017 Machine Learning サービス
+ SQL Server R Services 2016、9.1.0 またはそれ以降の R コンポーネントのアップグレード

SQL Server で、SQL Server に、CLR ベースのライブラリを追加するには、事前にリアルタイムのスコア付け機能を有効にする必要があります。

Microsoft R Server に基づく分散環境でリアルタイムのスコアリング方法の詳細についてを参照してください、 [publishService](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)関数で使用できる、 [mrsDeploy パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)、サポートします。R Server で実行されている web サービスとして、新しいリアルタイム スコアリングのモデルを公開します。

### <a name="restrictions"></a>制限

+ 事前に、サポートされているのいずれかを使用してモデルをトレーニングする必要があります**rx**アルゴリズム。 詳細については、次を参照してください。[アルゴリズムがサポートされている](#bkmk_rt_supported_algos)します。 リアルタイム スコアリング`sp_rxPredict`RevoScaleR と MicrosoftML の両方のアルゴリズムをサポートしています。

+ 新しいシリアル化関数を使用して、モデルを保存する必要があります: [rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) 、R 用と[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) Python 用です。 これらのシリアル化関数は、高速のスコア付けをサポートするために最適化されています。

+ リアルタイム スコアリングでは、インタープリター; は使用しませんそのため、インタープリターが必要となる機能は、スコア付けの手順ではサポートされません。  たとえば、次のようなものがあります。

  + モデルを使用して、`rxGlm`または`rxNaiveBayes`アルゴリズムは現在サポートされていません

  + R 変換関数、または、変換を含む数式を使用するモデルの RevoScaleR<code>A ~ log(B)</code>リアルタイム スコアリングではサポートされていません。 このタイプのモデルを使用するをお勧めで変換を実行し、リアルタイム スコアリングにデータを渡す前にデータを入力します。

+ リアルタイム スコアリングは現在の小さいデータ セット、少数の行から数百行の何千ものまで高速の予測に最適化されています。 使用して、大規模なデータセットで[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)高速な場合があります。

### <a name="a-namebkmkrtsupportedalgosalgorithms-that-support-real-time-scoring"></a><a name="bkmk_rt_supported_algos">リアルタイム スコアリングをサポートするアルゴリズム

+ RevoScaleR のモデル

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  モデルが付いた\*PREDICT 関数を使用したネイティブ スコアリングもサポートします。

+ MicrosoftML のモデル

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ MicrosoftML によって提供される変換

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>サポートされていないモデルの種類

R での変換に明示的にリストされている以外、前のセクションでは、リアルタイム スコアリングはサポートされていません。 

サポートされていない関数は、RevoScaleR とその他の Microsoft R 固有のライブラリの使用に慣れている開発者は、`rxGlm`または`rxNaiveBayes`revoscaler のモデルの PMML、アルゴリズムと CRAN から他の R ライブラリを使用して作成されたその他のモデルまたはその他のリポジトリ。

### <a name="known-issues"></a>既知の問題

+ `sp_rxPredict` NULL 値が、モデルとして渡されるときに不正確なメッセージが返されます。"System.Data.SqlTypes.SqlNullValueException:Data で Null"です。

## <a name="next-steps"></a>次のステップ

[リアルタイム スコアリングを実行する方法](r/how-to-do-realtime-scoring.md)
