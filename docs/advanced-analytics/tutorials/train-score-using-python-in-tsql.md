---
title: トレーニングとスコア付け用の SQL での Python モデルを使用する |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 02ffd5a25c076ef5a65a6e3a998aae485e37d982
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085024"
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>Sql Python モデルを使用して、トレーニングとスコア付け
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[前のレッスン](wrap-python-in-tsql-stored-procedure.md)SQL と Python を使用するための一般的なパターンを学習しました。 Python コードが 1 つの明確に定義された data.frame を出力する必要があり、こともできますが、スカラーまたはバイナリの複数の変数を出力するについて説明しました。 Python に適切な種類のデータを渡すし、結果を処理する SQL ストアド プロシージャを設計する必要がありますを学習できました。

このセクションでは、この同じパターンを使用して、SQL Server に追加したデータでモデルをトレーニングして、モデルを SQL Server テーブルに保存します。

+ Python machine learning 関数を呼び出すストアド プロシージャを設計します。
+ ストアド プロシージャには、モデルのトレーニングで使用する SQL Server からのデータが必要があります。
+ ストアド プロシージャは、二項変数として、トレーニング済みモデルを出力します。 
+ トレーニング済みモデルを保存するには、変数のモデルをテーブルに挿入します。 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>ストアド プロシージャを作成し、Python モデルのトレーニング

1. モデルを作成するストアド プロシージャを作成する SQL Server Management Studio では、次のコードを実行します。

    ```sql
    CREATE PROCEDURE generate_iris_model (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script @language = N'Python',
    @script = N'
    import pickle
    from sklearn.naive_bayes import GaussianNB
    GNB = GaussianNB()
    trained_model = pickle.dumps(GNB.fit(iris_data[[0,1,2,3]], iris_data[[4]]))
    '
    , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@trained_model varbinary(max) OUTPUT'
    , @trained_model = @trained_model OUTPUT;
    END;
    GO
    ```

2. このコマンドは、エラーなく実行する場合、新しいストアド プロシージャが作成され、データベースに追加します。 Management studio のストアド プロシージャを見つけることができます**オブジェクト エクスプ ローラー****プログラミング**します。

3. ストアド プロシージャを実行するようになりました。

    ```sql
    EXEC generate_iris_model
    ```

    ストアド プロシージャの入力が必要とするかを指定していないため、エラーが表示されます。

    "プロシージャまたは関数 'generate_iris_model' パラメーターが必要ですが '\@trained_model'、指定されませんでした"。

4. 必要な入力でモデルを生成し、テーブルに保存するには、いくつか追加のステートメントが必要です。

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. ここで、モデルの生成コードをもう一度実行してください。 

    エラーが発生する必要があります:"PRIMARY KEY 制約の違反は重複するキーをオブジェクト 'dbo.iris_models' 内に挿入できません。 重複するキー値が (Naive Bayes)"。

    モデル名は、INSERT ステートメントの一部として"Naive Bayes"に手動で入力によって提供されたためにです。 モデルに自動的に名前を付けるしより簡単に識別できるようには、実行のたびに異なるパラメーターや異なるアルゴリズムを使用して、モデルの多くを作成すると仮定すると、メタデータ スキームの設定を考慮する必要があります。

6. このエラーを回避するには、SQL ラッパーにわずかな変更を行うことができます。 この例では、現在の日付と時刻を追加して一意のモデル名が生成されます。

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes ' + CAST(GETDATE()as varchar)
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    ```

7. モデルを表示するには、単純な SELECT ステートメントを実行します。

    ```sql
    SELECT * FROM iris_models;
    GO
    ```

    **結果**

    |model_name | model |
    |------|------|
    | Naive Bayes | 0x800363736B6C656172... |
    | Naive Bayes Jan 01 2018 午前 9時 39分 | 0x800363736B6C656172... |
    | Naive Bayes Feb 01 2018 午前 10時 51分 | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>モデルからスコアを生成します。

最後に、みましょう、変数に、テーブルからこのモデルを読み込むし、スコアを生成する Python にそれを渡します。

1. スコア付けを実行するストアド プロシージャを作成する次のコードを実行します。 

    ```sql
    CREATE PROCEDURE predict_species (@model varchar(100))
    AS
    BEGIN
    DECLARE @nb_model varbinary(max) = (SELECT model FROM iris_models WHERE model_name = @model);
    EXEC sp_execute_external_script @language = N'Python', 
    @script = N'
    import pickle
    irismodel = pickle.loads(nb_model)
    species_pred = irismodel.predict(iris_data[[1,2,3,4]])
    iris_data["PredictedSpecies"] = species_pred
    OutputDataSet = iris_data.query( ''PredictedSpecies != SpeciesId'' )[[0, 5, 6]]
    print(OutputDataSet)
    '
    , @input_data_1 = N'select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "SpeciesId" from iris_data'
    , @input_data_1_name = N'iris_data'
    , @params = N'@nb_model varbinary(max)'
    , @nb_model = @nb_model
    WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));
    END;
    GO
    ```

    ストアド プロシージャでは、テーブルから、単純ベイズ モデルを取得し、モデルに関連付けられている関数を使用してスコアを生成します。 この例では、ストアド プロシージャは、モデル名を使用してテーブルからモデルを取得します。 ただし、モデルを保存するメタデータの種類、によっても取得できます、最新のモデルまたはモデル、最高精度。

2. モデルの名前"Naive Bayes"スコア付けのコードを実行するストアド プロシージャに渡すには、次の行を実行します。 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    ストアド プロシージャを実行すると、Python data.frame を返します。 T-SQL の行は、返される結果のスキーマを指定します。 `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    結果を新しいテーブルに挿入またはアプリケーションに戻すことができます。

    この例を作成できます簡単な Python iris データセットからデータをスコア付けを使用しています。 (行を参照してください`iris_data[[1,2,3,4]])`。)。ただし、多くの場合は、新しいデータを取得する SQL クエリを実行し、Python に渡す`InputDataSet`します。 

### <a name="remarks"></a>コメント

Python での作業に使用している場合は、データの読み込み、いくつかの概要と、グラフを作成し、モデルのトレーニングおよび同じ 250 行のコードですべてのスコアを生成することに慣れてする必要があります。

ただし、SQL Server のプロセス (モデルの作成、スコア付けなど) を運用化には場合、方法にパラメーターを使用して変更可能な手順を繰り返し可能なプロセスを分離できることを検討する必要があります。 ストアド プロシージャの入力と出力にマップされた入出力を明確に定義するストアド プロシージャで実行する Python コードを求める可能な限り、します。

さらに、モデルのトレーニングまたはスコアの生成のプロセスからのデータの探索プロセスを分離することでパフォーマンスを一般に向上できます。 

得点の付け方とトレーニング プロセス多くの場合、最適化できるまたはでアルゴリズムを使用して、SQL Server の並列処理などの機能を活用することで[revoscalepy](../python/what-is-revoscalepy.md)または[MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)そのサポートのストリーミング並列実行ではなく標準的な Python ライブラリを使用します。 

## <a name="next-lesson"></a>次のレッスン

最後のレッスンでは、計算コンテキストとして SQL Server を使用して、リモート クライアントから Python コードを実行します。 ストアド プロシージャの外部の Python を実行しないや、Python クライアントいない場合は、この手順は省略可能なです。

+ [Python クライアントから revoscalepy モデルを作成します。](use-python-revoscalepy-to-create-model.md)
