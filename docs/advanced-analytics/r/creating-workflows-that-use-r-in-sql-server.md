---
title: R - SQL Server Machine Learning Services での SSIS と SSRS のワークフローを作成します。
description: 統合シナリオが SQL Server Machine Learning サービスと R Services、Reporting Services (SSRS) と SQL Server Integration Services (SSIS) の組み合わせ。
ms.prod: sql
ms.technology: machine-learning
ms.date: 03/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 5d480b7cd24200b051fa2626fc41fa757703eaf8
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58512389"
---
# <a name="create-ssis-and-ssrs-workflows-with-r-on-sql-server"></a>SQL Server で R を使用した SSIS、SSRS のワークフローを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、2 つの重要な SQL Server 機能で SQL Server Machine Learning Services の言語とデータ サイエンスの機能を使用して、埋め込みの R と Python スクリプトを使用する方法について説明します。SQL Server Integration Services (SSIS) と SQL Server Reporting Services SSRS します。 SQL Server で R と Python のライブラリは、統計モデルと予測関数を提供します。 SSRS の SSIS と調整の ETL の変換と、視覚エフェクトをそれぞれ提供します。 この記事では、このワークフロー パターンでこれらすべての機能をまとめる方法について説明します。

> [!div class="checklist"]
> * 実行可能ファイルの R または Python を含むストアド プロシージャを作成します。
> * SSIS または SSRS からストアド プロシージャを実行します。

この記事の例では、R と、SSIS に関するほとんどの場合は、概念や手順は、Python の等しく適用されます。 2 番目のセクションは、SSRS の視覚エフェクトに関するガイダンスとリンクを提供します。

<a name="bkmk_ssis"></a> 

## <a name="use-ssis-for-automation"></a>SSIS を使用して automation

データ サイエンス ワークフローは何度も繰り返され、スケーリング、集計、確率計算、および属性の名前変更とマージなど、多くのデータ変換を含みます。 データ サイエンティストはこのようなタスクの多くを R、Python または他の言語で実行することに慣れていますが、これらのワークフローをエンタープライズ データで実行するには、ETL ツールとプロセスのシームレスな統合が必要になります。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] TRANSACT-SQL およびストアド プロシージャを使用して、R で複雑な操作を実行することができますの既存の ETL プロセスとデータ サイエンス タスクを統合することができます。 はなく一連のメモリを消費するタスクを実行するよりもデータの準備を最適化できますなど、最も効率的なツールを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]と[!INCLUDE[tsql](../../includes/tsql-md.md)]します。 

ここでは、データ処理を自動化する方法のいくつかのアイデアとモデリングのパイプラインを使用して[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:

+ オンプレミスからのデータを抽出またはトレーニング データをビルドするソース クラウド 
+ ビルドして、データ統合ワークフローの一部として R または Python モデルを実行
+ (スケジュールされた) 定期的にモデルの再トレーニングします。
+ R または Python スクリプトから結果を Excel、Power BI、Oracle、およびいくつかの名前、Teradata などの他の変換先に読み込む
+ SSIS タスクを使用して SQL database にデータの機能を作成するには
+ 条件分岐を使用して、R と Python のジョブのコンピューティング コンテキストを切り替える

## <a name="ssis-example"></a>SSIS の使用例

次の例では、作成者: Jimmy Wong この URL で、提供終了で今すぐ MSDN ブログの投稿に由来します。 `https://blogs.msdn.microsoft.com/ssis/2016/01/11/operationalize-your-machine-learning-project-using-sql-server-2016-ssis-and-r-services/`

この例では、SSIS を使用してタスクを自動化する方法を示します。 SQL Server Management Studio を使用して、埋め込まれた R を使用したストアド プロシージャを作成してから、それらのストアド プロシージャを実行し、 [T-SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task)SSIS パッケージ。

この例の手順を Management Studio、SSIS、SSIS デザイナー、パッケージのデザイン、T-SQL に慣れたにあります。 SSIS パッケージは、3 つ[T-SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-t-sql-statement-task)データのモデルや、予測の出力を取得するデータをスコア付けするトレーニング データをテーブルに挿入します。

### <a name="load-training-data"></a>トレーニング データの読み込み

データを格納するためのテーブルを作成する SQL Server Management Studio で、次のスクリプトを実行します。 作成し、この演習では、テスト データベースを使用する必要があります。 

```T-SQL
Use test-db
GO

Create table ssis_iris (
    id int not null identity primary key
    , "Sepal.Length" float not null, "Sepal.Width" float not null
    , "Petal.Length" float not null, "Petal.Width" float not null
    , "Species" varchar(100) null
);
GO
```

データ フレームにトレーニング データを読み込むストアド プロシージャを作成します。 この例は、組み込みあやめデータ セットを使用しています。 

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

SSIS デザイナーで作成、 [SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task)定義したストアド プロシージャを実行します。 スクリプトを**SQLStatement**既存のデータを削除、挿入、データを指定し、データを提供するストアド プロシージャを呼び出します。

```T-SQL
truncate table ssis_iris;
insert into ssis_iris("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")
exec dbo.load_iris;
```

![データを挿入](../media/create-workflows-using-r-in-sql-server/ssis-exec-sql-insert-data.png "データを挿入")

### <a name="generate-a-model"></a>モデルを生成します。

モデルを格納するテーブルを作成する SQL Server Management Studio で、次のスクリプトを実行します。 

```T-SQL
Use test-db
GO

Create table ssis_iris_models (
    model_name varchar(30) not null default('default model') primary key,
    model varbinary(max) not null
);
GO
```

使用して線形モデルを生成するストアド プロシージャを作成[rxLinMod](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxlinmod)します。 ライブラリをインポートする必要はありませんので、RevoScaleR と revoscalepy ライブラリは SQL Server で R と Python のセッションで自動的に使用できます。

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

SSIS デザイナーで作成、 [SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task)を実行する、 **generate_iris_rx_model**ストアド プロシージャ。 モデルでは、シリアル化され、ssis_iris_models テーブルに保存します。 スクリプトを**SQLStatement**のとおりです。

```T-SQL
insert into ssis_iris_models (model)
exec generate_iris_rx_model;
update ssis_iris_models set model_name = 'rxLinMod' where model_name = 'default model';
```

![線形モデルを生成](../media/create-workflows-using-r-in-sql-server/ssis-exec-rxlinmod.png "線形モデルを生成します。")

チェックポイントとしてこのタスクが完了すると、1 つの二項モデルが含まれていることを ssis_iris_models を照会できます。

### <a name="predict-score-outcomes-using-the-trained-model"></a>「トレーニング済み」のモデルを使用して (スコア) の結果を予測します。

手順のみを左の予測を生成するのにモデルが使用されているトレーニング データを読み込んで、モデルを生成するコードを作成したようになりました。 

これを行うには、R スクリプトを配置をトリガーする SQL クエリ、 [rxPredict](https://docs.microsoft.com//machine-learning-server/r-reference/revoscaler/rxpredict) ssis_iris_model で R の組み込み関数。 ストアド プロシージャを呼び出す**predict_species_length**このタスクを実行します。

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

SSIS デザイナーで作成、 [SQL 実行タスク](https://docs.microsoft.com/sql/integration-services/control-flow/execute-sql-task)を実行する、 **predict_species_length**ストアド プロシージャを予測花弁の長さを生成します。

```T-SQL
exec predict_species_length 'rxLinMod';
```

![予測を生成](../media/create-workflows-using-r-in-sql-server/ssis-exec-predictions.png "予測を生成")

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

この記事では、SSIS、SSRS の例では、埋め込まれた R または Python スクリプトが含まれているストアド プロシージャの実行の 2 つのケースを示しています。 重要な習得事項は、ことが利用できる R または Python スクリプトを任意のアプリケーションまたはストアド プロシージャの実行要求を送信できるツールです。 SSIS 用の他の重要なは、自動化および操作のチェーンに含まれる R または Python のデータ サイエンス機能とさまざまなデータの取得、クレンジング、操作、およびなどの操作をスケジュールするパッケージを作成することができます。 詳細とアイデアは、[SQL Server Machine Learning Services でのストアド プロシージャを使用して運用化の R コード](operationalizing-your-r-code.md)を参照してください。