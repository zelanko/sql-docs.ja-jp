---
title: R で SQL Server Machine Learning を使用してモデルから予測するクイック スタート
description: このクイック スタートでは、R と SQL Server のデータの事前構築済みのモデルを使用してスコア付けについて説明します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 7175b99eb20710f5dd08689bd055d3a4ec93ae92
ms.sourcegitcommit: baca29731a1be4f8fa47567888278394966e2af7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046904"
---
# <a name="quickstart-predict-from-model-using-r-in-sql-server"></a>クイック スタート:SQL Server で R を使用して、モデルから予測します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このクイック スタートでは、新しいデータに対して予測をスコア付けの前のクイック スタートで作成したモデルを使用します。 実行する_スコアリング_新しいデータを使用して、トレーニング済みモデルのいずれかをテーブルから取得し、予測の基になるデータの新しいセットを呼び出しています。 スコア付けは、データ サイエンスで使用されることの予測、確率、またはトレーニング済みのモデルに渡す新しいデータに基づくその他の値を生成することを意味する用語です。

## <a name="prerequisites"></a>前提条件

このクイック スタートの拡張機能は、[予測モデルの作成](quickstart-r-create-predictive-model.md)です。

## <a name="create-the-table-of-new-data"></a>新しいデータのテーブルを作成します。

最初に、新しいデータでテーブルを作成します。 

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

## <a name="predict-manual-transmission"></a>手動の転送を予測します。

ここでは、によって、`dbo.GLM_models`テーブルの複数の R モデル、異なるパラメーターまたはアルゴリズムを使用してすべてのビルドを含む可能性がありますまたはデータのさまざまなサブセットでトレーニングします。

特定の 1 つのモデルに基づく予測を取得するには、は、次の SQL スクリプトを記述する必要があります。

1. 必要なモデルを取得します。
2. 新しい入力データを取得します。
3. そのモデルと互換性がある R 予測関数を呼び出します。

この例では、という名前のモデルを使用しました`default model`します。

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

上記のスクリプトは、次の手順を実行します。

+ SELECT ステートメントを使用して、テーブルから 1 つのモデルを取得し、それを入力パラメーターとして渡します。

+ テーブルからモデルを取得したら、モデルに対して `unserialize` 関数を呼び出します。

+ 適切な引数を使用して `predict` 関数をモデルに適用し、新しい入力データを提供します。

+ この例で、 `str` R. から返されるデータのスキーマを確認する、テスト フェーズ中に関数を追加後でステートメントを削除することができます。

+ R スクリプトで使用される列名は、ストアド プロシージャの出力に必ずしもは渡されません。 ここでいくつかの新しい列名を定義するのに、WITH RESULTS 句を使用しました。

**結果**

![結果セットの手動転送 properbility を予測します。](./media/r-predict-am-resultset.png)

使用することも、 [TRANSACT-SQL の PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)予測された値または格納されたモデルに基づいてスコアを生成します。

## <a name="next-steps"></a>次の手順

R と SQL Server の統合により、規模を拡大して R ソリューションを配置しやすくなり、高パフォーマンスのデータ処理および高速 R 分析のために、R とリレーショナル データベースの優れた機能を活用できます。 

Microsoft データ サイエンスと R Services の開発チームによって作成されたエンド ツー エンドのシナリオを SQL Server で R を使用するソリューションについて学習を続行します。

> [!div class="nextstepaction"]
> [SQL Server R チュートリアル](sql-server-r-tutorials.md)
