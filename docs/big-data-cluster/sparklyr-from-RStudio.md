---
title: RStudio から sparklyr を使用して、
titleSuffix: SQL Server big data clusters
description: RStudio から sparklyr を使用してビッグ データ クラスターに接続します。
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 148e4942babafb35af2efe33eb427f9462f0a47e
ms.sourcegitcommit: 2e7686443a61b1a2cf4ca47d9ab1010b9e9b5188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59291582"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Sparklyr を使用して、SQL Server のビッグ データ クラスター内

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr では、Apache Spark 用 R インターフェイスを提供します。 Sparklyr は、Spark を使用して、R 開発者向けの一般的な方法です。 この記事では、RStudio を使用して SQL Server 2019 ビッグ データ クラスター (プレビュー) で、sparklyr を使用する方法について説明します。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 のビッグ データ クラスター デプロイ](quickstart-big-data-cluster-deploy.md)します。

### <a name="install-rstudio-desktop"></a>RStudio Desktop をインストールします。

インストールし、構成**RStudio Desktop**で、次の手順。

1. Windows クライアントで実行している場合[をダウンロードしてインストール R 3.4.4](https://cran.rstudio.com/bin/windows/base/old/3.4.4)します。

1. [ダウンロードしてインストール RStudio Desktop](https://www.rstudio.com/products/rstudio/download/)します。

1. インストールの完了後、必要なパッケージをインストールする RStudio Desktop 内で、次のコマンドを実行します。

   '' RStudio Desktop install.packages (リポジトリである"DBI"="https://cran.microsoft.com/snapshot/2019-01-01") install.packages (リポジトリ"dplyr"="https://cran.microsoft.com/snapshot/2019-01-01") install.packages (リポジトリ"sparklyr"="https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## Connect to Spark in a big data cluster

You can use sparklyr to connect from a client to the big data cluster using Livy and the HDFS/Spark gateway. 

In RStudio, create an R script and connect to Spark as in the following example:

> [!TIP]
> For the `<USERNAME>` and `<PASSWORD>` values, use the username (such as root) and password you set during the big data cluster deployment. For the `<IP>` and `<PORT>` values, see the documentation on the [HDFS/Spark gateway](connect-to-big-data-cluster.md#hdfs).

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "<username>", password = "<password>")

httr::set_config(httr::config(ssl_verifypeer = 0L, ssl_verifyhost = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Sparklyr クエリを実行します。

Spark に接続したら、sparklyr を実行することができます。 次の例では、sparklyr を使用して、あやめデータセットに対してクエリを実行します。

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>分散 R 計算

Sparklyr の 1 つの機能に機能が[分散 R 計算](https://spark.rstudio.com/guides/distributed-r/)で[spark_apply](https://spark.rstudio.com/reference/spark_apply/)します。

設定する必要がありますので、ビッグ データ クラスターは、Livy の接続を使用して、`packages = FALSE`への呼び出しで**spark_apply**します。 詳細については、次を参照してください。、 [Livy セクション](https://spark.rstudio.com/guides/distributed-r/#livy)の分散 R 計算に sparklyr ドキュメント。 この設定に渡された R コードで、Spark クラスターに既にインストールされている R パッケージを使用することができますのみ**spark_apply**します。 次の例では、この機能を示しています。

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターは](big-data-cluster-overview.md)します。