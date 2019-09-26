---
title: 単純な R スクリプトを作成して実行する
titleSuffix: SQL Server Machine Learning Services
description: SQL Server Machine Learning Services を使用して、SQL Server インスタンスで単純な R スクリプトを作成して実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d723fa9b90659eb31e96626a3a85c1299c17fa2f
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150315"
---
# <a name="quickstart-create-and-run-simple-r-scripts-with-sql-server-machine-learning-services"></a>クイック スタート: SQL Server Machine Learning Services を使用した単純な R スクリプトの作成と実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、 [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)を使用して、一連の単純な R スクリプトを作成して実行します。 ストアドプロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)に適切な形式の R スクリプトをラップし、スクリプトを SQL Server インスタンスで実行する方法について説明します。

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、R 言語がインストールされている[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)で SQL Server のインスタンスにアクセスする必要があります。

  SQL Server インスタンスは、Azure 仮想マシンまたはオンプレミスに配置できます。 外部スクリプト機能が既定で無効になっているため、[外部スクリプトを有効](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)にし、開始する前に**SQL Server Launchpad サービス**が実行されていることを確認する必要がある場合があることに注意してください。

- また、R スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-sql クエリまたはストアドプロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリツールを使用して実行できます。 このクイックスタートでは、 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)を使用します。

## <a name="run-a-simple-script"></a>単純なスクリプトを実行する

R スクリプトを実行するには、システムストアドプロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)に引数として渡します。
このシステムストアドプロシージャは、R ランタイムを SQL Server のコンテキストで開始し、データを R に渡し、R ユーザーセッションを安全に管理し、結果をクライアントに返します。

次の手順では、この例の R スクリプトを SQL Server インスタンスで実行します。

```r
a <- 1
b <- 2
c <- a/b
d <- a*b
print(c(c, d))
```

1. **SQL Server Management Studio**を開き、SQL Server インスタンスに接続します。

1. 完全な R スクリプトを`sp_execute_external_script`ストアドプロシージャに渡します。

   スクリプトは引数を`@script`通じて渡されます。 引数内の`@script`すべては、有効な R コードである必要があります。

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    a <- 1
    b <- 2
    c <- a/b
    d <- a*b
    print(c(c, d))
    '
    ```

1. 正しい結果が計算され、R `print`関数によって結果が**Messages**ウィンドウに返されます。

   次のようになります。

    **結果**

    ```text
    STDOUT message(s) from external script:
    0.5 2
    ```

## <a name="run-a-hello-world-script"></a>Hello World スクリプトを実行する

一般的なスクリプトの例としては、文字列 "Hello World" だけが出力されます。 次のコマンドを実行します。

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'OutputDataSet<-InputDataSet'
    , @input_data_1 = N'SELECT 1 AS hello'
WITH RESULT SETS(([Hello World] INT));
GO
```

ストアドプロシージャへ`sp_execute_external_script`の入力は次のとおりです。

| | |
|-|-|
| @language | 呼び出す言語拡張機能 (この場合は R) を定義します。 |
| @script | R ランタイムに渡されるコマンドを定義します。 Unicode テキストとして、この引数で R スクリプト全体を囲む必要があります。 また、 **nvarchar**型の変数にテキストを追加し、その変数を呼び出すこともできます。 |
| @input_data_1 | データフレームとして SQL Server するデータを返す R ランタイムに渡される、クエリによって返されるデータ |
|結果セットを含む | 句では、SQL Server に対して返されるデータテーブルのスキーマを定義し、列名として "Hello World" を追加し、データ型に**int**を追加します。 |

このコマンドは、次のテキストを出力します。

| ハローワールド |
|-------------|
| 1 |

## <a name="use-inputs-and-outputs"></a>入力と出力を使用する

既定では`sp_execute_external_script` 、は1つのデータセットを入力として受け取ります。通常は、有効な SQL クエリの形式で指定します。 次に、1つの R データフレームを出力として返します。

ここでは、の`sp_execute_external_script`既定の入力変数と出力変数を使用します。**Inputdataset**と**outputdataset**。

1. テストデータの小さなテーブルを作成します。

    ```sql
    CREATE TABLE RTestData (col1 INT NOT NULL)
    
    INSERT INTO RTestData
    VALUES (1);
    
    INSERT INTO RTestData
    VALUES (10);
    
    INSERT INTO RTestData
    VALUES (100);
    GO
    ```

1. テーブルに`SELECT`対してクエリを実行するには、ステートメントを使用します。
  
    ```sql
    SELECT *
    FROM RTestData
    ```

    **結果**

    ![RTestData テーブルの内容](./media/select-rtestdata.png)

1. 次の R スクリプトを実行します。 `SELECT`ステートメントを使用してテーブルからデータを取得し、それを R ランタイムを介して渡し、データをデータフレームとして返します。 句`WITH RESULT SETS`は、SQL に対して返されたデータテーブルのスキーマを定義し、列名*NewColName*を追加します。

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'OutputDataSet <- InputDataSet;'
        , @input_data_1 = N'SELECT * FROM RTestData;'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    **結果**

    ![テーブルからデータを返す R スクリプトからの出力](./media/r-output-rtestdata.png)

1. 次に、入力変数と出力変数の名前を変更してみましょう。 入力変数と出力変数の既定の名前は**inputdataset**と**outputdataset**で、このスクリプトによって名前が**SQL_in**および**SQL_out**に変更されます。

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N' SQL_out <- SQL_in;'
        , @input_data_1 = N' SELECT 12 as Col;'
        , @input_data_1_name = N'SQL_in'
        , @output_data_1_name = N'SQL_out'
    WITH RESULT SETS(([NewColName] INT NOT NULL));
    ```

    R では大文字と小文字が区別されることに注意してください。 R スクリプト (**SQL_out**、 **SQL_in**) で使用される入力変数と出力変数は、大文字小文字を`@input_data_1_name`含め`@output_data_1_name`、およびで定義されている名前と一致する必要があります。

   > [!TIP]
   > パラメーターとして渡すことができるのは、1 つの入力データセットのみです。また、1 つのデータセットのみを返すことができます。 ただし、R コード内から他のデータセットを呼び出し、データセットに加えて他の型の出力を返すことができます。 また、OUTPUT キーワードを任意のパラメーターに追加して、その結果を受け取ることもできます。

1. また、入力データのない R スクリプトを使用するだけで値を`@input_data_1`生成することもできます (は空白に設定されます)。

   次のスクリプトは、"hello" と "world" というテキストを出力します。

    ```sql
    EXECUTE sp_execute_external_script @language = N'R'
        , @script = N'
    mytextvariable <- c("hello", " ", "world");
    OutputDataSet <- as.data.frame(mytextvariable);
    '
        , @input_data_1 = N''
    WITH RESULT SETS(([Col1] CHAR(20) NOT NULL));
    ```

    **結果**

    ![入力とし@scriptてを使用したクエリ結果](./media/r-data-generated-output.png)

## <a name="check-r-version"></a>R バージョンの確認

SQL Server インスタンスにインストールされている R のバージョンを確認するには、次のスクリプトを実行します。

```sql
EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'print(version)';
GO
```

R `print`関数は、バージョンを **[メッセージ]** ウィンドウに返します。 次の出力例では、R バージョン3.4.4 がインストールされていることがわかります。

**結果**

```text
STDOUT message(s) from external script:
                   _
platform       x86_64-w64-mingw32
arch           x86_64
os             mingw32
system         x86_64, mingw32
status
major          3
minor          4.4
year           2018
month          03
day            15
svn rev        74408
language       R
version.string R version 3.4.4 (2018-03-15)
nickname       Someone to Lean On
```

## <a name="list-r-packages"></a>R パッケージの一覧表示

Microsoft では、SQL Server Machine Learning Services と共に事前にインストールされた多数の R パッケージを提供しています。

バージョン、依存関係、ライセンス、ライブラリパスの情報など、インストールされている R パッケージの一覧を表示するには、次のスクリプトを実行します。

```SQL
EXEC sp_execute_external_script @language = N'R'
    , @script = N'
OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
WITH result sets((
            Package NVARCHAR(255)
            , Version NVARCHAR(100)
            , Depends NVARCHAR(4000)
            , License NVARCHAR(1000)
            , LibPath NVARCHAR(2000)
            ));
```

出力は R の`installed.packages()`からのものであり、結果セットとして返されます。

**結果**

![R でインストールされたパッケージ](./media/rsql-installed-packages.png) 

## <a name="next-steps"></a>次の手順

SQL Server で R を使用して機械学習モデルを作成するには、次のクイックスタートに従ってください。

> [!div class="nextstepaction"]
> [SQL Server Machine Learning Services を使用して R で予測モデルを作成およびスコア付けする](quickstart-r-train-score-model.md)

SQL Server Machine Learning Services の詳細については、次の記事を参照してください。

- [SQL Server Machine Learning Services で R を使用してデータ型とオブジェクトを処理する](quickstart-r-data-types-and-objects.md)
- [SQL Server Machine Learning Services を使用した高度な R 関数の作成](quickstart-r-functions.md)
- [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
