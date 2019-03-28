---
title: microsoftml の Python パッケージ - SQL Server Machine Learning サービス
description: Microsoft の機械学習アルゴリズムを紹介し、python に関連する SQL Server machine learning ワークロードとしてモデル化します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/04/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 618c4b127c42aae6a5b8d7570f1962f8c8e38e9a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511719"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (SQL Server での Python モジュール)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

**microsoftml**高性能な機械学習アルゴリズムを提供する Microsoft から Python35 と互換性のあるモジュールです。 これには、トレーニングと変換、スコア付け、テキストと画像分析、および既存のデータから値を派生させるための特徴抽出の関数が含まれます。

ラーニング Api は Microsoft によって開発されている内部の machine learning アプリケーションのおよびが改良されてビッグ データで高パフォーマンスをサポートするために長年にわたってマルチコア処理と高速データ ストリーミングを使用してマシン。 このパッケージの R バージョンでは、Python と同等として送信された[MicrosoftML](../r/ref-r-microsoftml.md)、同様の機能を持ちます。 

## <a name="full-reference-documentation"></a>完全なリファレンス ドキュメント

**Microsoftml**ライブラリは、複数のマイクロソフト製品で配布されますが、使用量は同じライブラリは、SQL Server または別の製品を取得するかどうか。 関数では同じですが、ため[個々 の microsoftml 関数のドキュメントを](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)が下の 1 つの場所に発行される、 [Python リファレンス](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)の Microsoft Machine Learning Server。 製品固有の動作の存在、相違点は、関数のヘルプ ページに記録されます。

## <a name="versions-and-platforms"></a>バージョンとプラットフォーム

**Microsoftml**モジュールは、Python 3.5 に基づいており、使用可能な次の Microsoft 製品やダウンロードのいずれかをインストールする場合にのみ。

+ [SQL Server 2017 の Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 またはそれ以降](https://docs.microsoft.com/machine-learning-server/)
+ [データ サイエンス クライアント用 Python クライアント ライブラリ](setup-python-client-tools-sql.md)

> [!NOTE]
> 完全な製品リリース バージョンは、Windows 専用にする、SQL Server 2017 以降します。 Linux サポート**microsoftml**新[SQL Server 2019 Preview](../../linux/sql-server-linux-setup-machine-learning.md)。

## <a name="package-dependencies"></a>パッケージの依存関係

アルゴリズムで**microsoftml**依存[revoscalepy](ref-py-revoscalepy.md)の。

+ データ ソース オブジェクト。 データを使用して**microsoftml**関数を使用して作成される**revoscalepy**関数。
+ リモート (リモートの SQL Server インスタンスにシフト関数の実行) を計算します。 **Revoscalepy**ライブラリを作成して、リモートのアクティブ化のコンピューティング コンテキストを SQL server に関数を提供します。

ほとんどの場合、ロード、パッケージ化を使用するたびに**microsoftml**します。

## <a name="functions-by-category"></a>カテゴリ別の関数

このセクションでは、それぞれの使用方法の概要を把握するためのカテゴリ別の関数を示します。 使用することも、[目次](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)関数をアルファベット順に検索します。

## <a name="1-training-functions"></a>1-トレーニング関数

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | モデルのアンサンブルをトレーニングします。 |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | ランダム フォレスト。 |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | 線形モデル。 確率的双対座標。 |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | ブースト ツリー。 |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | ロジスティック回帰。 |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | ニューラル ネットワーク。 |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | 異常検出します。 |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2-変換関数

### <a name="categorical-variable-handling"></a>カテゴリ変数の処理

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | カテゴリには、テキスト列を変換します。 |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | ハッシュを計算し、カテゴリにテキスト列を変換します。 |

### <a name="schema-manipulation"></a>スキーマの操作

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | 1 つのベクトルに複数の列を連結します。 |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | データセットから列を削除します。 |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | データセットの列を保持します。 |


### <a name="variable-selection"></a>選択、変数

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |機能の数に基づいて選択します。 |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | 相互情報量に基づく特徴選択します。 |


### <a name="text-analytics"></a>テキスト分析

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | 数値の機能には、テキスト列を変換します。 |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | センチメント分析します。 |


### <a name="image-analytics"></a>画像分析 

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | イメージを読み込みます。 |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | 画像のサイズを変更します。 |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | イメージからピクセルを抽出します。 |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | 機能には、イメージを変換します。 |

### <a name="featurization-functions"></a>特徴の生成関数

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | データ ソースのデータの変換 |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3-スコア付け関数

| 関数 | 説明 |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Microsoft の機械学習モデルを使用してスコア |

## <a name="how-to-call-microsoftml"></a>Microsoftml を呼び出す方法

関数の**microsoftml**ストアド プロシージャにカプセル化された Python コードで呼び出すことができます。 ほとんどの開発者がビルド**microsoftml**ソリューションをローカルにし、完成した Python コードをデプロイの手順としてストアド プロシージャに移行します。

**Microsoftml**とは異なり、既定で Python がインストールされている用のパッケージ**revoscalepy**、SQL Server と共にインストールされる Python 実行可能ファイルを使用して Python セッションを開始するときに、既定では読み込まれません。

最初の手順としては、インポート、 **microsoftml**パッケージ化、およびインポート**revoscalepy**かどうかは、リモート コンピューティング コンテキストまたは関連する接続またはデータ ソース オブジェクトを使用する必要があります。 次に、必要がある個々 の関数を参照します。

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>関連項目

+ [Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)
+ [チュートリアル: T-SQL での Python コードを埋め込む](../tutorials/run-python-using-t-sql.md)
+ [Python リファレンス (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

