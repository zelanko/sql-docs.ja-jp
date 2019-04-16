---
title: 入力と出力 - SQL Server Machine Learning の Python で使用するためのクイック スタート
description: SQL Server での Python スクリプトのこのクイック スタートでは、入力と出力は、sp_execute_external_script のシステム ストアド プロシージャを構成する方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: a778c4a65b9e3f4cbf4ed77cff46e9061d4b6a8a
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2019
ms.locfileid: "59583225"
---
# <a name="quickstart-handle-inputs-and-outputs-using-python-in-sql-server"></a>クイック スタート: 入力と出力を SQL Server での Python の使用を処理します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、入力を処理する方法について説明し、SQL Server Machine Learning Services での Python を使用する場合に出力します。

既定では、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 1 つの入力データセットが有効な SQL クエリの形式で指定する通常を受け入れます。

他の種類の入力は、SQL 変数として渡すことができますたとえば、渡すことができます、トレーニング済みモデル変数としてシリアル化の関数を使用して[pickle](https://docs.python.org/3.0/library/pickle.html)または[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model)でモデルを記述する、。バイナリ形式です。

ストアド プロシージャが返す 1 つの Python [pandas](https://pandas.pydata.org/pandas-docs/stable/index.html)データ フレームの出力として、スカラー、および変数としてモデルを出力することもできます。 たとえば、二項変数としてトレーニング済みモデルを出力し、そのモデルをテーブルに書き込む、T-SQL INSERT ステートメントに渡すできます。 (バイナリ形式) でのプロットまたはスカラーを生成することもできます (日付と時刻をなど、個々 の値、経過時間、モデルのトレーニングなど)。

## <a name="prerequisites"></a>前提条件

前のクイック スタート[SQL server が存在することを確認する Python](quickstart-python-verify.md)情報を提供し、このクイック スタートに必要な Python 環境を設定するためにリンクします。

## <a name="create-the-source-data"></a>ソース データを作成する

次の T-SQL ステートメントを実行してテスト データの小さなテーブルを作成します。

```sql
CREATE TABLE PythonTestData (col1 INT NOT NULL)
INSERT INTO PythonTestData VALUES (1);
INSERT INTO PythonTestData VALUES (10);
INSERT INTO PythonTestData VALUES (100);
GO
```

テーブルが作成されたら、次のステートメントを使用してテーブルを照会します。
  
```sql
SELECT * FROM PythonTestData
```

**結果**

![PythonTestData テーブルの内容](./media/select-pythontestdata.png)

## <a name="inputs-and-outputs"></a>[スクリプト変換エディター]

既定値を見てみましょう sp_execute_external_script の入力と出力の変数:`InputDataSet`と`OutputDataSet`します。

1. R スクリプトの入力としてテーブルからデータを取得できます。 次のステートメントを実行します。 テーブルからデータを取得、R ランタイムのラウンド トリップ、および列の名前で値を返します*NewColName*します。

    クエリによって返されるデータは、データ フレームとして SQL Database にデータを返す R ランタイムに渡されます。 WITH RESULT SETS 句では、SQL Database の返されたデータ テーブルのスキーマを定義します。

    ```sql
    EXECUTE sp_execute_external_script
        @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    **結果**

    ![テーブルからデータを返す Python スクリプトの出力](./media/python-output-pythontestdata.png)

2. 入力または出力変数の名前を変更してみましょう。 上記のスクリプトは既定の入力を使用し、出力変数名は、 _InputDataSet_と_OutputDataSet_します。 関連付けられている入力データを定義する_InputDatSet_を使用する、 *@input_data_1*変数。

    このスクリプトでは、ストアド プロシージャの出力と入力変数の名前に変更されましたが*SQL_out*と*SQL_in*:

    ```sql
    EXECUTE sp_execute_external_script
      @language = N'Python'
      , @script = N'SQL_out = SQL_in'
      , @input_data_1 = N' SELECT 12 as Col;'
      , @input_data_1_name  = N'SQL_in'
      , @output_data_1_name =  N'SQL_out'
      WITH RESULT SETS (([NewColName] INT NOT NULL));
    ```

    入力と出力の変数の大文字と小文字`@input_data_1_name`と`@output_data_1_name`での Python コードで使用されているのと一致する必要がある`@script`Python は大文字小文字を区別します。

    パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、Python コード内から他のデータセットを呼び出すことができ、データセットに加え、他の型の出力を返すことができます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。 

    `WITH RESULT SETS`ステートメントは、SQL Server で使用されるデータのスキーマを定義します。 Python から返す列ごとに SQL 互換のデータ型を提供する必要があります。 スキーマ定義を使用して、新しい列名を提供する Python data.frame の列名を使用する必要はありませんので。

3. Python スクリプトを使用して値を生成し、入力クエリ文字列のままにできますも_@input_data_1_空白。

    ```sql
    EXECUTE sp_execute_external_script
    @language = N'Python'
    , @script = N'
    import pandas as pd
    mytextvariable = pandas.Series(["hello", " ", "world"]);
    OutputDataSet = pd.DataFrame(mytextvariable);'
    , @input_data_1 = N''
    WITH RESULT SETS (([Col1] CHAR(20) NOT NULL));
    ```

    **結果**

    ![使用してクエリ結果@script入力として](./media/python-data-generated-output.png)

## <a name="next-steps"></a>次のステップ

Python と SQL Server の間で表形式のデータを渡すときに発生する可能性のある問題のいくつかを確認します。

> [!div class="nextstepaction"]
> [クイック スタート:SQL Server での Python データ構造](quickstart-python-data-structures.md)