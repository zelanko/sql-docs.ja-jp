---
title: チュートリアル:Python で顧客を分類するためのデータの準備
description: この4部構成のチュートリアルシリーズの第2部では、SQL Server データベースからデータを準備し、SQL Server Machine Learning Services で Python のクラスタリングを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d91f3b9f1e3d1abe53d677d9f9058058d321d985
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294347"
---
# <a name="tutorial-prepare-data-to-categorize-customers-in-python-with-sql-server-machine-learning-services"></a>チュートリアル:SQL Server Machine Learning Services を使用して Python で顧客を分類するためのデータを準備する

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この4部構成のチュートリアルシリーズの第2部では、Python を使用して SQL database からデータを復元し、準備します。 このシリーズの後半で、このデータを使用して、SQL Server Machine Learning Services を使用した Python でのクラスターモデルのトレーニングとデプロイを行います。

この記事では、次の方法について説明します。

> [!div class="checklist"]
> * Python を使用して異なるディメンションに沿って顧客を分離する
> * SQL データベースから Python データフレームにデータを読み込む

[パート 1](python-clustering-model.md)では、前提条件をインストールし、サンプルデータベースを復元しました。

[パート 3](python-clustering-model-build.md) では、Python で K-Means クラスターモデルを作成してトレーニングする方法について説明します。

[パート 4](python-clustering-model-deploy.md)では、新しいデータに基づいて Python でクラスタリングを実行できる SQL データベースにストアドプロシージャを作成する方法について説明します。

## <a name="prerequisites"></a>前提条件

* このチュートリアルのパート2では、[**パート 1**](python-clustering-model.md)の前提条件を満たしていることを前提としています。

## <a name="separate-customers"></a>個別の顧客

クラスタリングの顧客を準備するには、まず次のディメンションに従って顧客を分離します。

* **orderRatio** = 返品順序の比率 (部分的または完全に返された注文の総数と注文の合計数)
* **Itemsratio** = 返される項目の比率 (返された項目の合計数と購入した項目の数)
* **Monetaryratio** = 返品金額の比率 (返される品目の合計金額と購入金額の合計金額)
* **frequency** = 返される頻度

Azure Data Studio で新しいノートブックを開き、次のスクリプトを入力します。

接続文字列で、必要に応じて接続の詳細を置き換えます。

```python
# Load packages.
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import revoscalepy as revoscale
from scipy.spatial import distance as sci_distance
from sklearn import cluster as sk_cluster

################################################################################################

## Connect to DB and select data

################################################################################################

# Connection string to connect to SQL Server named instance.
conn_str = 'Driver=SQL Server;Server=localhost;Database=tpcxbb_1gb;Trusted_Connection=True;'

input_query = '''SELECT
ss_customer_sk AS customer,
ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) AS orderRatio,
ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) AS itemsRatio,
ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) AS monetaryRatio,
COALESCE(returns_count, 0) AS frequency
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
GROUP BY sr_customer_sk ) returned ON ss_customer_sk=sr_customer_sk'''


# Define the columns we wish to import.
column_info = {
    "customer": {"type": "integer"},
    "orderRatio": {"type": "integer"},
    "itemsRatio": {"type": "integer"},
    "frequency": {"type": "integer"}
}
```

## <a name="load-the-data-into-a-data-frame"></a>データをデータフレームに読み込む

クエリの結果は、revoscalepy **RxSqlServerData**関数を使用して Python に返されます。 プロセスの一部として、前のスクリプトで定義した列情報を使用します。

```python
data_source = revoscale.RxSqlServerData(sql_query=input_query, column_Info=column_info,
                                        connection_string=conn_str)
revoscale.RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)
# import data source and convert to pandas dataframe.
customer_data = pd.DataFrame(revoscale.rx_import(data_source))
```

次に、データフレームの先頭を表示して、正しいかどうかを確認します。

```python
print("Data frame:", customer_data.head(n=5))
```

```results
Rows Read: 37336, Total Rows Processed: 37336, Total Chunk Time: 0.172 seconds
Data frame:     customer  orderRatio  itemsRatio  monetaryRatio  frequency
0    29727.0    0.000000    0.000000       0.000000          0
1    97643.0    0.068182    0.078176       0.037034          3
2    57247.0    0.000000    0.000000       0.000000          0
3    32549.0    0.086957    0.068657       0.031281          4
4     2040.0    0.000000    0.000000       0.000000          0
```

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このチュートリアルを続行しない場合は、SQL Server から tpcxbb_1gb データベースを削除してください。

## <a name="next-steps"></a>次の手順

このチュートリアルシリーズの第2部では、次の手順を完了しました。

* Python を使用して異なるディメンションに沿って顧客を分離する
* SQL データベースから Python データフレームにデータを読み込む

この顧客データを使用する機械学習モデルを作成するには、このチュートリアルシリーズの第3部に従います。

> [!div class="nextstepaction"]
> [チュートリアル: SQL Server Machine Learning Services を使用して Python で予測モデルを作成する](python-clustering-model-build.md)
