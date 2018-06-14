---
title: レッスン 2 を準備する R チュートリアル環境 PowerShell (SQL Server の Machine Learning) を使用して |Microsoft ドキュメント
description: SQL Server で R を埋め込む方法を示すチュートリアル ストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1280d7c82d48c8ed596271cd7a73fa13ec1664c7
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35249745"
---
# <a name="lesson-2-set-up-the-tutorial-environment-using-powershell"></a>レッスン 2: PowerShell を使用したチュートリアルの環境のセットアップします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

このステップでは、このチュートリアルに必要なデータベース オブジェクトを作成する PowerShell スクリプトを実行します。 スクリプトを作成し、前の手順で取得したサンプル データを使用してデータベースを読み込みます。 また、関数およびチュートリアルで使用するストアド プロシージャを作成します。

## <a name="create-and-load-database-objects"></a>作成し、データベース オブジェクトを読み込む

ダウンロードしたファイルの間で、PowerShell スクリプトが表示されます (`RunSQL_SQL_Walkthrough.ps1`) チュートリアルでは、環境を準備します。 スクリプトによって実行されるアクションは次のとおりです。

- まだインストールされていない場合は、SQL Native Client と SQL のコマンド ライン ユーティリティをインストールします。 これらのユーティリティは、 **bcp**を使用して、データベースにデータを一括読み込みするために必要です。

- 上のデータベースとテーブルを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、および .csv ファイルのソースとデータの一括挿入します。

- 複数の SQL 関数およびストアド プロシージャを作成します。

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>信頼された Windows id を使用するスクリプトを変更します。

既定では、スクリプトには、SQL Server データベースのユーザーのログインとパスワードが想定しています。 Windows ユーザー アカウントの下にある db_owner 場合は、オブジェクトを作成する、Windows id を使用できます。 これを行うには、開く`RunSQL_SQL_Walkthrough.ps1`コード エディターでおよび追加**`-T`** bcp 一括挿入コマンド (line 238)。

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script-to-create-objects"></a>オブジェクトを作成するスクリプトを実行します。

管理者として PowerShell コマンド プロンプトを開き、次のコマンドを実行します。
  
```ps
.\RunSQL_SQL_Walkthrough.ps1
```
次の情報を入力するように求められます。

- サーバー インスタンスの[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]がインストールされています。 既定のインスタンスに、コンピューター名などの単純な指定できます。

- データベース名。 このチュートリアルでは、スクリプトが前提としています`TaxiNYC_Sample`です。

- ユーザー名とユーザーのパスワード。 これらの値の SQL Server データベース ログインを入力します。 または、信頼された Windows id を受け入れるようにスクリプトを変更した場合は、これらの値を空白のままにするには Enter を押します。 Windows id は、接続で使用されます。

- 前のレッスンでダウンロードしたサンプル データの完全修飾ファイル名。 例: `C:\tempRSQL\nyctaxi1pct.csv`

これらの値を提供した後、スクリプトをすぐに実行します。 内のすべてのプレース ホルダー名、スクリプトの実行中に、[!INCLUDE[tsql](../../includes/tsql-md.md)]を提供する入力を使用するスクリプトを更新します。

## <a name="review-database-objects"></a>データベース オブジェクトを確認します。
   
スクリプトの実行が完了したら、データベース オブジェクトに存在の確認、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスを使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。 データベース、テーブル、関数、およびストアド プロシージャが表示されます。
  
   ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")

> [!NOTE]
> データベース オブジェクトが既に存在する場合、それらを再作成することはできません。
>   
> テーブルが既に存在する場合、データは追加され、上書きされません。 そのため、スクリプトを実行する前に、既存のオブジェクトを削除してください。

## <a name="objects-used-in-this-tutorial"></a>このチュートリアルで使用されるオブジェクト

次の表は、このレッスンで作成されたオブジェクトをまとめたものです。 1 つの PowerShell スクリプトを実行するだけですが (`RunSQL_SQL_Walkthrough.ps1`)、そのスクリプトは、データベースにオブジェクトを作成するには、さらに他の SQL スクリプトを呼び出します。 各オブジェクトの作成に使用されるスクリプトは、説明に記載されています。

|**オブジェクト名です。**|**オブジェクトの種類**|**description**|
|----------|------------------------|---------------|
|**TaxiNYC_Sample** | [データベース] |作成-db-tb のアップロード-data.sql スクリプトによって作成されます。 データベースと 2 つのテーブルを作成します。<br /><br />dbo.nyctaxi_sample テーブル: メイン NYC タクシー データセットが含まれています。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルは、このテーブルに挿入されます。<br /><br />dbo.nyc_taxi_models テーブル: トレーニング済みの高度な分析モデルを永続化に使用します。|
|**fnCalculateDistance** |スカラー値関数 (scalar-valued function) | FnCalculateDistance.sql スクリプトによって作成されます。 ピックアップと dropoff 場所間の直接の距離を計算します。 この関数を使用[データ機能の作成](../tutorials/sqldev-create-data-features-using-t-sql.md)、[トレーニング、モデルを保存および](sqldev-train-and-save-a-model-using-t-sql.md)と[R モデルを操作運用](../tutorials/sqldev-operationalize-the-model.md)です。|
|**fnEngineerFeatures** |テーブル値関数 (table-valued function) | FnEngineerFeatures.sql スクリプトによって作成されます。 モデルのトレーニング データの新しい機能を作成します。 この関数を使用[データ機能の作成](../tutorials/sqldev-create-data-features-using-t-sql.md)と[R モデルを操作運用](../tutorials/sqldev-operationalize-the-model.md)です。|
|**PlotHistogram** |ストアド プロシージャ (stored procedure) | PlotHistogram.sql スクリプトによって作成されます。 変数のヒストグラムをプロットする R 関数を呼び出すし、バイナリ オブジェクトとしてプロットを返します。 このストアド プロシージャがで使用される[調査し、視覚化データ](../tutorials/sqldev-explore-and-visualize-the-data.md)です。|
|**PlotInOutputFiles** |ストアド プロシージャ (stored procedure)| PlotInOutputFiles.sql スクリプトによって作成されます。 R 関数を使用してグラフィックスを作成し、ローカルの PDF ファイルとして出力を保存します。 このストアド プロシージャがで使用される[調査し、視覚化データ](../tutorials/sqldev-explore-and-visualize-the-data.md)です。|
|**PersistModel** |ストアド プロシージャ (stored procedure) | PersistModel.sql スクリプトによって作成されます。 Varbinary データ型をシリアル化された、指定されたテーブルに書き込むモデルを取得します。 |
|**PredictTip**  |ストアド プロシージャ (stored procedure) |PredictTip.sql スクリプトによって作成されます。 モデルを使用して予測を作成、トレーニング済みモデルを呼び出します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。 このストアド プロシージャがで使用される[R モデルを操作運用](../tutorials/sqldev-operationalize-the-model.md)です。|
|**PredictTipSingleMode**  |ストアド プロシージャ (stored procedure)| PredictTipSingleMode.sql スクリプトによって作成されます。 モデルを使用して予測を作成、トレーニング済みモデルを呼び出します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。 このストアド プロシージャがで使用される[R モデルを操作運用](../tutorials/sqldev-operationalize-the-model.md)です。|
|**TrainTipPredictionModel**  |ストアド プロシージャ (stored procedure)|TrainTipPredictionModel.sql スクリプトによって作成されます。 R パッケージを呼び出すことによって、ロジスティック回帰モデルをトレーニングします。 モデルは、tipped 列の値を予測し、ランダムに選択した 70% のデータを使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。 このストアド プロシージャが使用される[トレーニング、モデルを保存および](sqldev-train-and-save-a-model-using-t-sql.md)です。|

## <a name="next-lesson"></a>次のレッスン

[レッスン 3: 探索し、データの視覚化](../tutorials/sqldev-explore-and-visualize-the-data.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 1: サンプル データをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)
