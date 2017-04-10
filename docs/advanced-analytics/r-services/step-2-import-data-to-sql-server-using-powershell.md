---
title: "手順 2: PowerShell を使用して SQL Server にデータをインポートする (高度な分析 (データベース内) のチュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 3c5b5145-fa57-455a-b153-0400fc062dc0
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# 手順 2: PowerShell を使用して SQL Server にデータをインポートする (高度な分析 (データベース内) のチュートリアル)
この手順では、ダウンロードしたスクリプトのいずれかを実行して、チュートリアルで必要なデータベース オブジェクトを作成します。 スクリプトでは、使用するほとんどのストアド プロシージャも作成し、指定したデータベース内のテーブルにサンプル データをアップロードします。  
  
## スクリプトを実行して SQL オブジェクトを作成する  
ダウンロードしたファイルの中に、PowerShell スクリプトがあるはずです。 チュートリアルの環境を準備するには、このスクリプトを実行します。  
  
スクリプトによって実行されるアクションは次のとおりです。  
  
-   SQL Native Client と SQL コマンド ライン ユーティリティをまだインストールしていない場合は、インストールします。 これらのユーティリティは、**bcp** を使用して、データベースにデータを一括読み込みするために必要です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータベースとテーブルを作成し、テーブルにデータを一括挿入します。  
  
-   複数の SQL 関数およびストアド プロシージャを作成します。  
  
#### スクリプトを実行するには  
1.  管理者として PowerShell コマンド プロンプトを開き、次のコマンドを実行します。  
  
    ```  
    .\RunSQL_SQL_Walkthrough.ps1  
    ```  
  
    次の情報を入力するように求められます。  
  
    -   [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] がインストールされている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インスタンスの名前またはアドレス。  
  
    -   インスタンス上のアカウントのユーザー名とパスワード。 使用するアカウントには、データベースを作成し、テーブルおよびストアド プロシージャを作成して、データをテーブルにアップロードする権限が必要です。  
  
    -   ダウンロードしたばかりのサンプル データ ファイルのパスとファイル名。 例:  
  
        `C:\tempRSQL\nyctaxi1pct.csv`  
  
2.  この手順の一部として、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトも変更して、プレースホルダーをスクリプトの入力として使用するデータベース名とユーザー名に置き換えます。  
  
    少し時間をかけて、スクリプトによって作成されたストアド プロシージャと関数を確認してください。  
  
    |||  
    |-|-|  
    |**SQL スクリプト ファイル名**|**関数**|  
    |create-db-tb-upload-data.sql|データベースと 2 つのテーブルを作成します。<br /><br />nyctaxi_sample: メインの NYC タクシー データセットを格納します。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルが、このテーブルに挿入されます。<br /><br />nyc_taxi_models: トレーニング済みの Advanced Analytics モデルを保持するために使用します。|  
    |fnCalculateDistance.sql|乗車と降車の場所間の直線距離を計算するスカラー値関数を作成します。|  
    |fnEngineerFeatures.sql|モデルのトレーニング用の新しいデータ機能を作成するテーブル値関数を作成します。|  
    |PersistModel.sql|モデルを保存するために呼び出すことができるストアド プロシージャを作成します。 このストアド プロシージャは、varbinary データ型でシリアル化されたモデルを受け取り、それを指定したテーブルに書き込みます。|  
    |PredictTipBatchMode.sql|モデルを使用して予測を作成するトレーニング済みモデルを呼び出すストアド プロシージャを作成します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。|  
    |PredictTipSingleMode.sql|モデルを使用して予測を作成するトレーニング済みモデルを呼び出すストアド プロシージャを作成します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。|  
  
    このチュートリアルの後半部分で、いくつかの追加のストアド プロシージャを作成します。  
  
    |||  
    |-|-|  
    |**SQL スクリプト ファイル名**|**関数**|  
    |PlotHistogram.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャは変数のヒストグラムをプロットする R 関数を呼び出し、バイナリ オブジェクトとしてプロットを返します。|  
    |PlotInOutputFiles.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャでは、R 関数を使用してグラフィックを作成し、出力をローカル PDF ファイルとして保存します。|  
    |TrainTipPredictionModel.sql|R パッケージを呼び出して、ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成します。 モデルは、tipped 列の値を予測し、ランダムに選択した 70% のデータを使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|  
  
3.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および指定したログインを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにログインし、作成されたデータベース、テーブル、関数、およびストアド プロシージャが表示されることを確認します。  
  
    ![rsql_devtut_BrowseTables](../../advanced-analytics/r-services/media/rsql-devtut-browsetables.PNG "rsql_devtut_BrowseTables")  
  
    > [!NOTE]  
    > データベース オブジェクトが既に存在する場合、それらを再作成することはできません。  
    >   
    > テーブルが既に存在する場合、データは追加され、上書きされません。 そのため、スクリプトを実行する前に、既存のオブジェクトを削除してください。  
  
## 次の手順  
[手順 3: データの探索と視覚化](../../advanced-analytics/r-services/step-3-explore-and-visualize-the-data-in-database-advanced-analytics-tutorial.md)  
  
## 前の手順  
[手順 1: サンプル データのダウンロード](../../advanced-analytics/r-services/step-1-download-the-sample-data-in-database-advanced-analytics-tutorial.md)  
  
## 参照  
[SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
