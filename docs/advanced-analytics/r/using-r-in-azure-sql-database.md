---
title: "Azure SQL データベースでの R の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: e6376a5b03a272633e876b993c3a67467d7b4637
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="using-r-in-azure-sql-database"></a>Azure SQL データベースでの R の使用

年 2017年 10 月で SQL Server 開発チームには、R コードでのデータベースの SQL Server 2016 での R Services のようなストアド プロシージャを使用して実行をサポートする予定が発表されました。 

最新公開リリース スケジュールと今後のイベントの状態にして、次を参照してください。、 [SQL Server ブログ](https://blogs.technet.microsoft.com/dataplatforminsider/)または[Microsoft R Server のブログ](https://blogs.msdn.microsoft.com/rserver/)です。

> [!IMPORTANT]
> 現時点では、R サポートのプレビューなのみ、西中央アメリカの Azure SQL データベースで使用できる機能が R の機能と比べると限らおよび Python コードの SQL Server 2016 または 2017 年 1 で実行します。

## <a name="whats-included"></a>含まれるもの

データベース内 R 機能は、次のデータベース サービス階層とパフォーマンス レベルで使用できます。
 
- Premium サービス層 – P1、P2、P4、P6、P11、P15
- Premium RS サービス層 – PRS1、PRS2、PRS4、PRS6
- Premium エラスティック プール – 125 Edtu 以上
- Premium RS 弾力性プール – 125 Edtu 以上

プレビュー バージョンには、これらのパッケージが含まれています。

+   Microsoft R Open の R バージョン 3.3.3
+   ベース R パッケージと機能が事前インストールされています。
+   Microsoft R Server 9.2、RevoScaleR パッケージを含む

現在のプレビュー リリースでは、次のタスクを実行できます。

+ メモリに適合するすべてのデータを使用して、モデルのトレーニング
+   メモリに適合するすべてのデータを使用して、モデルのスコア付け
+   R スクリプトの実行の単純な並列処理 (を使用して、 @parallel sp_execute_external_script のパラメーター)
+   R スクリプトの実行の実行のストリーミング (を使用して@r_RowsPerReadsp_execute_external_script のパラメーター)
+   一度に 1 つの R スクリプトを実行します。


次のタスクは、Azure SQL データベースでの R のプレビュー リリースではサポートされません。

+ 特定のデータベースでの R スクリプトの実行を有効にすることはできません。
+ モニターの CPU に Dmv が提供され、R スクリプトのメモリ使用量は利用できません。
+ サード パーティのパッケージをインストールできません。 外部ライブラリの作成ステートメントはサポートされていません。

## <a name="example"></a>例

Azure SQL db では、すべて R からコマンドを実行、T-SQL ストアド プロシージャを使用して[sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)です。 

次の例では、基本 R. に含まれている iris データ セットを使用して、プレビュー機能を試す

### <a name="step-1-create-the-data-tables"></a>手順 1. データ テーブルを作成します。

まず、2 つのテーブルを作成して: R から抽出されたソース データを格納して、トレーニング済みモデルを格納するためです。

```sql
DROP TABLE IF EXISTS iris_data, iris_models;
GO
CREATE TABLE iris_data (
        id INT NOT NULL IDENTITY PRIMARY KEY
        , "Sepal.Length" FLOAT NOT NULL, "Sepal.Width" FLOAT NOT NULL
        , "Petal.Length" FLOAT NOT NULL, "Petal.Width" FLOAT NOT NULL
        , "Species" VARCHAR(100) NULL
);
CREATE TABLE iris_models (
    model_name VARCHAR(30) NOT NULL PRIMARY KEY,
    model VARBINARY(max) NOT NULL,
    native_model VARBINARY(MAX) NOT NULL
);
GO
```

### <a name="step-2-populate-table-with-data-from-the-iris-dataset"></a>手順 2. Iris データセットからデータを含むテーブルへの追加します。

テーブルが作成した後は、トレーニング データをテーブルに挿入する次のコードを実行します。 ストアド プロシージャの sp_execute_external_script では、R の呼び出しを INSERT INTO ステートメントで指定されたスキーマを使用して、データ フレームとして虹彩データセットを返します。

```sql
INSERT INTO iris_data
("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
EXEC sp_execute_external_script @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

### <a name="step-3-create-the-stored-procedure-that-generates-the-model"></a>手順 3. モデルを生成するストアド プロシージャを作成します。

次のストアド プロシージャは、実際に作成し、2 つのバイナリ形式のいずれかで保存できるモデルのトレーニングのための作業を行います。

```sql
CREATE PROCEDURE generate_iris_model
    @trained_model VARBINARY(MAX) OUTPUT, 
    @native_trained_model VARBINARY(MAX) OUTPUT
AS
BEGIN
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    iris_model <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris_rx_data);
    trained_model <- as.raw(serialize(iris_model, connection=NULL));
    native_trained_model <- rxSerializeModel(iris_model, realtimeScoringOnly = TRUE)
    '
  , @input_data_1 = N'SELECT "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@trained_model VARBINARY(MAX) OUTPUT, @native_trained_model VARBINARY(MAX) OUTPUT
    , @trained_model = @trained_model OUTPUT
    , @native_trained_model = @native_trained_model OUTPUT;
End
```

+ **出力**入力パラメーターにキーワードには、値を渡されも出力のために使用することことを示します。
+ 始まる行`iris_model`花属性に基づいて種を予測するデシジョン ツリー モデルを定義します。
+ 呼び出し`serialize`保存バイナリ形式でモデルを SQL Server に保存するために適しています。 
+ または、RevoScaleR アルゴリズムに基づくモデルを使用してできます、 [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)関数で、新しいネイティブ バイナリ形式でモデルを保存します。 この形式で保存されたモデルは、SQL Server の予測関数とスコアリングのため読み込むことができます。

### <a name="step-4-train-and-save-the-model"></a>手順 4. トレーニングし、モデルを保存

ストアド プロシージャが作成されたためを呼び出して、入力データを処理し、モデルを作成します。 次のコードは、テーブルに、モデルを保存するも**iris_models**花の種の予測に後で使用できるようにします。

```sql
DECLARE @model VARBINARY(MAX), @native_modelVARBINARY(MAX);
EXEC generate_iris_model @model OUTPUT, @native_model OUTPUT;
DELETE FROM iris_models WHERE model_name = 'iris.dtree';
INSERT INTO iris_models (model_name, model, native_model) VALUES('iris.dtree', @model, @native_model);
SELECT model_name, datalength(model)/1024. AS model_size_kb, datalength(native_model)/1024. AS native_model_size_kb FROM iris_models;
GO
```

### <a name="step-5-create-a-stored-procedure-for-scoring"></a>手順 5. スコアリングのためのストアド プロシージャを作成します。

次に、スコアリングのためのストアド プロシージャを作成します。 このストアド プロシージャは、テーブルから指定したモデルを読み込み、入力データに基づくスコアを作成します。

```sql
CREATE PROCEDURE predict_iris_species (@model varchar(100))
AS
BEGIN
  DECLARE @rx_model VARBINARY(MAX) = (SELECT model FROM iris_models WHERE model_name = @model);
  EXEC sp_execute_external_script @language = N'R'
  , @script = N'
    irismodel<-unserialize(rx_model);
    OutputDataSet <-rxPredict(irismodel, iris_rx_data, extraVarsToWrite = c("Species", "id"));
      '
  , @input_data_1 = N'SELECT "id", "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" FROM iris_data'
  , @input_data_1_name = N'iris_rx_data'
  , @params = N'@rx_model varbinary(max)'
  , @rx_model = @rx_model
  WITH RESULT SETS ( ("setosa_Pred" FLOAT, "versicolor_Pred" FLOAT, "virginica_Pred" FLOAT, "Species.Actual" VARCHAR(100), "id" INT));
END;
GO
```

これは、ストアド プロシージャの使用、 [rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)関数、でした使うことも、ネイティブの予測関数: T-SQL で示すように[ここ](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-general-availability-of-native-scoring-using-predict-function-in-azure-sql-database/)です。 予測関数の使用は、使用することが必要です、 [ **rx**モデル](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)を使用してモデルを保存および[rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)です。

### <a name="step-6-use-the-stored-procedure-to-generate-predictions"></a>手順 6. ストアド プロシージャを使用して予測を生成するには

モデルからスコアを生成するには、ストアド プロシージャを実行します。 テーブルに値を挿入するか、呼び出し元アプリケーションに、予測を返します。

```sql
EXEC predict_iris_species 'iris.dtree';
GO
```

## <a name="related-resources"></a>関連リソース

Azure Marketplace には、SQL Server 2017 を含む複数の仮想マシンも提供されます。

+ [Azure での機械学習の仮想マシンのプロビジョニングします。](provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

また、これらの Vm では、さまざまな人気の機械学習のツールが付属してあらかじめ構成されたご覧ください。

+ [データ サイエンス仮想マシン](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/overview)
+ [深層学習仮想マシン](https://docs.microsoft.com/azure/machine-learning/data-science-virtual-machine/deep-learning-dsvm-overview)

