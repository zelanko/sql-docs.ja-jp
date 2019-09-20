---
title: R で予測モデルを作成およびスコア付けする
titleSuffix: SQL Server Machine Learning Services
description: SQL Server Machine Learning Services を使用して R で簡単な予測モデルを作成した後、新しいデータを使用して結果を予測します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: quickstart
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5aad027f84bc1116aa57c6b0bc0d7b0893519c36
ms.sourcegitcommit: 1661c3e1bb38ed12f8485c3860fc2d2b97dd2c9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150335"
---
# <a name="quickstart-create-and-score-a-predictive-model-in-r-with-sql-server-machine-learning-services"></a>クイック スタート: SQL Server Machine Learning Services を使用して R で予測モデルを作成およびスコア付けする
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このクイックスタートでは、R を使用して予測モデルを作成してトレーニングし、SQL Server インスタンスのテーブルにモデルを保存した後、モデルを使用して[SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md)を使用して新しいデータの値を予測します。

このクイックスタートで使用するモデルは、車両が手動で転送された確率を予測する単純な汎用線形モデル (GLM) です。 R に含まれる**mtcars**データセットを使用します。

> [!TIP]
> 線形モデルのリフレッシャーが必要な場合は、rxLinMod を使用してモデルを調整するプロセスについて説明した次のチュートリアルを試してください。[線形モデルを調整する](/machine-learning-server/r/how-to-revoscaler-linear-model)

## <a name="prerequisites"></a>前提条件

- このクイックスタートでは、R 言語がインストールされている[SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)で SQL Server のインスタンスにアクセスする必要があります。

  SQL Server インスタンスは、Azure 仮想マシンまたはオンプレミスに配置できます。 外部スクリプト機能が既定で無効になっているため、[外部スクリプトを有効](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature)にし、開始する前に**SQL Server Launchpad サービス**が実行されていることを確認する必要がある場合があることに注意してください。

- また、R スクリプトを含む SQL クエリを実行するためのツールも必要です。 これらのスクリプトは、SQL Server インスタンスに接続し、T-sql クエリまたはストアドプロシージャを実行できる限り、任意のデータベース管理ツールまたはクエリツールを使用して実行できます。 このクイックスタートでは、 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)を使用します。

## <a name="create-the-model"></a>モデルの作成

モデルを作成するには、トレーニング用のソースデータを作成し、モデルを作成してデータを使用してトレーニングします。次に、モデルを SQL データベースに格納します。このモデルを使用して、新しいデータで予測を生成できます。

### <a name="create-the-source-data"></a>ソース データを作成する

1. **SQL Server Management Studio**を開き、SQL Server インスタンスに接続します。

1. トレーニングデータを保存するテーブルを作成します。

   ```sql
   CREATE TABLE dbo.MTCars(
       mpg decimal(10, 1) NOT NULL,
       cyl int NOT NULL,
       disp decimal(10, 1) NOT NULL,
       hp int NOT NULL,
       drat decimal(10, 2) NOT NULL,
       wt decimal(10, 3) NOT NULL,
       qsec decimal(10, 2) NOT NULL,
       vs int NOT NULL,
       am int NOT NULL,
       gear int NOT NULL,
       carb int NOT NULL
   );
   ```

1. 組み込みデータセット`mtcars`からデータを挿入します。

   ```SQL
   INSERT INTO dbo.MTCars
   EXEC sp_execute_external_script @language = N'R'
       , @script = N'MTCars <- mtcars;'
       , @input_data_1 = N''
       , @output_data_1_name = N'MTCars';
   ```

   > [!TIP]
   > 小規模と大規模の多くのデータセットが R ランタイムに付属しています。 R と共にインストールされたデータセットの`library(help="datasets")`一覧を取得するには、r コマンドプロンプトから「」と入力します。

### <a name="create-and-train-the-model"></a>モデルの作成とトレーニング

自動車速度データには、数値: 馬力 (`hp`) と weight (`wt`) の2つの列が含まれています。 このデータから、車両が手動で転送された確率を予測する汎用線形モデル (GLM) を作成します。

モデルを作成するには、R コード内に数式を定義し、入力パラメーターとしてそのデータを渡します。

```sql
DROP PROCEDURE IF EXISTS generate_GLM;
GO
CREATE PROCEDURE generate_GLM
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'carsModel <- glm(formula = am ~ hp + wt, data = MTCarsData, family = binomial);
        trained_model <- data.frame(payload = as.raw(serialize(carsModel, connection=NULL)));'
    , @input_data_1 = N'SELECT hp, wt, am FROM MTCars'
    , @input_data_1_name = N'MTCarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model VARBINARY(max)));
END;
GO
```

- の最初の引数`glm`は、に`hp + wt`依存するように`am`定義する*数式*パラメーターです。
- 入力データは、SQL クエリによって設定される変数 `MTCarsData` に格納されます。 入力データに特定の名前を割り当てない場合、既定の変数名は "_InputDataSet_" になります。

### <a name="store-the-model-in-the-sql-database"></a>SQL データベースにモデルを格納する

次に、モデルを予測や再トレーニングに使用できるように、SQL データベースに格納します。 

1. モデルを格納するテーブルを作成します。

   モデルを作成する R パッケージの出力は、通常、バイナリオブジェクトです。 そのため、モデルを格納するテーブルには、 **varbinary (max)** 型の列を指定する必要があります。

   ```sql
   CREATE TABLE GLM_models (
       model_name varchar(30) not null default('default model') primary key,
       model varbinary(max) not null
   );
   ```

1. 次の Transact-sql ステートメントを実行してストアドプロシージャを呼び出し、モデルを生成して、作成したテーブルに保存します。

   ```sql
   INSERT INTO GLM_models(model)
   EXEC generate_GLM;
   ```

   > [!TIP]
   > このコードをもう一度実行すると、次のエラーが発生します。"PRIMARY KEY 制約の違反...オブジェクト stopping_distance_models に重複するキーを挿入することはできません。 このエラーを避ける 1 つのオプションは、新しいモデルごとに名前を更新することです。 たとえば、わかりやすい名前に変更し、モデルの種類や作成日などを含めることができます。

     ```sql
     UPDATE GLM_models
     SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
     WHERE model_name = 'default model'
     ```

## <a name="score-new-data-using-the-trained-model"></a>トレーニング済みのモデルを使用して新しいデータをスコア付けする

*スコアリング*は、トレーニング済みのモデルに取り込まれた新しいデータに基づいて予測、確率、またはその他の値を生成することを意味するためにデータサイエンスで使用される用語です。 前のセクションで作成したモデルを使用して、新しいデータに対する予測をスコア付けします。

### <a name="create-a-table-of-new-data"></a>新しいデータのテーブルを作成する

最初に、新しいデータを含むテーブルを作成します。

```sql
CREATE TABLE dbo.NewMTCars(
    hp INT NOT NULL
    , wt DECIMAL(10,3) NOT NULL
    , am INT NULL
)
GO

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (110, 2.634)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (72, 3.435)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (220, 5.220)

INSERT INTO dbo.NewMTCars(hp, wt)
VALUES (120, 2.800)
GO
```

### <a name="predict-manual-transmission"></a>手動による転送を予測する

モデルに基づいて予測を取得するには、次を実行する SQL スクリプトを記述します。

1. 必要なモデルを取得します。
1. 新しい入力データを取得します。
1. そのモデルと互換性がある R 予測関数を呼び出します。

時間の経過と共に、テーブルには複数の R モデルが含まれ、さまざまなパラメーターまたはアルゴリズムを使用して構築されるか、データの異なるサブセットに対してトレーニングされることがあります。 この例では、という名前`default model`のモデルを使用します。

```sql
DECLARE @glmmodel varbinary(max) = 
    (SELECT model FROM dbo.GLM_models WHERE model_name = 'default model');

EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(glmmodel));
            new <- data.frame(NewMTCars);
            predicted.am <- predict(current_model, new, type = "response");
            str(predicted.am);
            OutputDataSet <- cbind(new, predicted.am);
            '
    , @input_data_1 = N'SELECT hp, wt FROM dbo.NewMTCars'
    , @input_data_1_name = N'NewMTCars'
    , @params = N'@glmmodel varbinary(max)'
    , @glmmodel = @glmmodel
WITH RESULT SETS ((new_hp INT, new_wt DECIMAL(10,3), predicted_am DECIMAL(10,3)));
```

上記のスクリプトでは、次の手順を実行します。

- SELECT ステートメントを使用して、テーブルから 1 つのモデルを取得し、それを入力パラメーターとして渡します。

- テーブルからモデルを取得したら、モデルに対して `unserialize` 関数を呼び出します。

- 適切な引数を使用して `predict` 関数をモデルに適用し、新しい入力データを提供します。

> [!NOTE]
> この例`str`では、関数はテストフェーズ中に追加され、R から返されるデータのスキーマを確認します。このステートメントは後で削除できます。
>
> R スクリプトで使用される列名は、ストアドプロシージャの出力に必ずしも渡されるとは限りません。 ここでは、WITH RESULTS 句を使用して、新しい列名を定義します。

**結果**

![Properbility の手動送信を予測するための結果セット](./media/r-predict-am-resultset.png)

また、 [PREDICT (transact-sql)](../../t-sql/queries/predict-transact-sql.md)ステートメントを使用して、格納されているモデルに基づいて予測値またはスコアを生成することもできます。

## <a name="next-steps"></a>次の手順

SQL Server での R データ型の処理の詳細については、次のクイックスタートを参照してください。

> [!div class="nextstepaction"]
> [SQL Server Machine Learning Services で R を使用してデータ型とオブジェクトを処理する](quickstart-r-data-types-and-objects.md)

SQL Server Machine Learning Services の詳細については、次の記事を参照してください。

- [SQL Server Machine Learning Services を使用した高度な R 関数の作成](quickstart-r-functions.md)
- [SQL Server Machine Learning Services (Python と R) とは何ですか?](../what-is-sql-server-machine-learning.md)
