---
title: 単純な Python スクリプトを作成して実行する
titleSuffix: SQL Server Machine Learning Services
description: SQL Server Machine Learning Services を使用して、SQL Server インスタンスで単純な Python スクリプトを作成して実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6f7fe62f746a8f6e74ebdf9f766b76c0edc720a
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "71204299"
---
# <a name="quickstart-create-and-run-simple-python-scripts-with-sql-server-machine-learning-services"></a>クイック スタート: SQL Server Machine Learning Services を使用した単純な Python スクリプトの作成と実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、 [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)を使用して、一連の単純な Python スクリプトを作成して実行します。 適切な形式の Python スクリプトをストアドプロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)にラップし、スクリプトを SQL Server インスタンスで実行する方法について説明します。

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、Python 言語がインストールされている[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)で SQL Server のインスタンスにアクセスする必要があります。

- また、Python スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-sql クエリまたはストアドプロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリツールを使用して実行できます。 このクイックスタートでは、 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)を使用します。

## <a name="run-a-simple-script"></a>単純なスクリプトを実行する

Python スクリプトを実行するには、これを引数としてシステムストアドプロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)に渡します。
このシステムストアドプロシージャは、SQL Server のコンテキストで Python ランタイムを起動し、python にデータを渡し、python ユーザーセッションを安全に管理し、結果をクライアントに返します。

次の手順では、このサンプル Python スクリプトを SQL Server インスタンスで実行します。

```python
a = 1
b = 2
c = a/b
d = a*b
print(c, d)
```

1. SQL Server インスタンスに接続されている**SQL Server Management Studio**で、新しいクエリウィンドウを開きます。

1. 完全な Python スクリプトを`sp_execute_external_script`ストアドプロシージャに渡します。

   スクリプトは `@script`引数を通じて渡されます。 `@script`引数内のすべては、有効な Python コードである必要があります。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

1. 正しい結果が計算され、Python `print`関数によって結果が**Messages**ウィンドウに返されます。

   次のようになります。

    **結果**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Hello World スクリプトを実行する

一般的なスクリプトの例としては、文字列 "Hello World" だけが出力されます。 次のコマンドを実行します。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'OutputDataSet = InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

`sp_execute_external_script` ストアドプロシージャへの入力には次のものが含まれます。

| | |
|-|-|
| @language | 呼び出す言語拡張機能を定義します (この例では Python)。 |
| @script | Python ランタイムに渡されるコマンドを定義します。<br>Python スクリプト全体を Unicode テキストとしてこの引数で囲む必要があります。 また、 **nvarchar**型の変数にテキストを追加し、その変数を呼び出すこともできます。 |
| @input_data_1 | データフレームとして SQL Server するデータを返す Python ランタイムに渡される、クエリによって返されるデータ |
| WITH RESULT SETS | 句では、SQL Server に対して返されるデータテーブルのスキーマを定義します。この場合は、列名として "Hello World" を、データ型に**int**を追加します。 |

このコマンドは、次のテキストを出力します。

| Hello World |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>入力と出力を使用する

既定では、`sp_execute_external_script` は1つのデータセットを入力として受け取ります。通常は、有効な SQL クエリの形式で指定します。 次に、1つの Python データフレームを出力として返します。

ここでは、`sp_execute_external_script`の既定の入力変数と出力変数を使用します。**Inputdataset**と**outputdataset**。

1. テストデータの小さなテーブルを作成します。

    ```sql
    CREATE TABLE PythonTestData (col1 INT NOT NULL)
    
    INSERT INTO PythonTestData
    VALUES (1);
    
    INSERT INTO PythonTestData
    VALUES (10);
    
    INSERT INTO PythonTestData
    VALUES (100);
    GO
    ```

1. テーブルに対してクエリを実行するには、`SELECT`ステートメントを使用します。
  
    ```sql
    SELECT *
    FROM PythonTestData
    ```

    **結果**

    ![PythonTestData テーブルの内容](./media/select-pythontestdata.png)

1. 次の Python スクリプトを実行します。 `SELECT` ステートメントを使用してテーブルからデータを取得し、それを Python ランタイムを介して渡し、データをデータフレームとして返します。 `WITH RESULT SETS` 句は、SQL に対して返されたデータテーブルのスキーマを定義し、列名 *NewColName* を追加します。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'OutputDataSet = InputDataSet;'
        , @input_data_1 = N'SELECT * FROM PythonTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **結果**

    ![テーブルからデータを返す Python スクリプトからの出力](./media/python-output-pythontestdata.png)

1. 次に、入力変数と出力変数の名前を変更します。 入力変数と出力変数の既定の名前は**inputdataset**と**outputdataset**で、次のスクリプトによって名前が**SQL_in**および**SQL_out**に変更されます。

    ```sql
    EXECUTE sp_execute_external_script @language = N'Python'
        , @script = N'SQL_out = SQL_in;'
        , @input_data_1 = N'SELECT 12 as Col;'
        , @input_data_1_name  = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    Python では大文字と小文字が区別されることに注意してください。 Python スクリプトで使用される入力変数と出力変数 (**SQL_out**、 **SQL_in**) は、大文字小文字を含め、`@input_data_1_name` および `@output_data_1_name` で定義されている名前と一致する必要があります。

   > [!TIP]
   > パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、Python コード内から他のデータセットを呼び出すことができます。また、データセットに加えて他の型の出力を返すこともできます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。

1. また、入力データのない Python スクリプトを使用して値を生成することもできます (`@input_data_1` は空白に設定されます)。

   次のスクリプトは、"hello" と "world" というテキストを出力します。

   ```sql
   EXECUTE sp_execute_external_script @language = N'Python'
       , @script = N'
   import pandas as pd
   mytextvariable = pandas.Series(["hello", " ", "world"]);
   OutputDataSet = pd.DataFrame(mytextvariable);
   '
       , @input_data_1 = N''
   WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
   ```

   **結果**

   ![入力とし@scriptてを使用したクエリ結果](./media/python-data-generated-output.png)

> [!NOTE]
> Python では、先頭のスペースを使用してステートメントをグループ化します。 そのため、前のスクリプトのように、埋め込まれた Python スクリプトが複数の行にまたがる場合は、SQL コマンドを使用して Python コマンドにインデントを設定しないようにしてください。 たとえば、次のスクリプトではエラーが生成されます。

  ```text
  EXECUTE sp_execute_external_script @language = N'Python'
      , @script = N'
      import pandas as pd
      mytextvariable = pandas.Series(["hello", " ", "world"]);
      OutputDataSet = pd.DataFrame(mytextvariable);
      '
      , @input_data_1 = N''
  WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
  ```

## <a name="check-python-version"></a>Python のバージョンを確認する

SQL Server インスタンスにインストールされている Python のバージョンを確認するには、次のスクリプトを実行します。

```sql
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import sys
print(sys.version)
'
GO
```

Python `print`関数は、バージョンを **[メッセージ]** ウィンドウに返します。 次の出力例では、Python バージョン3.5.2 がインストールされていることがわかります。

**結果**

```text
STDOUT message(s) from external script: 
3.5.2 |Continuum Analytics, Inc.| (default, Jul  5 2016, 11:41:13) [MSC v.1900 64 bit (AMD64)]
```

## <a name="list-python-packages"></a>Python パッケージの一覧表示

Microsoft では、SQL Server インスタンスに SQL Server Machine Learning Services と共にプレインストールされた多数の Python パッケージを提供しています。

バージョンなど、インストールされている Python パッケージの一覧を表示するには、次のスクリプトを実行します。

```SQL
EXECUTE sp_execute_external_script @language = N'Python'
    , @script = N'
import pip
for i in pip.get_installed_distributions():
    print(i)
'
GO
```

出力は Python の`pip.get_installed_distributions()`からのものであり、`STDOUT` メッセージとして返されます。

**結果**

```text
STDOUT message(s) from external script:
xlwt 1.2.0
XlsxWriter 0.9.6
xlrd 1.0.0
win-unicode-console 0.5
widgetsnbextension 2.0.0
wheel 0.29.0
Werkzeug 0.12.1
wcwidth 0.1.7
unicodecsv 0.14.1
traitlets 4.3.2
tornado 4.4.2
toolz 0.8.2
. . .
```

## <a name="next-steps"></a>次の手順

SQL Server で Python を使用して機械学習モデルを作成するには、次のクイックスタートに従ってください。

> [!div class="nextstepaction"]
> [SQL Server Machine Learning Services を使用した Python での予測モデルの作成とスコア付け](quickstart-python-train-score-model.md)

SQL Server Machine Learning Services の詳細については、次の記事を参照してください。

- [SQL Server Machine Learning Services での Python を使用したデータ型とオブジェクトの処理](quickstart-python-data-structures.md)
- [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
