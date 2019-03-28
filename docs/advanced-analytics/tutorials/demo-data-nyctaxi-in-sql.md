---
title: 埋め込みの R と Python の SQL Server Machine Learning の NYC タクシーのデモ データとスクリプトをダウンロードします。
description: ニューヨーク市タクシーのサンプル データをダウンロードして、データベースの作成の手順です。 データは、SQL Server のストアド プロシージャおよび T-SQL 関数のスクリプトを埋め込む方法を示す SQL Server の Python および R 言語のチュートリアルで使用されます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/31/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 502f46b67dbf282a7b3daeac76882915a7c3ac84
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511769"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>NYC タクシーのデモ データの SQL Server の Python および R のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事からパブリック データで構成されるサンプル データベースを設定する方法を説明します、[ニューヨーク市タクシーのデータセットとリムジン委員会](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)します。 このデータは、SQL server データベース内分析のためのいくつかの R と Python のチュートリアルで使用されます。 サンプル コードをすばやく実行するためには、データの代表的な 1% のサンプリングを作成しました。 システム データベースのバックアップ ファイルはわずか 90 MB、170万主データ テーブルの行を提供することです。

この手順を完了しておく[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)またはデータベースのバックアップ ファイルを復元して T-SQL クエリを実行できる他のツール。

チュートリアルとクイック スタートのこのデータ セットを使用して、次に示します。

+ [SQL Server で R を使用してデータベース内分析について説明します](sqldev-in-database-r-for-sql-developers.md)
+ [SQL Server で Python を使ってデータベース内分析について説明します](sqldev-in-database-python-for-sql-developers.md)

## <a name="download-files"></a>ファイルをダウンロードします。

サンプル データベースは、Microsoft によってホストされている SQL Server 2016 BAK ファイルです。 SQL Server 2016 以降復元することができます。 ファイルのダウンロードは、リンクをクリックするとすぐに開始します。 

ファイル サイズは約 90 MB です。

1. クリックして[NYCTaxi_Sample.bak](https://sqlmldoccontent.blob.core.windows.net/sqlml/NYCTaxi_Sample.bak)データベース バックアップ ファイルをダウンロードします。

2. C:\Program files \microsoft SQL server \mssql インスタンス name\MSSQL\Backup フォルダーにファイルをコピーします。

3. Management Studio で、右クリックして**データベース**選択と**復元ファイルおよびファイル グループ**します。

4. 入力*NYCTaxi_Sample*としてデータベース名。

5. クリックして**デバイスから**し、バックアップ ファイルを選択するファイルの選択 ページを開きます。 クリックして**追加**NYCTaxi_Sample.bak を選択します。

6. 選択、**復元**チェック ボックスをオン をクリック**OK**データベースを復元します。

## <a name="review-database-objects"></a>データベース オブジェクトを確認してください。
   
データベース オブジェクトに存在することを確認、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 データベース、テーブル、関数、およびストアド プロシージャを参照する必要があります。
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

### <a name="objects-in-nyctaxisample-database"></a>NYCTaxi_Sample データベース内のオブジェクト

次の表では、NYC タクシーのデモ データベースで作成されたオブジェクトをまとめたものです。

|**オブジェクト名です。**|**オブジェクトの種類**|**[説明]**|
|----------|------------------------|---------------|
|**NYCTaxi_Sample** | [データベース] | データベースと 2 つのテーブルを作成します。<br /><br />dbo.nyctaxi_sample テーブル:メインの NYC タクシー データセットが含まれています。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルは、このテーブルに挿入されます。<br /><br />dbo.nyc_taxi_models テーブル:トレーニング済みの高度な分析モデルを保持するために使用します。|
|**fnCalculateDistance** |スカラー値関数 (scalar-valued function) | 乗車と降車場所間の直線距離を計算します。 この関数が使用される[データ機能を作成](sqldev-create-data-features-using-t-sql.md)、[トレーニング、モデルを保存および](sqldev-train-and-save-a-model-using-t-sql.md)と[R モデルを運用する](sqldev-operationalize-the-model.md)。|
|**fnEngineerFeatures** |テーブル値関数 (table-valued function) | モデルのトレーニング用の新しいデータ機能を作成します。 この関数で使用[データ機能を作成](sqldev-create-data-features-using-t-sql.md)と[R モデルを運用する](sqldev-operationalize-the-model.md)します。|


ストアド プロシージャは、さまざまなチュートリアルについては、R と Python スクリプトを使用して作成されます。 次の表では、さまざまなレッスンからスクリプトを実行すると、NYC タクシーのデモ データベースに追加できる必要に応じてストアド プロシージャをまとめたものです。

|**ストアド プロシージャ**|**言語**|**[説明]**|
|-------------------------|------------|---------------|
|**RxPlotHistogram** |R | 変数のヒストグラムをプロットする RevoScaleR rxHistogram 関数を呼び出すし、バイナリ オブジェクトとしてプロットを返します。 このストアド プロシージャが使用される[の探索し、視覚化データ](sqldev-explore-and-visualize-the-data.md)します。|
|**RPlotRHist** |R| Hist 関数を使用してグラフィックを作成し、出力をローカル PDF ファイルとして保存します。 このストアド プロシージャが使用される[の探索し、視覚化データ](sqldev-explore-and-visualize-the-data.md)します。|
|**RxTrainLogitModel**  |R| R パッケージを呼び出すことによって、ロジスティック回帰モデルをトレーニングします。 モデルは、tipped 列の値を予測し、ランダムに選択した 70% のデータを使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。 このストアド プロシージャが使用される[トレーニング、モデルを保存および](sqldev-train-and-save-a-model-using-t-sql.md)します。|
|**RxPredictBatchOutput**  |R | モデルを使用して予測を作成するトレーニング済みモデルを呼び出します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。 このストアド プロシージャがで使用される[潜在的な結果を予測](sqldev-operationalize-the-model.md)します。|
|**RxPredictSingleRow**  |R| モデルを使用して予測を作成するトレーニング済みモデルを呼び出します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。 このストアド プロシージャがで使用される[潜在的な結果を予測](sqldev-operationalize-the-model.md)します。|

## <a name="query-the-data"></a>データのクエリ

検証手順として、データがアップロードされたことを確認するためのクエリを実行します。

1. データベースのオブジェクト エクスプ ローラーで右クリックし、 **NYCTaxi_Sample**データベース、および新しいクエリを開始します。

2. シンプルなクエリを実行します。

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
データベースには、1.7 100万行が含まれています。

3. データベース内では、 **nyctaxi_sample**データ セットを含むテーブル。 テーブルは、追加すると、セットベースの計算に対して最適化されている、[列ストア インデックス](../../relational-databases/indexes/columnstore-indexes-overview.md)します。 テーブルの簡単な概要を生成するには、このステートメントを実行します。

    ```sql
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
結果は、次のスクリーン ショットで示すものにするようになります。

  ![テーブルの概要情報](media/nyctaxidatatablesummary.png "クエリの結果")

## <a name="next-steps"></a>次のステップ

NYC タクシーのサンプル データは、実践的な学習をご利用いただけます。

+ [SQL Server で R を使用してデータベース内分析について説明します](sqldev-in-database-r-for-sql-developers.md)
+ [SQL Server で Python を使ってデータベース内分析について説明します](sqldev-in-database-python-for-sql-developers.md)