---
title: リアルタイムのスコアリングまたは SQL Server の Machine Learning でネイティブのスコア付けを実行する方法 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 91928b20316ec8555c7f309f134d083dea5c7569
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-perform-realtime-scoring-or-native-scoring-in-sql-server"></a>リアルタイムのスコアリングまたは SQL Server のネイティブのスコア付けを実行する方法
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server 2017 および SQL Server 2016 でネイティブのスコア付け機能と、リアルタイムのスコアリングを実行する方法の手順とサンプル コードを提供します。 リアルタイムのスコアリングとネイティブのスコア付けの両方の目的は、小さいバッチに分割のスコア付けの操作のパフォーマンスを向上させるためにです。

リアルタイムのスコアリングとネイティブのスコア付けの両方が機械学習モデルを R. をインストールすることがなくを使用するために設計されています必要なを行うには、互換性のある形式で事前トレーニング済みモデルを取得し、SQL Server データベースに保存します。

## <a name="choosing-a-scoring-method"></a>スコアリング方法の選択

高速バッチ予測は、次のオプションがサポートされています。

+ **ネイティブ スコアリング**: SQL Server 2017 で T-SQL で予測関数
+ **リアルタイムのスコアリング**: sp を使用して\_rxPredict ストアド プロシージャを SQL Server 2016 または SQL Server 2017 のいずれか。

> [!NOTE]
> SQL Server 2017 では、予測関数の使用をお勧めします。
> Sp を使用する\_rxPredict では、SQLCLR の統合を有効にすることが必要です。 このオプションを有効にするには、セキュリティへの影響を検討してください。

モデルの準備とスコアを生成し、全体的なプロセスは似ています。

1. サポートされているアルゴリズムを使用してモデルを作成します。
2. 特殊なバイナリ形式を使用して、モデルをシリアル化します。
3. モデルを SQL Server を使用できるようにします。 つまり、通常、シリアル化されたモデルを SQL Server テーブルに格納します。
4. 関数またはストアド プロシージャを呼び出すし、モデルと入力データを渡します。

### <a name="requirements"></a>必要条件

+ PREDICT 関数は、SQL Server 2017 のすべてのエディションで使用できるは既定で有効します。 R をインストールまたは追加の機能を有効にする必要はありません。

+ Sp を使用して場合\_rxPredict、いくつか追加の手順が必要です。 参照してください[リアルタイムのスコア付けを有効にする](#bkmk_enableRtScoring)です。

+ この時点では、RevoScaleR と MicrosoftML のみが互換性のあるモデルを作成できます。 追加のモデルの種類は、将来の使用可能なになる可能性があります。 現在サポートされているアルゴリズムの一覧で、次を参照してください。[リアルタイム スコアリング](../real-time-scoring.md)です。

### <a name="serialization-and-storage"></a>シリアル化と記憶域

高速のスコア付けのオプションのいずれかで、モデルを使用するには、特別なシリアル化された形式でサイズに対して最適化されているし、効率性をスコア付けのモデルを保存します。

+ 呼び出す`rxSerializeModel`サポートされているモデルの書き込み先、**生**形式です。
+ 呼び出す`rxUnserializeModel`他の R コードで使用するモデルを構築したり、モデルを表示します。

詳細については、次を参照してください。 [rxSerializeModel](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)です。

**SQL を使用します。**

コード SQL コードからを使用してモデルをトレーニングできます`sp_execute_external_script`、型の列では、テーブルにトレーニング済みモデルを直接挿入**varbinary (max)**です。

単純な例を参照してください[このチュートリアル。](../tutorials/rtsql-create-a-predictive-model-r.md)

**R を使用します。**

R コードからは、モデルをテーブルに保存するために 2 つの方法があります。

+ 呼び出す、`rxWriteObject`モデルをデータベースに直接書き込む、RevoScaleR パッケージからの関数。

  `rxWriteObject()`関数は SQL Server と同様に、ODBC データ ソースから R オブジェクトを取得したり、SQL Server へのオブジェクトを記述します。 この API は、単純なキー値ストアの後にモデル化されます。
  
  この関数を使用する場合は、まず新しいシリアル化の関数を使用してモデルをシリアル化することを確認します。 次に、設定、*シリアル化*で引数`rxWriteObject`FALSE に、シリアル化の手順を繰り返し行われないようにします。

+ モデルをファイルに raw 形式で保存することもとし、ファイルから SQL Server に読み込むことができます。 このオプションは、環境間でのモデルのコピーまたは移動する場合に便利です。

## <a name="native-scoring-with-predict"></a>ネイティブの予測をスコア付け

この例では、モデルを作成し、T-SQL からリアルタイムの予測関数を呼び出します。

### <a name="step-1-prepare-and-save-the-model"></a>手順 1. 準備してモデルを保存

サンプル データベースおよび必要なテーブルを作成する次のコードを実行します。

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

ここで、モデルを保存するためのテーブルを作成します。

```SQL
DROP TABLE IF EXISTS ml_models;
GO
CREATE TABLE ml_models ( model_name nvarchar(100) not null primary key
  , model_version nvarchar(100) not null
  , native_model_object varbinary(max) not null);
GO
```

次のコードに基づくモデルを作成する、 **iris**データセットという名前のテーブルに保存および**モデル**です。

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

バイナリ形式で保存されたモデルを表示するには、次のようなステートメントを実行することができます。

```SQL
SELECT *, datalength(native_model_object)/1024. as model_size_kb
FROM ml_models;
```

### <a name="step-2-run-predict-on-the-model"></a>手順 2. モデルで予測を実行します。

次の単純な予測ステートメントは、デシジョン ツリー モデルを使用して、分類を取得、**ネイティブ スコアリング**関数。 指定した属性、花びら長さと幅に基づく iris 種を予測します。

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

エラーが発生した場合は、"エラーが発生しました PREDICT 関数の実行中にします。 モデル壊れているか、無効な"は、クエリが、モデルを返されませんでしたを通常意味します。 正しく、モデルの名前を入力するかどうかや、モデル テーブルが空のかどうかを確認してください。

> [!NOTE]
> 列と値がによって返されたため**PREDICT**モデルの種類によって異なる場合を使用して、返されるデータのスキーマを定義する必要があります、 **WITH**句。

## <a name="realtime-scoring-with-sprxpredict"></a>リアルタイム sp_rxPredict スコアリング

セットアップに必要な手順を説明**リアルタイム**予測、および T-SQL から関数を呼び出す方法の例を示します。

### <a name ="bkmk_enableRtScoring"></a> 手順 1 です。 リアルタイムのプロシージャをスコア付けを有効にします。

スコア付けに使用する各データベースに対してこの機能を有効にする必要があります。 サーバーの管理者は、RevoScaleR パッケージに含まれている RegisterRExt.exe、コマンド ライン ユーティリティを実行する必要があります。

> [!NOTE]
> リアルタイム作業得点の付け方のためには、SQL CLR の機能はインスタンスで有効にする必要があります。さらに、データベースは、trustworthy としてマークする必要があります。 スクリプトを実行するときにこれらのアクションを実行します。 ただし、これを行う前に、追加のセキュリティに影響を検討してください。

1. 管理者特権のコマンド プロンプトを開き、RegisterRExt.exe があるフォルダーに移動します。 次のパスは、既定のインストールで使用できます。
    
    `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\`

2. インスタンスと、拡張ストアド プロシージャを有効にするターゲット データベースの名前に置き換えて、次のコマンドを実行します。

    `RegisterRExt.exe /installRts [/instance:name] /database:databasename`

    たとえば、既定のインスタンス上の CLRPredict データベースに、拡張ストアド プロシージャを追加するに次のように入力します。

    `RegisterRExt.exe /installRts /database:CLRPRedict`

    インスタンス名は、データベースが既定のインスタンスにある場合は省略可能です。 名前付きインスタンスを使用している場合は、インスタンス名を指定する必要があります。

3. RegisterRExt.exe では、次のオブジェクトを作成します。

    + 信頼されたアセンブリ
    + ストアド プロシージャ `sp_rxPredict`
    + 新しいデータベース ロール、`rxpredict_users`です。 データベース管理者は、このロールを使用して、リアルタイムのスコア付けの機能を使用するユーザーに権限を与えることができます。

4. 実行する必要がある任意のユーザーを追加`sp_rxPredict`新しいロールにします。

> [!NOTE]
> 
> SQL Server 2017 で追加のセキュリティ対策は CLR 統合に関する問題を回避する実施します。 これらのメジャーは、次のストアド プロシージャの使用に関する追加の制限を強制します。 

### <a name="step-2-prepare-and-save-the-model"></a>手順 2. 準備してモデルを保存

Sp で必要なバイナリ形式\_rxPredict は、予測関数を使用して必要な形式と同じです。 そのため、R コードへの呼び出しが含まれる[rxSerializeModel](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxserializemodel)、必ずを指定して`realtimeScoringOnly = TRUE`この例のように。

```R
model <- rxSerializeModel(model.name, realtimeScoringOnly = TRUE)
```

### <a name="step-3-call-sprxpredict"></a>手順 3. 呼び出し sp_rxPredict

Sp を呼び出す\_rxPredict とすると、他のストアド プロシージャです。 現在のリリースでは、ストアド プロシージャは 2 つのパラメーターを受け取ります: _@model_バイナリ形式でモデルおよび_@inputData_ 、スコアリングに使用するデータの有効な SQL クエリとして定義されている.

バイナリ形式、PREDICT 関数によって使用される同じであるために、前の例から、モデルおよびデータ テーブルを使用できます。

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
> Sp を呼び出す\_rxPredict スコアリングのため、入力データには、モデルの要件に一致する列が含まれていない場合は失敗します。 現時点では、次の .NET データ型のみがサポートされている: float、short、ushort、double、long、ulong と文字列。
> 
> そのため、リアルタイムのスコアリングのために使用する前に、入力データでサポートされていない型を除外する必要があります。
> 
> 対応する SQL 型については、次を参照してください。 [SQL-CLR 型マッピング](https://msdn.microsoft.com/library/bb386947.aspx)または[CLR パラメーター データのマッピング](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data)です。

## <a name="disable-realtime-scoring"></a>リアルタイムのスコア付けを無効にします。

リアルタイムのスコア付けの機能を無効にするには、管理者特権のコマンド プロンプトを開きし、次のコマンドを実行します。 `RegisterRExt.exe /uninstallrts /database:<database_name> [/instance:name]`

## <a name="realtime-scoring-in-microsoft-r-server-or-machine-learning-server"></a>Microsoft R Server または Machine Learning Server スコアリング リアルタイム

Machine Learning のサーバーには、分散のリアルタイム web サービスとして公開されたモデルからスコア付けがサポートされています。 詳細については、次の記事を参照してください。

+ [Machine Learning のサーバーで web サービスとは](https://docs.microsoft.com/machine-learning-server/operationalize/concept-what-are-web-services)
+ [操作運用とは何ですか。](https://docs.microsoft.com/machine-learning-server/operationalize/concept-operationalize-deploy-consume)
+ [Azureml モデル管理 sdk web サービスとしての Python モデルを配置します。](https://docs.microsoft.com/machine-learning-server/operationalize/python/quickstart-deploy-python-web-service)
+ [新しい web サービスとしての R コード ブロックまたはリアルタイム モデルをパブリッシュします。](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/publishservice)
+ [R の mrsdeploy パッケージ](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)
