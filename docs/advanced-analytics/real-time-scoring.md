---
title: リアルタイムのスコアリング sp_rxPredict ストアド プロシージャの SQL Server Machine Learning Services を使用します。
description: Sp_rxPredict、SQL Server で R で記述された事前トレーニング済みモデルに対するデータの入力をスコア付けを使用して予測を生成します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: def60a6de7d5a6f3641a6de88410543e9e592ba4
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645161"
---
# <a name="real-time-scoring-with-sprxpredict-in-sql-server-machine-learning"></a>リアルタイムのスコアリングでは、SQL Server machine learning で sp_rxPredict
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

リアルタイムのスコアリングは、 [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)システム ストアド プロシージャと CLR の拡張機能で SQL Server の高パフォーマンスの予測やワークロードの予測にスコア。 リアルタイム スコアリングし、言語に依存しないのは、R または Python の実行時間に依存関係のない実行します。 モデルの作成し、Microsoft の関数を使用してトレーニングし、SQL Server のバイナリ形式にシリアル化すると仮定すると、リアルタイム スコアリングする際の R または Python のアドオンがない SQL Server インスタンスで新しいデータの入力から予測される結果を生成インストールされています。

## <a name="how-real-time-scoring-works"></a>リアルタイムのスコアリング動作

SQL Server 2017 と SQL Server 2016 でのリアルタイム スコアリングはサポートされて[モデルの種類がサポートされている](#bkmk_py_supported_algos)線形およびロジスティック回帰、デシジョン ツリー モデル化の。 Machine learning の特別なバイナリ形式で格納されているモデルに提供されるユーザー入力に基づいてスコアを生成するのにネイティブの C++ ライブラリを使用します。

トレーニング済みモデルは、外部言語のランタイムを呼び出さずにスコア付けに使用できます、ため、複数のプロセスのオーバーヘッドが減少します。 運用環境のシナリオをスコア付け用の予測パフォーマンスを向上させる多くをサポートしています。 データが SQL Server を越える、ため、結果は生成され、R と SQL の間のデータ変換されることがなく新しいテーブルに挿入します。

複数の手順は、リアルタイム スコアリングします。

1. スコア付けを行うストアド プロシージャは、データベースごとに有効にする必要があります。
2. バイナリ形式で事前トレーニング済みモデルを読み込みます。
3. スコア付けする、表形式または 1 つのいずれかの行では、モデルへの入力として新しい入力データを入力します。
4. スコアを生成するには、呼び出し、 [sp_rxPredict](https://docs.microsoft.com//sql/relational-databases/system-stored-procedures/sp-rxpredict-transact-sql)ストアド プロシージャ。

> [!TIP]
> リアルタイムのスコア付けの動作の例は、次を参照してください[エンド ツー エンド ローン償却予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス。](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)

## <a name="prerequisites"></a>前提条件

+ [SQL Server の CLR 統合を有効にする](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration)します。

+ [リアルタイム スコアリングを有効にする](#bkmk_enableRtScoring)します。

+ 事前に、サポートされているのいずれかを使用してモデルをトレーニングする必要があります**rx**アルゴリズム。 リアルタイムのスコアリングと、R 用`sp_rxPredict`連携[RevoScaleR と MicrosoftML アルゴリズムをサポートされています。](#bkmk_rt_supported_algos)します。 Python の場合、次を参照してください。 [revoscalepy と microsoftml アルゴリズムをサポートされています。](#bkmk_py_supported_algos)

+ モデルを使用して、シリアル化[rxSerialize](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel) 、R 用と[rx_serialize_model](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model) Python 用です。 これらのシリアル化関数は、高速のスコア付けをサポートするために最適化されています。

+ それを呼び出す対象となるデータベース エンジンのインスタンスにモデルを保存します。 このインスタンスには、R または Python のランタイム拡張機能は必要ありません。

> [!Note]
> リアルタイム スコアリングは現在の小さいデータ セット、少数の行から数百行の何千ものまで高速の予測に最適化されています。 使用して、大規模なデータセットで[rxPredict](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxpredict)高速な場合があります。

<a name="bkmk_py_supported_algos"></a>

## <a name="supported-algorithms"></a>サポートされているアルゴリズム

### <a name="python-algorithms-using-real-time-scoring"></a>リアルタイム スコアリングを使用する Python アルゴリズム

+ revoscalepy モデル

  + [rx_lin_mod](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-lin-mod) \*
  + [rx_logit](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-logit) \*
  + [rx_btrees](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-btrees) \*
  + [rx_dtree](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dtree) \*
  + [rx_dforest](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-dforest) \*
  
  モデルが付いた\*PREDICT 関数を使用したネイティブ スコアリングもサポートします。

+ microsoftml のモデル

  + [rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees)
  + [rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)
  + [rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression)
  + [rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm)
  + [rx_neural_net](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network)
  + [rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear)

+ Microsoftml によって提供される変換

  + [featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text)
  + [concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical)
  + [categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash)


<a name="bkmk_rt_supported_algos"></a>

### <a name="r-algorithms-using-real-time-scoring"></a>リアルタイム スコアリングを使用して R アルゴリズム

+ RevoScaleR のモデル

  + [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod) \*
  + [rxLogit](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlogit) \*
  + [rxBTrees](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxbtrees) \*
  + [rxDtree](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdtree) \*
  + [rxdForest](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdforest) \*
  
  モデルが付いた\*PREDICT 関数を使用したネイティブ スコアリングもサポートします。

+ MicrosoftML のモデル

  + [rxFastTrees](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [rxFastForest](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastforest)
  + [rxLogisticRegression](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxlogisticregression)
  + [rxOneClassSvm](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxoneclasssvm)
  + [rxNeuralNet](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxneuralnet)
  + [rxFastLinear](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfastlinear)

+ MicrosoftML によって提供される変換

  + [featurizeText](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/rxfasttrees)
  + [concat](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/concat)
  + [categorical](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categorical)
  + [categoricalHash](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/categoricalHash)
  + [selectFeatures](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/selectFeatures)

### <a name="unsupported-model-types"></a>サポートされていないモデルの種類

リアルタイム スコアリングでは、インタープリター; は使用しませんそのため、インタープリターが必要となる機能は、スコア付けの手順ではサポートされません。  たとえば、次のようなものがあります。

  + モデルを使用して、`rxGlm`または`rxNaiveBayes`アルゴリズムがサポートされていません。

  + 変換関数またはなど、変換を含む数式を使用してモデル化<code>A ~ log(B)</code>リアルタイム スコアリングではサポートされていません。 このタイプのモデルを使用して、リアルタイム スコアリングにデータを渡す前に、入力データの変換を実行することをお勧めします。


## <a name="example-sprxpredict"></a>例: sp_rxPredict

このセクションは、セットアップに必要な手順を説明します**リアルタイム**予測、R で T-SQL から関数を呼び出す方法の例を示します。

<a name ="bkmk_enableRtScoring"></a> 

### <a name="step-1-enable-the-real-time-scoring-procedure"></a>手順 1. リアルタイムのスコアリングのプロシージャを有効にします。

スコア付けに使用する各データベースに対してこの機能を有効にする必要があります。 サーバーの管理者は、RevoScaleR パッケージに含まれているコマンド ライン ユーティリティ、RegisterRExt.exe を実行する必要があります。

> [!NOTE]
> リアルタイムのスコアリング動作するためには、SQL CLR の機能はインスタンスで有効にする必要があります。さらに、データベースは、trustworthy としてマークする必要があります。 スクリプトを実行するときにこれらのアクションが実行されます。 ただし、これを行う前に、追加のセキュリティに影響を検討してください。

1. 管理者特権でコマンド プロンプトを開くし、RegisterRExt.exe があるフォルダーに移動します。 次のパスは、既定のインストールで使用できます。
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. インスタンスと拡張ストアド プロシージャを有効にするターゲット データベース名に置き換えて、次のコマンドを実行するには。

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    たとえば、既定のインスタンスに CLRPredict データベースには、拡張ストアド プロシージャを追加するに次のように入力します。

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    既定のインスタンス、データベースがある場合は、インスタンス名です。 名前付きインスタンスを使用している場合は、インスタンス名を指定する必要があります。

3. RegisterRExt.exe には、次のオブジェクトが作成されます。

    + 信頼されたアセンブリ
    + ストアド プロシージャ `sp_rxPredict`
    + 新しいデータベース ロール、`rxpredict_users`します。 データベース管理者は、このロールを使用して、リアルタイムのスコア付け機能を使用するユーザーに権限を与えることができます。

4. 実行する必要があるすべてのユーザーを追加`sp_rxPredict`新しいロールにします。

> [!NOTE]
> 
> SQL Server 2017 では、追加のセキュリティ メジャーは、CLR 統合の問題を回避するにです。 これらのメジャーは、次のストアド プロシージャの使用に関する追加の制限を強制します。 

### <a name="step-2-prepare-and-save-the-model"></a>手順 2. 準備し、モデルを保存

Sp によって必要なバイナリ形式\_rxPredict は、PREDICT 関数を使用するために必要な形式と同じです。 そのため、R コードで呼び出しを含める[rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)、必ずを指定して`realtimeScoringOnly = TRUE`、この例のように。

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>手順 3. Sp_rxPredict を呼び出す

Sp を呼び出す\_rxPredict するとしては、他のストアド プロシージャ。 現在のリリースでは、ストアド プロシージャには、2 つのパラメーター: _\@モデル_バイナリ形式でモデルと _\@inputData_ 、スコアリングに使用するデータとして定義されています。有効な SQL クエリを使用します。

バイナリ形式は、PREDICT 関数で使用されると同じであるために、前の例のモデルとデータ テーブルを使用できます。

```sql
DECLARE @irismodel varbinary(max)
SELECT @irismodel = [native_model_object] from [ml_models]
WHERE model_name = 'iris.dtree' 
AND model_version = 'v1''

EXEC sp_rxPredict
@model = @irismodel,
@inputData = N'SELECT * FROM iris_rx_data'
```

> [!NOTE]
> 
> Sp を呼び出す\_rxPredict スコアリングの入力データには、モデルの要件に一致する列が含まれていない場合は失敗します。 現時点では、次の .NET データ型のみがサポートされています: float、short、ushort、double、long、ulong と文字列。
> 
> そのため、リアルタイム スコアリングのために使用する前に、入力データでサポートされていない型を除外する必要があります。
> 
> 対応する SQL 型については、次を参照してください。 [SQL-CLR 型マッピング](/dotnet/framework/data/adonet/sql/linq/sql-clr-type-mapping)または[CLR パラメーター データのマッピング](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data)します。

## <a name="disable-real-time-scoring"></a>リアルタイム スコアリングを無効にします。

リアルタイムのスコア付け機能を無効にするには、管理者特権でコマンド プロンプトを開きし、次のコマンドを実行します。 `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="next-steps"></a>次の手順

RxPredict を使用して、スコア付け方法の例は、次を参照してください。[エンド ツー エンド ローン償却予測ビルドを使用して Azure HDInsight Spark クラスターと SQL Server 2016 R サービス](https://blogs.msdn.microsoft.com/rserver/2017/06/29/end-to-end-loan-chargeoff-prediction-built-using-azure-hdinsight-spark-clusters-and-sql-server-2016-r-service/)します。

SQL Server でのスコア付けの詳細については、次を参照してください。 [SQL Server machine learning で予測を生成する方法](r/how-to-do-realtime-scoring.md)します。
