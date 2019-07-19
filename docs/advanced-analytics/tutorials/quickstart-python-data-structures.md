---
title: Python、SQL Server Machine Learning でのデータ構造を操作するためのクイック スタート
description: このクイック スタートでは、SQL Server での Python スクリプトの学習の使用方法データ構造 sp_execute_external_script のシステム ストアド プロシージャで。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: ffbbd39c08221db4afa6427626ca618e04617166
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962089"
---
# <a name="quickstart-python-data-structures-in-sql-server"></a>クイック スタート: SQL Server での Python データ構造
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、SQL Server Machine Learning Services での Python を使用する場合は、データ構造を使用する方法を示します。

SQL Server が、Python 依存**pandas**パッケージで、表形式のデータの操作に適しています。 ただし、Python から SQL Server にはスカラーを渡すし、「とにかく動作する」を想定できません。 このクイック スタートでは、Python と SQL Server の間で表形式のデータを渡すときに間で実行する可能性のあるその他の問題についての準備に、一部の基本的なデータ型定義を確認します。

+ データ フレームを持つテーブルは、_複数_列。
+ 1 つの列、データ フレームは、系列と呼ばれるリストのようなオブジェクトです。
+ 1 つの値は、データ フレームのセルし、インデックスを使用して呼び出す必要があります。

Data.frame には、表形式の構造が必要な場合、データ フレームとして、計算の 1 つの結果をどのようには公開しますか。 1 つの答えでは、データ フレームに変換が簡単にデータ系列として単一のスカラー値を表すためです。 

## <a name="prerequisites"></a>必須コンポーネント

前のクイック スタート[SQL server が存在することを確認する Python](quickstart-python-verify.md)情報を提供し、このクイック スタートに必要な Python 環境を設定するためにリンクします。

## <a name="scalar-value-as-a-series"></a>一連のスカラー値

この例では、単純な算術計算には、系列をスカラーに変換します。

1. 系列には、インデックスは、次に示すように、手動またはプログラムによって割り当てることができますが必要です。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    s = pandas.Series(c, index =["simple math example 1"])
    print(s)
    '
    ```

2. 系列は、data.frame に変換されていない、ためメッセージ ウィンドウで、値が返されますが、結果がより表形式であることを確認できます。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. 系列の長さを増やすには配列を使用して新しい値を追加できます。 

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    s = pandas.Series([c,d])
    print(s)
    '
    ```

    インデックスを指定しない場合は、0 から始まる配列の長さで終わる値を持つインデックスが生成されます。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    0    0.5
    1    2.0
    dtype: float64
    ```

4. 数を増やす場合**インデックス**値、新規に追加しないで**データ**値、連続データを作成するデータ値が繰り返されます。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
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

## <a name="convert-series-to-data-frame"></a>系列をデータ フレームに変換します。

表形式の構造体に、数学のスカラー結果を変換すること、SQL Server が処理できる形式に変換する必要います。 

1. 一連を data.frame に変換する、pandas を呼び出す[データ フレーム](https://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe)メソッド。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
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
    WITH RESULT SETS (( ResultValue float ))
    ```

2. 結果は、以下に示します。 Data.frame から特定の値を取得するインデックスを使用する場合でも、出力の一部ではないインデックス値。

    **結果**

    |ResultValue|
    |------|
    |0.5|
    |2|

## <a name="output-values-into-dataframe"></a>Data.frame に出力値

単純な算術演算の結果を含む、2 つの系列を data.frame への変換のしくみを見てみましょう。 最初には、Python によって生成される連続した値のインデックスがあります。 2 つ目は、文字列値の任意のインデックスを使用します。

1. この例では、整数インデックスを使用する系列の値を取得します。

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
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
    WITH RESULT SETS (( ResultValue float ))
    ```

    自動生成されたインデックスは 0 から始まることに注意してください。 範囲のインデックス値を使用してお試しくださいし、動作を確認します。

2. これで、文字列のインデックスを持つその他のデータ フレームから 1 つの値を取得しましょう。 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    import pandas as pd
    a = 1
    b = 2
    c = a/b
    s = pandas.Series(c, index =["simple math example 1", "simple math example 2"])
    print(s)
    df = pd.DataFrame(s, index=["simple math example 1"])
    OutputDataSet = df
    '
    WITH RESULT SETS (( ResultValue float ))
    ```

    **結果**

    |ResultValue|
    |------|
    |0.5|

    数値インデックスを使用して、このシリーズから値を取得しようとすると、エラーが表示されます。

## <a name="next-steps"></a>次の手順

次に、SQL Server で Python を使用して、予測モデルを構築します。

> [!div class="nextstepaction"]
> [作成、トレーニング、および SQL Server でのストアド プロシージャで Python モデルを使用](quickstart-python-train-score-in-tsql.md)