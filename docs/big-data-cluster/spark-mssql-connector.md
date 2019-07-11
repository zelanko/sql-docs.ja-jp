---
title: Spark SQL Server に接続する.
titleSuffix: SQL Server big data clusters
description: Spark で MSSQL Spark コネクタを使用して、SQL Server への読み書きする方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: shivsood
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: aaa9cd54c3540c17f9995f985f4537dafe05d5c2
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727463"
---
# <a name="how-to-read-and-write-to-sql-server-from-spark-using-the-mssql-spark-connector"></a>読み取りし、MSSQL Spark コネクタを使用して Spark から SQL Server への書き込み方法

キーのビッグ データの使用パターンでは、基幹業務アプリケーションにアクセスするために SQL Server データの書き込み後に、Spark での大量データ処理です。 これらの使用状況パターン SQL の主要な最適化を利用し、書き込みを効率的なメカニズムを提供するコネクタを享受できます。

この記事では、MSSQL の Spark コネクタを使用してビッグ データ クラスター内で、次の場所を読み書きする方法の例を示します。

1. SQL Server のマスター インスタンス
1. SQL Server のデータ プール

   ![MSSQL Spark コネクタのダイアグラム](./media/spark-mssql-connector/mssql-spark-connector-diagram.png)

サンプルでは、次のタスクを実行します。

- ファイルを HDFS から読み取るし、いくつかの基本的な処理を実行します。
- SQL テーブルと SQL Server のマスター インスタンスにデータ フレームを作成し、データ フレームにテーブルを読みます。
- SQL の外部テーブルとして SQL Server のデータ プールに、データ フレームを作成し、データ フレームに外部テーブルを読みます。

## <a name="mssql-spark-connector-interface"></a>MSSQL Spark コネクタ インターフェイス

SQL Server 2019 プレビューの提供、 **MSSQL Spark コネクタ**ビッグ データの SQL Server 一括を使用するクラスターへの書き込み Api for Spark SQL の書き込み。 MSSQL Spark コネクタでは、Spark データ ソースの Api に基づいており、馴染みのある Spark の JDBC コネクタ インターフェイスを提供します。 インターフェイスのパラメーターを参照してください[Apache Spark ドキュメント](http://spark.apache.org/docs/latest/sql-data-sources-jdbc.html)します。 MSSQL Spark コネクタは、名前によって参照される**com.microsoft.sqlserver.jdbc.spark**します。

次の表では、インターフェイスのパラメーターが変更されたかを初めて使用するについて説明します。

| プロパティ名 | 省略可 | 説明 |
|---|---|---|
| **IsolationLevel** | [はい] | これには、接続の分離レベルについて説明します。 MSSQLSpark コネクタの既定値は**READ_COMMITTED** |

SQL Server の一括のコネクタで使用では、Api を記述します。 一括書き込みパラメーターは、ユーザーが省略可能なパラメーターとして渡すことができ、として渡される、基になる API をコネクタでは、します。 一括の詳細については、書き込み操作を参照してください[SQLServerBulkCopyOptions]( ../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md#sqlserverbulkcopyoptions)します。

## <a name="prerequisites"></a>必須コンポーネント

- A [SQL Server のビッグ データ クラスター](deploy-get-started.md)します。

- [Azure Data Studio](https://aka.ms/azdata-insiders)します。

## <a name="create-the-target-database"></a>ターゲット データベースを作成します。

1. Azure データ Studio を開き、 [、ビッグ データ クラスターの SQL Server のマスター インスタンスに接続する](connect-to-big-data-cluster.md)します。

1. 新しいクエリを作成し、という名前のサンプル データベースを作成するには、次のコマンドを実行**MyTestDatabase**します。

   ```sql
   Create DATABASE MyTestDatabase
   GO
   ```

## <a name="load-sample-data-into-hdfs"></a>HDFS にサンプル データを読み込む

1. ダウンロード[AdultCensusIncome.csv](https://amldockerdatasets.azureedge.net/AdultCensusIncome.csv)ローカル コンピューターにします。

1. Azure データの Studio を起動し、 [、ビッグ データ クラスターに接続する](connect-to-big-data-cluster.md)します。

1. お使いのビッグ データ クラスターで HDFS のフォルダーを右クリックし、選択**新しいディレクトリ**します。 ディレクトリの名前を付けます**spark_data**します。

1. 右クリックして、 **spark_data**ディレクトリ、および select**ファイルをアップロード**します。 アップロード、 **AdultCensusIncome.csv**ファイル。

   ![AdultCensusIncome CSV ファイル](./media/spark-mssql-connector/spark_data.png)

## <a name="run-the-sample-notebook"></a>サンプルの notebook を実行します。

MSSQL Spark コネクタは、このデータとの使用を示すためには、サンプルの notebook をダウンロードし、Azure データの Studio で開くおよび各コード ブロックを実行することができます。 Notebook の使用方法の詳細については、次を参照してください。 [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)します。

1. PowerShell または bash のコマンド ラインからダウンロードするには、次のコマンドを実行、 **mssql_spark_connector.ipynb**サンプルの notebook:

   ```PowerShell
   curl -o mssql_spark_connector.ipynb "https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/spark/data-virtualization/mssql_spark_connector.ipynb"
   ```

1. Azure データ Studio では、サンプルのノートブック ファイルを開きます。 ビッグ データ クラスターの HDFS/Spark ゲートウェイに接続していることを確認します。

1. MSSQL Spark コネクタの使用状況を表示するサンプルでは、各コード セルを実行します。

## <a name="next-steps"></a>次の手順

ビッグ データ クラスターに関する詳細については、次を参照してください[で Kubernetes クラスターのビッグ データの SQL Server をデプロイする方法。](deployment-guidance.md)