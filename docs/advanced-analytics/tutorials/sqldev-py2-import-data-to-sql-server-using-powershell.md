---
title: 手順 2 は、PowerShell を使用して SQL server のデータをインポート |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f8b90a18c0cdce9c4c2c73db4b599e488570f018
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461868"
---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>手順 2: PowerShell を使用して SQL server のデータをインポートします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルの一部[SQL 開発者向けの in-database Python analytics](sqldev-in-database-python-for-sql-developers.md)します。 

この手順で、チュートリアルで必要なデータベース オブジェクトを作成、ダウンロードしたスクリプトのいずれかを実行します。 このスクリプトもいくつかのストアド プロシージャを作成し、指定したデータベース内のテーブルにサンプル データをアップロードします。

## <a name="create-database-objects-and-load-data"></a>データベース オブジェクトを作成し、データを読み込む

PowerShell スクリプトの表示、ダウンロードしたファイルの間で`RunSQL_SQL_Walkthrough.ps1`します。 このスクリプトでは、チュートリアルでは、環境を準備します。

このスクリプトで、次のアクションが実行されます。

- まだインストールされていない場合は、SQL Native Client と SQL のコマンド ライン ユーティリティをインストールします。 これらのユーティリティは、 **bcp**を使用して、データベースにデータを一括読み込みするために必要です。

- 上のデータベースとテーブルの作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、およびテーブルにデータを一括挿入します。

- 複数の SQL 関数およびストアド プロシージャを作成します。

問題が発生した場合は、手動で手順を実行する参照として、スクリプトを使用できます。

### <a name="modify-the-script-to-use-a-trusted-windows-identity"></a>信頼できる Windows id を使用するスクリプトを変更します。

既定では、スクリプトは、SQL Server データベースのユーザーのログインとパスワードを想定しています。 Windows ユーザー アカウントで db_owner 場合は、オブジェクトを作成する、Windows id を使用できます。 これを行うには、開く`RunSQL_SQL_Walkthrough.ps1`を追加するコード エディターで**`-T`** bcp に bulk insert コマンド。

```text
bcp $db_tb in $csvfilepath -t ',' -S $server -f taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U $u -P $p -T
```

### <a name="run-the-script"></a>スクリプトを実行します

1. 管理者として PowerShell コマンド プロンプトを開きます。 既に前の手順で作成したフォルダー内でない場合、フォルダーに移動し、次のコマンドを実行します。
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```

2. スクリプトでは、次の情報メッセージが表示されます。

    - 名前またはアドレスの[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Python を使用した Machine Learning サービスがインストールされているインスタンス。
    - インスタンス上のアカウントのユーザー名とパスワード。 使用するアカウントにデータベースを作成し、テーブルおよびストアド プロシージャは、作成、テーブルに一括で読み込むことが必要です。 
    - ユーザー名とパスワードを指定しない場合は、自分の Windows id が SQL Server へのサインインに使用されます。
    - ダウンロードしたばかりのサンプル データ ファイルのパスとファイル名。 例を次に示します。 `C:\temp\pysql\nyctaxi1pct.csv`

    > [!NOTE]
    > データを正常に読み込むには、ライブラリ xmlrw.dll は bcp.exe と同じフォルダーでなければなりません。

3. スクリプトを変更します、[!INCLUDE[tsql](../../includes/tsql-md.md)]した置換のプレース ホルダーをデータベース名とユーザー名を以前ダウンロードしたスクリプトを提供します。
  
4. スクリプトが完了したら、ログイン、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースがテーブルを確認する指定されたログインを使用して、インスタンスは、次の関数、およびストアド プロシージャが作成されています。 次の図は、オブジェクトで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。

    ![SSMS でのテーブルの参照](media/sqldev-python-browsetables1.png "SSMS でのテーブルの表示")

    > [!NOTE]
    > データベース オブジェクトが既に存在する場合、もう一度は作成できません。
    > 
    > 同じ名前とスキーマの既存のテーブルが見つからないかどうか、上書きされないのデータが追加されます。 そのため、必ず削除するか、スクリプトを実行する前に既存のテーブルを切り捨てるしてください。

## <a name="list-of-stored-procedures-and-functions"></a>ストアド プロシージャと関数の一覧

次の SQL Server オブジェクトは、スクリプトによって作成されます。

|**SQL スクリプト ファイル名**|**関数**|
|------|------|
|create-db-tb-upload-data.sql|データベースと 2 つのテーブルを作成します。<br /><br />nyctaxi_sample: メインの NYC タクシー データセットを格納します。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルが、このテーブルに挿入されます。<br /><br />nyc_taxi_models: トレーニング済みの Advanced Analytics モデルを保持するために使用します。|
|fnCalculateDistance.sql|乗車と降車の場所間の直線距離を計算するスカラー値関数を作成します。|
|fnEngineerFeatures.sql|モデルのトレーニング用の新しいデータ機能を作成するテーブル値関数を作成します。|
|TrainingTestingSplit.sql|2 つの部分に nyctaxi_sample テーブル内のデータを分割: nyctaxi_sample_training nyctaxi_sample_testing とします。|
|PredictTipSciKitPy.sql|トレーニング済みモデルを呼び出すストアド プロシージャを作成します (scikit-について説明します)、モデルを使用して予測を作成します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。|
|PredictTipRxPy.sql|モデルを使用して予測を作成するトレーニング済みモデル (revoscalepy) を呼び出すストアド プロシージャを作成します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。|
|PredictTipSingleModeSciKitPy.sql|トレーニング済みモデルを呼び出すストアド プロシージャを作成します (scikit-について説明します)、モデルを使用して予測を作成します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。|
|PredictTipSingleModeRxPy.sql|モデルを使用して予測を作成するトレーニング済みモデル (revoscalepy) を呼び出すストアド プロシージャを作成します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。|

このチュートリアルの後半部分で、これらのストアド プロシージャを作成します。
    
|**SQL スクリプト ファイル名**|**関数**|
|------|------|
|SerializePlots.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャでは、Python を使用してグラフィックを作成し、グラフ オブジェクトをシリアル化します。|
|TrainTipPredictionModelSciKitPy.sql|ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成します (scikit、について説明します)。 モデルでは、tipped 列の値を予測して、データのランダムに選択された 60% を使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|
|TrainTipPredictionModelRxPy.sql|ロジスティック回帰モデル (revoscalepy) をトレーニングするストアド プロシージャを作成します。 モデルでは、tipped 列の値を予測して、データのランダムに選択された 60% を使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|

## <a name="next-step"></a>次の手順

[手順 3: データの探索と視覚化](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>前の手順

[手順 1: サンプル データのダウンロード](demo-data-nyctaxi-in-sql.md)

