---
title: SQL Server の Python のモデルを使用してトレーニングと予測の |Microsoft Docs
description: 作成し、Python とクラシックあやめデータ セットを使用してモデルをトレーニングします。 SQL Server に、モデルを保存し、予測結果の生成に使用すること。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/18/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 839bcecdeaf7b5e2a7ea1297fe941353bffed20e
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461838"
---
# <a name="use-a-python-model-in-sql-server-for-training-and-scoring"></a>SQL Server の Python のモデルを使用するトレーニングとスコア付け
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この Python 演習では、作成、トレーニング、およびモデルを使用して、SQL Server での一般的なパターンを学習します。 この演習では、2 つのストアド プロシージャを作成します。 1 つ目は、単純ベイズ花の特性に基づき、Iris species を予測するモデルを生成します。 2 番目の手順では、スコア付けします。 予測のセットを出力する最初の手順で生成されたモデルを呼び出します。 この演習のステップでは、SQL Server データベース エンジンのインスタンスで Python コードを実行する基礎となる基本的な手法を学習します。

この演習で使用するサンプル データは、 [Iris データセット](demo-data-iris-in-sql.md)で、 **irissql**データベース。

## <a name="create-a-model-using-a-sproc"></a>ストアド プロシージャを使用して、モデルを作成します。

1. Management Studio で、新しいクエリ ウィンドウに接続を開いて、 **irissql**データベース。 

    ```sql
    USE irissql
    GO
    ```

2. 構築し、モデルをトレーニングするストアド プロシージャを作成する新しいクエリ ウィンドウで、次のコードを実行します。 SQL Server で再利用するために格納されているモデルでは、バイト ストリームとしてシリアル化され、データベース テーブル内の varbinary (max) 列に格納されています。 モデルが作成されると、トレーニング、シリアル化、およびデータベースに保存できます呼び出すことが他の手順で、またはワークロードをスコア付けの T-SQL の予測関数から。

   このコードでは、pickle を使用して、モデルと単純ベイズ アルゴリズムを提供する scikit シリアル化します。 データの列 0 ~ 4 を使用して、モデルがトレーニングされます、 **iris_data**テーブル。 プロシージャの 2 番目の部分に表示パラメーターのデータ入力を明示して、モデルが出力されます。 

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

3. ストアド プロシージャが存在することを確認します。 新しいストアド プロシージャと呼ばれる場合は、前の手順から T-SQL スクリプトの実行エラーが発生せず、 **generate_iris_model**が作成され、追加、 **irissql**データベース。 Management studio のストアド プロシージャを見つけることができます**オブジェクト エクスプ ローラー****プログラミング**します。

## <a name="execute-the-sproc-to-create-and-train-models"></a>作成およびモデルをトレーニングするストアド プロシージャを実行します。

1. ストアド プロシージャを作成した後は、次のコードを実行するために以下を実行します。 ストアド プロシージャを実行するための特定のステートメントは`EXEC`5 番目の行にします。

   このスクリプトは、("Naive Bayes") と同じ手順を再実行によって作成された新しいものを確保するために同じ名前の既存のモデルを削除します。 モデルの削除せずに、オブジェクトが既に存在することを示すエラーが発生しました。 

    ```sql
    DECLARE @model varbinary(max);
    DECLARE @new_model_name varchar(50)
    SET @new_model_name = 'Naive Bayes '
    SELECT @new_model_name 
    EXEC generate_iris_model @model OUTPUT;
    DELETE iris_models WHERE model_name = @new_model_name;
    INSERT INTO iris_models (model_name, model) values(@new_model_name, @model);
    GO
    ```

2. 結果を出力領域に表示します。 スクリプトには、モデルが存在することを示す、SELECT ステートメントが含まれています。 モデルの一覧を取得する別の方法は`SELECT * FROM iris_models`で**irissql**します。

    **結果**

    |   | (列名なし |
    |---|-----------------|
    | 1 | Naive Bayes     | 


## <a name="create-and-execute-a-sproc-for-generating-predictions"></a>作成して予測を生成するためのストアド プロシージャの実行

作成し、トレーニング、モデルを保存したが、これで、次の手順移動します。 予測を生成するストアド プロシージャを作成します。 これを行うには、Python を開始し、前回の演習で作成し、スコア付けへのデータ入力にシリアル化されたモデルを読み込みます Python スクリプトに渡すを呼び出し元の sp_execute_external_script でします。

1. スコア付けを実行するストアド プロシージャを作成する次のコードを実行します。 実行時に、このプロシージャはバイナリ モデルを読み込み、列を使用して`[1,2,3,4]`として入力し、列を指定`[0,5,6]`として出力します。

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
    OutputDataSet = iris_data[[0,5,6]] 
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

2. プロシージャを使用するモデルを認識できるように、"Naive Bayes"モデルの名前を与える、ストアド プロシージャを実行します。 

    ```sql
    EXEC predict_species 'Naive Bayes';
    GO
    ```

    ストアド プロシージャを実行すると、Python data.frame を返します。 T-SQL の行が返される結果のスキーマを指定します:`WITH RESULT SETS ( ("id" int, "SpeciesId" int, "SpeciesId.Predicted" int));`します。 結果を新しいテーブルに挿入またはアプリケーションに戻すことができます。

    ![ストアド プロシージャの実行からの結果セット](media/train-score-using-python-NB-model-results.png)

    結果は、150 species フローラル特性を入力として使用する予測です。 観測のほとんどは、予測の種は実際の種と一致します。

    この例を作成できます簡単な Python iris データセットをトレーニングとスコア付けの両方を使用しています。 一般的な方法は必要に応じて、新しいデータを取得する SQL クエリを実行してとして Python に渡す`InputDataSet`します。 

## <a name="conclusion"></a>まとめ

この演習でさまざまなタスクを各ストアド プロシージャが、システム ストアド プロシージャを使用するためのストアド プロシージャを作成する方法を学習しました[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) Python プロセスを開始します。 Python プロセスへの入力は、パラメーターとして sp_execute_external スクリプトに渡されます。 Python スクリプト自体と SQL Server データベースのデータの変数は、入力として渡されます。

Python での作業に使用している場合は、データの読み込み、いくつかの概要と、グラフを作成し、モデルのトレーニングおよび同じ 250 行のコードですべてのスコアを生成することに慣れてする必要があります。 この記事では、別々 のプロシージャに処理を編成することでよく使用されるアプローチとは異なります。 この方法はいくつかのレベルで便利です。

利点の 1 つは、パラメーターを使用して変更できる繰り返し可能な手順にプロセスを分離することができます。 入力と出力ストアド プロシージャの入力にマップされると実行時に渡すことができる出力を明確に定義するストアド プロシージャで実行する Python コードを必要する可能な限り、します。 この演習では、(この例では"Naive Bayes"という名前) のモデルを作成する Python コードはスコア付けプロセスで、モデルで呼び出す 2 番目のストアド プロシージャへの入力として渡されます。

2 番目の利点は、そのトレーニングとスコアリング プロセスを最適化できますまたはでアルゴリズムを使用して、SQL Server の並列処理、リソースの管理などの機能を活用することで[revoscalepy](../python/what-is-revoscalepy.md)または[MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)ストリーミングをサポートして、並列実行します。 トレーニングとスコア付け、分離して特定のワークロードの最適化を対象にすることができます。

## <a name="next-steps"></a>次の手順

前のチュートリアルでは、ローカルでの実行に重点を置いています。 ただし、ことができますもコードを実行する Python クライアント ワークステーションでは、リモート計算コンテキストとして SQL Server を使用します。 SQL Server に接続するクライアント ワークステーションのセットアップに関する詳細については、次を参照してください。 [Python クライアント ツールのセットアップ](../python/setup-python-client-tools-sql.md)します。

+ [Python クライアントから revoscalepy モデルを作成します。](use-python-revoscalepy-to-create-model.md)
