---
title: R - SQL Server Machine Learning Services での SSIS と SSRS のワークフローを作成します。
description: 統合シナリオが SQL Server Machine Learning サービスと R Services、Reporting Services (SSRS) と SQL Server Integration Services (SSIS) の組み合わせ。
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/15/2019
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 76ddf3e3fdb43fea6bb8fd224f8199cda4134b64
ms.sourcegitcommit: e9fcd10c7eb87a4f09ac2d8f7647018e83a5f5c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2019
ms.locfileid: "57976302"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>SQL Server で R を使用した SSIS、SSRS のワークフローを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、Microsoft R ライブラリからのデータ サイエンスの職務、リレーショナル データを結合する方法で重要な 2 つの SQL Server 機能、SQL Server Integration Services (SSIS)、および SQL Server Reporting Services SSRS、ストアド プロシージャを使用する方法を説明しますおよび調整されたデータの変換および視覚エフェクトの BI 機能。 機能について説明します[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]データ サイエンスのソリューションに適しています。 この記事も通知コードと SQL Server で、ストアド プロシージャに埋め込まれた R コードなどのデータがで提供される視覚エフェクトでは利用しやすいこと[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]します。

## <a name="bring-compute-power-to-the-data"></a>データにコンピューティング能力をもたらす

SQL Server で R と Python の統合の主要な設計目標は、分析データの近くにするようにしています。 これは、複数の利点を提供します。

+ データのセキュリティ。 データのソースを R に近い場所を使えるように無駄や安全でないデータ移動を回避できます。
+ 速さ。 データベースは、セットベースの操作用に最適化されています。 インメモリ テーブルなどのデータベースの最新技術の概要と集計、処理が非常を行い、データ サイエンスを補完します。
+ 展開との統合が容易。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] その他の多くのデータ管理タスクやアプリケーションの操作のサーバーの全体のポイントです。 レポート ウェアハウスまたはデータベースに存在するデータを使用すると、機械学習ソリューションによって使用されるデータが一貫して最新の状態であることを確認します。 
+ クラウドとオンプレミス間の効率。 R でデータを処理する代わりに、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] や Azure Data Factory などのエンタープライズ データ パイプラインに依存できます。 Power BI や [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を使用して、結果や分析を簡単にレポートできます。

さまざまなデータ処理や分析タスクで SQL と R を正しく組み合わて使用することで、データ サイエンティストと開発者の両方の生産性がさらに向上します。

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-data-transformation-and-automation"></a>データ変換と自動化のための SSIS を使用します。

データ サイエンス ワークフローは何度も繰り返され、スケーリング、集計、確率計算、および属性の名前変更とマージなど、多くのデータ変換を含みます。 データ サイエンティストはこのようなタスクの多くを R、Python または他の言語で実行することに慣れていますが、これらのワークフローをエンタープライズ データで実行するには、ETL ツールとプロセスのシームレスな統合が必要になります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では Transact-SQL とストアド プロシージャを介して R で複雑な操作を実行できるため、再開発の最小限の作業も行わずに、既存の ETL プロセスに R 固有のタスクを統合できます。 はなく一連のメモリを消費するタスクを実行すると、R よりもデータの準備を最適化できますなど、最も効率的なツールを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]と[!INCLUDE[tsql](../../includes/tsql-md.md)]します。 

ここでは、データ処理を自動化する方法のいくつかのアイデアとモデリングのパイプラインを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ 使用[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]SQL データベースに必要なデータ特徴を作成するタスク
+ 条件分岐を使用して、R ジョブの計算コンテキストを切り替える。
+ データベースに独自のデータを生成する R ジョブを実行し、アプリケーションとそのデータを共有
+ 使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、R スクリプトのテキストの変数に保存されたを読み込むし、SQL Server で実行

## <a name="ssis-example"></a>SSIS の使用例

作成者: Jimmy Wong この URL で、提供終了で今すぐ MSDN ブログの投稿から次の例の発生元:`https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`します。

この例では、SSIS を使用してタスクを自動化する方法を示します。 SQL Server Management Studio を使用して、埋め込まれた R を使用したストアド プロシージャを作成してから、それらのストアド プロシージャを実行し、 [T-SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task)SSIS パッケージ。

この例の手順を Management Studio、SSIS、SSIS デザイナー、パッケージのデザイン、T-SQL に慣れたにあります。 SSIS パッケージは、3 つ[T-SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task)データのモデルや、予測の出力を取得するデータをスコア付けするトレーニング データをテーブルに挿入します。

### <a name="create-tables"></a>テーブルの作成

いくつかのテーブルを作成する SQL Server Management Studio で、次のスクリプトを実行します。 データとモデルを格納する別の格納に 1 つ。 Ssis_iris テーブルの役割では、運用化のシナリオでのトレーニング データとして機能です。 

```T-SQL
Use irissql
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

### <a name="create-a-stored-procedure-that-loads-training-data"></a>トレーニング データを読み込むストアド プロシージャを作成します。

このスクリプトは、組み込みの R のデータ セットを使用してデータ フレームに Iris を読み込むストアド プロシージャを作成します。

```T-SQL
Create procedure load_iris
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'iris_df <- iris;'
        , @input_data_1 = N''
        , @output_data_1_name = N'iris_df'
    with result sets (("Sepal.Length" float not null, "Sepal.Width" float not null, "Petal.Length" float not null, "Petal.Width" float not null, "Species" varchar(100)));
end;
```

### <a name="define-an-execute-sql-task-that-refreshes-the-model"></a>モデルを更新する SQL 実行タスクを定義します。

SSIS デザイナーで作成、 [SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task)します。

![データを挿入](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "データを挿入")

[Sqlstatement] のスクリプトは次のとおりです。 スクリプトは、既存のデータが削除されから新しいデータを使用して、再読み込み、 **load_iris**前の手順で作成されるストアド プロシージャ。

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

### <a name="create-a-stored-procedure-that-generates-a-model"></a>モデルを生成するストアド プロシージャを作成します。

このストアド プロシージャを使用して線形モデルを作成するコードは、 [rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)します。 RevoScaleR と revoscalepy ライブラリは SQL Server で R と Python のセッションで自動的に読み込まれます。

```T-SQL
Create procedure generate_iris_rx_model
as
begin
    execute sp_execute_external_script
        @language = N'R'
        , @script = N'
          irisLinMod <- rxLinMod(Sepal.Length ~ Sepal.Width + Petal.Length + Petal.Width + Species, data = ssis_iris);
          trained_model <- data.frame(payload = as.raw(serialize(irisLinMod, connection=NULL)));'
        , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris'
        , @input_data_1_name = N'ssis_iris'
        , @output_data_1_name = N'trained_model'
    with result sets ((model varbinary(max)));
end;
GO
```

### <a name="define-an-execute-sql-task-that-runs-the-model-generation-stored-procedure"></a>モデル生成のストアド プロシージャを実行する SQL 実行タスクを定義します。

この手順で[SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task)実行、 **generate_iris_rx_model**ストアド プロシージャをモデルの作成と ssis_iris_models テーブルに挿入します。

![線形モデルを生成](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "線形モデルを生成します。")

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

このタスクが完了したら後、は、1 つの二項モデルが含まれていることを ssis_iris_models を照会できます。

### <a name="predict-score-outcomes-using-the-trained-model"></a>「トレーニング済み」のモデルを使用して (スコア) の結果を予測します。

この単純な例では、という前提はその ssis_iris_model はトレーニング済みのモデルです。 トレーニング済みモデルの目的は、予測を生成するが後、は、私たちを使用して予測を実行する準備ができました。 

これを行うには、R スクリプトを配置をトリガーする SQL クエリ、 [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) ssis_iris_model で R の組み込み関数。 SQL Server のストアド プロシージャと呼ばれる**predict_species_length**このタスクを実行します。

```T-SQL
Create procedure predict_species_length (@model varchar(100))
as
begin
    declare @rx_model varbinary(max) = (select model from ssis_iris_models where model_name = @model);
    -- Predict based on the specified model:
    exec sp_execute_external_script
        @language = N'R'
        , @script = N'
irismodel <-unserialize(rx_model);
irispred <- rxPredict(irismodel, ssis_iris[,2:6]);
OutputDataSet <- cbind(ssis_iris[1], irispred$Sepal.Length_Pred, ssis_iris[2]);
colnames(OutputDataSet) <- c("id", "Sepal.Length.Actual", "Sepal.Length.Expected");
#OutputDataSet <- subset(OutputDataSet, Species.Length.Actual != Species.Expected);
'
    , @input_data_1 = N'
    select id, "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from ssis_iris
    '
    , @input_data_1_name = N'ssis_iris'
    , @params = N'@rx_model varbinary(max)'
    , @rx_model = @rx_model
    with result sets ( ("id" int, "Species.Length.Actual" float, "Species.Length.Expected" float)
        );
end;
```

### <a name="define-an-execute-sql-task-that-predicts-outcomes"></a>結果を予測する SQL 実行タスクを定義します。

使用して[SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task)、実行、 **predict_species_length**ストアド プロシージャを予測花弁の長さを生成します。

![予測を生成](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "予測を生成")

```T-SQL
exec predict_species_length 'rxLinMod';
```

### <a name="run-the-solution"></a>ソリューションを実行します。

SSIS デザイナーで f5 キーを押して、パッケージを実行します。 次のスクリーン ショットのような結果が表示されます。

![F5 キーを押してデバッグ モードで実行する](../media/create-workflows-using-r-in-sql-server/ssis-exec-F5-run.png "f5 キーを押してデバッグ モードで実行するには")

<a name="bkmk_ssrs"></a> 

## <a name="use-ssrs-for-visualizations"></a>SSRS を使用して、視覚エフェクト

R には、グラフの興味のある視覚化を作成できます、つまり各チャートまたはグラフを個別に生成するのには、外部データ ソースで適切に統合されたことはありません。 共有も困難な可能性があります。

使用して[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]、を介して R で複雑な操作を実行する[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャで、さまざまなエンタープライズ レポートなどのツールで簡単に使用できる[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と Power BI です。

### <a name="ssrs-example"></a>SSRS の例

[R Graphics Device for Microsoft Reporting Services (SSRS)](https://rgraphicsdevice.codeplex.com/) (Microsoft Reporting Services (SSRS) 用の R グラフィックス デバイス)

この CodePlex プロジェクトを提供するカスタム レポート アイテムを作成するために、コードで使用できるイメージとしての R のグラフィックス出力をレンダリングする[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]レポートします。  カスタム レポート アイテムを使用すると、次の操作を実行できます。

+ R グラフィックス デバイスを使用して作成したグラフとプロットを [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ダッシュボードに公開する

+ [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] パラメーターを R プロットに渡す

> [!NOTE]
> このサンプルでは、Reporting Services サーバー、および Visual Studio で、Reporting Services の R グラフィックス デバイスをサポートするコードをインストールする必要があります。 手動によるコンパイルと構成も必要です。

## <a name="next-steps"></a>次のステップ

この記事では、SSIS、SSRS の例では、埋め込まれた R または Python スクリプトが含まれているストアド プロシージャの実行の 2 つのケースを示しています。 重要な習得事項は、ことが利用できる R または Python スクリプトを任意のアプリケーションまたはストアド プロシージャの実行要求を送信できるツールです。 SSIS 用の他の重要なは、自動化および操作のチェーンに含まれる R または Python のデータ サイエンス機能とさまざまなデータの取得、クレンジング、操作、およびなどの操作をスケジュールするパッケージを作成することができます。 詳細とアイデアは、次を参照してください。 [SQL Server Machine Learning Services でのストアド プロシージャを使用して運用化の R コード](operationalizing-your-r-code.md)します。