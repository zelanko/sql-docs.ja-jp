---
title: R と Python (SQL Server Machine Learning) の埋め込みの NYC タクシーのデモ データとスクリプトのダウンロード |Microsoft Docs
description: ニューヨーク市タクシーのサンプル データをダウンロードして、データベースの作成の手順です。 データを R を埋め込む方法を示す SQL Server チュートリアルで使用して、SQL Server での Python にはストアド プロシージャと T-SQL 関数します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/02/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 700720f7538467dc3edc38414544eb2c402437a6
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232576"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>SQL Server 用の NYC タクシーのデモ データ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、R と Python のチュートリアルでは、SQL Server データベース内分析のサンプル データを取得する方法について説明します。

データの発生元、 [NYC タクシーのデータセットとリムジン委員会](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)パブリック データ セット。 しました、データセットのスナップショットと利用可能なデータのキャプチャの 1% のデモ データベース。 システム データベースのバックアップ ファイルはわずか 90 MB、170万主データ テーブルの行を提供することです。

この記事の手順を実行が完了したら、 **NYCTaxi_Sample**データベースが実践的な学習のデモにデータを提供する、ローカルのインスタンスで使用できます。 データベース名にする必要があります**NYCTaxi_Sample**まま変更せずに、デモ スクリプトを実行する場合。

## <a name="prerequisites"></a>前提条件

必要なは、インターネット接続をコンピューターと、データベース エンジンのインスタンスのローカルの管理者権限。

ことが役立ちます[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)やその他のツールをオブジェクトの作成を確認します。

## <a name="download-demo-database"></a>デモのデータベースをダウンロードします。

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
|**fnCalculateDistance** |スカラー値関数 (scalar-valued function) | FnCalculateDistance.sql スクリプトによって作成されます。 乗車と降車場所間の直線距離を計算します。 この関数が使用される[データ機能を作成](sqldev-create-data-features-using-t-sql.md)、[トレーニング、モデルを保存および](../r/sqldev-train-and-save-a-model-using-t-sql.md)と[R モデルを運用する](sqldev-operationalize-the-model.md)。|
|**fnEngineerFeatures** |テーブル値関数 (table-valued function) | FnEngineerFeatures.sql スクリプトによって作成されます。 モデルのトレーニング用の新しいデータ機能を作成します。 この関数で使用[データ機能を作成](sqldev-create-data-features-using-t-sql.md)と[R モデルを運用する](sqldev-operationalize-the-model.md)します。|
|**PlotHistogram** |ストアド プロシージャ (stored procedure) | PlotHistogram.sql スクリプトによって作成されます。 変数のヒストグラムをプロットする R 関数を呼び出すし、バイナリ オブジェクトとしてプロットを返します。 このストアド プロシージャが使用される[の探索し、視覚化データ](sqldev-explore-and-visualize-the-data.md)します。|
|**PlotInOutputFiles** |ストアド プロシージャ (stored procedure)| PlotInOutputFiles.sql スクリプトによって作成されます。 R 関数を使用してグラフィックを作成し、ローカル PDF ファイルとして出力を保存します。 このストアド プロシージャが使用される[の探索し、視覚化データ](sqldev-explore-and-visualize-the-data.md)します。|
|**PersistModel** |ストアド プロシージャ (stored procedure) | PersistModel.sql スクリプトによって作成されます。 モデルは、varbinary データ型のシリアル化された、指定されたテーブルに書き込みます。 |
|**PredictTip**  |ストアド プロシージャ (stored procedure) |PredictTip.sql スクリプトによって作成されます。 モデルを使用して予測を作成するトレーニング済みモデルを呼び出します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。 このストアド プロシージャがで使用される[R モデルを運用する](sqldev-operationalize-the-model.md)します。|
|**PredictTipSingleMode**  |ストアド プロシージャ (stored procedure)| PredictTipSingleMode.sql スクリプトによって作成されます。 モデルを使用して予測を作成するトレーニング済みモデルを呼び出します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。 このストアド プロシージャがで使用される[R モデルを運用する](sqldev-operationalize-the-model.md)します。|
|**TrainTipPredictionModel**  |ストアド プロシージャ (stored procedure)|TrainTipPredictionModel.sql スクリプトによって作成されます。 R パッケージを呼び出すことによって、ロジスティック回帰モデルをトレーニングします。 モデルは、tipped 列の値を予測し、ランダムに選択した 70% のデータを使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。 このストアド プロシージャが使用される[トレーニング、モデルを保存および](../r/sqldev-train-and-save-a-model-using-t-sql.md)します。|

## <a name="query-data-for-verification"></a>検証のためのデータを照会します。

検証手順として、データがアップロードされたことを確認するためのクエリを実行します。

1. データベースのオブジェクト エクスプ ローラーで右クリックし、 **NYCTaxi_Sample**データベース、および新しいクエリを開始します。

2. 実行**`select * from dbo.nyctaxi_sample`** 170万のすべての行を返します。

## <a name="next-steps"></a>次の手順

NYC タクシーのサンプル データは、実践的な学習をご利用いただけます。

+ [SQL Server で R を使用してデータベース内分析について説明します](sqldev-in-database-r-for-sql-developers.md)