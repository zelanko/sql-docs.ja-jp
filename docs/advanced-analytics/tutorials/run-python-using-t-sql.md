---
title: T-SQL を使用して Python を実行 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: db959c9d8802ad3d3d2f7e8bdb64e194130dfeba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="run-python-using-t-sql"></a>T-SQL を使用して実行の Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルでは、SQL Server 2017 での Python コードを実行する方法について説明します。 SQL Server と、Python の間でデータを移動するプロセスの手順を説明し、ストアド プロシージャで適切な形式の Python コードをラップする方法について説明します[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)をビルドするには、トレーニング、および SQL の機械学習モデルを使用サーバー。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するは、まず SQL Server 2017 をインストールし、」の説明に従って、インスタンスで、Machine Learning のサービスを有効にする必要があります[インストール SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)です。 

インストールする必要がありますも[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)です。 代わりに、限り、サーバーおよびデータベースに接続して T-SQL クエリまたはストアド プロシージャを実行できますデータベース管理またはクエリ、別のツールを使用することができます。

セットアップを完了したら、このチュートリアルでは、ストアド プロシージャのコンテキストでの Python コードを実行する方法についてに戻ります。 

## <a name="overview"></a>概要

このチュートリアルには、4 つのレッスンが含まれています。

+ SQL Server および Python 間のデータ移動の基礎: 基本的な要件、データ構造、入力、出力をについて説明します。
+ サンプル データの読み込みなどの単純な Python タスクにストアド プロシージャの使い方を練習します。
+ Python 機械学習モデルを作成するストアド プロシージャを使用し、モデルからスコアを生成します。
+ 省略可能なレッスンからを実行する Python として SQL Server を使用して、リモート クライアントのユーザーに対して、_計算コンテキスト_です。 は、モデルを構築するためのコードが含まれていますただし、ある程度の Python 環境と Python tools に精通してがあることが必要です。

SQL Server 2017 に固有の他の Python サンプルは、ここで指定した: [SQL Server の Python のチュートリアル](../tutorials/sql-server-python-tutorials.md)

## <a name="verify-that-python-is-enabled-and-the-launchpad-is-running"></a>Python を有効にし、スタート パッドを実行していることを確認してください。

1. Management Studio で、サービスが有効になっているかどうかを確認するには、このステートメントを実行します。

    ```sql
    sp_configure 'external scripts enabled'
    ```

    場合**run_value** 1 の場合は、マシン学習機能はインストールして使用します。

    エラーの一般的な原因は、SQL Server と Python 間の通信を管理するには、スタート パッドが停止されたことです。 スタート パッドの状態を表示するには、Windows を使用して**Services**パネル、または SQL Server 構成マネージャーを開くことによってです。 サービスが停止すると、再起動します。

2. 次に、Python ランタイムが作業し、SQL Server と通信することを確認します。 これを行うには、新しく開きます**クエリ**SQL Server Management Studio でのウィンドウおよび Python のインストール先のインスタンスに接続します。

    ```sql
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'print(3+4)'
    ```

    すべてが適切では場合、は、次のような結果のメッセージが表示されます。

    ```text
    STDOUT message(s) from external script: 
    7
    ```

3. エラーが発生する場合は、さまざまなサーバーおよび Python 通信できることを確認することがあります。 

    Windows ユーザー グループを追加する必要があります`SQLRUserGroup`スタート パッドが Python と SQL Server 間の通信を提供できることを確認する、インスタンス上のログインとして。 (同じグループは両方の R の使用および Python コードの実行) します。詳細については、次を参照してください。[有効黙示的な認証](../r/add-sqlrusergroup-to-database.md)です。
    
    さらに、無効になっているネットワーク プロトコルを有効にするにまたは SQL Server は、外部クライアントと通信できるようにするには、ファイアウォールを解放する必要があります。 詳細については、次を参照してください。[のセットアップに関するトラブルシューティング](../common-issues-external-script-execution.md)です。

## <a name="basic-python-interaction"></a>基本的な Python 対話

これには SQL Server での Python コードを実行する 2 つの方法があります。

+ システム ストアド プロシージャの引数としての Python スクリプトの追加**sp_execute_external_script**
+ リモート Python クライアントでは、SQL Server に接続し、計算コンテキストとして SQL Server を使用してコードを実行します。 これは、必要があります[revoscalepy](../python/what-is-revoscalepy.md)です。

このチュートリアルの主な目的は、ストアド プロシージャでの Python を使用することができます。

1. SQL Server および Python の間のデータの前後の渡す方法を表示する単純なコードを実行します。

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

2. すべてのセットアップが正常にあり、その Python と SQL Server が互いに通信した場合、正しい結果が計算され、および、Python`print`関数に結果を返します、**メッセージ**windows です。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    0.5 2
    ```
    
    取得中に**stdout**メッセージは、コードをテストするときに便利ですより多くの場合する必要がありますで結果を返す表形式、アプリケーションで使用したり、テーブルに書き込むようにします。 

ここでは、これらの規則に注意してください。

+ 内のすべての`@script`引数が有効な Python コードをする必要があります。 
+ コードは、インデント、変数名、およびなどに関するすべての Pythonic 規則に従う必要があります。 エラーが発生したときに、空白文字および大文字小文字の区別を確認してください。
+ 既定で読み込まれていないすべてのライブラリを使用している場合、スクリプトの先頭にインポート ステートメントを使用して、それらを読み込む必要があります。 
+ ライブラリが既にインストールされていない場合は、停止、およびパッケージのインストール、Python SQL Server の外部」の説明に従って: [SQL Server に新しい Python パッケージをインストール](../python/install-additional-python-packages-on-sql-server.md)

## <a name="inputs-and-outputs"></a>[スクリプト変換エディター]

既定では、 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 1 つの入力データセットが有効な SQL クエリの形式で指定する通常を受け入れます。 その他の種類の入力は、SQL 変数として渡されることができます: たとえば、渡せるトレーニング済みモデルを変数としてなどを使用してシリアル化の関数[pickle](https://docs.python.org/3.0/library/pickle.html)または[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model)でモデルを記述する、バイナリ形式です。

ストアド プロシージャが返す 1 つの Python[パンダ](http://pandas.pydata.org/pandas-docs/stable/index.html)出力としてデータ フレーム。 ただし変数としてスカラーおよびモデルを出力することができます。 たとえば、バイナリ変数として、トレーニング済みモデルを出力でき、そのモデルをテーブルに書き込む、T SQL の INSERT ステートメントに渡すできます。 バイナリ形式でプロットまたはスカラーを生成することもできます (日付と時刻をなど、個々 の値、経過時間、モデルのトレーニングなど)。

ここは、既定値だけを見てみましょう入力と出力変数では、`InputDataSet`と`OutputDataSet`です。 

1. いくつかの数値演算を行い、結果を出力するには、次のコードを実行します。

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

2. Python コードにはスカラーでは、データ フレームではありませんがによって生成されるため、エラーを取得する必要があります。

        **Results**

        ```text
        line 43, in transform
            raise TypeError('OutputDataSet should be of type pandas.DataFrame')
        ```

3. これで表形式のデータセットに渡す Python、既定の入力変数を使用するときの動作を参照してください`InputDataSet`です。 

    ```sql
    EXECUTE sp_execute_external_script 
    @language = N'Python', 
    @script = N'
    OutputDataSet = InputDataSet
    ',
    @input_data_1 = N'SELECT 1 as Col1'
    ```

    ストアド プロシージャを返します、data.frame、自動的に、Python コード内の余分な何もする必要はありません。

    **結果**

    | ありません columnname|
    |------|
    | 1|

    既定では、1 つの表形式の入力データセットが、名前を持つ`InputDataSet`します。 ただし、次のように行を追加してその名前を変更することができます:`@input_data_1_name = N'myResultName'`です。

    Python を使用する列名は、出力で保持されません。 指定された列名の入力クエリが`Col1`、その名前が返されないは、Python スクリプトで使用される任意の列見出し。 SQL Server にデータを返す場合に、列の名前とデータ型を指定するには、T-SQL を使用して`WITH RESULT SETS`句。

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

    Python 列名は、data.frame と共に返されることはありませんので、結果のセットの句は、出力のスキーマを定義します。

    **結果**

    | ResultValue|
    |------|
    | 1|

5. これで、一般的な Python エラーを確認してみましょう。 前の例からの行を変更`@input_data_1_name = N'MyInput'`に`@input_data_1_name = N'myinput'`です。

    Python のエラーは、SQL Server で使用される、サテライト サービスによって、メッセージとしてに渡されます。 メッセージは長くなるし、SQL Server エラーまたは Python エラーに加えてスタート パッドのエラーを含めるため物置テキストからで患者をします。 キーのメッセージは、この行には。

    ```text
    MyOutput = MyInput
    NameError: name 'MyInput' is not defined
    ```

    R と同様に、Python と小文字は区別ことに注意してください。 そのため、任意の種類のエラーを取得する場合、変数名を確認し、間隔、インデント、およびデータ型の問題を検索します。

## <a name="python-data-structures"></a>Python のデータ構造体

SQL Server は、Python に依存**パンダ**パッケージは表形式のデータを操作するために役立ちます。 ただし、既に見たよう Python から SQL Server にはスカラーを渡すし、"単に動作"予想されることはできません。 このセクションの Python と SQL Server の間で表形式のデータを渡すときに間で実行するその他の問題についての準備に、一部の基本的なデータ型定義を確認します。

+ データ フレームを含むテーブルは、_複数_列です。
+ データ フレームの 1 つの列は、系列と呼ばれるリストのようなオブジェクトです。
+ 1 つの値は、データ フレームのセルには、インデックスによって呼び出すことがあります。

Data.frame が表形式構造を必要とする場合、データ フレームとして計算の 1 つの結果をどのようにを公開しますか。 1 つの応答では、データ フレームに簡単に変換されるデータ系列として単一のスカラー値を表すです。 

1. この例では、いくつかの単純な計算はしを系列にはスカラーに変換します。 系列には、割り当てることができます、ここで示すように、手動またはプログラムによって、インデックスが必要です。

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

2. 系列は、data.frame に変換されていない、ため、[メッセージ] ウィンドウで、値が返されますが、結果がより表形式であることを確認できます。

    **結果**

    ```text
    STDOUT message(s) from external script: 
    0.5
    simple math example 1    0.5
    dtype: float64
    ```

3. 系列の長さを上げるためには配列を使用して新しい値は、追加できます。 

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

表形式構造体に、スカラー演算の結果を変換すること、必要がありますに SQL Server が処理できる形式に変換します。 

1. 系列を data.frame に変換する呼び出しパンダ[データ フレーム](http://pandas.pydata.org/pandas-docs/stable/dsintro.html#dataframe)メソッドです。

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

2. Data.frame から特定の値を取得するインデックスを使用する場合でも、インデックス値が出力をされないことに注意してください。

    **結果**

    |ResultValue|
    |------|
    |0.5|
    |2|

### <a name="output-values-into-dataframe-using-an-index"></a>インデックスを使用して data.frame に出力値

単純な算術演算の結果を含む、2 つの系列が、data.frame への変換のしくみを見てみましょう。 最初には、Python によって生成される連続した値のインデックスがあります。 2 つ目は、文字列値の任意のインデックスを使用します。

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

    自動生成されたインデックスは 0 から始まることに注意してください。 範囲外のインデックス値を使用してくださいし、何が起こるかを確認します。

2. 今すぐみましょう文字列インデックスを持つ他のデータ フレームから 1 つの値を取得します。 

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

    エラーが発生したこのシリーズの値を取得する数値のインデックスを使用しようとする場合。

この演習は、別の Python データ構造を操作し、データ フレームとして正しい結果を取得することを確認する方法の概要を把握することを目的としています。 可能性がありますが終了したことを出力する 1 つの値データ フレームはその分よりも多くの問題です。 幸いにも、すべての種類のストアド プロシージャとの間の値には、変数として簡単に渡すことができます。 次のレッスンをについて説明します。

## <a name="tips"></a>ヒント

+ Python では、プログラミング言語間では、最も柔軟なの 1 つ単一引用符と二重引用符で囲ま; に関してこれらは、ほぼ同義です。 

    ただし、T-SQL は、特定の点のみに対して単一引用符を使用し、`@script`引数では、単一引用符を使用して、Unicode 文字列としての Python コードを囲みます。 したがって、Python コードを確認し、いくつかの単一引用符を二重引用符に変更する必要があります。

+ ストアド プロシージャを見つけることができません`sp_execute_external_script`しますか? 外部スクリプトの実行をサポートするためにインスタンスを構成する可能性があります終了していないことを示します。 SQL Server 2017 セットアップを実行し、機械学習の言語としての Python を選択すると、後にする必要があります明示的に有効にする機能を使用して、 `sp_configure`、インスタンスを再起動します。 

    詳細については、「[インストール SQL Server 2017 Machine Learning Services (In-database)](../install/sql-machine-learning-services-windows-install.md)です。

## <a name="next-steps"></a>次の手順

[SQL ストアド プロシージャでの Python コードを折り返す](wrap-python-in-tsql-stored-procedure.md)