---
title: チュートリアル:Python でモデルをデプロイして顧客を分類する
description: この4部構成のチュートリアルシリーズの第4部では、SQL Server Machine Learning Services を含むクラスターモデルを Python にデプロイします。
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: eef8a0f0f11e6d9085a1685145e4c6815979470d
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199353"
---
# <a name="tutorial-deploy-a-model-in-python-to-categorize-customers-with-sql-server-machine-learning-services"></a>チュートリアル:モデルを Python にデプロイして、SQL Server Machine Learning Services で顧客を分類する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この4部構成のチュートリアルシリーズの第4部では、SQL Server Machine Learning Services を使用して、Python で開発されたクラスターモデルを SQL database にデプロイします。

クラスターを定期的に実行するには、新しい顧客が登録するときに、任意のアプリから Python スクリプトを呼び出すことができる必要があります。 これを行うには、データベースの SQL ストアドプロシージャ内に Python スクリプトを配置して、SQL Server に Python スクリプトを配置します。 モデルは SQL database で実行されるため、データベースに格納されているデータに対して簡単にトレーニングできます。

このセクションでは、SQL Server に書き込んだ Python コードを移動し、SQL Server Machine Learning Services のヘルプを使用してクラスタリングを展開します。

この記事では、次の方法について説明します。

> [!div class="checklist"]
> * モデルを生成するストアドプロシージャを作成する
> * SQL Server でクラスタリングを実行する
> * クラスタリング情報を使用する

[パート 1](python-clustering-model.md)では、前提条件をインストールし、サンプルデータベースを復元しました。

[パート 2](python-clustering-model-prepare-data.md) では、クラスタリングを実行するために SQL データベースからデータを準備する方法を学習しました。

[パート 3](python-clustering-model-build.md) では、Python で K-Means クラスタリング モデルを作成してトレーニングする方法について学習しました。

## <a name="prerequisites"></a>前提条件

* このチュートリアルシリーズのパート 4 では、[**パート 1**](python-clustering-model.md) の前提条件を満たしていること、[**パート 2**](python-clustering-model-prepare-data.md) と[**パート 3**](python-clustering-model-build.md) の手順を完了していることを前提としています。

## <a name="create-a-stored-procedure-that-generates-the-model"></a>モデルを生成するストアドプロシージャを作成する

次の T-sql スクリプトを実行して、ストアドプロシージャを作成します。 この手順では、パート1とこのチュートリアルシリーズで開発した手順を再作成します。

* 購入と返却履歴に基づいて顧客を分類する
* K-Means アルゴリズムを使用して 4 つの顧客のクラスターを生成する

```sql
USE [tpcxbb_1gb]
GO

CREATE procedure [dbo].[py_generate_customer_return_clusters]
AS

BEGIN
    DECLARE

-- Input query to generate the purchase history & return metrics
     @input_query NVARCHAR(MAX) = N'
SELECT
  ss_customer_sk AS customer,
  CAST( (ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) ) AS FLOAT) AS orderRatio,
  CAST( (ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) ) AS FLOAT) AS itemsRatio,
  CAST( (ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) ) AS FLOAT) AS monetaryRatio,
  CAST( (COALESCE(returns_count, 0)) AS FLOAT) AS frequency
FROM
  (
    SELECT
      ss_customer_sk,
      -- return order ratio
      COUNT(distinct(ss_ticket_number)) AS orders_count,
      -- return ss_item_sk ratio
      COUNT(ss_item_sk) AS orders_items,
      -- return monetary amount ratio
      SUM( ss_net_paid ) AS orders_money
    FROM store_sales s
    GROUP BY ss_customer_sk
  ) orders
  LEFT OUTER JOIN
  (
    SELECT
      sr_customer_sk,
      -- return order ratio
      count(distinct(sr_ticket_number)) as returns_count,
      -- return ss_item_sk ratio
      COUNT(sr_item_sk) as returns_items,
      -- return monetary amount ratio
      SUM( sr_return_amt ) AS returns_money
    FROM store_returns
    GROUP BY sr_customer_sk
  ) returned ON ss_customer_sk=sr_customer_sk
 '

EXEC sp_execute_external_script
      @language = N'Python'
    , @script = N'

import pandas as pd
from sklearn.cluster import KMeans

#get data from input query
customer_data = my_input_data

#We concluded in step 2 in the tutorial that 4 would be a good number of clusters
n_clusters = 4

#Perform clustering
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orderRatio","itemsRatio","monetaryRatio","frequency"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
    , @input_data_1 = @input_query
    , @input_data_1_name = N'my_input_data'
             with result sets (("Customer" int, "orderRatio" float,"itemsRatio" float,"monetaryRatio" float,"frequency" float,"cluster" float));
END;
GO
```

## <a name="perform-clustering-in-sql-database"></a>SQL Database でクラスタリングを実行する

ストアドプロシージャを作成したので、次のスクリプトを実行して、プロシージャを使用してクラスタリングを実行します。

```sql
--Create a table to store the predictions in

DROP TABLE IF EXISTS [dbo].[py_customer_clusters];
GO

CREATE TABLE [dbo].[py_customer_clusters] (
    [Customer] [bigint] NULL
  , [OrderRatio] [float] NULL
  , [itemsRatio] [float] NULL
  , [monetaryRatio] [float] NULL
  , [frequency] [float] NULL
  , [cluster] [int] NULL
  ,
    ) ON [PRIMARY]
GO

--Execute the clustering and insert results into table
INSERT INTO py_customer_clusters
EXEC [dbo].[py_generate_customer_return_clusters];

-- Select contents of the table to verify it works
SELECT * FROM py_customer_clusters;
```

## <a name="use-the-clustering-information"></a>クラスタリング情報を使用する

クラスター化の手順はデータベースに格納されているため、同じデータベースに格納されている顧客データに対して効率的にクラスタリングを実行できます。 顧客データが更新されるたびにプロシージャを実行し、更新されたクラスタリング情報を使用することができます。

(このチュートリアルの[第3部](python-clustering-model-build.md#analyze-the-results)では4つのクラスターがどのように記述されているかを確認できます)、非アクティブなグループであるクラスター0の顧客にプロモーション電子メールを送信するとします。 次のコードは、クラスター0の顧客の電子メールアドレスを選択します。

```sql
USE [tpcxbb_1gb]
--Get email addresses of customers in cluster 0 for a promotion campaign
SELECT customer.[c_email_address], customer.c_customer_sk
  FROM dbo.customer
  JOIN
  [dbo].[py_customer_clusters] as c
  ON c.Customer = customer.c_customer_sk
  WHERE c.cluster = 0
```

**C. クラスター**の値を変更して、他のクラスターの顧客の電子メールアドレスを返すことができます。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このチュートリアルを終了すると、SQL Server から tpcxbb_1gb データベースを削除できます。

## <a name="next-steps"></a>次の手順

このチュートリアルシリーズの第4部では、次の手順を完了しました。

* モデルを生成するストアドプロシージャを作成する
* SQL Server でクラスタリングを実行する
* クラスタリング情報を使用する

SQL Server Machine Learning Services での Python の使用の詳細については、次のページを参照してください。

* [クイック スタート:SQL Server Machine Learning Services を使用した単純な Python スクリプトの作成と実行](quickstart-python-create-script.md)
* [SQL Server Machine Learning Services のその他の Python チュートリアル](sql-server-python-tutorials.md)
* [Sqlmlutils を使用して Python パッケージをインストールする](../package-management/install-additional-python-packages-on-sql-server.md)

