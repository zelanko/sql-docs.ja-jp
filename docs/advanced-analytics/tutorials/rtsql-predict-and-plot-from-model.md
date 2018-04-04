---
title: 予測し、モデル (SQL のクイック スタートで R) からプロット |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/20/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
dev_langs:
- R
- SQL
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: b30c2443b8b1532d008e717e1b86fdb62adbe0a1
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="predict-and-plot-from-model-r-in-sql-quickstart"></a>予測は、モデル (SQL のクイック スタートで R) から
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

実行する_スコアリング_新しいデータを使用して、トレーニング済みモデルの 1 つ、テーブルから取得し、新しい予測を基になるデータのセットを呼び出します。 スコアリングは、予測、確率、またはトレーニング済みモデルに渡す新しいデータに基づくその他の値を生成することを意味するデータ サイエンスでときどき使わ用語です。

## <a name="create-the-table-of-new-speeds"></a>新しい速度のテーブルを作成する

元のトレーニング データの速度が時速 25 マイルで止まっていることに気づきましたか。 これは元のデータが 1920 年の実験に基づいていたためです。

時速 60 マイルあるいは時速 100 マイルまで速度を出すことができた場合、1920 年代の自動車が停止するまでにどれくらいかかるか知りたくありませんか。 この質問に答えるには、新しい速度値を指定する必要があります。

```sql
CREATE TABLE [dbo].[NewCarSpeed]([speed] [int] NOT NULL,
    [distance] [int]  NULL) ON [PRIMARY]
GO
INSERT [dbo].[NewCarSpeed] (speed)
VALUES (40),  (50),  (60), (70), (80), (90), (100)
```

## <a name="predict-stopping-distance"></a>停止距離を予測する

これまでに、テーブルには複数の R モデルが含まれています。それぞれ異なるパラメーターまたはアルゴリズムを使用して構築されるか、異なるデータのサブセットに対してトレーニングされています。

![rsql_basictut_listofmodels](media/rsql-basictut-listofmodels.png)

1 つの特定のモデルに基づく予測を取得するには、SQL スクリプトは、次の操作を記述する必要があります。

1. 必要なモデルを取得します。
2. 新しい入力データを取得します。
3. そのモデルと互換性がある R 予測関数を呼び出します。

この例では、モデルに基づいているため、 **rxLinMod**の一部として提供されているアルゴリズム、 **RevoScaleR** 、パッケージを呼び出す、 [rxPredict](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxpredict)関数ではなく、汎用的な R`predict`関数。

```sql
DECLARE @speedmodel varbinary(max) = (SELECT model FROM [dbo].[stopping_distance_models] WHERE model_name = 'latest model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            str(predicted.distance);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT speed FROM [dbo].[NewCarSpeed] '
    , @input_data_1_name = N'NewCarData'
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ SELECT ステートメントを使用して、テーブルから 1 つのモデルを取得し、それを入力パラメーターとして渡します。
+  テーブルからモデルを取得したら、モデルに対して `unserialize` 関数を呼び出します。

    > [!TIP] 
    > ご覧新しい[シリアル化機能が](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxserializemodel)をサポートする RevoScaleR、によって提供される[リアルタイム スコアリング](../../advanced-analytics/real-time-scoring.md)です。
+  適切な引数を使用して `rxPredict` 関数をモデルに適用し、新しい入力データを提供します。
+  この例で、 `str` R. から返されるデータのスキーマを確認する、テスト段階で関数を追加後でステートメントを削除することができます。
+ R スクリプトで使用する列名は、ストアド プロシージャの出力に必ずしもは渡されません。 ここで新しい列名を定義するのにと結果の句を使用しました。

**結果**

![rsql_basictut_scoringresults_smalldata](media/rsql-basictut-scoringresults-smalldata.PNG)

## <a name="perform-scoring-in-parallel"></a>スコア付けを並列で実行する

この小さなデータ セットでは予測はすぐに戻されます。 しかし、大量の予測を非常に高速で行う必要がある場合はどうでしょうか。 方法は多数あります速度を向上させる SQL Server での操作に多くの場合は、操作を並列に処理できることができます。 特にスコア付けに関して簡単にできる方法の 1 つは *@parallel* パラメーターを `sp_execute_external_script` に追加して、値を **1** に設定することです。

自動車の速度の数十万個の値を含む大きなテーブルがあるとします。 コミュニティには多くのサンプル T-SQL スクリプトがあり、多数のテーブルの生成に役立ちます。そのため、ここではそれらを掲載しません。 たとえば、多くの整数を含む 1 つの列があり、モデルの `speed` の入力としてそれを使用する場合です。

これを行うには、同じ予測クエリを実行してより大きなデータセットを置き換えるし、のみを追加、`@parallel = 1`引数。

```sql
DECLARE @speedmodel varbinary(max) = (select model from [dbo].[stopping_distance_models] where model_name = 'default model');
EXEC sp_execute_external_script
    @language = N'R'
    , @script = N'
            current_model <- unserialize(as.raw(speedmodel));
            new <- data.frame(NewCarData);
            predicted.distance <- rxPredict(current_model, new);
            OutputDataSet <- cbind(new, ceiling(predicted.distance));
            '
    , @input_data_1 = N' SELECT [speed] FROM [dbo].[HugeTableofCarSpeeds] '
    , @input_data_1_name = N'NewCarData'
    , @parallel = 1
    , @params = N'@speedmodel varbinary(max)'
    , @speedmodel = @speedmodel
WITH RESULT SETS (([new_speed] INT, [predicted_distance] INT))
```

+ 並列実行は、非常に大きなデータを扱う場合にのみ、通常の利点を提供します。 SQL データベース エンジンは、並列実行は不要であることができます。 また、データを取得する SQL クエリには、並列クエリ プランを生成する機能があることが必要です。

+ 並列実行のオプションを使用するときは、WITH RESULT SETS 句を使用して、前もって出力結果スキーマを指定する**必要があります**。 事前に出力スキーマを指定すると、SQL Server が複数の並列データセットの結果を集計できます。指定しないと、不明なスキーマが生成されることになります。

+ 場合*トレーニング*の代わりに、モデル*スコアリング*、このパラメーターは多くの場合、特殊効果を必要はありません。 モデルの種類によって異なりますが、モデルの作成では、概要を作成する前にすべての行を読み取る必要があります。

+ モデルのトレーニングを行うときに、並列処理の利点を取得することをお勧めのいずれかを使用すること、 **RevoScaleR**アルゴリズムです。 指定しない場合でも、これらのアルゴリズムが、自動的に処理を配布するよう設計されて<code>@parallel =1</code>への呼び出しで`sp_execute_external_script`です。 RevoScaleR アルゴリズムに最適なパフォーマンスを取得する方法についてのガイダンスについては、次を参照してください。[分散し、Microsoft R で ScaleR で並列コンピューティング](https://docs.microsoft.com/r-server/r/how-to-revoscaler-distributed-computing)です。

## <a name="create-an-r-plot-of-the-model"></a>モデルの R プロットを作成する

SQL Server Management Studio を含む多くのクライアントは、[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)を使用して作成されたプロットを直接表示できません。 代わりに、R プロットを生成するための一般的なプロセスは、R コードの一部として、プロットを作成し、イメージをファイルに書き込むにです。

また、イメージを表示できるすべてのアプリケーションにシリアル化されたバイナリ プロット オブジェクトを取得できます。

次の例は、既定で R に含まれるプロット関数を使用して単純なグラフィックを作成する方法を示します。イメージは指定したファイルに出力され、ストアド プロシージャによって SQL 変数にも出力されます。

```sql
 EXECUTE sp_execute_external_script
 @language = N'R'
 , @script = N'
     imageDir <- ''C:\\temp\\plots'';
     image_filename = tempfile(pattern = "plot_", tmpdir = imageDir, fileext = ".jpg")
     print(image_filename);
     jpeg(filename=image_filename,  width=600, height = 800);
     print(plot(distance~speed, data=InputDataSet, xlab="Speed", ylab="Stopping distance", main = "1920 Car Safety"));
     abline(lm(distance~speed, data = InputDataSet));
     dev.off();
     OutputDataSet <- data.frame(data=readBin(file(image_filename, "rb"), what=raw(), n=1e6));
     '
  , @input_data_1 = N'SELECT speed, distance from [dbo].[CarSpeed]'
  WITH RESULT SETS ((plot varbinary(max)));
```

+ `tempfile`関数は、ファイル名として使用できる文字列を返しますが、ファイルがまだ生成されています。
+ 引数の`tempfile`プレフィックスとファイル拡張機能だけでなく、ディレクトリを指定することができます。 パスとファイルの完全な名前を確認するための印刷を使用してメッセージ`str()`です。
+ `jpeg` 関数は、指定したパラメーターで R デバイスを作成します。
+ プロットを作成した後により多くのビジュアル機能を追加できます。 この場合、回帰直線が追加を使用して`abline`です。
+ プロットへの機能の追加が終了したら、`dev.off()` 関数を使用してグラフィック デバイスを閉じる必要があります。
+ `readBin` 関数は、読み取るファイル、形式指定、およびレコード数を受け取ります。 `rb`* * ' キーワードは、ファイルがテキストではなくバイナリであることを示します。

**結果**

![rsql_basictut_plotresult_small](media/rsql-basictut-plotresult-small.png)

R 用の優れたグラフィックス パッケージを使用して、もっと複雑なプロットを作成する必要がある場合には、次の記事を参照することをお勧めします。 どちらでも、広く使用されている **ggplot2** パッケージが必要です。

+ [SQL Server 2016 R Services を使用したローンの分類](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/09/27/loan-classification-using-sql-server-2016-r-services/): 保険データに基づいたエンド ツー エンドのシナリオ。 必要があります、**変形**パッケージです。
+ [グラフと R を使用してプロットを作成します。](../../advanced-analytics/tutorials/walkthrough-create-graphs-and-plots-using-r.md)

## <a name="conclusions"></a>結論

R と SQL Server の統合により、規模を拡大して R ソリューションを配置しやすくなり、高パフォーマンスのデータ処理および高速 R 分析のために、R とリレーショナル データベースの優れた機能を活用できます。 

R サンプルの詳細については、これらの追加リソースを参照してください。

+  [SQL Server R チュートリアル](../../advanced-analytics/tutorials/sql-server-r-tutorials.md)

    Microsoft データ サイエンスと R サービスの開発チームによって作成されたエンド ツー エンドのシナリオを SQL Server で R を使用したソリューションの学習を継続します。

+ [SQL Server の Python のチュートリアル](../../advanced-analytics/tutorials/sql-server-python-tutorials.md)

    SQL Server 2017、Python 言語とリモート計算コンテキストとスケーラブルなアルゴリズムの電源を使用します。

+ [チュートリアルおよび Microsoft R のサンプル データ](https://docs.microsoft.com/r-server/r/tutorial-introduction)

    新しい RevoScaleR パッケージを使用してモデルを作成し、データを変換する方法を説明します。

+ [MicrosoftML を概要します。](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

    高速でスケーラブルな機械学習 Microsoft Research からのアルゴリズムの詳細を表示します。
