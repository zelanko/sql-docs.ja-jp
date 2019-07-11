---
title: 作成し、Spark の machine learning MLeap を使用したモデルのエクスポート
titleSuffix: SQL Server big data clusters
description: PySpark を使用して、SQL Server のビッグ データ クラスター (プレビュー) で Spark を使用した機械学習モデルを作成します。 MLeap、と共にエクスポートし、SQL Server で Java を使って、モデル、スコア付けします。
author: lgongmsft
ms.author: lgong
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aa4c31eca725e8e662937259f078cf00a3441915
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727377"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-sql-server-big-data-clusters"></a>作成、エクスポート、および SQL Server のビッグ データ クラスターで Spark 機械学習モデルをスコア付け

次の例は、使用してモデルを構築する方法を示します[Spark ML](https://spark.apache.org/docs/latest/ml-guide.html)、モデルをエクスポート[MLeap](http://mleap-docs.combust.ml/)、SQL Server で、モデルのスコア付けとその[Java 言語の拡張機能](../language-extensions/language-extensions-overview.md)します。 これは、SQL Server 2019 のビッグ データ クラスターのコンテキストで行います。

次の図は、このサンプルで実行される作業を示しています。

![Spark を使用したトレーニング スコアのエクスポート](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>必須コンポーネント

このサンプルのすべてのファイルは、 [ https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml)します。

サンプルを実行するには、次の前提条件も必要です。

- A[ビッグ データの SQL Server クラスター](deploy-get-started.md)

- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Spark ML を使用したモデルのトレーニング

このサンプルでは、国勢調査データ (**AdultCensusIncome.csv**)、Spark ML パイプライン モデルを構築するために使用します。

1. 使用して、 [mleap_sql_test/setup.sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/setup.sh)データ セットをインターネットからダウンロードして、SQL Server のビッグ データ クラスターで HDFS に保存するファイル。 これにより、Spark がアクセスすることができます。

1. サンプルの notebook をダウンロードし、 [train_score_export_ml_models_with_spark.ipynb](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb)します。 PowerShell または bash のコマンド ラインからは、notebook のダウンロードには、次のコマンドを実行します。

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   この notebook には、サンプルのこのセクションの必要なコマンドを持つセルが含まれています。

1. Azure Data Studio でノートブックを開き、各コード ブロックを実行します。 Notebook の使用方法の詳細については、次を参照してください。 [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)します。

データは最初に Spark に読み取られ、トレーニング セットとテスト データ セットに分割します。 コードは、トレーニング データでのパイプライン モデルをトレーニングします。 最後に、MLeap バンドルにモデルをエクスポートします。

> [!TIP]
> 確認の notebook の外部でこれらの手順に関連付けられている Python コードを実行したり、 [mleap_sql_test/mleap_pyspark.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_pyspark.py)ファイル。

## <a name="model-scoring-with-sql-server"></a>SQL Server でのスコア付けモデル

これで、Spark ML パイプライン モデルが共通のシリアル化で[MLeap バンドル](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html)形式、Spark がなくても Java でのモデル スコア付けすることができます。 

このサンプルでは、 [Java 言語の拡張機能](../language-extensions/language-extensions-overview.md)SQL server。 SQL Server で、モデルのスコア付けをするためには、まず、Java にモデルを読み込むことができ、スコアを付けている Java アプリケーションを構築する必要があります。 場合は、この Java アプリケーションのサンプル コードを見つけることができます、 [mssql mleap-アプリ フォルダー](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mssql-mleap-app)します。

サンプルをビルドした後は TRANSACT-SQL を使用して Java アプリケーションを呼び出すし、データベースのテーブル モデルのスコア付けすることができます。 これは、次で確認できます[mleap_sql_test/mleap_sql_tests.py](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparklm/mleap_sql_test/mleap_sql_tests.py)ソース ファイル。

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターに関する詳細については、次を参照してください[で Kubernetes クラスターのビッグ データの SQL Server をデプロイする方法。](deployment-guidance.md)
