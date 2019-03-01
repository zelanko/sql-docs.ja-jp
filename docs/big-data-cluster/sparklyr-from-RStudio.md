---
title: RStudio から sparklyr を使用して、
titleSuffix: SQL Server 2019 big data clusters
description: RStudio から sparklyr を使用してビッグ データ クラスターに接続します。
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 83980f9d08a3894b0fbf7871cf899483e06702c4
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018358"
---
# <a name="use-sparklyr-in-sql-server-2019-big-data-cluster"></a>Sparklyr を使用して、SQL Server 2019 ビッグ データ クラスター

Sparklyr では、Apache Spark 用 R インターフェイスを提供します。 Sparklyr は、Spark を使用して、R 開発者に選択する方法です。 この記事では、RStudio を使用して SQL Server 2019 ビッグ データ クラスター (プレビュー) で、sparklyr を使用する方法について説明します。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 のビッグ データ クラスター デプロイ](quickstart-big-data-cluster-deploy.md)します。
- [RStudio をインストールします。](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>SS19 ビッグ データ クラスターで spark に接続します。

RStudio で、RScript を作成し、次のように、Spark に接続します。 Spark のビッグ データ クラスターが接続でアクセスできるようにする Livy を使用、 [HDFS/Spark ゲートウェイ](connect-to-big-data-cluster.md#hdfs)します。 認証の場合、ユーザー名と、デプロイ時に設定したパスワードを使用します。

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "***root***", password = "****")

httr::set_config(httr::config(ssl_verifypeer = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Sparklyr クエリを実行します。

Spark に接続したら、sparklyr を実行することができます。 次の例では、sparklyr を使用して、あやめデータセットに対してクエリを実行します。

``` r
copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。