---
title: R で SQL Server Machine Learning を使用して、予測モデルを作成するクイック スタート
description: このクイック スタートでは、SQL Server のデータを使用して予測をプロットする R でモデルを構築する方法を説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 278eba1189b376b57f2dec7249a378832c18095c
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046865"
---
# <a name="quickstart-create-a-predictive-model-using-r-in-sql-server"></a>クイック スタート:SQL Server で R を使用して予測モデルを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、R を使用するモデルをトレーニングする方法について説明し、SQL Server のテーブルに、モデルを保存します。 モデルは、手動の送信を車両がどのように収めるされている確率を予測する単純な一般化線形モデル (GLM) です。 使用して、 `mtcars` R. に含まれているデータセット

## <a name="prerequisites"></a>前提条件

前のクイック スタート[SQL server が存在することを確認する R](quickstart-r-verify.md)情報を提供し、このクイック スタートに必要な R 環境を設定するためにリンクします。

## <a name="create-the-source-data"></a>ソース データを作成する

最初に、トレーニング データを保存するテーブルを作成します。

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

次に、データセット内のビルドからのデータを挿入`mtcars`します。

```SQL
INSERT INTO dbo.MTCars
EXEC sp_execute_external_script
        @language = N'R'
        , @script = N'MTCars <- mtcars;'
        , @input_data_1 = N''
        , @output_data_1_name = N'MTCars';
```

+ 一部の人などに使用する一時テーブルは、一部の R クライアントがバッチ間のセッションを切断することに注意してください。

+ 小規模と大規模の多くのデータセットが R ランタイムに付属しています。 R と共にインストールされるデータセットの一覧を取得するには、R コマンド プロンプトから「`library(help="datasets")`」と入力します。

## <a name="create-a-model"></a>モデルを作成する

自動車の速度のデータには、2 つの列、両方の数値では、処理能力が含まれています (`hp`) と重量 (`wt`)。 このデータから、手動の送信を車両がどのように収めるされている確率を推定する一般化線形モデル (GLM) を作成します。

モデルを構築するには、R コード内で数式を定義し、入力パラメーターとしてデータを渡します。

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

+ 最初の引数`glm`は、*数式*パラメーターを定義する`am`に依存している`hp + wt`します。
+ 入力データは、SQL クエリによって設定される変数 `MTCarsData` に格納されます。 入力データに特定の名前を割り当てない場合、既定の変数名は "_InputDataSet_" になります。

## <a name="create-a-table-for-the-model"></a>モデルのテーブルを作成します。

次に、再トレーニングまたは予測に使用することができますので、モデルを格納します。 モデルを作成する R パッケージの出力は、通常は**バイナリ オブジェクト**です。 そのため、モデルを格納するテーブルでの列を提供する必要があります**varbinary (max)** 型。

```sql
CREATE TABLE GLM_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
```

## <a name="save-the-model"></a>モデルを保存する

モデルを保存するには、次の Transact-SQL ステートメントを実行してストアド プロシージャを呼び出し、モデルを生成し、テーブルに保存します。

```sql
INSERT INTO GLM_models(model)
EXEC generate_GLM;
```

このコードをもう一度実行する場合、このエラーを取得することに注意してください。

```sql
Violation of PRIMARY KEY constraint...Cannot insert duplicate key in object dbo.stopping_distance_models
```

このエラーを避ける 1 つのオプションは、新しいモデルごとに名前を更新することです。 たとえば、わかりやすい名前に変更し、モデルの種類や作成日などを含めることができます。

```sql
UPDATE GLM_models
SET model_name = 'GLM_' + format(getdate(), 'yyyy.MM.HH.mm', 'en-gb')
WHERE model_name = 'default model'
```

## <a name="next-steps"></a>次の手順

最後のクイック スタートでは、モデルがある、できたから予測を生成し、結果をプロットする方法について説明します。

> [!div class="nextstepaction"]
> [クイック スタート:予測し、プロットをモデルから](quickstart-r-predict-from-model.md)