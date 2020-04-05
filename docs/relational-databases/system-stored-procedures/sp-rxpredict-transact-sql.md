---
title: sp_rxPredict |マイクロソフトドキュメント
ms.date: 03/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>= sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 45afb5e861aee7b8cf253f6c241a884b54ff9451
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80662839"
---
# <a name="sp_rxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server データベースにバイナリ形式で格納された機械学習モデルから成る特定の入力の予測値を生成します。

R と Python の機械学習モデルでほぼリアルタイムでスコアリングを提供します。 `sp_rxPredict``rxPredict`は[、RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)および[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)の R 関数のラッパーとして提供されるストアド プロシージャであり、[リボスケータ](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)と[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)の Python 関数[rx_predict。](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) C++ で記述され、スコアリング操作専用に最適化されています。

モデルは R または Python を使用して作成する必要がありますが、いったんシリアル化され、ターゲット データベース エンジン インスタンスのバイナリ形式で格納されると、R または Python 統合がインストールされていない場合でも、そのデータベース エンジン インスタンスから使用できます。 詳細については、「 [sp_rxPredict を使用したリアルタイム スコアリング](https://docs.microsoft.com/sql/machine-learning/real-time-scoring)」を参照してください。

## <a name="syntax"></a>構文

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>引数

**モデル**

サポートされている形式での事前トレーニング済みモデル。 

**input**

有効な SQL クエリ

### <a name="return-values"></a>戻り値

スコア列と、入力データ ソースからのパススルー列が返されます。
アルゴリズムがこのような値の生成をサポートしている場合は、信頼区間などの追加のスコア列を返すことができます。

## <a name="remarks"></a>解説

ストアド プロシージャの使用を有効にするには、インスタンスで SQLCLR を有効にする必要があります。

> [!NOTE]
> このオプションを使用すると、セキュリティに影響があります。 サーバーで SQLCLR を有効にできない場合は[、Transact-SQL PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017)関数などの代替実装を使用します。

ユーザーはデータベース`EXECUTE`に対する権限を必要とします。

### <a name="supported-algorithms"></a>サポートされているアルゴリズム

モデルを作成してトレーニングするには[、SQL Server 2 マシン ラーニング サービス (R または Python)](https://docs.microsoft.com/sql/machine-learning/what-is-sql-server-machine-learning) [、SQL Server 2016 R サービス、SQL Server](https://docs.microsoft.com/sql/machine-learning/r/sql-server-r-services)の[機械学習サーバー (スタンドアロン) (R または Python)](https://docs.microsoft.com/sql/machine-learning/r/r-server-standalone)、または[SQL Server 2016 R サーバー (スタンドアロン)](https://docs.microsoft.com/sql/machine-learning/r/r-server-standalone?view=sql-server-2016)で提供される、R または Python でサポートされているアルゴリズムのいずれかを使用します。

#### <a name="r-revoscaler-models"></a>R: レボスケールモデル

  + [rxリンモッド](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDツリー](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdフォレスト](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R: マイクロソフトML モデル

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [をクリックします。](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R: マイクロソフト ML によって提供される変換

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python:レボスケーラックモデル

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>パイソン: マイクロソフトモデル

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python: microsoftml によって提供される変換

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>サポートされていないモデルの種類

次のモデルタイプはサポートされていません。

+ RevoScaleR`rxNaiveBayes`でまたは`rxGlm`アルゴリズムを使用するモデル
+ R の PMML モデル
+ 他のサードパーティライブラリを使用して作成されたモデル 

## <a name="examples"></a>例

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

有効な SQL クエリに加えて*\@、inputData*の入力データには、格納されたモデルの列と互換性のある列が含まれている必要があります。

`sp_rxPredict`サポートされているのは、double、浮動小数点、短い、ushort、long、ulong、および文字列の .NET 列型だけです。 リアルタイム スコアリングに使用する前に、入力データ内のサポートされていない型をフィルター処理する必要がある場合があります。 

  対応する SQL 型の詳細については、「[SQL と CLR 型のマッピング](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping)」または「[CLR パラメーター データのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。

