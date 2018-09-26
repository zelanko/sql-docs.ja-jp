---
title: R と Python (SQL Server Machine Learning) の埋め込みの NYC タクシーのデモ データとスクリプトのダウンロード |Microsoft Docs
description: ニューヨーク市タクシーのサンプル データをダウンロードして、データベースの作成の手順です。 データを R を埋め込む方法を示す SQL Server チュートリアルで使用して、SQL Server での Python にはストアド プロシージャと T-SQL 関数します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 58a996ae500a27a6878b30fc072bf09a75d4ba43
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712755"
---
# <a name="nyc-taxi-demo-data-for-sql-server"></a>SQL Server 用の NYC タクシーのデモ データ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL server データベース内分析に R と Python を使用する方法のチュートリアルについては、システムを準備します。

この演習では、サンプル データを環境を準備するための PowerShell スクリプトをダウンロードし、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプト ファイルのいくつかのチュートリアルで使用します。 完了したら、 **NYCTaxi_Sample**データベースが実践的な学習のデモにデータを提供する、ローカルのインスタンスで使用できます。 

## <a name="prerequisites"></a>前提条件

インターネット接続、PowerShell、およびコンピューターのローカル管理者権限を必要があります。 おく[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)やその他のツールをオブジェクトの作成を確認します。

## <a name="download-nyc-taxi-demo-data-and-scripts-from-github"></a>NYC タクシーのデモ データとスクリプトを Github からダウンロードします。

1.  Windows PowerShell コマンド コンソールを開きます。
  
    使用して、**管理者として実行**先ディレクトリを作成するか、または指定したコピー先にファイルを書き込みます。
  
2.  パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。 ここで使用した既定値は **TempRSQL**です。
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    *DestDir* で指定したフォルダーが存在しない場合、PowerShell スクリプトによって作成されます。
  
    > [!TIP]
    > エラーが発生する場合は PowerShell スクリプトの実行ポリシーを一時的に設定できます**無制限**を Bypass 引数を使用し、変更、現在のセッションにスコープには、このチュートリアルでのみです。
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > このコマンドを実行しても、構成は変更されません。
  
    インターネット接続によっては、ダウンロードに時間がかかる場合があります。
  
3.  すべてのファイルがダウンロードされると、PowerShell スクリプトが表示されます、 *DestDir*フォルダー。 PowerShell コマンド プロンプトで次のコマンドを実行し、ダウンロードされたファイルを確認します。
  
    ```
    ls
    ```
  
    **結果:**
  
    ![PowerShell スクリプトによってダウンロードされたファイルの一覧](media/rsql-devtut-filelist.png "PowerShell スクリプトによってダウンロードされたファイルの一覧")

## <a name="create-nyctaxisample-database"></a>NYCTaxi_Sample データベースを作成します。

ダウンロードしたファイルの間で PowerShell スクリプトを表示する必要があります (**RunSQL_SQL_Walkthrough.ps1**) データベースを作成して、一括読み込みデータ。 スクリプトによって実行されるアクションは次のとおりです。

+ まだインストールされていない場合は、SQL Native Client と SQL のコマンド ライン ユーティリティをインストールします。 これらのユーティリティは、 **bcp**を使用して、データベースにデータを一括読み込みするために必要です。

+ データベースとテーブルを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、および .csv ファイルをソースとデータを一括挿入します。

+ 複数の SQL 関数およびいくつかのチュートリアルで使用されるストアド プロシージャを作成します。

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>信頼できる Windows id を使用するスクリプトを変更します。

既定では、スクリプトは、SQL Server データベースのユーザーのログインとパスワードを想定しています。 Windows ユーザー アカウントで db_owner 場合は、オブジェクトを作成する、Windows id を使用できます。 これを行うには、開く`RunSQL_SQL_Walkthrough.ps1`コード エディターで、追加**`-T`** 一括挿入 (行 238) のコマンドを bcp に。

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>オブジェクトを作成するスクリプトを実行します。

C:\tempRSQL で、管理者の PowerShell コマンド プロンプトを使用して、次のコマンドを実行します。
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
次の情報の入力を求められます。

- サーバー インスタンスの[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]がインストールされています。 既定のインスタンスには、コンピューター名だけでこれができます。

- データベース名。 このチュートリアルでは、スクリプトを想定して`NYCTaxi_Sample`します。

- ユーザー名とユーザーのパスワード。 これらの値には、SQL Server データベースのログインを入力します。 または、信頼できる Windows id を受け入れるようにスクリプトを変更した場合は、これらの値を空白のままにするには Enter を押します。 Windows id は、接続で使用されます。

- 前のレッスンでダウンロードしたサンプル データの完全修飾ファイル名。 例: `C:\tempRSQL\nyctaxi1pct.csv`

これらの値を指定した後、スクリプトをすぐに実行します。 内のすべてのプレース ホルダー名、スクリプトの実行中に、[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプトを使用して、指定した入力を更新します。

## <a name="review-database-objects"></a>データベース オブジェクトを確認してください。
   
スクリプトの実行が完了したら、データベース オブジェクトに存在の確認、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 データベース、テーブル、関数、およびストアド プロシージャを参照する必要があります。
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> データベース オブジェクトが既に存在する場合、それらを再作成することはできません。
>   
> テーブルが既に存在する場合、データは追加され、上書きされません。 そのため、スクリプトを実行する前に、既存のオブジェクトを削除してください。

### <a name="objects-in-nyctaxisample-database"></a>NYCTaxi_Sample データベース内のオブジェクト

次の表では、NYC タクシーのデモ データベースで作成されたオブジェクトをまとめたものです。 1 つの PowerShell スクリプトを実行するだけですが (`RunSQL_SQL_Walkthrough.ps1`)、そのスクリプトは、データベースにオブジェクトを作成するには、さらに他の SQL スクリプトを呼び出します。 説明では、各オブジェクトを作成するために使用するスクリプトが説明されています。

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

1. オブジェクト エクスプ ローラーで、[データベース] で、 **NYCTaxi_Sample**データベース、[テーブル] フォルダーを開きます。

2. 右クリックし、 **dbo.nyctaxi_sample**選択**上位 1000 行**をいくつかのデータを返します。

## <a name="next-steps"></a>次の手順

NYC タクシーのサンプル データは、実践的な学習をご利用いただけます。

+ [SQL Server で R を使用してデータベース内分析について説明します](sqldev-in-database-r-for-sql-developers.md)