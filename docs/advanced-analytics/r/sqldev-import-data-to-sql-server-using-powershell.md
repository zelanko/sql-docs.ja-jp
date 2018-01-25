---
title: "レッスン 2: PowerShell を使用して SQL server のデータのインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 3c5b5145-fa57-455a-b153-0400fc062dc0
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: b526c291fe101210188554b872ace0577670f3fa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-2-import-data-to-sql-server-using-powershell"></a>レッスン 2: PowerShell を使用して SQL server のデータをインポートします。

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

この手順では、ダウンロードしたスクリプトのいずれかを実行して、チュートリアルで必要なデータベース オブジェクトを作成します。 スクリプトでは、使用するほとんどのストアド プロシージャも作成し、指定したデータベース内のテーブルにサンプル データをアップロードします。

## <a name="run-the-scripts-to-create-sql-objects"></a>SQL オブジェクトを作成するスクリプトを実行します。

ダウンロードしたファイルの間では、チュートリアルでは、環境を準備するために実行する PowerShell スクリプトが表示されます。 スクリプトによって実行されるアクションは次のとおりです。

- SQL Native Client と SQL コマンド ライン ユーティリティをまだインストールしていない場合は、インストールします。 これらのユーティリティは、 **bcp**を使用して、データベースにデータを一括読み込みするために必要です。

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータベースとテーブルを作成し、テーブルにデータを一括挿入します。

- 複数の SQL 関数およびストアド プロシージャを作成します。

### <a name="run-the-script"></a>スクリプトを実行します。

1.  管理者として PowerShell コマンド プロンプトを開き、次のコマンドを実行します。
  
    ```ps
    .\RunSQL_SQL_Walkthrough.ps1
    ```
  
    次の情報を入力するように求められます。
  
    - [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] がインストールされている [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] インスタンスの名前またはアドレス。
  
    - インスタンス上のアカウントのユーザー名とパスワード。 アカウントは、データベースを作成、テーブルおよびストアド プロシージャを作成し、テーブルにデータをアップロードする権限が必要です。 ユーザー名とパスワードを指定しない場合、Windows id は SQL Server へのサインインに使用されます。
  
    - ダウンロードしたばかりのサンプル データ ファイルのパスとファイル名。 例:
  
        `C:\tempRSQL\nyctaxi1pct.csv`
  
2.  この手順の一部として、すべての [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトも変更して、プレースホルダーをスクリプトの入力として使用するデータベース名とユーザー名に置き換えます。
  
    少し時間をかけて、スクリプトによって作成されたストアド プロシージャと関数を確認してください。
  
    |**SQL スクリプト ファイル名**|**関数**|
    |-|-|
    |create-db-tb-upload-data.sql|データベースと 2 つのテーブルを作成します。<br /><br />nyctaxi_sample: メインの NYC タクシー データセットを格納します。 ストレージとクエリのパフォーマンスを向上させるために、クラスター化列ストア インデックスをテーブルに追加します。 NYC タクシー データセットの 1% のサンプルが、このテーブルに挿入されます。<br /><br />nyc_taxi_models: トレーニング済みの Advanced Analytics モデルを保持するために使用します。|
    |fnCalculateDistance.sql|乗車と降車の場所間の直線距離を計算するスカラー値関数を作成します。|
    |fnEngineerFeatures.sql|モデルのトレーニング用の新しいデータ機能を作成するテーブル値関数を作成します。|
    |PersistModel.sql|モデルを保存するために呼び出すことができるストアド プロシージャを作成します。 このストアド プロシージャは、varbinary データ型でシリアル化されたモデルを受け取り、それを指定したテーブルに書き込みます。|
    |PredictTipBatchMode.sql|モデルを使用して予測を作成するトレーニング済みモデルを呼び出すストアド プロシージャを作成します。 ストアド プロシージャは、その入力パラメーターとしてクエリを受け取り、入力行のスコアを格納する数値の列を返します。|
    |PredictTipSingleMode.sql|モデルを使用して予測を作成するトレーニング済みモデルを呼び出すストアド プロシージャを作成します。 このストアド プロシージャは、インライン パラメーターとして渡された個々の機能の値と共に、入力として新しい監視を受け取り、新しい監視の結果を予測する値を返します。|
  
    このチュートリアルの後半部分で、いくつかの追加のストアド プロシージャを作成します。
  
    |**SQL スクリプト ファイル名**|**関数**|
    |------|------|
    |PlotHistogram.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャは変数のヒストグラムをプロットする R 関数を呼び出し、バイナリ オブジェクトとしてプロットを返します。|
    |PlotInOutputFiles.sql|データ探索のためのストアド プロシージャを作成します。 このストアド プロシージャでは、R 関数を使用してグラフィックを作成し、出力をローカル PDF ファイルとして保存します。|
    |TrainTipPredictionModel.sql|R パッケージを呼び出して、ロジスティック回帰モデルをトレーニングするストアド プロシージャを作成します。 モデルは、tipped 列の値を予測し、ランダムに選択した 70% のデータを使用してトレーニングされます。 ストアド プロシージャの出力は、テーブル nyc_taxi_models に保存されているトレーニング済みのモデルです。|
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および指定したログインを使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] インスタンスにログインし、作成されたデータベース、テーブル、関数、およびストアド プロシージャが表示されることを確認します。
  
    ![rsql_devtut_BrowseTables](media/rsql-devtut-browsetables.png "rsql_devtut_BrowseTables")
  
    > [!NOTE]
    > データベース オブジェクトが既に存在する場合、それらを再作成することはできません。
    >   
    > テーブルが既に存在する場合、データは追加され、上書きされません。 そのため、スクリプトを実行する前に、既存のオブジェクトを削除してください。

## <a name="next-lesson"></a>次のレッスン

[レッスン 3: 探索し、データの視覚化](../tutorials/sqldev-explore-and-visualize-the-data.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 1: サンプル データをダウンロードします。](../tutorials/sqldev-download-the-sample-data.md)
