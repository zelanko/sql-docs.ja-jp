---
title: トレーニング セットとスコアリング用の SQL で使用する Python モデル |Microsoft ドキュメント
titleSuffix: SQL Server
ms.custom: ''
ms.date: 02/28/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 976ccb21ed125bb65ba52eb05fd8b08664061a31
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="use-python-model-in-sql-for-training-and-scoring"></a>SQL で Python モデルをトレーニングおよびスコア付けを使用します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[前のレッスン](wrap-python-in-tsql-stored-procedure.md)、SQL と共に Python を使用するための一般的なパターンについて学習しました。 コードを 1 つの明確に定義された data.frame を出力し、できます必要に応じて、Python がスカラーまたはバイナリの複数の変数を出力することを学習しました。 Python に適切な種類のデータを渡すし、結果を処理する SQL ストアド プロシージャを設計することを学習しました。

このセクションでは、この同じパターンを使用して、SQL Server に追加したデータに対してモデルをトレーニングし、SQL Server テーブルにモデルを保存します。

+ Python の machine learning 関数を呼び出すストアド プロシージャをデザインするとします。
+ ストアド プロシージャでは、モデルのトレーニングで使用する SQL Server からのデータが必要です。
+ ストアド プロシージャは、バイナリの変数として、トレーニング済みモデルを出力します。 
+ トレーニング済みモデルを保存するには、変数のモデルをテーブルに挿入します。 

## <a name="create-the-stored-procedure-and-train-a-python-model"></a>ストアド プロシージャを作成し、Python モデルのトレーニング

1. モデルを構築するストアド プロシージャを作成する SQL Server Management Studio では、次のコードを実行します。

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

2. このコマンドがエラーなく実行している場合、新しいストアド プロシージャが作成され、データベースに追加します。 Management Studio でストアド プロシージャを見つけることができます**オブジェクト エクスプ ローラー****プログラミング**です。

3. これで、ストアド プロシージャを実行します。

    ```sql
    EXEC generate_iris_model
    ```

    ストアド プロシージャの入力が必要と指定されていないため、エラーを取得してください。

    "プロシージャまたは関数 'generate_iris_model' パラメーターが必要ですが '@trained_model' が指定されていません"。

4. 必須の入力を使用してモデルを生成し、テーブルに保存するには、いくつか追加のステートメントが必要です。

    ```sql
    DECLARE @model varbinary(max);
    EXEC generate_iris_model @model OUTPUT;
    INSERT INTO iris_models (model_name, model) values('Naive Bayes', @model);
    ```

5. ここで、モデルの生成コードをもう一度実行してください。 

    エラーが発生する必要があります:"PRIMARY KEY 制約の違反は重複するキーをオブジェクト 'dbo.iris_models' 内に挿入できません。 重複キーの値は (Naive Bayes)"です。

    モデル名が手動で入力して"Naive Bayes"で、INSERT ステートメントの一部として提供されるためです。 作成を計画する多数のモデルでは、実行のたびに異なるパラメーターや異なるアルゴリズムを使用すると仮定した場合、する必要がありますメタデータ スキームの設定のモデルに自動的に名前を付けるしより簡単に識別できるようにします。

6. このエラーを回避するには、SQL ラッパーにわずかな変更をすることができます。 この例では、現在の日付と時刻を付加して一意のモデル名が生成されます。

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
    | Naive Bayes Jan 01 2018  9:39AM | 0x800363736B6C656172... |
    | Naive Bayes Feb 01 2018 10時 51分 AM | 0x800363736B6C656172... |

## <a name="generate-scores-from-the-model"></a>モデルからスコアを生成します。

最後に、みましょう、変数にテーブルからこのモデルを読み込むし、スコアを生成する Python に渡します。

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

    ストアド プロシージャは、テーブルから、Naïve Bayes モデルを取得し、モデルに関連付けられている関数を使用してスコアを生成します。 この例では、ストアド プロシージャは、モデルの名前を使用してテーブルからモデルを取得します。 ただし、によっては、モデルを保存するメタデータの種類、でしたやはり、最新のモデルまたはモデルで最も高い精度。

2. モデル名"Naive Bayes"をスコア付けのコードを実行するストアド プロシージャに渡す次の行を実行します。 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    ストアド プロシージャを実行すると、Python data.frame を返します。 T-SQL の行は、返される結果のスキーマを指定します。 `WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`

    結果を新しいテーブルに挿入またはそれらのアプリケーションに戻ることができます。

    この例が加えられました単純な Python iris データセットからデータをスコア付けを使用しています。 (行を参照してください`iris_data[[1,2,3,4]])`)。ただし、通常は、新しいデータを取得する SQL クエリを実行し、としての Python に渡す`InputDataSet`です。 

### <a name="remarks"></a>解説

Python での作業を使用している場合は、データの読み込み、いくつかの概要と、グラフを作成し、モデルをトレーニング セットと同じ 250 の行のコードですべてのスコアを生成するのには慣れてする必要があります。

しかし、目標が SQL Server のプロセス (モデルの作成、スコア付けなど) を操作運用する場合は、パラメーターを使用して変更できる反復可能な手順に、プロセスを分離することができる方法を検討する必要があります。 可能な限り、するストアド プロシージャの入力と出力にマップされる入出力を明確に定義するストアド プロシージャで実行する Python コード。

さらに、パフォーマンスは、モデルのトレーニングまたはスコアの生成のプロセスからのデータの探索プロセスを分離することによって一般的に向上できます。 

得点の付け方とトレーニング プロセス多くの場合、最適化できる並列処理など、SQL Server の機能を活用することで、またはでアルゴリズムを使用して[revoscalepy](../python/what-is-revoscalepy.md)または[MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)そのサポートのストリーミング並列実行ではなく標準の Python ライブラリを使用します。 

## <a name="next-lesson"></a>次のレッスン

最後のレッスンでは、計算コンテキストとして SQL Server を使用して、リモート クライアントから Python コードを実行します。 Python クライアントがないか、ストアド プロシージャの外に Python を実行するつもりがない場合、この手順は省略可能です。

+ [Python クライアントから revoscalepy モデルを作成します。](use-python-revoscalepy-to-create-model.md)
