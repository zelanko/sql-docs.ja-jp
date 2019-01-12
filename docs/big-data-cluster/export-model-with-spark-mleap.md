---
title: MLeap と Spark ML モデルをエクスポートします。
titleSuffix: SQL Server 2019 big data clusters
description: Spark の機械学習モデル MLeap をエクスポートする方法について説明します。
author: lgongmsft
ms.author: shivprashant
ms.reviewer: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: ee858f66c99ff7b85e2e6c456ad509ec7deb0a6e
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2019
ms.locfileid: "54242133"
---
# <a name="export-spark-machine-learning-models-with-mleap"></a>Spark の machine learning MLeap を使用したモデルをエクスポートします。

一般的な機械学習シナリオには、モデルのトレーニングを Spark と Spark の外部でスコア付けが含まれます。 Spark 外部ために使用できるように、移植可能な形式でモデルをエクスポートします。 [MLeap](https://github.com/combust/mleap)はこのような 1 つのモデル交換形式です。 これにより、Spark は machine learning パイプラインと移植可能な形式としてエクスポートし、任意の JVM ベースのシステムで使用するモデル、`Mleap`ランタイム。

このガイドでは、Mleap を使用して spark モデルをエクスポートする方法を示します。 手順は次に示します、コードは、次のセクションで詳しく説明します。

1. まず、Spark のモデルを作成します。 この操作に**Spark を使用したモデルのトレーニング セットと機械学習を作成する[ここです。](train-and-create-machinelearning-models-with-spark.md)**
2. 次の手順として、 **training\test データとモデルのインポート**
3. **モデルとしてエクスポート`Mleap`バンドル**します。 このエクスポートされたバンドルは、spark の外部のスコア付けするようになりました使用できます。
4. インポートを検証する、`Mleap`バックを再度バンドルし、Spark でスコア付けするに使用します。

## <a name="step-1---start-by-creating-a-spark-model"></a>手順 1 - Spark モデルを作成することにより、
実行[Spark を使用したモデルのトレーニング セットと機械学習を作成する](train-and-create-machinelearning-models-with-spark.md)トレーニング/テストのセットと、モデルを作成し、HDFS ストレージに保存します。 としてモデルをエクスポートする必要が`AdultCensus.mml`下、`spark_ml`ディレクトリ。

## <a name="step-2---import-the-trainingtest-data-and-the-model"></a>手順 2 - training\test データとモデルのインポート

手順 1 の作成、 `AdultCensus.mml`、spark モデルであります。 

この手順では、spark のモデルをインポートします。

```python
import mleap.pyspark
from mleap.pyspark.spark_support import SimpleSparkSerializer
from pyspark.ml import PipelineModel

model_name = "AdultCensus.mml"
model_fs = "/spark_ml/" + model_name

print("load pyspark model from hbfs")
model = PipelineModel.load(model_fs)
print("Model is " , model)
print("Model stages", model.stages)
```

## <a name="step-3---export-the-model-as-mleap-bundle"></a>手順 3 - としてモデルをエクスポート`Mleap`バンドル

移植可能なとして Spark モデルをエクスポート`Mleap`モデル化し、ローカル ストレージに保持します。 この手順の投稿、モデルがポータブル コンピューターで使用できる`Mleap`書式設定し、Spark 外部で使用することができます。

```python
import os

#Get the train and test datasets

# Write the train and test data sets to intermediate storage

train_data_path = "/spark_ml/AdultCensusIncomeTrain"
test_data_path = "/spark_ml/AdultCensusIncomeTest"

train = spark.read.orc(train_data_path)
test = spark.read.orc(test_data_path)

print("train: ({}, {})".format(train.count(), len(train.columns)))
train.printSchema()

print("test: ({}, {})".format(test.count(), len(test.columns)))
test.printSchema()

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# serialize the model to a zip file in JSON format
model_name_export = "adult_census_pipeline.zip"
model_name_path = os.getcwd()
model_file = os.path.join(model_name_path, model_name_export)

# remove an old model file, if needed.
try:
    os.remove(model_file)
except OSError:
    pass

model_file_path = "jar:file:{}".format(model_file)
model.serializeToBundle(model_file_path, model.transform(train))

```

永続化、`Mleap`ローカルから hdfs のバンドル

```python
print("persist the mleap bundle from local to hdfs")
from subprocess import Popen, PIPE
proc = Popen(["hadoop", "fs", "-put", "-f", model_file, os.path.join("/spark_ml", model_name_export)], stdout=PIPE, stderr=PIPE)
s_output, s_err = proc.communicate()
if(s_err):
    print("Error when storing to HDFS")
```

## <a name="step-3---validate-by-importing-the-mleap-bundle-and-scoring-in-spark"></a>手順 3 - インポートによって検証、`Mleap`バンドルと Spark でスコア
手順 2 で、既にエクスポートしたモデルに移植可能な`Mleap`Spark 外部で使用できる形式です。 この手順でインポート、 `Mleap` Spark でシリアル化し、テスト セットでのスコア付けする Spark で使用します。
   
```python
model_deserialized = PipelineModel.deserializeFromBundle(model_file_path)
print("The deserialized model is ", model_deserialized)
print("The deserialized model stages are", model_deserialized.stages)

from pyspark.ml.evaluation import BinaryClassificationEvaluator

# make prediction
pred = model_deserialized.transform(test)


# evaluate. note only 2 metrics are supported out of the box by Spark ML.
bce = BinaryClassificationEvaluator(rawPredictionCol='rawPrediction')
au_roc = bce.setMetricName('areaUnderROC').evaluate(pred)
au_prc = bce.setMetricName('areaUnderPR').evaluate(pred)

print("Results of using the model score test set")
print("Area under ROC: {}".format(au_roc))
print("Area Under PR: {}".format(au_prc))
```

## <a name="references"></a>References

* [PySpark ノートブックの概要](notebooks-guidance.md)
* [トレーニング セットと Spark を使用した機械学習モデルを作成します。](train-and-create-machinelearning-models-with-spark.md)
