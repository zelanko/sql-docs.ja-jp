---
title: "手順 2: PowerShell を使用して SQL server のデータのインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: d39e391e494e37c63731431579e82900ef3dbeeb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>手順 2: PowerShell を使用して SQL server のデータをインポートします。

この記事では、チュートリアルのパート[SQL 開発者のためのデータベースでの Python analytics](sqldev-in-database-python-for-sql-developers.md)です。 

この手順で、チュートリアルに必要なデータベース オブジェクトを作成するにはダウンロードしたスクリプトのいずれかを実行します。 スクリプトは、いくつかのストアド プロシージャを作成し、指定したデータベース内のテーブルにサンプル データをアップロードします。

## <a name="create-database-objects-and-load-data"></a>データベース オブジェクトを作成し、データを読み込みます

PowerShell スクリプトでは、表示、ダウンロードしたファイルの間で`RunSQL_SQL_Walkthrough.ps1`です。 このスクリプトの目的は、チュートリアルでは、環境の準備を開始します。

このスクリプトで、次のアクションが実行されます。

- まだインストールされていない場合は、SQL Native Client と SQL のコマンド ライン ユーティリティをインストールします。 これらのユーティリティは、 **bcp**を使用して、データベースにデータを一括読み込みするために必要です。

- データベースとテーブルを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、およびテーブルにデータを一括挿入します。

- 複数の SQL 関数およびストアド プロシージャを作成します。

問題に遭遇した場合は、手動で手順を実行する参照としてスクリプトを使用できます。

1. 管理者として PowerShell コマンド プロンプトを開きます。 いない場合は既に、前の手順で作成したフォルダーで、フォルダーを移動し、次のコマンドを実行します。
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```

2. スクリプトは、次の情報が表示されます。

    - 名前またはアドレスの[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Python の Machine Learning のサービスがインストールされているインスタンス。
    - インスタンス上のアカウントのユーザー名とパスワード。 データベースを作成し、テーブルおよびストアド プロシージャを作成してデータの一括読み込みのテーブルに機能を使用するアカウントが必要です。 
    - ユーザー名とパスワードを指定しない場合は、SQL Server へのサインインに使用される、Windows id れ、パスワードの入力に昇格されます。
    - ダウンロードしたばかりのサンプル データ ファイルのパスとファイル名。 たとえば、IPv4 アドレスの場合、「 `C:\temp\pysql\nyctaxi1pct.csv`

    > [!NOTE]
    > データを正常に読み込むには、ライブラリ xmlrw.dll は bcp.exe と同じフォルダーでなければなりません。

3. スクリプトを変更も、[!INCLUDE[tsql](../../includes/tsql-md.md)]したユーザーとデータベースの名前で置き換えます。 置き換えプレース ホルダー名、以前にダウンロードしたスクリプトを提供します。
  
4. スクリプトが完了すると、ログインに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースがテーブルを確認する、指定したログインを使用して、インスタンスは、次の関数、およびストアド プロシージャが作成されています。 次の図は、オブジェクトで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。

    ![SSMS でのテーブル参照](media/sqldev-python-browsetables1.png "SSMS でのテーブルの表示")

    > [!NOTE]
    > データベース オブジェクトが既に存在していた場合は、再度作成することはできません。
    > 
    > 同じ名前とスキーマの既存のテーブルが見つからないかどうかは、データが追加されます、上書きされません。 そのため、ドロップまたはスクリプトを実行する前に既存のテーブルを切り捨てることを確認します。

## <a name="list-of-stored-procedures-and-functions"></a>ストアド プロシージャと関数の一覧

次の SQL Server オブジェクトは、スクリプトによって作成されます。

|**SQL スクリプト ファイル名**|**関数**|
|------|------|
|create-db-tb-upload-data.sql|データベースと 2 つのテーブルを作成します。<br /><br />nyctaxi_sample: メインの NYC タクシー データセットを格納します。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルが、このテーブルに挿入されます。<br /><br />nyc_taxi_models: トレーニング済みの Advanced Analytics モデルを保持するために使用します。|
|fnCalculateDistance.sql|乗車と降車の場所間の直線距離を計算するスカラー値関数を作成します。|
|fnEngineerFeatures.sql|モデルのトレーニング用の新しいデータ機能を作成するテーブル値関数を作成します。|
|TrainingTestingSplit.sql|2 つの部分に nyctaxi_sample テーブル内のデータを分割: nyctaxi_sample_training nyctaxi_sample_testing とします。|
|PredictTipSciKitPy.sql|トレーニング済みモデルを呼び出すストアド プロシージャを作成 (scikit-説明) モデルを使用して予測を作成します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。|
|PredictTipRxPy.sql|モデルを使用して予測を作成、トレーニング済みモデル (revoscalepy) を呼び出すストアド プロシージャを作成します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。|
|PredictTipSingleModeSciKitPy.sql|トレーニング済みモデルを呼び出すストアド プロシージャを作成 (scikit-説明) モデルを使用して予測を作成します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。|
|PredictTipSingleModeRxPy.sql|モデルを使用して予測を作成、トレーニング済みモデル (revoscalepy) を呼び出すストアド プロシージャを作成します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。|

このチュートリアルの後半では、これらの追加のストアド プロシージャを作成します。
    
|**SQL スクリプト ファイル名**|**関数**|
|------|------|
|SerializePlots.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャは、Python を使用してグラフィックスを作成し、そのグラフのオブジェクトをシリアル化します。|
|TrainTipPredictionModelSciKitPy.sql|ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成 (scikit-説明)。 モデルでは、先端が、列の値を予測してはトレーニング データのランダムに選択された 60% を使用します。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|
|TrainTipPredictionModelRxPy.sql|(Revoscalepy) ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成します。 モデルでは、先端が、列の値を予測してはトレーニング データのランダムに選択された 60% を使用します。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|

## <a name="next-step"></a>次の手順

[手順 3: データの探索と視覚化](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>前の手順

[手順 1: サンプル データのダウンロード](sqldev-py1-download-the-sample-data.md)

