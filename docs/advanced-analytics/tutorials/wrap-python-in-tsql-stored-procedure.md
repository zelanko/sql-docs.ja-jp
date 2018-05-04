---
title: ストアド プロシージャでの Python コードをラップ |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3b7ffeac0dfe1e441f188aae67e28004e294fc3e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="wrap-python-code-in-a-stored-procedure"></a>ストアド プロシージャでの Python コードを折り返す
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[前のレッスン](run-python-using-t-sql.md)、Python SQL サーバーと通信する方法を学習します。 このレッスンでは、Python サンプル データセットからデータを取得し、SQL Server テーブルにそのデータを書き込むのストアド プロシージャでの Python コードを埋め込む方法を学習します。

システム ストアド プロシージャ[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)に Python SQL 変数と SQL のデータセットを通過するラッパーを提供します。 また、Python での結果の出力を処理しに渡して SQL Server 形式で SQL データ型と互換性のあるします。

このしくみを見てみましょう。

## <a name="prepare-the-database-and-tables"></a>データベースとテーブルを準備します。

リモート クライアントを設定および Visual Studio Code、Visual Studio、PyCharm、またはその他のツールを使用して、シナリオを簡略化する Python コードを実行することはできますが、このレッスンではすべてのコードは、ストアド プロシージャの一部として実行してください。

1. SQL Server Management Studio を起動し、新しい開きます**クエリ**ウィンドウです。  

2. このプロジェクトの新しいデータベースを作成し、コンテキストの変更、**クエリ**ウィンドウが、新しいデータベースを使用します。

    ```sql
    CREATE DATABASE sqlpy
    GO
    USE sqlpy
    GO
    ```

    > [!TIP] 
    > SQL Server の初心者または自分が所有するサーバーで作業している、よくある間違いにログインし、ルーティング グループにある作業を開始、**マスター**データベース。 適切なデータベースを使用していることを確認する常に、コンテキストを使用して指定、`USE <database name>`ステートメントです。

3. 一部の空テーブルの追加: データを格納する 1 つと、モデルのトレーニングを行うを格納する 1 つです。 後で Python を使用してテーブルを作成します。

    次のコードでは、トレーニング データのテーブルを作成します。

    ```sql
    DROP TABLE IF EXISTS iris_data;
    GO
    CREATE TABLE iris_data (
      id INT NOT NULL IDENTITY PRIMARY KEY
      , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
      , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
      , "Species" VARCHAR(100) NOT NULL, "SpeciesId" INT NOT NULL
    );
    ```

    覚えなくても、支払いを行う、T-SQL に慣れていない場合、`DROP...IF`ステートメントです。 テーブルを作成しようとして、既に存在する、SQL Server はエラーを返します"が既にデータベースに ' iris_data' という名前のオブジェクトです。"。 このようなエラーを回避する方法の 1 つは、コードの一部として、既存のテーブルまたはその他のオブジェクトを削除するのにです。

4. トレーニング済みモデルを格納するために使用するテーブルを作成する次のコードを実行します。 SQL Server での Python (R) モデルを保存するする必要があるシリアル化型の列に格納されている**varbinary (max)** です。 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    モデルの内容に加え通常とも、モデルの名前、日付をトレーニング ソース アルゴリズムとパラメーター、ソース データなどの他の便利メタデータの列を追加し、などです。 ここではおうまくシンプルにし、モデル名のみを使用します。

## <a name="populate-the-table"></a>テーブルを設定します。

Python から SQL Server にトレーニング データを移動するには、は、テーブルは、複数の手順を示します。

+ 必要なデータを取得するストアド プロシージャをデザインするとします。
+ 実際にデータを取得するストアド プロシージャを実行するとします。
+ INSERT ステートメントを使用して、取得したデータの保存場所を指定します。

1. Python コードが含まれる次のストアド プロシージャを作成します。 

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    from sklearn import datasets
    iris = datasets.load_iris()
    iris_data = pandas.DataFrame(iris.data)
    iris_data["Species"] = pandas.Categorical.from_codes(iris.target, iris.target_names)
    iris_data["SpeciesId"] = iris.target
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

    このコードを実行するときにメッセージが表示、"コマンド正常に完了します" この方法がすべては、お客様の仕様に従って、ストアド プロシージャが作成されたことです。

2. 実際には、テーブルの作成、ストアド プロシージャを実行し、データの書き込み先のテーブルを指定します。 実行すると、ストアド プロシージャは、組み込み Python サンプル データから、虹彩データセットを読み込む Python コードを実行します。

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    初めて使用する T-SQL で、INSERT ステートメントが新しいデータのみによって追加されることを認識します。既存のデータを確認、または削除し、テーブルをリビルドするされません。 テーブル内の同じデータの複数のコピーを取得するを避けるため、ステートメントを実行できますこのまず:`TRUNCATE TABLE iris_data`です。 T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql)ステートメントでは既存のデータが削除されますが、テーブルの構造をそのまま保持します。

    > [!TIP]
    > ストアド プロシージャを変更した後でする必要はありませんを削除して再作成します。 使用して、 [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql)ステートメントです。 

3. データが正しく読み込まれたことを確認するには、いくつかのクエリを実行できます。

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

[次のレッスン](../tutorials/train-score-using-python-in-tsql.md)、機械学習モデルを作成し、テーブルに保存します。

### <a name="further-reading-about-stored-procedures"></a>ストアド プロシージャについての詳細情報

SQL Server に慣れていない場合は、最初に複雑になり、ストアド プロシージャがあります。 ストアド プロシージャは、アプリケーションとサーバー間でデータを渡すための強力で柔軟なインターフェイスです。 ストアド プロシージャを使用すると、動的に定義できます、入力を簡単に渡す新しいモデル名、新しいパラメーター、および、新しいデータで、Python コードを変更することがなく。

ストアド プロシージャのしくみの概要については、次を参照してください。[ストアド プロシージャ (データベース エンジン)](https://docs.microsoft.com/sql/relational-databases/stored-procedures/stored-procedures-database-engine)、またはこのチュートリアル:[書き込み TRANSACT-SQL ステートメント](https://docs.microsoft.com/sql/t-sql/tutorial-writing-transact-sql-statements)です。

いくつかの優れたチュートリアル コミュニティ サイトなど[SQL Server Central](http://www.sqlservercentral.com/)または[SQL チーム](http://www.sqlteam.com/)です。

最適なことができます: T-SQL での Python コード カプセル化する方法を考える、これらの機能を使用しても検討します。

+ ストアド プロシージャの既定値を定義します。
+ 入力変数を通過する OUTPUT キーワードを使用します。
+ 適切なデータ型と列名を持つアプリケーションによって使用されるデータと結果を使用してスキーマ定義を作成します。
+ バッチ処理を向上させるためにヒントを提供します。
+ EXECUTE AS を使用して、コードをテストする別のユーザーを偽装する句

## <a name="next-lesson"></a>次のレッスン

[Python のモデルをトレーニングし、SQL Server でスコアを生成](../tutorials/train-score-using-python-in-tsql.md)
