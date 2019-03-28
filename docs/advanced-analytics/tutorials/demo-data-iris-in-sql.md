---
title: Python および R のチュートリアル - SQL Server Machine Learning のあやめのデモ データ セット
Description: Iris データセットとモデルを格納するテーブルを含むデータベースを作成します。 このデータセットは、SQL Server ストアド プロシージャで R 言語または Python コードをラップする方法を示す演習で使用されます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: f4a57f89a89ed8d5cbf81cc3d63fc1f19b42e51a
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510099"
---
#  <a name="iris-demo-data-for-python-and-r-tutorials-in-sql-server"></a>SQL Server での Python および R のチュートリアル: あやめのデモ データ 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この演習でデータを格納する SQL Server データベースを作成、[あやめデータ セット](https://en.wikipedia.org/wiki/Iris_flower_data_set)と同じデータに基づくモデルです。 あやめデータは、SQL Server がインストールされている、R と Python のディストリビューションに含まれているし、SQL Server の machine learning のチュートリアルに使用されます。 

この手順を完了しておく[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)または T-SQL クエリを実行できる他のツール。

チュートリアルとクイック スタートのこのデータ セットを使用して、次に示します。

+  [クイック スタート:作成、トレーニング、および SQL Server でのストアド プロシージャで Python モデルを使用](quickstart-python-train-score-in-tsql.md)

## <a name="create-the-database"></a>データベースの作成

1. SQL Server Management Studio を起動し、新しく開きます**クエリ**ウィンドウ。  

2. このプロジェクトで新しいデータベースを作成し、コンテキストの変更、**クエリ**に新しいデータベースを使用するウィンドウ。

    ```sql
    CREATE DATABASE irissql
    GO
    USE irissql
    GO
    ```

    > [!TIP] 
    > よくある間違いがログインを表示していることに注意することがなく作業を開始するには、SQL Server を初めて使用するか、または自分が所有するサーバーで作業している場合、**マスター**データベース。 適切なデータベースを使用していることを確認して、常に指定を使用して、コンテキスト、`USE <database name>`ステートメント (たとえば、 `use irissql`)。

3. いくつか空のテーブルの追加: データを格納して、トレーニング済みモデルを格納します。 **Iris_models**テーブルが他の演習で生成されたシリアル化されたモデルを格納するために使用します。

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

    > [!TIP] 
    > 記憶する的確を T-SQL に慣れていない場合、`DROP...IF`ステートメント。 テーブルを作成しようとすると、既に存在する、SQL Server には、エラーが返されます。「が既にデータベースに ' iris_data' という名前のオブジェクト。」 このようなエラーを回避するために 1 つの方法では、コードの一部として、既存のテーブルまたはその他のオブジェクトを削除します。

4. トレーニング済みモデルを格納するために使用するテーブルを作成する次のコードを実行します。 SQL Server での Python (または R) モデルを保存するする必要があるシリアル化型の列に格納されている**varbinary (max)** します。 

    ```sql
    DROP TABLE IF EXISTS iris_models;
    GO
    
    CREATE TABLE iris_models (
      model_name VARCHAR(50) NOT NULL DEFAULT('default model') PRIMARY KEY,
      model VARBINARY(MAX) NOT NULL
    );
    GO
    ```

    モデルの内容に加え通常とも、モデルの名前、日付がトレーニングを受けたソース アルゴリズムとパラメーターをソース データなどの他の便利なメタデータの列を追加しなど。 ここで単純さの維持し、モデル名だけを使用して、なります。

## <a name="populate-the-table"></a>テーブルを設定します

あやめの組み込みのデータは、R または Python のいずれかから取得できます。 Python または R データ フレームにデータを読み込むを使用して、データベース内のテーブルに挿入できます。 SQL Server テーブルに外部のセッションからトレーニング データの移動は、マルチ ステップのプロセスです。

+ 必要なデータを取得するストアド プロシージャをデザインします。
+ 実際にデータを取得するストアド プロシージャを実行します。
+ 取得したデータの保存場所を指定する INSERT ステートメントを構築します。

1. Python の統合システムで Python コードを使用して、データを読み込む次のストアド プロシージャを作成します。

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

    このコードを実行するときにメッセージが表示、「コマンドの完了しました」 つまり、すべては、指定どおりに、ストアド プロシージャが作成されたことです。

2. また、R 統合を持つシステムでは、代わりに R を使用するプロシージャを作成します。

    ```sql
    CREATE PROCEDURE get_iris_dataset
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'R', 
    @script = N'
    library(RevoScaleR)
    data(iris)
    iris$SpeciesID <- c(unclass(iris$Species))
    iris_data <- iris
    ', 
    @input_data_1 = N'', 
    @output_data_1_name = N'iris_data'
    WITH RESULT SETS (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100) not null, "SpeciesId" int not null));
    END;
    GO
    ```

3. 実際には、テーブルを設定するには、ストアド プロシージャを実行し、データの書き込み先となるテーブルを指定します。 実行すると、ストアド プロシージャは、組み込みのあやめデータ セットの読み込みとにデータを挿入し、Python または R コードを実行、 **iris_data**テーブル。

    ```sql
    INSERT INTO iris_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species", "SpeciesId")
    EXEC dbo.get_iris_dataset;
    ```

    T-SQL を初めて、INSERT ステートメントでのみ新しいデータが追加されることを認識します。既存のデータを確認し、削除またはテーブルを再構築をことはありません。 テーブルで同じデータの複数のコピーの取得を避けるため、ステートメントを実行できますこのまず:`TRUNCATE TABLE iris_data`します。 T-SQL [TRUNCATE TABLE](https://docs.microsoft.com/sql/t-sql/statements/truncate-table-transact-sql)ステートメントは、既存のデータが削除されますが、状態テーブルの構造は保持します。

    > [!TIP]
    > ストアド プロシージャを変更した後で必要ありませんを削除して再作成します。 使用して、 [ALTER PROCEDURE](https://docs.microsoft.com/sql/t-sql/statements/alter-procedure-transact-sql)ステートメント。 


## <a name="query-the-data"></a>データのクエリ

検証手順として、データがアップロードされたことを確認するためのクエリを実行します。

1. データベースのオブジェクト エクスプ ローラーで右クリックし、 **irissql**データベース、および新しいクエリを開始します。

2. シンプルなクエリを実行します。

    ```sql
    SELECT TOP(10) * FROM iris_data;
    SELECT COUNT(*) FROM iris_data;
    ```

## <a name="next-steps"></a>次のステップ

次のクイック スタートでは、機械学習モデルを作成し、し、テーブルに保存から予測される結果を生成するモデルを使用します。

+ [クイック スタート:作成、トレーニング、および SQL Server でのストアド プロシージャで Python モデルを使用](quickstart-python-train-score-in-tsql.md)
