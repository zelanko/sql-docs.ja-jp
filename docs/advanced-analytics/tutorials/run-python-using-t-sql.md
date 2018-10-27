---
title: SQL Server で T-SQL を使用して Python の実行 |Microsoft Docs
description: T-SQL やストアド プロシージャを使用して、Python の統合を有効にする SQL Server データベース エンジン インスタンス上の Python コードを実行するための基礎について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3b4a7987a0fc9d50bbc5c8803d741be13acf7433
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050899"
---
# <a name="run-python-using-t-sql"></a>T-SQL を使用した Python の実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server 2017 での Python コードを実行する方法について説明します。 SQL Server と Python 間のデータ移動の基礎をチュートリアル: 要件、データ構造、入力と出力します。 ストアド プロシージャで適切な形式での Python コードをラップする方法についても説明[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)にビルド、トレーニング、および SQL Server で機械学習モデルを使用します。

## <a name="prerequisites"></a>前提条件

、コード例を以下の手順を実行するまず SQL Server 2017 のインストールし、」の説明に従って、インスタンスで、Machine Learning サービスを有効にする必要があります[インストール SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)します。 

インストールする必要がありますも[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)します。 または、サーバーとデータベースに接続し、T-SQL クエリまたはストアド プロシージャを実行する限り他のデータベースの管理またはクエリ ツールを使用できます。

環境の準備ができたらは、ストアド プロシージャのコンテキストでの Python コードを実行する方法については、このページに戻ります。 

## <a name="verify-python-exists"></a>Python の存在を確認します。

次の手順では、Python を有効にし、SQL Server スタート パッド サービスが実行されていることを確認します。

1. データベース エンジンのインスタンス上に Python の統合がインストールされているかどうかを確認します。 検索する必要があります**python.exe**という名前のフォルダーで**PYTHON_SERVICES** C:\Program files \microsoft SQL Server\MSSQL14 にします。MSSQLSERVER\. これは、Python コードを実行する SQL Server を使用する Python の実行可能ファイルです。

2. 外部スクリプトを有効にするかどうかを確認します。 Management Studio で、次のステートメントを実行します。

    ```sql
    sp_configure 'external scripts enabled'
    ```

    場合**run_value**は 1 です。 machine learning の機能がインストールされすぐに使用します。

    エラーの一般的な原因は、 [SQL Server スタート パッド サービス](../concepts/extensibility-framework.md#launchpad)、SQL Server と Python 間の通信を管理する機能が停止しました。 スタート パッドの状態を表示するには、Windows を使用して**サービス**パネル、または SQL Server 構成マネージャーを開くことによって。 サービスが停止した場合は、それを再起動します。

3. Python ランタイムが作業し、SQL Server と通信することを確認します。 これを行うには、新しく開きます**クエリ**ウィンドウに SQL Server Management Studio で Python がインストールされているインスタンスに接続します。

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    場合は、次のような結果のメッセージが表示されます。

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. エラーが発生する場合のさまざまなサーバーと Python が通信できるようにすることがあります。 

    Windows ユーザー グループを追加する必要があります`SQLRUserGroup`スタート パッドで Python と SQL Server 間の通信を提供できることを確認する、インスタンス上のログインとして。 (同じグループが両方の R の使用し、Python コードの実行)。詳細については、次を参照してください。[暗黙の認証を有効](../security/add-sqlrusergroup-to-database.md)します。
    
    さらに、無効になっているネットワーク プロトコルを有効にまたは SQL Server が外部クライアントと通信できるようにファイアウォールを開く必要があります。 詳細については、次を参照してください。[セットアップのトラブルシューティング](../common-issues-external-script-execution.md)します。

### <a name="call-revoscalepy-functions"></a>Revoscalepy 関数を呼び出す

確認する**revoscalepy**を含むスクリプトの実行が使用できる[rx_summary](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-summary)統計概要データを生成します。 このスクリプトでは、revoscalepy に含まれている組み込みのサンプルからサンプル .xdf データ ファイルを取得する方法を示します。 RxOptions 関数は、提供、 **sampleDataDir**サンプル ファイルの場所を返すパラメーターです。

Rx_summary 型のオブジェクトを返すため`class revoscalepy.functions.RxSummary.RxSummaryResults`、複数の要素が含まれています、pandas を使用して表形式でデータ フレームだけを抽出することができます。

```SQL
EXEC sp_execute_external_script @language = N'Python', 
@script = N'
import os
from pandas import DataFrame
from revoscalepy import rx_summary
from revoscalepy import RxXdfData
from revoscalepy import RxOptions

sample_data_path = RxOptions.get_option("sampleDataDir")
print(sample_data_path)

ds = RxXdfData(os.path.join(sample_data_path, "AirlineDemoSmall.xdf"))
summary = rx_summary("ArrDelay + DayOfWeek", ds)
print(summary)
dfsummary = summary.summary_data_frame
OutputDataSet = dfsummary
'
WITH RESULT SETS  ((ColName nvarchar(25) , ColMean float, ColStdDev  float, ColMin  float,   ColMax  float, Col_ValidObs  float, Col_MissingObs int))
```

## <a name="basic-python-interaction"></a>基本的な Python の対話

SQL Server での Python コードを実行する 2 つの方法はあります。

+ Python スクリプトを追加する、システム ストアド プロシージャの引数として[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)します。

+ [Python クライアントをリモート](../python/setup-python-client-tools-sql.md)、SQL Server に接続し、計算コンテキストとして SQL Server を使用してコードを実行します。 これは、必要があります[revoscalepy](../python/what-is-revoscalepy.md)します。

次の演習は最初の対話モデルに重点を置いて: Python コードをストアド プロシージャに渡す方法です。

1. SQL Server と Python 間のデータの前後の渡す方法を確認する簡単なコードを実行します。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    d = a*b
    print(c, d)
    '
    ```

2. Python と SQL Server が互いに通信を正しく設定するすべてのものがあると仮定すると、正しい結果が計算される、および Python`print`関数に結果を返す、**メッセージ**windows。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```
    
    取得中に**stdout**メッセージは、コードをテストするときに便利ですより多くの場合する必要があるアプリケーションで使用したり、テーブルに書き込むように表形式で結果を返します。 

ここでは、これらのルールに注意してください。

+ 内のすべて、`@script`引数は有効な Python コードである必要があります。 
+ コードは、インデント、変数名、およびなどに関するすべての Python ルールに従う必要があります。 エラーが発生したときに、ホワイト スペースと大文字小文字の区別を確認します。
+ 既定で読み込まれていないすべてのライブラリを使用している場合は、読み込みに、スクリプトの先頭に import ステートメントを使用する必要があります。 SQL Server では、いくつかの製品に固有のライブラリを追加します。 詳細については、次を参照してください。 [Python ライブラリ](../python/python-libraries-and-data-types.md)します。
+ ライブラリがインストールされていない場合は停止し、」の説明に従って、SQL Server の外部での Python パッケージをインストール: [SQL Server に新しい Python パッケージをインストール](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>[スクリプト変換エディター]

既定では、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 1 つの入力データセットが有効な SQL クエリの形式で指定する通常を受け入れます。 

他の種類の入力は、SQL 変数として渡すことができますたとえば、渡すことができます、トレーニング済みモデル変数としてシリアル化の関数を使用して[pickle](https://docs.python.org/3.0/library/pickle.html)または[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model)でモデルを記述する、。バイナリ形式です。

ストアド プロシージャが返す 1 つの Python [pandas](http://pandas.pydata.org/pandas-docs/stable/index.html)データ フレームの出力として、スカラー、および変数としてモデルを出力することもできます。 たとえば、二項変数としてトレーニング済みモデルを出力し、そのモデルをテーブルに書き込む、T-SQL INSERT ステートメントに渡すできます。 (バイナリ形式) でのプロットまたはスカラーを生成することもできます (日付と時刻をなど、個々 の値、経過時間、モデルのトレーニングなど)。

ここでは、既定値だけを見てみましょう sp_execute_external_script の入力と出力の変数:`InputDataSet`と`OutputDataSet`します。 

1. いくつかの計算し、結果を出力するには、次のコードを実行します。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    a = 1
    b = 2
    c = a/b
    print(c)
    OutputDataSet = c
    '
    WITH RESULT SETS ((ResultValue float))
    ```

2. Python コードの生成はスカラーでは、データ フレームではありませんので、エラーが表示されます。

    **結果**

    ```text
    line 43, in transform
        raise TypeError('OutputDataSet should be of type pandas.DataFrame')
    ```

3. 既定の入力変数を使用して、Python に表形式のデータセットを渡すときに起こる表示`InputDataSet`します。 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    ストアド プロシージャは、Python コードでは余分な何もする必要はありません、自動的に data.frame を返します。

    **結果**

    | columnname なし|
    |------|
    | 1|

    既定では、1 つの表形式の入力データセットが、名前を持つ`InputDataSet`します。 ただし、このような行を追加してその名前を変更できます。`@input_data_1_name = N'myResultName'`します。

    Python で使用される列名は、出力で保持されません。 指定された列名の入力クエリが`Col1`、その名前が返されないも Python スクリプトで使用される任意の列見出しになります。 SQL Server にデータを取得するときに、列名とデータ型を指定するに T-SQL を使用して、`WITH RESULT SETS`句。

4. この例では、入力と出力変数の新しい名前を提供します。

    ```sql
    execute sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    MyOutput = MyInput
    ',
    @input_data_1_name = N'MyInput',
    @input_data_1 = N'SELECT 1 as Col1',
    @output_data_1_name = N'MyOutput'
    WITH RESULT SETS ((ResultValue int))
    ```

    結果のセットの句は、Python の列名は、data.frame と共に返されることはありませんので、出力のスキーマを定義します。

    **結果**

    | ResultValue|
    |------|
    | 1|

5. これで、一般的な Python エラーを見てみましょう。 前の例からの行を変更`@input_data_1_name = N'MyInput'`に`@input_data_1_name = N'myinput'`します。

    Python のエラーは、SQL Server で使用するサテライト サービスによって、メッセージとしてに渡されます。 メッセージは長くなるし、SQL Server エラーまたは Python のエラーに加えてスタート パッドのエラーは、テキストは掘り出すで患者があるためです。 重要なメッセージは、この行には。

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    Python、R のように小文字が区別されることを思い出してください。 そのため、任意の種類のエラーが発生したときに、変数の名前を確認し、空白文字、インデント、およびデータ型の問題を検索します。

## <a name="python-data-structures"></a>Python のデータ構造体

SQL Server が、Python 依存**pandas**パッケージで、表形式のデータの操作に適しています。 ただし、Python から SQL Server にはスカラーを渡すし、本来は、「とにかく動作する」ことはできませんを既に説明しました。 このセクションでの Python と SQL Server の間で表形式のデータを渡すときに間で実行する可能性のあるその他の問題の準備に、一部の基本的なデータ型定義を確認します。

+ データ フレームを持つテーブルは、_複数_列。
+ 1 つの列、データ フレームは、系列と呼ばれるリストのようなオブジェクトです。
+ 1 つの値は、データ フレームのセルし、インデックスを使用して呼び出す必要があります。

Data.frame には、表形式の構造が必要な場合、データ フレームとして、計算の 1 つの結果をどのようには公開しますか。 1 つの答えでは、データ フレームに変換が簡単にデータ系列として単一のスカラー値を表すためです。 

1. この例では、単純な算術計算には、系列をスカラーに変換します。 系列には、インデックスは、次に示すように、手動またはプログラムによって割り当てることができますが必要です。

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

### <a name="convert-series-to-data-frame"></a>系列をデータ フレームに変換します。

表形式の構造体に、数学のスカラー結果を変換すること、SQL Server が処理できる形式に変換する必要います。 

1. 一連を data.frame に変換する、pandas を呼び出す[データ フレーム](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe)メソッド。

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

2. Data.frame から特定の値を取得するインデックスを使用する場合でも、出力をインデックス値がないことに注意してください。

    **結果**

    |ResultValue|
    |------|
    |0.5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>インデックスを使用して data.frame に出力値

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

この演習の別の Python のデータ構造を操作し、データ フレームとして正しい結果を取得することを確認する方法が理解できるためのものでした。 その出力を 1 つの値をデータ フレームはその分よりもさらに問題が終了可能性があります。 さいわい、変数としてすべての種類のストアド プロシージャとの間の値を簡単に渡すことができます。 次のレッスンをについて説明します。

## <a name="tips"></a>ヒント

+ Python では、プログラミング言語間で、最も柔軟性が高いの 1 つ単一引用符と二重引用符に関してほぼ同義です。 

    ただし、T-SQL では、特定の情報のみに対して単一引用符を使用し、`@script`引数では、単一引用符を使用して、Unicode 文字列としての Python コードを囲みます。 そのため、Python コードを確認し、いくつかの単一引用符を二重引用符に変更する必要があります。

+ ストアド プロシージャを見つけることができません`sp_execute_external_script`でしょうか。 外部スクリプトの実行をサポートするためにインスタンスを構成する可能性があります完了していないことを意味します。 SQL Server 2017 セットアップを実行し、機械学習言語として Python を選択すると、後にする必要がありますも明示的に有効に機能を使用して、 `sp_configure`、インスタンスを再起動します。 

    詳細については、次を参照してください。[インストール SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)します。

## <a name="next-steps"></a>次の手順

[デモのあやめのデータセットを設定します。](demo-data-iris-in-sql.md)