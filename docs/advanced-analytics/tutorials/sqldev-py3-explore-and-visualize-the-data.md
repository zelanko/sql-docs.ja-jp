---
title: レッスン 1 の探索と、Python、T-SQL、SQL Server Machine Learning を使用してデータを視覚化します。
description: 埋め込む方法を示すチュートリアル SQL Server での Python ストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: e9dd0a0884c96a8f5b17948c21b7f891a2e997ab
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860493"
---
# <a name="explore-and-visualize-the-data"></a>探索し、データの視覚化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルの一部[SQL 開発者向けの in-database Python analytics](sqldev-in-database-python-for-sql-developers.md)します。 

このステップでは、サンプル データを探索し、いくつかのプロットを生成します。 その後、Python でのグラフィック オブジェクトをシリアル化しし、それらのオブジェクトを逆シリアル化して、プロットを作成する方法について説明します。

## <a name="review-the-data"></a>データを確認します。

まず、少し、データ スキーマを参照するように、NYC タクシー データを使用するが容易にいくつかの変更を行いました

+ 元のデータセットは、タクシーの識別子と乗車記録に個別のファイルを使用します。 列に 2 つの元のデータセットを参加_medallion_、 _hack_license_、および_pickup_datetime_します。  
+ 元のデータセットでは、多数のファイルをスパンおよびが非常に大きくします。 レコードの元の数の 1% だけを取得する downsampled を用意しています。 現在のデータ テーブルには、1,703, 957 行と 23 列があります。

**タクシーの識別子**

_Medallion_列はタクシーの一意の ID 番号を表します。

_Hack_license_列には、タクシー運転手のライセンスの数 (匿名化された) が含まれています。

**乗車と料金の記録**

各乗車記録には、乗車場所、降車場所、走行距離が含まれています。

各料金記録には、支払の種類、支払の合計額、チップ額など、支払情報が含まれています。

最後の 3 つの列はさまざまな機械学習タスクに利用できます。  _tip_amount_ 列には連続する数値が含まれ、回帰分析用の **label** 列として利用できます。 _tipped_ 列には yes/no 値のみが含まれ、二項分類に利用されます。 _tip_class_ 列には複数の **クラス ラベル** が含まれ、複数クラスの分類タスク用のラベルとして利用できます。

ラベル列に使用される値はすべてに基づいて、`tip_amount`これらのビジネス ルールを使用し、列。

+ ラベル列`tipped`が使用可能な値 0 および 1

    場合`tip_amount`> 0、 `tipped` = 1 それ以外の場合以外は`tipped`= 0。

+ ラベル列`tip_class`が可能なクラスの値 0-4

    クラス 0: `tip_amount` = $0

    クラス 1: `tip_amount` > $0 と`tip_amount`< = $5
    
    クラス 2: `tip_amount` > $5 と`tip_amount`< = $10
    
    クラス 3: `tip_amount` > $10 と`tip_amount`< = $20
    
    クラス 4: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>T-SQL で Python を使用してプロットを作成します。

データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 視覚化は、データや外れ値の分布を理解するため、このような強力なツールであるために、Python は、データを視覚化するための多くのパッケージを提供します。 **Matplotlib**モジュールは、視覚化より一般的なライブラリの 1 つし、ヒストグラム、散布、ボックス プロット、およびその他のデータ探索グラフを作成するための多くの関数が含まれています。

このセクションでは、ストアド プロシージャを使用してプロットを操作する方法について説明します。 はなく、サーバー上のイメージを開くよりもに、Python オブジェクトを格納`plot`として**varbinary**データ、および、書き込み、ファイルを共有したり別の場所に表示します。

### <a name="create-a-plot-as-varbinary-data"></a>Varbinary データとしてプロットを作成します。

ストアド プロシージャが返すシリアル化された Python`figure`オブジェクトのストリームとして**varbinary**データ。 直接、バイナリ データを表示することはできませんが、逆シリアル化し、数値を表示するクライアントでの Python コードを使用して、クライアント コンピューターにイメージ ファイルを保存します。

1. ストアド プロシージャを作成**PyPlotMatplotlib**PowerShell スクリプトは、既にしなかった場合は、します。

    - 変数`@query`クエリ テキストを定義します。 `SELECT tipped FROM nyctaxi_sample`、Python のコード ブロックに、スクリプトの入力変数を引数として渡される`@input_data_1`します。
    - Python スクリプトは非常に単純: **matplotlib** `figure`オブジェクトを使用して、ヒストグラム、散布図のプロットを作成し、これらのオブジェクトを使用してシリアル化は、`pickle`ライブラリ。
    - シリアル化する Python のグラフィック オブジェクト、 **pandas**出力データ フレーム。
  
    ```sql
    DROP PROCEDURE IF EXISTS PyPlotMatplotlib;
    GO

    CREATE PROCEDURE [dbo].[PyPlotMatplotlib]
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

2. 今すぐ入力クエリとしてハード コードされたデータからプロットを生成する引数なしで、ストアド プロシージャを実行します。

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. 結果は、次のようになります。
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. [Python クライアント](../python/setup-python-client-tools-sql.md)、バイナリ プロット オブジェクトを生成する SQL Server インスタンスに接続し、プロットを表示できますようになりました。 

    これを行うには、サーバー名、データベース名、および適切な資格情報に置き換えて、次の Python コードを実行します。 Python のバージョンが、クライアントとサーバーで同じことを確認します。 また、Python ライブラリ (matplotlib など)、クライアントがサーバーにインストールされているライブラリを基準と同等以上のバージョンであることを確認してください。
  
    **SQL Server 認証を使用します。**
    
    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Windows 認証を使用します。**

    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=True;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  接続が成功した場合、次のようなメッセージが表示されます。
  
    *プロットは、ディレクトリに保存されます: xxxx*
  
6.  出力ファイルは、Python の作業ディレクトリに作成されます。 プロットを表示するには、Python の作業ディレクトリをファイルを開きます。 次の図は、クライアント コンピューターに保存されたプロットを示します。
  
    ![チップの金額と料金の金額](media/sqldev-python-sample-plot.png "量と料金でチップの金額") 

## <a name="next-step"></a>次の手順

[T-SQL を使用してデータ機能を作成します。](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>前の手順

[NYC タクシー データ セットをダウンロードします。](demo-data-nyctaxi-in-sql.md)

