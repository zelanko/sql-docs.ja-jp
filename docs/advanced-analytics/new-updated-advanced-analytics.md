---
title: "更新 - SQL Server ドキュメントの Advanced Analytics |Microsoft ドキュメント"
description: "更新されたコンテンツで最近変更したドキュメントについては、Microsoft SQL Server の高度な分析のためのスニペットを表示します。"
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 07/17/2017
ms.author: genemi
ms.workload: advanced-analytics
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79f979ecda1ff0851978d19ef28fa3cf909f9a43
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>新規または最近更新された: SQL Server の Advanced Analytics



ほとんど毎日、Microsoft は [Docs.Microsoft.com](http://docs.microsoft.com/) ドキュメント Web サイトの既存記事の一部を更新しています。 この記事では、最近更新された記事からの抜粋を示します。 新しい記事へのリンクも示される場合があります。

この記事は、定期的に再実行されるプログラムによって生成されます。 場合によっては、抜粋の形式が不完全であったり、ソース記事からのマークダウンとして表示されることがあります。 イメージはここでは表示されません。

最近の更新として次の日付範囲と対象のものが報告されます。



- *更新日の範囲:* &nbsp; **2017 年 5 月 23 日**&nbsp;から &nbsp; **2017 年 7 月 17 日**
- *サブジェクト領域:* &nbsp; **for SQL Server の Advanced Analytics**です。




&nbsp;

## <a name="new-articles-created-recently"></a>最近新しく作成された記事

以下のリンクは、最近追加された新しい記事に移動します。


1. [外部スクリプトの実行に関する一般的な問題](common-issues-external-script-execution.md)
2. [Machine Learning のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)
3. [SQL Server の Python のチュートリアル](tutorials/sql-server-python-tutorials.md)
4. [SQL Server R チュートリアル](tutorials/sql-server-r-tutorials.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>最近更新された記事の簡易一覧

この短い一覧には、抜粋のセクションに記載されているすべての更新された記事へのリンクが示されています。



&nbsp;

## <a name="updated-articles-with-excerpts"></a>更新された記事と抜粋

このセクションでは、最近大幅な更新があった記事から収集された更新の抜粋を示します。

ここで示す抜粋は、適切なセマンティック コンテキストから切り離されて表示されます。 また、実際の記事で抜粋を囲んでいる重要なマークダウン構文から切り離されていることもあります。 したがって、これらの抜粋は一般的なガイダンス専用です。 抜粋は、クリックして実際の記事を参照する価値があるかどうかを判断するためだけに使用できます。

これらおよびその他の理由から、これらの抜粋からコードをコピーしたり、テキストの抜粋を正確な情報源と考えたりしないでください。 代わりに、実際の記事を参照してください。



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-introducing-revoscalepypythonwhat-is-revoscalepymd"></a>1.&nbsp;[Revoscalepy の概要](python/what-is-revoscalepy.md)

*更新日: 2017 年 6 月 23 日* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([次へ](#TitleNum_2))

<!-- Source markdown line 112.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 cab7330ac9944508aaa360e00cbc2e866455776d 33f4e0e2421fa79fc11931dc7f29bff4432c6f5a  (PR=2171  ,  Filename=what-is-revoscalepy.md  ,  Dirpath=docs\advanced-analytics\python\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**MicrosoftML で revoscalepy の使用**


MicrosoftML の Python 関数は、計算コンテキストと revoscalepy に用意されているデータ ソースと統合されます。 したがって、MicrosoftML アルゴリズムを使用して定義し、Python でモデルをトレーニングして revoscalepy 関数を使用して、ローカルまたは SQl Server のコンピューティング コンテキストに Python コードを実行します。

だけ、Python コード内のモジュールをインポートし、必要がある個々 の関数を参照します。

```
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

**必要条件**


SQL Server での Python コードを実行する必要がありますがインストールした SQL Server 2017 機能と共に**Machine Learning サービス**、Python 言語を有効にします。 SQL Server の以前のバージョンは、Python の統合をサポートしていません。

> [!NOTE]
> Python のオープン ソース ディストリビューションは、SQL Server のコンピューティング コンテキストをサポートしていません。 ただし、発行および Windows から Python アプリケーションを使用する必要がある場合は、SQL Server をインストールしなくても、Microsoft Machine Learning のサーバーをインストールできます。 詳細については、[作成、スタンドアロン R Server--.. を参照してください。/r/create-a-standalone-r-server.md)

**詳細なヘルプを取得します。**





&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-step-5-train-and-save-a-model-using-t-sqltutorialssqldev-py5-train-and-save-a-model-using-t-sqlmd"></a>2.&nbsp;[手順 5: トレーニングと保存 T-SQL を使用して、モデル](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)

*最終更新日: 2017-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_1) | [次](#TitleNum_3))

<!-- Source markdown line 121.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c1cbe92282b96105ffdb69efa803f58dc0ac7e2 e4077a2154a90de468c435efa5b2225125d5b0e7  (PR=1904  ,  Filename=sqldev-py5-train-and-save-a-model-using-t-sql.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



1. [![SsManStudio--.. を含める/../includes/ssmanstudio-md.md)]、新しいクエリ ウィンドウを開くし、ストアド プロシージャを作成するには、次のステートメントを実行_TrainTipPredictionModelRxPy_です。  このモデルは、準備が完了したトレーニング データに基づくされます。 ストアド プロシージャには、入力データの定義が既に含まれているために、入力クエリを提供する必要はありません。

    ```SQL
    DROP PROCEDURE IF EXISTS TrainTipPredictionModelRxPy;
    GO

    CREATE PROCEDURE [dbo].[TrainTipPredictionModelRxPy] (@trained_model varbinary(max) OUTPUT)
    AS
    BEGIN
    EXEC sp_execute_external_script 
      @language = N'Python',
      @script = N'
    import numpy
    import pickle
    import pandas
    from revoscalepy.functions.RxLogit import rx_logit_ex
    
    ## Create a logistic regression model using rx_logit_ex function from revoscalepy package
    logitObj = rx_logit_ex("tipped ~ passenger_count + trip_distance + trip_time_in_secs + direct_distance", data = InputDataSet);
    
    ## Serialize model
    trained_model = pickle.dumps(logitObj)
    ',
    @input_data_1 = N'
    select tipped, fare_amount, passenger_count, trip_time_in_secs, trip_distance, 
    dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) as direct_distance
    from nyctaxi_sample_training
    ',
    @input_data_1_name = N'InputDataSet',
    @params = N'@trained_model varbinary(max) OUTPUT',
    @trained_model = @trained_model OUTPUT;
    ;
    END;
    ```



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-step-6-operationalize-the-modeltutorialssqldev-py6-operationalize-the-modelmd"></a>3.&nbsp;[手順 6: モデルを操作可能](tutorials/sqldev-py6-operationalize-the-model.md)

*最終更新日: 2017-06-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_2) | [次](#TitleNum_4))

<!-- Source markdown line 236.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1eb50ac902d4e80bafb1dd7fdf8f607dcdf0d33f 57d5abdc6119db1ecd81587d625054a5bbfb5fc8  (PR=1904  ,  Filename=sqldev-py6-operationalize-the-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=dbf91e0d6f8257227cfe8ac6d13c484d0a566f57) -->



使用してスコア付けを実行するストアド プロシージャの定義をここでは、 **revoscalepy**モデル。

```
CREATE PROCEDURE [dbo].[PredictTipSingleModeRxPy] (@model varchar(50), @passenger_count int = 0,
  @trip_distance float = 0,
  @trip_time_in_secs int = 0,
  @pickup_latitude float = 0,
  @pickup_longitude float = 0,
  @dropoff_latitude float = 0,
  @dropoff_longitude float = 0)
AS
BEGIN
  DECLARE @inquery nvarchar(max) = N'
    SELECT * FROM [dbo].[fnEngineerFeatures-- 
      @passenger_count,
      @trip_distance,
      @trip_time_in_secs,
      @pickup_latitude,
      @pickup_longitude,
      @dropoff_latitude,
      @dropoff_longitude)
    '
  DECLARE @lmodel2 varbinary(max) = (select model from nyc_taxi_models2 where name = @model);
  EXEC sp_execute_external_script 
    @language = N'Python',
    @script = N'
      import pickle;
      import numpy;
      import pandas;
      from revoscalepy.functions.RxPredict import rx_predict_ex;
```




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-use-python-with-revoscalepy-to-create-a-modeltutorialsuse-python-revoscalepy-to-create-modelmd"></a>4.&nbsp;[モデルを作成する revoscalepy での Python の使用](tutorials/use-python-revoscalepy-to-create-model.md)

*最終更新日: 2017-06-21* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([以前](#TitleNum_3))

<!-- Source markdown line 119.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0886939f86fe12d7ff7b339689a02c7fc75e0786 23dd469349a05d535063aab3c14aec152ed2cd7b  (PR=2141  ,  Filename=use-python-revoscalepy-to-create-model.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=76839e39427e24688609353b8708d59fee772d28) -->



**コードを確認します。**


コードを確認し、いくつかの主要手順を強調表示してみましょう。

**ソースのデータの定義と計算コンテキスト**


これを使用する重要な部分は、 **revoscalepy**とその関連の R パッケージ**RevoScaleR**です。 データ ソースは、計算コンテキストと異なります。 _データソース_コードで使用されるデータを定義します。 _計算コンテキスト_コードを実行する場所を定義します。

> [!NOTE]
> RevoScaleR でサポートされるデータ ソースの種類によってのサポートは、リリース前のバージョンに制限があります。 最新のリリースに含まれる関数の詳細については、[は revoscalepy--.. を参照してください。/python/what-is-revoscalepy.md)。

全体的なを作成すると、データ ソースを使用して処理し、コンテキストは、次のように計算。

1. など、Python 変数の作成_sqlQuery_と_connectionString_ソースとを使用するデータを定義します。 これらの変数を渡す、 **RxSqlServerData**コンス トラクターを実装する、**データ ソース オブジェクト**という名前_データソース_です。
2. 使用してコンピューティング コンテキスト オブジェクトを作成、 **RxInSqlServer**コンス トラクターです。 この例では、計算コンテキストとして使用する同じ SQL Server インスタンスにデータがあることを前提に以前に定義された同じ接続文字列を渡します。 ただし、データ ソースと計算コンテキストが別のサーバーになります。 生成される**コンテキスト オブジェクトをコンピューティング**という_computeContext_です。
3. アクティブなコンピューティング コンテキストを選択します。 既定では、操作はつまり、異なるコンピューティング コンテキストを指定しない場合は、ローカルで実行されます、データ ソースからデータをフェッチする、およびモデルの調整は、現在の Python 環境で実行されます。

    RevoScaleR で、関数を使用することも`rxSetComputeContext`計算コンテキストの切り替えにします。 プレビュー バージョンで、関数はまだ実装されていない**revoscalepy**への引数としてコンピューティング コンテキストを指定できますが、 **rx_lin_mod_ex**です。





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>類似した記事

このセクションでは、同じ GitHub.com リポジトリ [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/) 内の他の対象領域の記事で、この対象領域において最近更新された記事とよく似たものの一覧を示します。

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のある対象領域

- [新規 + 更新 (4 + 4): **SQL の Advanced Analytics** に関するドキュメント](../advanced-analytics/new-updated-advanced-analytics.md)
- [新規 + 更新 (2 + 0): **SQL の Analysis Services** に関するドキュメント](../analysis-services/new-updated-analysis-services.md)
- [新規 + 更新 (1 + 2): **SQL への接続**に関するドキュメント](../connect/new-updated-connect.md)
- [新規 + 更新 (6 + 0): **SQL のデータベース エンジン**に関するドキュメント](../database-engine/new-updated-database-engine.md)
- [新規 + 更新 (13 + 2): **SQL 用の Linux** に関するドキュメント](../linux/new-updated-linux.md)
- [新規 + 更新 (1 + 0): **SQL のマスター データ サービス (MDS)** に関するドキュメント](../master-data-services/new-updated-master-data-services.md)
- [新規 + 更新 (1 + 0): **SQL の ODBC (Open Database Connectivity)** に関するドキュメント](../odbc/new-updated-odbc.md)
- [新規 + 更新 (8 + 4): **SQL のリレーショナル データベース**に関するドキュメント](../relational-databases/new-updated-relational-databases.md)
- [新規 + 更新 (2 + 2): **Microsoft SQL Server** に関するドキュメント](../sql-server/new-updated-sql-server.md)
- [新規 + 更新 (0 + 1): **SQL Server Management Studio (SSMS)** に関するドキュメント](../ssms/new-updated-ssms.md)
- [新規 + 更新 (1 + 0): **Transact-SQL** に関するドキュメント](../t-sql/new-updated-t-sql.md)
- [新規 + 更新 (1 + 0): **SQL 用のツール**に関するドキュメント](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>新しい記事または最近更新された記事のない対象領域

- [新規 + 更新 (0 + 0): **SQL の ActiveX データ オブジェクト (ADO)** に関するドキュメント](../ado/new-updated-ado.md)
- [新規 + 更新 (0 + 0): **SQL の Data Quality Services** に関するドキュメント](../data-quality-services/new-updated-data-quality-services.md)
- [新規 + 更新 (0 + 0): **SQL のデータ マイニング拡張機能 (DMX)** に関するドキュメント](../dmx/new-updated-dmx.md)
- [新規 + 更新 (0 + 0): **SQL の Integration Services** に関するドキュメント](../integration-services/new-updated-integration-services.md)
- [新規 + 更新 (0 + 0): **SQL の多次元式 (MDX)** に関するドキュメント](../mdx/new-updated-mdx.md)
- [新規 + 更新 (0 + 0): **SQL の PowerShell** に関するドキュメント](../powershell/new-updated-powershell.md)
- [新規 + 更新 (0 + 0): **SQL の Reporting Services** に関するドキュメント](../reporting-services/new-updated-reporting-services.md)
- [新規 + 更新 (0 + 0): **SQL のサンプル**に関するドキュメント](../sample/new-updated-sample.md)
- [新規 + 更新 (0 + 0): **SQL Server Data Tools (SSDT)** に関するドキュメント](../ssdt/new-updated-ssdt.md)
- [新規 + 更新 (0 + 0): **SQL Server Migration Assistant (SSMA)** に関するドキュメント](../ssma/new-updated-ssma.md)
- [新規 + 更新 (0 + 0): **SQL の XQuery** に関するドキュメント](../xquery/new-updated-xquery.md)


&nbsp;


