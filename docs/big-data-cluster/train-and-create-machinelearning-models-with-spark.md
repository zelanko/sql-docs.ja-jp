---
title: Spark を使用したトレーニング/作成の ML モデル
titleSuffix: SQL Server big data clusters
description: PySpark を使用して、SQL Server のビッグ データ クラスター (プレビュー) で Spark を使用した機械学習モデルを作成します。
author: lgongmsft
ms.author: shivprashant
ms.manager: craigg
ms.reviewer: jroth
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: b9217b56da2e00ba50288f1643df809f482c2517
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860563"
---
# <a name="train-and-create-machine-learning-models-with-spark"></a>トレーニングし、Spark を使用した機械学習モデルを作成します。

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

AI と機械学習、ビッグ データの SQL Server クラスターで Spark が使用できます。 この例では、どの機械学習モデルをトレーニング データを使用して Spark (PySpark) で Python を使用してに格納されている HDFS を示します。 

例は、一度に使用できるコード スニペットを Azure データ Studio Notebook と各セルの実行 1 つステップからのステップ バイ ステップ ガイド。 Notebook から Spark に接続する方法の詳細については、参照[ここ](notebooks-guidance.md)

例。

1. 始まり**データと予測の目的を理解します。**
2. **データを HDFS にアップロードし、データを準備する**モデルを作成します。
3. **使用する機能の選択**
4. **トレーニングとテスト セットとして分割されるデータ**
5. まとめて、 **ml パイプラインと、モデルのビルド**
6. 作成したモデルを使用して、**予測を行う**
7. 最後の手順として**後から使用して作成されたモデルを永続化**します。

E2E 機械学習には、いくつかの追加の手順、つまり、データの探索、機能の選択とプリンシパル コンポーネント分析、モデルの選択が含まれます。 次の手順の多くは、簡潔にするため、ここで無視されます。

## <a name="step-1---understanding-the-data-and-prediction-desired"></a>手順 1 - データと予測の目的を理解します。

この例から adult census income データを使用して[ここ]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv )します。 `AdultCensusIncome.csv`、所得範囲が各行および年齢、時間週ごと、学歴、職業などの特定の成人向けコンテンツなどの他の特性。 場合に予測できるモデルを構築、所得範囲。 モデルの有効期間と時間、週ごとの特徴としてと予測のかどうか、収入になります > 50 K または < 50 k. 

## <a name="step-2---upload-the-data-to-hdfs-and-basic-explorations-on-data"></a>手順 2 - データを HDFS と基本的な探索データのアップロード
Azure Data Studio から、HDFS/Spark ゲートウェイに接続し、というディレクトリを作成`spark_ml`HDFS 下。 ダウンロード[AdultCensusIncome.csv]( https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv )ローカル コンピューターから HDFS にアップロードします。 アップロード`AdultCensusIncome.csv`作成したフォルダーにします。


ここで、コードを記述します。 次のコードをコピーして、Azure Data Studio で、notebook の個々 のセルに貼り付けます。 

次のコードでは、Spark データ フレームに CSV ファイルを読み取ります。 さらには、行と列の数をカウントし、読み込まれたデータを表示します。

```python
datafile = "/spark_ml/AdultCensusIncome.csv"

#Read the data to a spark data frame.
data_all = spark.read.format('csv').options(header='true', inferSchema='true', ignoreLeadingWhiteSpace='true', ignoreTrailingWhiteSpace='true').load(datafile)
print("Number of rows: {},  Number of coulumns : {}".format(data_all.count(), len(data_all.columns)))

#Replace "-" with "_" in column names
columns_new = [col.replace("-", "_") for col in data_all.columns]
data_all = data_all.toDF(*columns_new)

#Print Schema and show top 5 row
data_all.printSchema() 
data_all.show(5)
```

## <a name="step-3---select-features-to-use"></a>手順 3 - 使用する機能の選択

この手順で使用して、次の 2 つの用語
1. `Label`    予測する値を表します。 これは、データ内の列として表されます。  
2. `Features` 予測するデータの特性を表します。 別名として時間 `predictors` 

この例では`Label`は、**収入**列。 わかりやすくするために、次のように選択します。**年齢**と**hours_per_week**として`Features`します。 実際には最適な予測ラベルを特徴付ける内容を理解するいくつかの相関関係手法を適用することで、機能が選択しました。

```python
# Choose feature columns and the label column.
label = "income"
xvars = ["age", "hours_per_week"] #all numeric

print("label = {}".format(label))
print("features = {}".format(xvars))

select_cols = xvars
select_cols.append(label)
data = data_all.select(select_cols)

```

## <a name="step-4---split-as-training-and-test-set"></a>手順 4 - トレーニングとテスト セットとして分割

行の 75% を使用して、モデルと、モデルの評価を 25% の残りの部分をトレーニングします。 さらに、トレーニングを保持し、HDFS ストレージにデータ セットをテストします。 ステップがないと、必要に応じてを示すために表示される ORC 形式で読み込んで保存します。 たとえば、他の形式`Parquet`こともできます。

この手順を参照する必要があります AdultCensusIncomeTest と AdultCensusIncomeTrain を名前で作成された 2 つのディレクトリを投稿します。

```python

# Split data into train and test.
train, test = data.randomSplit([0.75, 0.25], seed=123)

print("train ({}, {})".format(train.count(), len(train.columns)))
print("test ({}, {})".format(test.count(), len(test.columns)))

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train.write.mode('overwrite').orc(train_data_path)
test.write.mode('overwrite').orc(test_data_path)
print("train and test datasets saved to {} and {}".format(train_data_path, test_data_path))

```

## <a name="step-5---put-together-a-pipeline-and-build-a-model"></a>手順 5 - パイプラインを作成し、モデルを構築します。
[Spark ML パイプライン](https://spark.apache.org/docs/2.3.1/ml-pipeline.html)をワークフローとしてすべての手順をシーケンス処理し、さまざまなアルゴリズムとそのパラメーターを実験に簡単にできるようにします。 次のコードでは、最初のステージを構築し、Ml パイプラインでこれらのステージをまとめて配置します。  LogisticRegression は、モデルの作成に使用されます。

```python
from pyspark.ml import Pipeline, PipelineModel
from pyspark.ml.feature import OneHotEncoder, StringIndexer, VectorAssembler
from pyspark.ml.classification import LogisticRegression

reg = 0.1
print("Using LogisticRegression model with Regularization Rate of {}.".format(reg))

# create a new Logistic Regression model.
lr = LogisticRegression(regParam=reg)

dtypes = dict(train.dtypes)
dtypes.pop(label)

si_xvars = []
ohe_xvars = []
featureCols = []
for idx,key in enumerate(dtypes):
    if dtypes[key] == "string":
        featureCol = "-".join([key, "encoded"])
        featureCols.append(featureCol)
        
        tmpCol = "-".join([key, "tmp"])
        si_xvars.append(StringIndexer(inputCol=key, outputCol=tmpCol, handleInvalid="skip")) #, handleInvalid="keep"
        ohe_xvars.append(OneHotEncoder(inputCol=tmpCol, outputCol=featureCol))
    else:
        featureCols.append(key)

# string-index the label column into a column named "label"
si_label = StringIndexer(inputCol=label, outputCol='label')

# assemble the encoded feature columns in to a column named "features"
assembler = VectorAssembler(inputCols=featureCols, outputCol="features")

```

ここで、まとめるパイプライン。 

```python
# put together the pipeline
stages = []
stages.extend(si_xvars)
stages.extend(ohe_xvars)
stages.append(si_label)
stages.append(assembler)
stages.append(lr)
pipe = Pipeline(stages=stages)
print("Pipeline Created")

```

これで、パイプラインを作成すると、モデルのトレーニングに使用します。

```python
# train the model
model = pipe.fit(train)
print("Model Trained")
print("Model is ", model)
print("Model Stages", model.stages)

```

## <a name="step-6---predict-using-the-model-and-evaluate-the-model-accuracy"></a>手順 6 - 予測モデルを使用して、モデルの精度を評価
次のコードでは、上記の手順で作成したモデルを使用して結果を予測するのにテスト データ セットを使用します。 使用してモデルの精度を測定`areaUnderROC`と`areaUnderPR`メトリック。

```python
from pyspark.ml.evaluation import BinaryClassificationEvaluator
# make prediction
pred = model.transform(test)

# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```


## <a name="step-7---persist-the-models-to-hdfs"></a>手順 7 - HDFS にモデルを永続化
最後に、後で使用できる HDFS 内のモデルを永続化します。 ここでは、作成したモデル/spark_ml/AdultCensus.mml として保存の投稿します。

```python
##NOTE: by default the model is saved to and loaded from path

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

model.write().overwrite().save(model_fs)
print("saved model to {}".format(model_fs))

# load the model file (from dbfs)
model2 = PipelineModel.load(model_fs)
assert str(model2) == str(model)
print("loaded model from {}".format(model_fs))
```

## <a name="next-steps"></a>次のステップ

PySpark ノートブックを使用する方法の詳細については、次を参照してください。 [notebook を使用する方法](notebooks-guidance.md)します。