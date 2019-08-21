---
title: RStudio から sparklyr を使用する
titleSuffix: SQL Server big data clusters
description: RStudio から sparklyr を使用してビッグデータクラスターに接続します。
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d23ce447f097d092059f7298ca5478ed6c3f19fc
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653323"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>SQL Server ビッグデータクラスターでの sparklyr の使用

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr には、Apache Spark 用の R インターフェイスが用意されています。 Sparklyr は、R 開発者が Spark を使用する一般的な方法です。 この記事では、 [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] rstudio を使用してで sparklyr を使用する方法について説明します。

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 ビッグデータクラスターをデプロイ](quickstart-big-data-cluster-deploy.md)します。

### <a name="install-rstudio-desktop"></a>RStudio Desktop のインストール

次の手順で**Rstudio Desktop**をインストールして構成します。

1. Windows クライアントで実行している場合は、 [R 3.4.4 をダウンロードしてインストール](https://cran.rstudio.com/bin/windows/base/old/3.4.4)します。

1. [RStudio Desktop をダウンロードしてインストール](https://www.rstudio.com/products/rstudio/download/)します。

1. インストールが完了したら、RStudio Desktop 内で次のコマンドを実行して、必要なパッケージをインストールします。

   ```RStudioDesktop
   install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## <a name="connect-to-spark-in-a-big-data-cluster"></a>ビッグデータクラスターで Spark に接続する

Sparklyr を使用して、Livy と HDFS/Spark ゲートウェイを使用してクライアントからビッグデータクラスターに接続できます。 

RStudio で、次の例のように R スクリプトを作成し、Spark に接続します。

> [!TIP]
> `<USERNAME>` および`<PASSWORD>`の値には、ビッグデータクラスターのデプロイ時に設定したユーザー名 (root など) とパスワードを使用します。 およびの値については、[ビッグデータクラスターへの接続](connect-to-big-data-cluster.md)に関するドキュメントを参照してください。 `<PORT>` `<IP>`

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

## <a name="run-sparklyr-queries"></a>Sparklyr クエリの実行

Spark に接続した後、sparklyr を実行できます。 次の例では、sparklyr を使用して、虹彩データセットに対してクエリを実行します。

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>分散 R 計算

Sparklyr の1つの機能は、 [spark_apply](https://spark.rstudio.com/reference/spark_apply/)を使用して[R 計算を配布](https://spark.rstudio.com/guides/distributed-r/)する機能です。

ビッグデータクラスターは Livy 接続を使用するため、 `packages = FALSE` **spark_apply**の呼び出しでを設定する必要があります。 詳細については、分散 R 計算に関する sparklyr ドキュメントの[Livy セクション](https://spark.rstudio.com/guides/distributed-r/#livy)を参照してください。 この設定では、 **spark_apply**に渡された r コードで、Spark クラスターに既にインストールされている r パッケージのみを使用できます。 この機能の例を次に示します。

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細について[は[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] ](big-data-cluster-overview.md)、「」を参照してください。
