---
title: "手順 3: 探索し、データの視覚化 |Microsoft ドキュメント"
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
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 737a925e2902fbd017abcdf996d88652c995a044
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="step-3-explore-and-visualize-the-data"></a>手順 3: 探索し、データの視覚化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルのパート[SQL 開発者のためのデータベースでの Python analytics](sqldev-in-database-python-for-sql-developers.md)です。 

このステップでは、サンプル データを探索し、いくつかのプロットを生成します。 その後、Python でグラフィックス オブジェクトをシリアル化し、それらのオブジェクトを逆シリアル化し、プロットする方法を説明します。

## <a name="review-the-data"></a>データを確認します。

最初に、時間がかかるデータ スキーマを参照するように NYC タクシー データを使用するが容易に変更が加えられました

+ 元のデータセットは、タクシー識別子とトリップ レコードの個別のファイルを使用します。 私たちが参加している 2 つの元のデータセットの列で_medallion_、 _hack_license_、および_pickup_datetime_です。  
+ 元のデータセット ファイルの数をまたがるあり非常に大きいです。 ダウン サンプル レコードの元の数の 1% だけを取得しました。 現在のデータ テーブルには、1,703,957 行と 23 列があります。

**タクシーの識別子**

_Medallion_列は、タクシーの一意の ID 番号を表します。

_Hack_license_列には (匿名化された) タクシー運転免許証番号が含まれています。

**乗車と料金の記録**

各乗車記録には、乗車場所、降車場所、走行距離が含まれています。

各料金記録には、支払の種類、支払の合計額、チップ額など、支払情報が含まれています。

最後の 3 つの列はさまざまな機械学習タスクに利用できます。  _tip_amount_ 列には連続する数値が含まれ、回帰分析用の **label** 列として利用できます。 _tipped_ 列には yes/no 値のみが含まれ、二項分類に利用されます。 _tip_class_ 列には複数の **クラス ラベル** が含まれ、複数クラスの分類タスク用のラベルとして利用できます。

ラベル列として使用される値はすべてに基づいて、`tip_amount`これらのビジネス ルールを使用し、列。

+ ラベル列`tipped`が可能な値 0 および 1

    場合`tip_amount`> 0、 `tipped` = 1 それ以外の場合`tipped`= 0。

+ ラベル列`tip_class`0 ~ 4 の可能なクラスの値を持つ

    クラス 0: `tip_amount` $0 を =

    クラス 1: `tip_amount` > $0 と`tip_amount`< 5 ドルを =
    
    クラス 2: `tip_amount` > $5 と`tip_amount`< 10 ドルを =
    
    クラス 3: `tip_amount` > $10 と`tip_amount`< $20 を =
    
    4 のクラス: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>T-SQL で Python を使用してプロットを作成します。

データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 視覚エフェクトは、データ、外れ値の分布を理解するため、このような強力なツールであるために、Python は、データの視覚化多くのパッケージを提供します。 **Matplotlib**モジュールの視覚エフェクト、人気のあるライブラリの 1 つは、ヒストグラム、散布、ボックス プロット、およびその他のデータ探索のグラフを作成するための多くの関数が含まれています。

このセクションでは、ストアド プロシージャを使用してプロットを操作する方法を学習します。 はなく、サーバー上のイメージを開くよりもに、Python オブジェクトを格納`plot`として**varbinary**データ、および、書き込み、ファイルにしたり共有したりできる他の場所を表示します。

### <a name="create-a-plot-as-varbinary-data"></a>Varbinary データとしてプロットを作成します。

**Revoscalepy** SQL Server 2017 Machine Learning サービスに含まれているモジュールに似た機能をサポートしている、 **RevoScaleR** R. 用のパッケージ この例は、Python の該当するショートカットを使用して`rxHistogram`からデータに基づくヒストグラムをプロットする、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 

ストアド プロシージャが返すシリアル化された Python`figure`オブジェクトのストリームとして**varbinary**データ。 バイナリ データを直接表示することはできませんが、逆シリアル化し、金額を表示するクライアントでの Python コードを使用してクライアント コンピューター上の画像ファイルを保存します。

1. ストアド プロシージャを作成_SerializePlots_PowerShell スクリプトは、既にしなかった場合は、します。

    - 変数`@query`クエリ テキストを定義`SELECT tipped FROM nyctaxi_sample`、スクリプトの入力変数の引数としての Python コード ブロックに渡される`@input_data_1`です。
    - Python スクリプトが非常に単純な: **matplotlib** `figure`オブジェクトが、ヒストグラム、散布図のプロットに使用され、これらのオブジェクトは、シリアル化を使用して、`pickle`ライブラリです。
    - シリアル化する Python グラフィックス オブジェクト、**パンダ**の出力データ フレーム。
  
    ```SQL
    CREATE PROCEDURE [dbo].[SerializePlots]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'
      EXECUTE sp_execute_external_script
      @language = N'Python',
      @script = N'
    import matplotlib
    matplotlib.use("Agg")
    import matplotlib.pyplot as plt
    import pandas as pd
    import pickle

    fig_handle = plt.figure()
    plt.hist(InputDataSet.tipped)
    plt.xlabel("Tipped")
    plt.ylabel("Counts")
    plt.title("Histogram, Tipped")
    plot0 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.tip_amount)
    plt.xlabel("Tip amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Tip amount")
    plot1 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.fare_amount)
    plt.xlabel("Fare amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Fare amount")
    plot2 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.scatter( InputDataSet.fare_amount, InputDataSet.tip_amount)
    plt.xlabel("Fare Amount ($)")
    plt.ylabel("Tip Amount ($)")
    plt.title("Tip amount by Fare amount")
    plot3 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    OutputDataSet = plot0.append(plot1, ignore_index=True).append(plot2, ignore_index=True).append(plot3, ignore_index=True)
    ',
    @input_data_1 = @query
    WITH RESULT SETS ((plot varbinary(max)))
    END
    GO
    ```

2. 今すぐ入力クエリとしてハード コードされたデータから、プロットを生成する引数なしで、ストアド プロシージャを実行します。

    ```
    EXEC [dbo].[SerializePlots]
    ```

3. 結果は、次のようにする必要があります。
  
    ```
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. Python クライアントから今すぐバイナリ プロット オブジェクトを生成する SQL Server インスタンスに接続して、プロットを表示します。 

    これを行うには、サーバー名、データベース名、および適切な資格情報を置き換えて、次の Python コードを実行します。 Python のバージョンが、クライアントとサーバーで同じことを確認してください。 また、Python ライブラリ (matplotlib) などは、クライアントがサーバーにインストールされているライブラリに対する相対同じまたはそれ以降のバージョンであることを確認してください。
  
    **SQL Server 認証を使用します。**
    
    ```python
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[SerializePlots]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Windows 認証を使用します。**

    ```python
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=yes;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[SerializePlots]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  接続が成功した場合は、次のようなメッセージが表示されます。
  
    *プロットがディレクトリに保存されます: xxxx*
  
6.  Python の作業ディレクトリには、出力ファイルが作成されます。 表示するには、プロット Python の作業ディレクトリを検索して、ファイルを開きます。 次の図は、クライアント コンピューターに保存されたプロットを示しています。
  
    ![Vs 運賃金額の量をヒント](media/sqldev-python-sample-plot.png "ヒント量 vs 運賃量") 

## <a name="next-step"></a>次の手順

[手順 4: T-SQL を使用してデータ機能を作成する](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>前の手順

[手順 2: PowerShell を使用した SQL Server へのデータのインポート](sqldev-py2-import-data-to-sql-server-using-powershell.md)

