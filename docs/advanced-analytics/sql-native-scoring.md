---
title: SQL Server machine learning でのネイティブ スコアリング |Microsoft Docs
description: SQL Server で R または Python で記述された事前トレーニング済みモデルに対して dta 入力のスコアリング、T-SQL の予測関数を使用して予測を生成します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 372c81310fea86094543319f21e409142810de97
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713154"
---
# <a name="native-scoring-using-the-predict-t-sql-function"></a>T-SQL の予測関数を使用して、ネイティブのスコアリング
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

ネイティブ スコアリングは[T-SQL の予測関数](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)と予測値を生成する SQL Server 2017 でネイティブの C++ の拡張機能の機能または*スコア*のほぼリアルタイムでの新しいデータ入力します。 この手法は、ワークロードの予測および予測の最も高速の可能な処理速度を提供していますが、プラットフォームとライブラリの要件が付属して: RevoScaleR と revoscalepy から関数の C++ 実装だけです。

ネイティブ スコアリングでは、既にトレーニング済みのモデルがあることが必要です。 SQL Server 2017 Windows または Linux、または Azure SQL Database では、呼び出せる PREDICT 関数を呼び出すには、TRANSACT-SQL でネイティブの入力パラメーターとして指定する新しいデータに対してスコア付けします。 PREDICT 関数では、指定したデータ入力に対するスコアを返します。

## <a name="how-native-scoring-works"></a>ネイティブのスコアリング動作

ネイティブ スコアリングでネイティブ C++ ライブラリ、既にトレーニング済みのモデルを読み取ることができる Microsoft からが以前特別なバイナリ形式で格納または、生のバイト ストリームとしてディスクに保存および作成した新しいデータ入力のスコアを生成します。 モデルをトレーニングすると、パブリッシュ、および格納されている場合、そのことができるため R または Python インタープリターを呼び出さずにスコア付け。 複数プロセスの対話処理のオーバーヘッドを軽減、そのための運用環境のエンタープライズ シナリオで予測パフォーマンスをはるかに高速です。

ネイティブ スコアリングを使用するには、T-SQL の予測関数を呼び出す、次の必須の入力を渡します。

+ サポートされているアルゴリズムに基づく互換性のあるモデル。
+ 入力データは、通常、SQL クエリとして定義されます。

関数は、通過するソース データの列と共に、入力データの予測を返します。

## <a name="prerequisites"></a>前提条件

予測が SQL Server 2017 データベース エンジンのすべてのエディションで使用可能な Windows、SQL Server 2017 (Windows)、SQL Server 2017 (Linux) または Azure SQL Database で SQL Server 2017 Machine Learning サービスを含む、既定で有効にします。 R、Python をインストールまたはその他の機能を有効にする必要はありません。

+ 事前に、サポートされているのいずれかを使用してモデルをトレーニングする必要があります**rx**以下に示すアルゴリズム。

+ モデルを使用して、シリアル化[rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) 、R 用と[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) Python 用です。 これらのシリアル化関数は、高速のスコア付けをサポートするために最適化されています。

<a name="bkmk_native_supported_algos"></a> 

## <a name="supported-algorithms"></a>サポートされているアルゴリズム

+ revoscalepy モデル

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod)
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) 
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) 
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) 
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) 

+ RevoScaleR のモデル

  + [rxLinMod](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlinmod)
  + [rxLogit](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxlogit)
  + [rxBTrees](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxbtrees)
  + [rxDtree](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdtree)
  + [rxDForest](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdforest)

MicrosoftML または microsoftml からモデルを使用する必要がある場合を使用して、 [sp_rxPredict とリアルタイム スコアリング](real-time-scoring.md)します。

サポートされていないモデルの種類では、次の種類があります。

+ その他の変換を含むモデル
+ モデルを使用して、`rxGlm`または`rxNaiveBayes`で同等の RevoScaleR または revoscalepy アルゴリズム
+ PMML モデル
+ その他のオープン ソースまたはサードパーティ製のライブラリを使用して作成されたモデル

## <a name="example-predict-t-sql"></a>例: 予測 (T-SQL)

この例では、モデルを作成し、T-SQL からリアルタイムの予測関数を呼び出します。

### <a name="step-1-prepare-and-save-the-model"></a>手順 1. 準備し、モデルを保存

サンプル データベースと必要なテーブルを作成する次のコードを実行します。

```SQL
CREATE DATABASE NativeScoringTest;
GO
USE NativeScoringTest;
GO
DROP TABLE IF EXISTS iris_rx_data;
GO
CREATE TABLE iris_rx_data (
  "Sepal.Length" float not null, "Sepal.Width" float not null
  , "Petal.Length" float not null, "Petal.Width" float not null
  , "Species" varchar(100) null
);
GO
```

テーブルからデータにデータを次のステートメントを使用して、 **iris**データセット。

```SQL
INSERT INTO iris_rx_data ("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width" , "Species")
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'iris_data <- iris;'
  , @input_data_1 = N''
  , @output_data_1_name = N'iris_data';
GO
```

ここで、モデルを格納するためのテーブルを作成します。

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

次のコードに基づくモデルを作成する、 **iris**データセットという名前のテーブルに保存します**モデル**します。

```SQL
DECLARE @model varbinary(max);
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N'
    iris.sub <- c(sample(1:50, 25), sample(51:100, 25), sample(101:150, 25))
    iris.dtree <- rxDTree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = iris[iris.sub, ])
    model <- rxSerializeModel(iris.dtree, realtimeScoringOnly = TRUE)
    '
  , @params = N'@model varbinary(max) OUTPUT'
  , @model = @model OUTPUT
  INSERT [dbo].[ml_models]([model_name], [model_version], [native_model_object])
  VALUES('iris.dtree','v1', @model) ;
```

> [!NOTE] 
> 使用してください、 [rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)モデルを保存する RevoScaleR から関数。 標準的な R`serialize`関数は、必要な形式を生成できません。

バイナリ形式で格納されたモデルを表示するには、次のようなステートメントを実行できます。

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>手順 2. モデルの予測を実行します。

次の単純な PREDICT ステートメント、デシジョン ツリー モデルを使用してから、分類を取得します、**ネイティブ スコアリング**関数。 指定した属性、花弁の長さと幅に基づく iris species を予測します。

```SQL
DECLARE @model varbinary(max) = (
  SELECT native_model_object
  FROM ml_models
  WHERE model_name = 'iris.dtree'
  AND model_version = 'v1');
SELECT d.*, p.*
  FROM PREDICT(MODEL = @model, DATA = dbo.iris_rx_data as d)
  WITH(setosa_Pred float, versicolor_Pred float, virginica_Pred float) as p;
go
```

エラーが発生した場合は、"エラーが発生しました PREDICT 関数の実行中にします。 モデルは、壊れているか無効です"、クエリが、モデルを返されませんでしたを通常意味します。 正しく、モデルの名前を入力するかどうかや、モデル テーブルが空のかどうかを確認します。

> [!NOTE]
> 列と値がによって返されるため、 **PREDICT**はモデルの種類によって異なる場合を使用して、返されるデータのスキーマを定義する必要があります、 **WITH**句。

## <a name="next-steps"></a>次の手順

ネイティブ スコアリングを含む完全なソリューションでは、SQL Server 開発チームからこれらのサンプルを参照してください。

+ ML スクリプトのデプロイ: [Python モデルを使用します。](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/step/3.html)
+ ML スクリプトのデプロイ: [R モデルを使用します。](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/step/3.html)