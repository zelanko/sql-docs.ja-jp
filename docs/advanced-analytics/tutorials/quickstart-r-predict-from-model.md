---
title: R を使用してモデルから予測するクイックスタート
description: このクイックスタートでは、R での構築済みモデルを使用したスコアリングと、データの SQL Server について説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: e81731683fb71b074ed754ab6ab4eaab40d08c20
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345406"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>クイック スタート: SQL Server で R を使用してモデルから予測する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイックスタートでは、前のクイックスタートで作成したモデルを使用して、新しいデータに対する予測をスコア付けします。 新しいデータを使用して_スコア_付けを実行するには、テーブルからトレーニング済みのモデルの1つを取得し、予測の基になる新しいデータセットを呼び出します。 スコアリングは、トレーニング済みのモデルに取り込まれた新しいデータに基づいて予測、確率、またはその他の値を生成することを意味するためにデータサイエンスで使用されることがあります。

## <a name="prerequisites"></a>前提条件

このクイックスタートは、[予測モデルを作成する](quickstart-r-create-predictive-model.md)ための拡張機能です。

## <a name="create-the-table-of-new-data"></a>新しいデータのテーブルを作成する

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

## <a name="predict-manual-transmission"></a>手動による転送を予測する

現在、テーブルに`dbo.GLM_models`は複数の R モデルが含まれており、さまざまなパラメーターまたはアルゴリズムを使用して構築されているか、データの異なるサブセットに対してトレーニングされています。

1つの特定のモデルに基づいて予測を取得するには、次を実行する SQL スクリプトを記述する必要があります。

1. 必要なモデルを取得します。
2. 新しい入力データを取得します。
3. そのモデルと互換性がある R 予測関数を呼び出します。

この例では、という名前`default model`のモデルを使用します。

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

+ SELECT ステートメントを使用して、テーブルから 1 つのモデルを取得し、それを入力パラメーターとして渡します。

+ テーブルからモデルを取得したら、モデルに対して `unserialize` 関数を呼び出します。

+ 適切な引数を使用して `predict` 関数をモデルに適用し、新しい入力データを提供します。

+ この例`str`では、関数はテストフェーズ中に追加され、R から返されるデータのスキーマを確認します。このステートメントは後で削除できます。

+ R スクリプトで使用される列名は、ストアドプロシージャの出力に必ずしも渡されるとは限りません。 ここでは、WITH RESULTS 句を使用して、新しい列名を定義しました。

**結果**

![Properbility の手動送信を予測するための結果セット](./media/r-predict-am-resultset.png)

また、 [transact-sql で PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)を使用して、格納されているモデルに基づいて予測値またはスコアを生成することもできます。

## <a name="next-steps"></a>次の手順

R と SQL Server の統合により、規模を拡大して R ソリューションを配置しやすくなり、高パフォーマンスのデータ処理および高速 R 分析のために、R とリレーショナル データベースの優れた機能を活用できます。 

Microsoft のデータサイエンスおよび R サービスの開発チームによって作成されたエンドツーエンドのシナリオを通じて、SQL Server で R を使用したソリューションについて学習を続けます。

> [!div class="nextstepaction"]
> [SQL Server R チュートリアル](sql-server-r-tutorials.md)
