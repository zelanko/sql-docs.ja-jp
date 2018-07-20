---
title: SQL Server Machine Learning で R を使用して、予測モデルを作成するクイック スタート |Microsoft Docs
description: このクイック スタートでは、SQL Server のデータを使用して予測をプロットする R でモデルを構築する方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: quickstart
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 7ca2fcac5bef63a4abf2449b56c25a600b9255c3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086824"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>クイック スタート: SQL Server で R を使用して予測モデルを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、R を使用するモデルをトレーニングする方法について説明し、SQL Server のテーブルに、モデルを保存します。 モデルは、速度に基づいて自動車の停止距離を予測するシンプルな回帰モデルです。 使用して、`cars`データセットが R に含まれるため、サイズが小さく、簡単に理解できます。

## <a name="prerequisites"></a>前提条件

前のクイック スタート[の Hello World R と SQL を](rtsql-using-r-code-in-transact-sql-quickstart.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

## <a name="create-the-source-data"></a>ソース データを作成する

最初に、トレーニング データを保存するテーブルを作成します。

```sql
CREATE TABLE CarSpeed ([speed] int not null, [distance] int not null)
INSERT INTO CarSpeed
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'car_speed <- cars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'car_speed'
```

+ 一部の人などに使用する一時テーブルは、一部の R クライアントがバッチ間のセッションを切断することに注意してください。

+ 小規模と大規模の多くのデータセットが R ランタイムに付属しています。 R と共にインストールされるデータセットの一覧を取得するには、R コマンド プロンプトから「`library(help="datasets")`」と入力します。

## <a name="create-a-regression-model"></a>回帰モデルを作成する

自動車の速度データには、`dist` と `speed` の 2 つの列 (どちらも数値) が含まれます。 一部の速度には複数の観測値があります。 このデータから、自動車の速度と自動車を停止するために必要な距離との関係を記述する線形回帰モデルを作成します。

線形モデルの要件はシンプルです。

+ 従属変数 `speed` と独立変数 `distance` の関係を記述する式を定義する

+ モデルのトレーニングで使用する入力データを提供する

> [!TIP]
> 線形モデルの更新機能を必要がある場合はお勧めこのチュートリアルでは、rxLinMod を使用して、モデルに合わせて調整するプロセスについて説明します[Fitting Linear Models。](https://docs.microsoft.com/r-server/r/how-to-revoscaler-linear-model)

モデルを実際に構築するには、R コード内に式を定義し、データを入力パラメーターとして渡します。

```sql
DROP PROCEDURE IF EXISTS generate_linear_model;
GO
CREATE PROCEDURE generate_linear_model
AS
BEGIN
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'lrmodel <- rxLinMod(formula = distance ~ speed, data = CarsData);
        trained_model <- data.frame(payload = as.raw(serialize(lrmodel, connection=NULL)));'
    , @input_data_1 = N'SELECT [speed], [distance] FROM CarSpeed'
    , @input_data_1_name = N'CarsData'
    , @output_data_1_name = N'trained_model'
    WITH RESULT SETS ((model varbinary(max)));
END;
GO
```

+ rxLinMod の最初の引数は、距離を速度に依存するものとして定義する "*formula*" パラメーターです。
+ 入力データは、SQL クエリによって設定される変数 `CarsData` に格納されます。 入力データに特定の名前を割り当てない場合、既定の変数名は "_InputDataSet_" になります。

## <a name="create-a-table-for-storing-the-model"></a>モデルを格納するテーブルを作成する

次に、再トレーニングまたは予測に使用することができますので、モデルを格納します。 モデルを作成する R パッケージの出力は、通常は**バイナリ オブジェクト**です。 したがって、モデルを格納するテーブルには **varbinary** 型の列が必要です。

```sql
CREATE TABLE stopping_distance_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null);
```

## <a name="save-the-model"></a>モデルを保存する

モデルを保存するには、次の Transact-SQL ステートメントを実行してストアド プロシージャを呼び出し、モデルを生成し、テーブルに保存します。

```sql
INSERT INTO stopping_distance_models (model)
EXEC generate_linear_model;
```

このコードをもう一度実行する場合、このエラーを取得することに注意してください。

```
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

このエラーを避ける 1 つのオプションは、新しいモデルごとに名前を更新することです。 たとえば、わかりやすい名前に変更し、モデルの種類や作成日などを含めることができます。

```sql
UPDATE stopping_distance_models
SET model_name = 'rxLinMod ' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="output-additional-variables"></a>追加の変数を出力する

一般に、ストアド プロシージャ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) からの R の出力は、1 つのデータ フレームに制限されています。 (この制限は、将来的に削除される可能性があります)。

ただし、データ フレームに加え、スカラーなどの他の型の出力を返すことはできます。

たとえば、モデルをトレーニングするが、モデルの係数のテーブルをすぐに表示する必要があるとします。 係数のテーブルをメインの結果セットとして作成し、トレーニング済みのモデルを SQL 変数に出力します。 すぐに再モデルを使用して、変数を呼び出すことによって、または次のように、テーブルにモデルを保存する可能性があります。

```sql
DECLARE @model varbinary(max), @modelname varchar(30)
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
        speedmodel <- rxLinMod(distance ~ speed, CarsData)
        modelbin <- serialize(speedmodel, NULL)
        OutputDataSet <- data.frame(coefficients(speedmodel));'
    , @input_data_1 = N'SELECT [speed], [distance] FROM CarSpeed'
    , @input_data_1_name = N'CarsData'
    , @params = N'@modelbin varbinary(max) OUTPUT'
    , @modelbin = @model OUTPUT
    WITH RESULT SETS (([Coefficient] float not null));

-- Save the generated model
INSERT INTO [dbo].[stopping_distance_models] (model_name, model)
VALUES ('latest model', @model)
```

**結果**

![rslq_basictut_coefficients](media/rslq-basictut-coefficients.PNG)

### <a name="summary"></a>まとめ

SQL パラメーターと R の変数を操作するため、これらの規則に従う`sp_execute_external_script`:

+ 名前では R スクリプトにマップされているすべての SQL パラメーターを表示する必要があります、  _\@params_引数。
+ これらのパラメーターの 1 つの出力に OUTPUT キーワードを追加、  _\@params_一覧。
+ マップされるパラメーターを一覧表示した後は 1 行ずつ、すぐに R 変数への SQL パラメーターの後に、マッピングを提供、  _\@params_一覧。

## <a name="next-steps"></a>次のステップ

最後のクイック スタートでは、モデルがある、できたから予測を生成し、結果をプロットする方法について説明します。

> [!div class="nextstepaction"]
> [クイック スタート: 予測し、プロットをモデルから](../tutorials/rtsql-predict-and-plot-from-model.md)