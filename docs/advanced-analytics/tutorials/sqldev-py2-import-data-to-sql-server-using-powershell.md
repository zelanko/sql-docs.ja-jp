---
title: "手順 2: PowerShell を使用して SQL Server にデータをインポートする | Microsoft Docs"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-vnext-ctp2
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62a06d6c442428132f84b3f8e5a665e872a8d361
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="step-2-import-data-to-sql-server-using-powershell"></a>手順 2: PowerShell を使用して SQL Server にデータをインポートする

この手順では、ダウンロードしたスクリプトのいずれかを実行して、チュートリアルで必要なデータベース オブジェクトを作成します。 スクリプトでは、使用するほとんどのストアド プロシージャも作成し、指定したデータベース内のテーブルにサンプル データをアップロードします。

## <a name="create-sql-objects-and-data"></a>SQL オブジェクトとデータを作成します。

ダウンロードしたファイルの中に、PowerShell スクリプトがあるはずです。 チュートリアルの環境を準備するには、このスクリプトを実行します。  このスクリプトで、次のアクションが実行されます。

- まだインストールされていない場合は、SQL Native Client と SQL のコマンド ライン ユーティリティをインストールします。 これらのユーティリティは、 **bcp**を使用して、データベースにデータを一括読み込みするために必要です。

- データベースとテーブルを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス、およびテーブルにデータを一括挿入します。

- 複数の SQL 関数およびストアド プロシージャを作成します。

### <a name="run-the-script"></a>スクリプトを実行します。

1. 管理者として PowerShell コマンド プロンプトを開き、次のコマンドを実行します。
  
    ```  
    .\RunSQL_SQL_Walkthrough.ps1  
    ```  

    次の情報を入力するように求められます。
    - 名前またはアドレスの[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]機械学習の Python のサービスがインストールされているインスタンス
    - インスタンス上のアカウントのユーザー名とパスワード。 使用するアカウントには、データベースを作成し、テーブルおよびストアド プロシージャを作成して、データをテーブルにアップロードする権限が必要です。 ユーザー名とパスワードを指定しない場合、Windows id は SQL Server へのサインインに使用されます。
    - ダウンロードしたばかりのサンプル データ ファイルのパスとファイル名。 たとえば、IPv4 アドレスの場合、「 `C:\tempRSQL\nyctaxi1pct.csv`

    > [!NOTE]
    > Xmlrw.dll が、bcp.exe と同じフォルダーにあることを確認してください。 それ以外の場合は、経由でコピーしてください。

2.  この手順の一部として、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトも変更して、プレースホルダーをスクリプトの入力として使用するデータベース名とユーザー名に置き換えます。
  
3. 少し時間をかけて、スクリプトによって作成されたストアド プロシージャと関数を確認してください。
     
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
  
4. このチュートリアルの後半部分で、いくつかの追加のストアド プロシージャを作成します。
    
    |**SQL スクリプト ファイル名**|**関数**|
    |------|------|
    |SerializePlots.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャは、Python を使用してグラフィックスを作成し、そのグラフのオブジェクトをシリアル化します。|
    |TrainTipPredictionModelSciKitPy.sql|ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成 (scikit-説明)。 モデルでは、先端が、列の値を予測してはトレーニング データのランダムに選択された 60% を使用します。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|
    |TrainTipPredictionModelRxPy.sql|(Revoscalepy) ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成します。 モデルでは、先端が、列の値を予測してはトレーニング データのランダムに選択された 60% を使用します。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|
  
3. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および指定したログインを使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスにログインし、作成されたデータベース、テーブル、関数、およびストアド プロシージャが表示されることを確認します。

    ![SSMS でのテーブル参照](media/sqldev-python-browsetables1.png "SSMS でのテーブルの表示")

    > [!NOTE]
    > データベース オブジェクトが既に存在する場合、それらを再作成することはできません。 テーブルが既に存在する場合、データは追加され、上書きされません。 そのため、スクリプトを実行する前に、既存のオブジェクトを削除してください。
    > 指示に従って[ここ](https://docs.microsoft.com/en-us/sql/advanced-analytics/r/set-up-sql-server-r-services-in-database#bkmk_enableFeature)外部スクリプト サービスを有効にします。
    


## <a name="next-step"></a>次の手順

[手順 3: データの探索と視覚化](sqldev-py3-explore-and-visualize-the-data.md)

## <a name="previous-step"></a>前の手順

[手順 1: サンプル データのダウンロード](sqldev-py1-download-the-sample-data.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)



