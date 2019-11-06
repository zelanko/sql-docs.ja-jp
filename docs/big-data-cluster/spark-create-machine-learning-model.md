---
title: MLeap を使用した Spark machine learning モデルの作成とエクスポート
titleSuffix: SQL Server big data clusters
description: PySpark を使用して、Spark on [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (プレビュー) で機械学習モデルのトレーニングと作成を行います。 MLeap でエクスポートし、SQL Server で Java でモデルをスコア付けします。
author: RogPodge
ms.author: roliu
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bba570a4ac68cf5a4d1405d4152669ed9ed211a0
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653415"
---
# <a name="create-export-and-score-spark-machine-learning-models-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Spark machine learning モデルを作成、エクスポート、およびスコア付けする[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

次のサンプルは、 [SPARK ML](https://spark.apache.org/docs/latest/ml-guide.html)でモデルを構築し、そのモデルを[mleap](http://mleap-docs.combust.ml/)にエクスポートし、その[Java 言語拡張機能](../language-extensions/language-extensions-overview.md)を使用して SQL Server でモデルをスコア付けする方法を示しています。 これは、SQL Server 2019 ビッグデータクラスターのコンテキストで行われます。

次の図は、このサンプルで実行される作業を示しています。

![Spark を使用してスコアエクスポートをトレーニングする](./media/spark-create-machine-learning-model/train-score-export-with-spark.png)

## <a name="prerequisites"></a>前提条件

このサンプルのすべてのファイルは、 [https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml](https://github.com/microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/spark/sparkml)にあります。

このサンプルを実行するには、次の前提条件も満たされている必要があります。

- [SQL Server ビッグデータクラスター](deploy-get-started.md)

- [ビッグ データ ツール](deploy-big-data-tools.md)
   - **kubectl**
   - **curl**
   - **Azure Data Studio**

## <a name="model-training-with-spark-ml"></a>Spark ML を使用したモデルトレーニング

このサンプルでは、国勢調査 data (**AdultCensusIncome**) を使用して Spark ML パイプラインモデルを作成します。

1. [Mleap_sql_test/setup. sh](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/setup.sh)ファイルを使用して、インターネットからデータセットをダウンロードし、SQL Server ビッグデータクラスターの HDFS に配置します。 これにより、Spark からアクセスできるようになります。

1. 次に、サンプル notebook [train_score_export_ml_models_with_spark](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb)をダウンロードします。 PowerShell または bash コマンドラインから、次のコマンドを実行して notebook をダウンロードします。

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/sparkml/train_score_export_ml_models_with_spark.ipynb"
   ```

   このノートブックには、サンプルのこのセクションに必要なコマンドを含むセルが含まれています。

1. Azure Data Studio で notebook を開き、各コードブロックを実行します。 ノードブックの操作に関する詳細については、「[SQL Server 2019 Preview でノートブックを使用する方法](notebooks-guidance.md)」を参照してください。

データはまず Spark に読み取られ、トレーニングデータセットとテストデータセットに分割されます。 次に、トレーニングデータを使用してパイプラインモデルをトレーニングします。 最後に、モデルを MLeap バンドルにエクスポートします。

> [!TIP]
> また、これらの手順に関連付けられている Python コードを、 [mleap_sql_test/mleap_pyspark](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_pyspark.py)ファイルの notebook の外部で確認または実行することもできます。

## <a name="model-scoring-with-sql-server"></a>SQL Server を使用したモデルのスコアリング

Spark ML パイプラインモデルが共通のシリアル化[Mleap バンドル](http://mleap-docs.combust.ml/core-concepts/mleap-bundles.html)形式であるため、spark がなくても、Java でモデルをスコア付けすることができます。 

このサンプルでは、SQL Server の[Java 言語拡張機能](../language-extensions/language-extensions-overview.md)を使用します。 SQL Server でモデルをスコア付けするには、まず、Java にモデルを読み込んでスコアを付けることができる Java アプリケーションを構築する必要があります。 この Java アプリケーションのサンプルコードについては、 [mssql-mleap アプリフォルダー](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mssql-mleap-app)を参照してください。

サンプルをビルドした後、Transact-sql を使用して Java アプリケーションを呼び出し、データベーステーブルを使用してモデルをスコア付けすることができます。 これは、 [mleap_sql_test/mleap_sql_tests](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/sql-big-data-cluster/spark/sparkml/mleap_sql_test/mleap_sql_tests.py)ソースファイルに表示されます。

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細については、「 [How [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] to deploy on Kubernetes](deployment-guidance.md) 」を参照してください。
