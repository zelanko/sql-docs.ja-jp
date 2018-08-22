---
title: リアルタイム スコアリングまたは SQL Server Machine Learning でのネイティブ スコアリングを実行する方法 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: dfea308f268d666ce070c21a7dd9afa513f95406
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2018
ms.locfileid: "40393332"
---
# <a name="how-to-perform-real-time-scoring-or-native-scoring-in-sql-server"></a>リアルタイム スコアリングまたは SQL Server のネイティブ スコアリングを実行する方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で結果を予測する 2 つのアプローチをほぼリアルタイムの R で記述された事前トレーニング済みモデルを使用してを示しますリアルタイム スコアリングとネイティブ スコアリングの両方が機械学習モデルを R. をインストールすることがなくを使用するために設計されています事前トレーニング済みモデルを SQL Server データベースに保存されます-互換性のある形式で指定された新しい入力の予測スコアをすばやく生成するのに標準的なデータ アクセス手法を使用できます。

## <a name="choose-a-scoring-method"></a>スコアリング方法を選択します。

高速のバッチ予測では、次のオプションがサポートされます。

+ **ネイティブ スコアリング**: SQL Server 2017 Windows、SQL Server 2017 Linux、および Azure SQL Database での関数の T-SQL を予測します。
+ **リアルタイム スコアリング**: sp を使用して\_rxPredict ストアド プロシージャを SQL Server 2016 または SQL Server 2017 (Windows のみ)。

> [!NOTE]
> SQL Server 2017 では、PREDICT 関数の使用をお勧めします。
> Sp を使用する\_rxPredict では、SQLCLR の統合を有効にすることが必要です。 このオプションを有効にする前に、セキュリティへの影響を検討してください。

モデルの準備とスコアを生成し、全体的なプロセスは似ています。

1. サポートされているアルゴリズムを使用してモデルを作成します。
2. 特別なバイナリ形式を使用して、モデルをシリアル化します。
3. モデルを SQL Server が使用できるようにします。 つまり、通常、シリアル化されたモデルを SQL Server テーブルに格納します。
4. 関数またはストアド プロシージャを呼び出し、モデルと入力データを渡します。

### <a name="requirements"></a>要件

+ PREDICT 関数は、SQL Server 2017 のすべてのエディションで使用可能な既定で有効です。 R をインストールまたは追加の機能を有効にする必要はありません。

+ Sp を使用して場合\_rxPredict、追加の手順が必要です。 参照してください[リアルタイム スコアリングを有効にする](#bkmk_enableRtScoring)します。

+ この時点では、RevoScaleR と MicrosoftML のみが互換性のあるモデルを作成できます。 追加のモデルの種類は、後で使用可能なになります可能性があります。 現在サポートされているアルゴリズムの一覧で、次を参照してください。[リアルタイム スコアリング](../real-time-scoring.md)します。

### <a name="serialization-and-storage"></a>シリアル化および保存

で高速のスコア付けのオプションのいずれかを、モデルを使用するには、特別なシリアル化された形式でサイズに対して最適化されているし、効率性をスコア付けのモデルを保存します。

+ 呼び出す`rxSerializeModel`にサポートされているモデルを記述する、**生**形式。
+ 呼び出す`rxUnserializeModel`を他の R コードで使用するモデルを再構築する、またはモデルを表示します。

詳細については、次を参照してください。 [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)します。

**SQL を使用します。**

SQL コードを使用して、モデルをトレーニングできます`sp_execute_external_script`、型の列では、テーブルに、トレーニング済みモデルを直接挿入**varbinary (max)** します。

簡単な例では、次を参照してください[このチュートリアル。](../tutorials/rtsql-create-a-predictive-model-r.md)

**R を使用します。**

R コードからは、テーブルに、モデルを保存する 2 つの方法があります。

+ 呼び出す、`rxWriteObject`モデルをデータベースに直接書き込む、RevoScaleR パッケージからの関数。

  `rxWriteObject()`関数が SQL Server などの ODBC データ ソースから R オブジェクトを取得またはオブジェクトを SQL Server に書き込むことができます。 API は、単純なキー値ストアの後にモデル化されます。
  
  この関数を使用する場合は、最初に、新しいシリアル化関数を使用して、モデルをシリアル化することを確認します。 次に、設定、*シリアル化*で引数`rxWriteObject`をシリアル化の手順を回避するために、FALSE にします。

+ モデルをファイルに raw 形式で保存することもでき、その SQL Server に、ファイルから読み取る。 このオプションは、環境間でのモデルのコピーまたは移動する場合に便利です。

## <a name="native-scoring-with-predict"></a>ネイティブの予測をスコア付け

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

## <a name="real-time-scoring-with-sprxpredict"></a>リアルタイム sp_rxPredict をスコア付け

このセクションは、セットアップに必要な手順を説明します**リアルタイム**予測、T-SQL から関数を呼び出す方法の例を示します。

### <a name ="bkmk_enableRtScoring"></a> 手順 1 です。 リアルタイムのスコアリングのプロシージャを有効にします。

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

```SQL
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

## <a name="real-time-scoring-in-other-microsoft-product"></a>その他の Microsoft 製品のリアルタイム スコアリング

SQL Server データベース内分析ではなく、スタンドアロン サーバーまたは Microsoft の Machine Learning Server を使用する場合は、ストアド プロシージャと予測を生成するための T-SQL 関数だけでなく他のオプションがあります。

スタンドアロン サーバーと Machine Learning Server の両方の概念をサポートする、 *web サービス*コードのデプロイ。 R をバンドルするまたは実行時に新しいデータ入力の評価と呼ばれる、web サービスとして事前トレーニング済みモデル Python。 詳細については、次の記事を参照してください。

+ [Machine Learning Server での web サービスとは](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [運用化とは何ですか。](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Python のモデルを azureml モデル管理 sdk を使用した web サービスとしてデプロイします。](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [新しい web サービスとして、R コードのブロックまたはリアルタイムのモデルを発行します。](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [R の mrsdeploy パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
