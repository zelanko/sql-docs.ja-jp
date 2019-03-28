---
title: SQL Server Machine Learning Services の MicrosoftML の R 関数ライブラリ
description: SQL Server 2016 R Services で R と SQL Server 2017 Machine Learning Services の MicrosoftML 関数ライブラリの概要
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 73d9dcf56c0eb5e69704adf169946f6aa28a432c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512259"
---
# <a name="microsoftml-r-library-in-sql-server"></a>MicrosoftML (SQL Server での R ライブラリ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**MicrosoftML**は高性能な機械学習アルゴリズムを提供する Microsoft からの R 関数ライブラリです。 これには、トレーニングと変換、スコア付け、テキストと画像分析、および既存のデータから値を派生させるための特徴抽出の関数が含まれます。

Api の内部の machine learning のアプリケーション、Microsoft によって開発され、されている洗練されたビッグ データで高パフォーマンスをサポートするために長年にわたってマルチコア処理と高速データ ストリーミングを使用して学習するマシン。 MicrosoftML には、テキストとイメージの処理のためのさまざまな変換も含まれています。

## <a name="full-reference-documentation"></a>完全なリファレンス ドキュメント

**MicrosoftML**ライブラリは、複数のマイクロソフト製品で配布されますが、使用量は同じライブラリは、SQL Server または別の製品を取得するかどうか。 関数では同じですが、ため[個々 の RevoScaleR 関数に関するドキュメントの](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)が下の 1 つの場所に発行される、 [R 参照](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)の Microsoft Machine Learning Server。 製品固有の動作の存在、相違点は、関数のヘルプ ページに記録されます。

## <a name="versions-and-platforms"></a>バージョンとプラットフォーム

**MicrosoftML**ライブラリは、R から 3.4.3 に基づいており、使用可能な次の Microsoft 製品やダウンロードのいずれかをインストールする場合にのみ。

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)
+ [SQL Server 2017 の Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 またはそれ以降](https://docs.microsoft.com/machine-learning-server/)
+ [Microsoft R client](set-up-a-data-science-client.md)

> [!NOTE]
> 完全な製品リリース バージョンは、Windows 専用にする、SQL Server 2017 以降します。 Linux サポート**MicrosoftML**新[SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md)。

## <a name="package-dependencies"></a>パッケージの依存関係

アルゴリズムで**MicrosoftML**依存[RevoScaleR](ref-r-revoscaler.md)の。

+ データ ソース オブジェクト。 データを使用して**MicrosoftML**関数を使用して作成される**RevoScaleR**関数。
+ リモート (リモートの SQL Server インスタンスにシフト関数の実行) を計算します。 **RevoScaleR**ライブラリを作成して、リモートのアクティブ化のコンピューティング コンテキストを SQL server に関数を提供します。

ほとんどの場合、ロード、パッケージ化を使用するたびに**MicrosoftML**します。

## <a name="functions-by-category"></a>カテゴリ別の関数

このセクションでは、それぞれの使用方法の概要を把握するためのカテゴリ別の関数を示します。 使用することも、[目次](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference)関数をアルファベット順に検索します。

<a name="ml-algorithms"></a>

## <a name="1-machine-learning-algorithms"></a>1-機械学習アルゴリズム

| 関数名 | 説明 |
|---------------|-------------|
|[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees) | FastRank、MART 勾配ブースティング アルゴリズムの効率的な実装の実装。  |
|[rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | ランダム フォレスト、分位点回帰のフォレストの実装を使用して[rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)します。  |
|[rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | L-BFGS を使用してロジスティック回帰。  |
|[rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm) | 1 クラス サポート ベクター マシン。  
|[rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet) | バイナリ、多クラス、および回帰ニューラル ネットワーク。  |
|[rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear) | 線形の二項分類と回帰の確率的双対座標最適化します。 |
|[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble) | 数が 1 つのモデルから取得よりも予測パフォーマンスが向上を取得するさまざまな種類のモデルをトレーニングします。|

<a name="ml-transforms"></a>

## <a name="2-transformation-functions"></a>2-変換関数

| 関数名 | 説明 |
|---------------|-------------|
|[concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat) | 複数の列から 1 つのベクトルの値を持つ列を作成する変換です。  |
|[categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical) | ディクショナリをカテゴリ別の変換を使用してインジケーター ベクトルを作成します。  |
|[categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalhash) | カテゴリ別の値をハッシュすることでをインジケーター配列に変換します。 |
|[featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizetext) | 指定したテキストのコーパスから n グラムと呼ばれる、連続したワードのシーケンスの数のバッグを生成します。 言語検出、トークン化、ストップ ワードを削除する、テキストの正規化、および特徴の生成を提供します。  |
|[getSentiment](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/getsentiment) | 自然言語テキストをスコア付けし、テキストのセンチメントが正である確率を含む列を作成します。|
|[ngram](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/ngram) | 引数の数およびハッシュ ベースの特徴の抽出を定義できます。|
|[selectColumns](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectcolumns) | 他のすべての削除、再トレーニングする列のセットを選択します。 |
|[selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectfeatures) | 指定されたモードを使用して、指定された変数から機能を選択します。|
|[loadImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loadimage) | イメージ データの読み込み。|
|[resizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/resizeimage) | 指定したサイズ変更メソッドを使用してディメンションを指定するイメージのサイズを変更します。|
|[extractPixels](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/extractpixels) | イメージからのピクセルの値を抽出します。|
|[featurizeImage](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/featurizeimage) | 事前トレーニング済みのディープ ニューラル ネットワーク モデルを使用してイメージ特徴付けを行います。|


## <a name="3-scoring-and-training-functions"></a>3-スコア付けとトレーニング関数

| 関数名 | 説明 |
|---------------|-------------|
|[rxPredict.mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxpredict) | ストアド プロシージャを使用して、SQL Server または R コードがはるかに高速の予測パフォーマンスを提供するリアルタイム スコアリングの有効化は、スコア付けのライブラリを実行します。|
|[rxFeaturize](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfeaturize) | 入力のデータ セットからのデータを出力データ セットに変換します。|
|[mlModel](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mlmodel) | Microsoft R の Machine Learning モデルの概要を示します。|


## <a name="4-loss-functions-for-classification-and-regression"></a>分類と回帰の 4 損失関数

| 関数名 | 説明 |
|---------------|-------------|
|[expLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | 指数の分類の損失関数の仕様。 | 
|[logLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | ログの分類の損失関数の仕様。  |
|[hingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | 型のヒンジ損失関数の分類の仕様。 | 
|[smoothHingeLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | スムーズな型のヒンジ分類の損失関数の仕様。  |
| [poissonLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | ポワソン回帰損失関数の仕様。 | 
|[squaredLoss](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/loss) | 二乗回帰損失関数の仕様。   |   

## <a name="5-feature-selection-functions"></a>5-特徴選択関数

| 関数名 | 説明 |
|---------------|-------------|
|[minCount](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mincount) | カウント モードで機能の選択を指定します。 |
|[mutualInformation](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/mutualinformation) | 相互情報量のモードで機能の選択を指定します。 |

## <a name="6-ensemble-modeling-functions"></a>6 アンサンブルのモデリング関数

| 関数名 | 説明 |
|---------------|-------------|
|[fastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fasttrees) | 関数名との高速ツリー モデルのトレーニングに引数リストを作成します[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)します。|
|[fastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest) | 関数名との高速フォレスト モデルをトレーニングする引数リストを作成します[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)します。|
|[fastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/fastlinear) | 関数名との高速線形モデルのトレーニングに引数リストを作成します[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)します。|
|[logisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/logisticregression) | 関数名と、ロジスティック回帰モデルのトレーニングに引数リストを作成します[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)します。|
|[oneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/oneclasssvm) | 関数名とで OneClassSvm モデルのトレーニングに引数リストを作成します[rxEnsemble](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxensemble)します。|

## <a name="7-neural-networking-functions"></a>7 ニューラル ネットワーク関数

| 関数名 | 説明 |
|---------------|-------------|
|[optimizer](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/optimizer) | 最適化アルゴリズムを指定します、 [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)機械学習アルゴリズムです。|


## <a name="8-package-state-functions"></a>8 パッケージの状態の関数

| 関数名 | 説明 |
|---------------|-------------|
|[rxHashEnv](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxHashEnv) | パッケージ全体の状態を格納するために使用する環境オブジェクト。 |


## <a name="how-to-use-microsoftml"></a>MicrosoftML を使用する方法

関数の**MicrosoftML**ストアド プロシージャにカプセル化された R コードで呼び出すことができます。 ほとんどの開発者がビルド**MicrosoftML**ソリューションをローカルにし、完成した R コードをデプロイの手順としてストアド プロシージャに移行します。

**MicrosoftML** R がインストールされている「アウトの-使える」SQL Server 2017 でのパッケージ化します。 インスタンスの R コンポーネントをアップグレードする場合にも SQL Server 2016 で使用可能です。[バインドを使用して SQL Server のインスタンスをアップグレードします。](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

既定では、パッケージが読み込まれていません。 最初の手順として読み込み、 **MicrosoftML**をパッケージ化し、読み込む**RevoScaleR**かどうかは、リモート コンピューティング コンテキストまたは関連する接続またはデータ ソース オブジェクトを使用する必要があります。 次に、必要がある個々 の関数を参照します。

```R
library(microsoftml);
library(RevoScaleR);
logisticRegression(args);
```

## <a name="see-also"></a>関連項目

+ [R のチュートリアル](../tutorials/sql-server-r-tutorials.md)
+ [計算コンテキストを使用する方法を学習します。](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [SQL 開発者向けの R:トレーニングし、モデルの運用化](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [GitHub の Microsoft の製品サンプル](https://github.com/Microsoft/SQL-Server-R-Services-Samples)
+ [R の参照 (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/r-reference/introducing-r-server-r-package-reference) 