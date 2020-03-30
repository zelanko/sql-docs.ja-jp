---
title: Python のチュートリアル:データを準備する
description: この 4 部構成のチュートリアル シリーズのパート 2 では、Python を使用して、スキー レンタルを予測するデータを SQL Server Machine Learning Services で準備します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/02/2020
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9aeefb0b6fd9ca1a744d132fccf1eedfedbaa6e7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75681749"
---
# <a name="python-tutorial-prepare-data-to-train-a-linear-regression-model-in-sql-server-machine-learning-services"></a>Python のチュートリアル:SQL Server Machine Learning Services で線形回帰モデルをトレーニングするためのデータを準備する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

この 4 部構成のチュートリアル シリーズのパート 2 では、Python を使用して SQL Server データベースからデータを準備します。 このシリーズの後半では、本データを使用して、SQL Server Machine Learning Services とともに Python で線形回帰モデルをトレーニングし、デプロイします。

この記事では、次の方法について学習します。

> [!div class="checklist"]
> * SQL Server データベースから **pandas** データ フレームにデータを読み込む
> * いくつかの列を削除して Python でデータを準備する

[第 1 部](python-ski-rental-linear-regression.md)では、サンプル データベースを復元する方法を学習しました。

[パート 3](python-ski-rental-linear-regression-train-model.md) では、Python で線形回帰機械学習モデルをトレーニングする方法について学習します。

[第 4 部](python-ski-rental-linear-regression-deploy-model.md)では、モデルを SQL Server に格納し、そして第 2 部と第 3 部で開発した Python スクリプトからストアド プロシージャを作成する方法について学習します。 ストアド プロシージャは、新しいデータに基づいて予測を行うために SQL Server で実行されます。

## <a name="prerequisites"></a>前提条件

* このチュートリアルのパート 2 は、[パート 1](python-ski-rental-linear-regression.md) とその前提条件を完了していることを前提としています。

## <a name="explore-and-prepare-the-data"></a>データの探索と準備

Python でデータを使用するには、SQL Server データベースから、pandas データ フレームにデータを読み込みます。

Azure Data Studio で新しい Python notebook を作成し、次のスクリプトを実行します。 `<SQL Server>` を独自の SQL Server 名に置換します。

次の Python スクリプトでは、データベースの **dbo.rental_data** テーブルから、データセットを pandas データ フレーム **df** にインポートします。

接続文字列で、必要に応じて接続の詳細を置き換えます。

```python
import pyodbc
import pandas
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Connection string to your SQL Server instance
conn_str = pyodbc.connect('DRIVER={ODBC Driver 17 for SQL Server}; SERVER=localhost; DATABASE=TutorialDB; Trusted_Connection=yes')

query_str = 'SELECT Year, Month, Day, Rentalcount, Weekday, Holiday, Snow FROM dbo.rental_data'

df = pandas.read_sql(sql=query_str, con=conn_str)

print("Data frame:", df)

# Get all the columns from the dataframe.
columns = df.columns.tolist()

# Filter the columns to remove ones we don't want to use in the training
columns = [c for c in columns if c not in ["Year"]]
```

次のような結果が表示されます。

```results
Data frame:      Year  Month  Day  RentalCount  WeekDay  Holiday  Snow
0    2014      1   20          445        2        1     0
1    2014      2   13           40        5        0     0
2    2013      3   10          456        1        0     0
3    2014      3   31           38        2        0     0
4    2014      4   24           23        5        0     0
..    ...    ...  ...          ...      ...      ...   ...
448  2013      2   19           57        3        0     1
449  2015      3   18           26        4        0     0
450  2015      3   24           29        3        0     1
451  2014      3   26           50        4        0     1
452  2015     12    6          377        1        0     1

[453 rows x 7 columns]
```

## <a name="next-steps"></a>次のステップ

このチュートリアル シリーズの第 2 部では、次の手順を完了しました。

* SQL Server データベースから **pandas** データ フレームにデータを読み込む
* いくつかの列を削除して Python でデータを準備する

TutorialDB データベースのデータを使用する機械学習モデルをトレーニングするには、このチュートリアル シリーズのパート 3 に従ってください。

> [!div class="nextstepaction"]
> [Python のチュートリアル:線形回帰モデルをトレーニングする](python-ski-rental-linear-regression-train-model.md)