---
title: R と Python (SQL Server Machine Learning) の埋め込みの NYC タクシーのデモ データとスクリプトのダウンロード |Microsoft Docs
description: ニューヨーク市タクシーのサンプル データをダウンロードして、データベースの作成の手順です。 データは、SQL Server のストアド プロシージャおよび T-SQL 関数のスクリプトを埋め込む方法を示す SQL Server の Python および R 言語のチュートリアルで使用されます。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/19/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f9482a43a37f3c4feee497ae2fd93029143c84f9
ms.sourcegitcommit: 70e47a008b713ea30182aa22b575b5484375b041
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49806712"
---
# <a name="nyc-taxi-demo-data-for-sql-server-python-and-r-tutorials"></a>NYC タクシーのデモ データの SQL Server の Python および R のチュートリアル
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事からパブリック データで構成されるサンプル データベースを設定する方法を説明します、[ニューヨーク市タクシーのデータセットとリムジン委員会](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)します。 このデータは、SQL server データベース内分析のためのいくつかの R と Python のチュートリアルで使用されます。 サンプル データは、パブリック データ セットの 1% です。 システム データベースのバックアップ ファイルはわずか 90 MB、170万主データ テーブルの行を提供することです。

この手順を完了しておく[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)またはデータベースのバックアップ ファイルを復元して T-SQL クエリを実行できる他のツール。

チュートリアルとクイック スタートのこのデータ セットを使用して、次に示します。

+  [SQL Server の Python のモデルを使用するトレーニングとスコア付け](train-score-using-python-in-tsql.md)

## <a name="download-files"></a>ファイルをダウンロードします。

サンプル データベースは、Microsoft によってホストされているバックアップ ファイルです。 ファイルのダウンロードは、リンクをクリックするとすぐに開始します。 

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
|**NYCTaxi_Sample** | [データベース] |作成-db-tb のアップロード-data.sql スクリプトによって作成されます。 データベースと 2 つのテーブルを作成します。<br /><br />dbo.nyctaxi_sample テーブル: メインの NYC タクシー データセットが含まれています。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルは、このテーブルに挿入されます。<br /><br />dbo.nyc_taxi_models テーブル: トレーニング済みの高度な分析モデルを保持するために使用します。|
|**fnCalculateDistance** |スカラー値関数 (scalar-valued function) | FnCalculateDistance.sql スクリプトによって作成されます。 乗車と降車場所間の直線距離を計算します。 この関数が使用される[データ機能を作成](sqldev-create-data-features-using-t-sql.md)、[トレーニング、モデルを保存および](sqldev-train-and-save-a-model-using-t-sql.md)と[R モデルを運用する](sqldev-operationalize-the-model.md)。|
|**fnEngineerFeatures** |テーブル値関数 (table-valued function) | FnEngineerFeatures.sql スクリプトによって作成されます。 モデルのトレーニング用の新しいデータ機能を作成します。 この関数で使用[データ機能を作成](sqldev-create-data-features-using-t-sql.md)と[R モデルを運用する](sqldev-operationalize-the-model.md)します。|
|**PlotHistogram** |ストアド プロシージャ (stored procedure) | PlotHistogram.sql スクリプトによって作成されます。 変数のヒストグラムをプロットする R 関数を呼び出すし、バイナリ オブジェクトとしてプロットを返します。 このストアド プロシージャが使用される[の探索し、視覚化データ](sqldev-explore-and-visualize-the-data.md)します。|
|**PlotInOutputFiles** |ストアド プロシージャ (stored procedure)| PlotInOutputFiles.sql スクリプトによって作成されます。 R 関数を使用してグラフィックを作成し、ローカル PDF ファイルとして出力を保存します。 このストアド プロシージャが使用される[の探索し、視覚化データ](sqldev-explore-and-visualize-the-data.md)します。|
|**PersistModel** |ストアド プロシージャ (stored procedure) | PersistModel.sql スクリプトによって作成されます。 モデルは、varbinary データ型のシリアル化された、指定されたテーブルに書き込みます。 |
|**PredictTip**  |ストアド プロシージャ (stored procedure) |PredictTip.sql スクリプトによって作成されます。 モデルを使用して予測を作成するトレーニング済みモデルを呼び出します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。 このストアド プロシージャがで使用される[R モデルを運用する](sqldev-operationalize-the-model.md)します。|
|**PredictTipSingleMode**  |ストアド プロシージャ (stored procedure)| PredictTipSingleMode.sql スクリプトによって作成されます。 モデルを使用して予測を作成するトレーニング済みモデルを呼び出します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。 このストアド プロシージャがで使用される[R モデルを運用する](sqldev-operationalize-the-model.md)します。|
|**TrainTipPredictionModel**  |ストアド プロシージャ (stored procedure)|TrainTipPredictionModel.sql スクリプトによって作成されます。 R パッケージを呼び出すことによって、ロジスティック回帰モデルをトレーニングします。 モデルは、tipped 列の値を予測し、ランダムに選択した 70% のデータを使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。 このストアド プロシージャが使用される[トレーニング、モデルを保存および](sqldev-train-and-save-a-model-using-t-sql.md)します。|

## <a name="query-the-data"></a>データのクエリ

検証手順として、データがアップロードされたことを確認するためのクエリを実行します。

1. データベースのオブジェクト エクスプ ローラーで右クリックし、 **NYCTaxi_Sample**データベース、および新しいクエリを開始します。

2. シンプルなクエリを実行します。

    ```sql
    SELECT TOP(10) * FROM dbo.nyctaxi_sample;
    SELECT COUNT(*) FROM dbo.nyctaxi_sample;
    ```
データベースには、1.7 100万行が含まれています。

## <a name="next-steps"></a>次の手順

NYC タクシーのサンプル データは、実践的な学習をご利用いただけます。

+ [SQL Server で R を使用してデータベース内分析について説明します](sqldev-in-database-r-for-sql-developers.md)