---
title: SQL Server での Python のモデル トレーニングとストアド プロシージャを使用して予測 |Microsoft Docs
description: SQL Server ストアド プロシージャを作成、トレーニング、および Python モデルを使用してクラシックあやめデータ セットでの Python コードを埋め込みます。 SQL Server にトレーニング済みモデルを保存し、予測結果の生成に使用すること。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/23/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 17b51d695a923b6db1661e6e15605a1f05d08178
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51293158"
---
# <a name="create-train-and-use-a-python-model-with-stored-procedures-in-sql-server"></a>作成、トレーニング、および SQL Server でのストアド プロシージャで Python モデルを使用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この実習では SQL Server の統合に Python を追加すると、 [Machine Learning サービス](../install/sql-machine-learning-services-windows-install.md)データベース エンジンのインスタンスに機能します。 内の Python コードをラップする、このようなインスタンスで、[ストアド プロシージャ](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)を運用環境のワークロード用のスクリプトを扱えるようにします。 ストアド プロシージャにコードを埋め込む機能が、設計、テスト、およびデータ サイエンスと機械学習タスクを管理する方法の恩恵を被っています。 により、スクリプト モデル SQL Server に接続できる任意のアプリケーションにアクセスできます。

この Python 演習では、作成し、2 つのストアド プロシージャを実行します。 1 つ目は、クラシックあやめデータ セットを使用し、単純ベイズ花の特性に基づき、Iris species を予測するモデルを生成します。 2 番目の手順では、スコア付けします。 予測のセットを出力する最初の手順で生成されたモデルを呼び出します。 ストアド プロシージャのコードを配置すると、操作は他のストアド プロシージャおよびクライアント アプリケーションによっては包含、再利用可能なおよび呼び出し可能です。 

このチュートリアルを完了すると、学習内容。

> [!div class="checklist"]
> * ストアド プロシージャで Python コードを埋め込む方法
> * ストアド プロシージャの入力を通じたコードへの入力を渡す方法
> * モデルを運用するストアド プロシージャの使用方法

## <a name="prerequisites"></a>前提条件

この演習で使用するサンプル データは、 [ **irissql** ](demo-data-iris-in-sql.md)データベース。

必要です、T-SQL エディターなど[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)します。

## <a name="create-a-stored-procedure-that-generates-models"></a>モデルを生成するストアド プロシージャを作成します。

SQL Server 開発の一般的なパターンでは、個別のストアド プロシージャにプログラミング可能な操作を整理します。 この手順では、結果を予測するモデルを生成するストアド プロシージャを作成します。 

1. Management Studio で、新しいクエリ ウィンドウに接続を開いて、 **irissql**データベース。 

    ```sql
    USE irissql
    GO
    ```

2. 新しいストアド プロシージャを作成する次のコードにコピーします。 

   実行すると、このプロシージャを呼び出す[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) Python セッションを開始します。 
   
   Python コードで必要な入力は、このストアド プロシージャに対する入力パラメーターとして渡されます。 出力は、Python に基づくトレーニング済みのモデルになります**scikit-学習**機械学習アルゴリズムのライブラリです。 

   このコードを使用して[ **pickle** ](https://docs.python.org/2/library/pickle.html)モデルをシリアル化します。 データの列 0 ~ 4 を使用して、モデルがトレーニングされます、 **iris_data**テーブル。 
   
   プロシージャの 2 番目の部分に表示パラメーターのデータ入力を明示して、モデルが出力されます。 可能な限り、入力を明確に定義するストアド プロシージャで実行されている Python コードしてにマップするストアド プロシージャの入力と出力の実行時に渡されたを出力します。 

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

3. ストアド プロシージャが存在することを確認します。 

   新しいストアド プロシージャと呼ばれる場合は、前の手順から T-SQL スクリプトの実行エラーが発生せず、 **generate_iris_model**が作成され、追加、 **irissql**データベース。 Management studio のストアド プロシージャを見つけることができます**オブジェクト エクスプ ローラー****プログラミング**します。

## <a name="execute-the-procedure-to-create-and-train-models"></a>作成し、モデルをトレーニングする手順を実行します。

この手順では、出力としてシリアル化し、トレーニング済みモデルを作成する、埋め込みコードを実行する手順を実行します。 SQL Server で再利用するために格納されているモデルでは、バイト ストリームとしてシリアル化され、データベース テーブル内の varbinary (max) 列に格納されています。 モデルは、作成、トレーニング、シリアル化、およびデータベースに保存されますが、一度呼び出すことができるその他のプロシージャまたは、[予測 T-SQL](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)でワークロードをスコア付け関数。

1. プロシージャを実行する次のコードをコピーします。 ストアド プロシージャを実行するための特定のステートメントは`EXEC`5 番目の行にします。

   このスクリプトは、("Naive Bayes") と同じ手順を再実行によって作成された新しいものを確保するために同じ名前の既存のモデルを削除します。 モデルの削除せずに、オブジェクトが既に存在することを示すエラーが発生しました。 という名前のテーブルで、モデルが格納されている**iris_models**、作成時にプロビジョニング、 **irissql**データベース。

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


## <a name="create-and-execute-a-stored-procedure-for-generating-predictions"></a>作成して予測を生成するためのストアド プロシージャの実行

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

この演習でさまざまなタスクを各ストアド プロシージャが、システム ストアド プロシージャを使用する専用のストアド プロシージャを作成する方法を学習しました[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) Python プロセスを開始します。 Python プロセスへの入力は、パラメーターとして sp_execute_external スクリプトに渡されます。 Python スクリプト自体と SQL Server データベースのデータの変数は、入力として渡されます。

一般に、Python コードの光沢のある、またはを行ベースの出力を返す単純な Python コードで SSMS を使用する予定する必要がありますのみ。 ツールでは、SSMS は、T SQL に似たクエリ言語をサポートし、フラットな行セットを返します。 コードでは、ヒストグラム、散布図のようなビジュアルの出力を生成する場合、イメージをレンダリングするツールやエンドユーザー アプリケーション必要があります。

操作の範囲を処理する包括的なスクリプトを記述するために使用するいくつかの Python 開発者向け別々 のプロシージャにタスクを整理することがありますないように思われます。 トレーニングとスコア付けがさまざまなユース ケース。 、分離して、別のスケジュールと操作へのスコープ アクセス許可の各タスクを配置できます。

同様に、リソースや並列処理、リソースの管理などのアルゴリズムを使用するようにスクリプトを記述することで、SQL Server の機能を利用しても[revoscalepy](../python/what-is-revoscalepy.md)または[MicrosoftML](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)ですストリーミングと並列実行をサポートします。 トレーニングとスコア付け、分離して特定のワークロードの最適化を対象にすることができます。

最終的な利点は、パラメーターを使用してプロセスを変更できることです。 この演習では、(この例では"Naive Bayes"という名前)、モデルを作成した Python コードは、スコア付けプロセスでモデルを呼び出す 2 番目のストアド プロシージャへの入力として渡されました。 この演習は、1 つのモデルのみを使用しますが、方法、モデルのスコア付けのタスクのパラメーター化すればスクリプトをさらに便利な想像してみてください。

## <a name="next-steps"></a>次の手順

Python を新しい SQL developer の場合は、ローカル セッションからリモートの SQL Server インスタンスの実行をシフトすることができますと Python コードをローカルで使用するためのツールを確認します。

> [!div class="nextstepaction"]
> [Python クライアント ワークステーションをセットアップ](../python/setup-python-client-tools-sql.md)します。

