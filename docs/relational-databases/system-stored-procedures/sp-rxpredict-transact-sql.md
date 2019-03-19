---
title: sp_rxPredict |Microsoft Docs
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sp_rxPredict
- sp_rxPredict_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_rxPredict procedure
author: HeidiSteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 50e25162f88c42c0728f951702d304975fb7091b
ms.sourcegitcommit: 11ab8a241a6d884b113b3cf475b2b9ed61ff00e3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161599"
---
# <a name="sprxpredict"></a>sp_rxPredict  
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Machine learning モデルを SQL Server データベースにバイナリ形式で格納されているので構成される特定の入力に対して予測された値を生成します。

R と Python の機械学習のモデルがほぼリアルタイムでのスコア付けを提供します。 `sp_rxPredict` ストアド プロシージャのラッパーとして提供されるは、`rxPredict`で R 関数[RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)と[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)、および[rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-predict) でのPython関数[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)と[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)します。 C++ で記述され、専用の操作をスコア付けは最適化されています。

シリアル化され、ターゲット データベース エンジンのインスタンスでバイナリ形式で格納すると、R や Python を使用して、モデルを作成する必要があります、R または Python の統合がインストールされていない場合でもデータベース エンジンのインスタンスから使用できます。 詳細については、次を参照してください。 [sp_rxPredict とリアルタイム スコアリング](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring)します。

## <a name="syntax"></a>構文

```
sp_rxPredict  ( @model, @input )
```

### <a name="arguments"></a>引数

**model**

サポートされている形式で事前トレーニング済みモデル。 

**input**

有効な SQL クエリ

### <a name="return-values"></a>戻り値

入力データ ソースからのパススルー列と、スコア列が返されます。
追加、信頼区間などの列にスコアを付け、アルゴリズムがこのような値の生成をサポートするかどうかに返されることができます。

## <a name="remarks"></a>コメント

ストアド プロシージャの使用を有効にするには、インスタンスで SQLCLR を有効にする必要があります。

> [!NOTE]
> このオプションの enabing するセキュリティへの影響があります。 代替の実装を使用して、 [TRANSACT-SQL 予測](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql?view=sql-server-2017)関数の場合は、サーバーで SQLCLR を有効にすることはできません。

ユーザーのニーズ`EXECUTE`データベースに対する権限。

### <a name="supported-algorithms"></a>サポートされているアルゴリズム

作成しモデルのトレーニング、R や Python のサポートされるアルゴリズムのいずれかを使用するのには、用意[SQL Server 2016 R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services?view=sql-server-2017)、 [SQL Server 2016 R Server (スタンドアロン)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2016)、 [SQL Server 2017 MachineLearning サービス (R または Python)](https://docs.microsoft.com//sql/advanced-analytics/what-is-sql-server-machine-learning?view=sql-server-2017)、または[SQL Server 2017 Server (スタンドアロン) (R または Python)](https://docs.microsoft.com/sql/advanced-analytics/r/r-server-standalone?view=sql-server-2017)します。

#### <a name="r-revoscaler-models"></a>R:RevoScaleR のモデル

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree)
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest)

#### <a name="r-microsoftml-models"></a>R:MicrosoftML のモデル

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

#### <a name="r-transformations-supplied-by-microsoftml"></a>R:MicrosoftML によって提供される変換

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

#### <a name="python-revoscalepy-models"></a>Python: revoscalepy モデル

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit)
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees)
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree)
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest)


#### <a name="python-microsoftml-models"></a>Python: microsoftml モデル

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

#### <a name="python-transformations-supplied-by-microsoftml"></a>Python:Microsoftml によって提供される変換

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-referencee/microsoftml/categorical-hash)
  
### <a name="unsupported-model-types"></a>サポートされていないモデルの種類

モデルの種類がサポートされていません。

+ モデルを使用して、`rxGlm`または`rxNaiveBayes`revoscaler アルゴリズム
+ R でのモデルの PMML
+ その他のサード パーティ製ライブラリを使用して作成されたモデル 

## <a name="examples"></a>使用例

```sql
DECLARE @model = SELECT @model 
FROM model_table 
WHERE model_name = 'rxLogit trained';

EXEC sp_rxPredict @model = @model,
@inputData = N'SELECT * FROM data';
```

有効な SQL クエリ内の入力データだけでなく*@inputData*格納されたモデルで列と互換性のある列を含める必要があります。

`sp_rxPredict` 次の .NET の列型のみをサポートしています: float、short、ushort、double、long、ulong と文字列。 リアルタイム スコアリングのために使用する前に、入力データでサポートされていない型を除外する必要があります。 

  対応する SQL 型については、次を参照してください。 [SQL-CLR 型マッピング](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping)または[CLR パラメーター データのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)します。

