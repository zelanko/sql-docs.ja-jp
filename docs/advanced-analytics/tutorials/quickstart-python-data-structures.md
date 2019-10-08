---
title: Python と SQL のデータ型およびオブジェクトの操作
titleSuffix: SQL Server Machine Learning Services
description: このクイックスタートでは、Python でデータ型とデータオブジェクトを操作する方法と、SQL Server Machine Learning Services を使用して SQL Server する方法について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/04/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 06540305d84ea16b76363ebb21cea0a246fd9ed8
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006057"
---
# <a name="quickstart-handle-data-types-and-objects-using-python-in-sql-server-machine-learning-services"></a>クイック スタート: SQL Server Machine Learning Services での Python を使用したデータ型とオブジェクトの処理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、SQL Server Machine Learning Services で Python を使用するときのデータ構造の使用方法を示します。

SQL Server は、表形式のデータを操作するのに最適な Python **pandas** パッケージに依存しています。 ただし、スカラーを Python から SQL Server に渡すことはできません。 このクイックスタートでは、いくつかの基本的なデータ型の定義を確認して、Python と SQL Server 間で表形式のデータを渡すときに実行する可能性のある追加の問題を準備します。

前もって理解しておくべき概念は次のとおりです。

- データフレームは、_複数_の列を含むテーブルです。
- データフレームの1つの列は、系列と呼ばれるリストのようなオブジェクトです。
- データフレームの単一の値はセルと呼ばれ、インデックスによってアクセスされます。

データフレームにテーブル構造が必要な場合、計算の1つの結果をデータフレームとして公開するにはどうすればよいでしょうか。 1つの答えは、単一のスカラー値を系列として表すことです。これは、データフレームに簡単に変換できます。 

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、Python 言語がインストールされている[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)で SQL Server のインスタンスにアクセスする必要があります。

- また、Python スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-sql クエリまたはストアドプロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリツールを使用して実行できます。 このクイックスタートでは、 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)を使用します。

## <a name="scalar-value-as-a-series"></a>系列としてのスカラー値

この例では、単純な数値演算を行い、スカラーを系列に変換します。

1. 系列にはインデックスが必要です。このインデックスは、次に示すように手動で割り当てることも、プログラムで割り当てることもできます。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   print(c)
   s = pandas.Series(c, index =["simple math example 1"])
   print(s)
   '
   ```

   系列はデータフレームに変換されていないため、[メッセージ] ウィンドウに値が返されますが、結果がより表形式になっていることがわかります。

   **結果**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   dtype: float64
   ```

1. 系列の長さを増やすには、配列を使用して新しい値を追加します。 

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   '
   ```

   インデックスを指定しない場合は、0から始まり、配列の長さで終わる値を持つインデックスが生成されます。

   **結果**

   ```text
   STDOUT message(s) from external script: 
   0    0.5
   1    2.0
   dtype: float64
   ```

1. **インデックス**値の数を増やしても、新しい**データ**値を追加しない場合、データ値は系列に合わせて繰り返されます。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   a = 1
   b = 2
   c = a/b
   s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
   print(s)
   '
   ```

   **結果**

   ```text
   STDOUT message(s) from external script: 
   0.5
   simple math example 1    0.5
   simple math example 2    0.5
   dtype: float64
   ```

## <a name="convert-series-to-data-frame"></a>系列をデータフレームに変換します

スカラー数値演算の結果を表形式構造に変換した後も、SQL Server で処理できる形式に変換する必要があります。

1. 系列をデータフレームに変換するには、pandas の[データフレーム](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe)メソッドを呼び出します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   df = pd.DataFrame(s)
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   結果は次のようになります。 インデックスを使用してデータフレームから特定の値を取得する場合でも、インデックス値は出力の一部ではありません。

   **結果**

   |ResultValue|
   |------|
   |0.5|
   |2|

## <a name="output-values-into-dataframe"></a>値をデータフレームに出力します。

次に、2つの系列の計算結果から特定の値をデータフレームに出力します。 最初のには、Python によって生成される連続する値のインデックスがあります。 2番目の例では、文字列値の任意のインデックスを使用します。

1. 次の例では、整数インデックスを使用して系列から値を取得します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   d = a*b
   s = pandas.Series([c,d])
   print(s)
   df = pd.DataFrame(s, index=[1])
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **結果**

   |ResultValue|
   |------|
   |2.0|

   自動生成されたインデックスは0から始まることに注意してください。 範囲外のインデックス値を使用して、何が起こるかを確認してください。

1. 次に、文字列インデックスを使用して、他のデータフレームから1つの値を取得します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   a = 1
   b = 2
   c = a/b
   s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
   print(s)
   df = pd.DataFrame(s, index=["simple math example 1"])
   OutputDataSet = df
   '
   WITH RESULT SETS((ResultValue FLOAT))
   ```

   **結果**

   |ResultValue|
   |------|
   |0.5|

   数値インデックスを使用してこの系列から値を取得しようとすると、エラーが発生します。

## <a name="next-steps"></a>次の手順

SQL Server で高度な Python 関数を記述する方法については、次のクイックスタートを参照してください。

> [!div class="nextstepaction"]
> [SQL Server Machine Learning Services を使用した高度な Python 関数の作成](quickstart-python-functions.md)

SQL Server Machine Learning Services での Python の使用の詳細については、次の記事を参照してください。

- [Python で予測モデルを作成してスコア付けする](quickstart-python-train-score-model.md)
- [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
