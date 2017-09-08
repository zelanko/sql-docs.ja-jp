---
title: "手順 3: データの探索と視覚化 | Microsoft Docs"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-python
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
ms.openlocfilehash: dfb80fcd3241b22f0ac72c2cf4cd8a18d1add857
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="step-3-explore-and-visualize-the-data"></a>手順 3: データの探索と視覚化

データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 この手順をサンプル データの調査し、いくつかのプロットを生成します。 後で、Python でグラフィックス オブジェクトをシリアル化し、それらのオブジェクトを逆シリアル化し、プロットする方法を学習します。

> [!NOTE]
> このチュートリアルは、二項分類タスクのみです。他の 2 つの機械学習タスク、回帰と多クラス分類の異なるモデルを構築してみましょうへようこそ があります。

## <a name="review-the-data"></a>データを確認する

元のデータセットでは、タクシーの識別子と乗車記録が別々のファイルに入力されていましたが、 サンプル データの利用を簡単にするために、 _medallion_、 _hack_license_、 _pickup_datetime_列で元のデータセットを結合しました。  レコードもサンプリングされており、元のレコード数の 1% だけが取得されています。 結果的にダウンサンプリングされたデータセットは 1,703,957 行と 23 列です。

**タクシーの識別子**

- _medallion_ 列はタクシーの一意の識別子を表します。
- _hack_license_ 列には、タクシー運転手のライセンス番号が含まれます (匿名にしてあります)。

**乗車と料金の記録**

- 各乗車記録には、乗車場所、降車場所、走行距離が含まれています。
- 各料金記録には、支払の種類、支払の合計額、チップ額など、支払情報が含まれています。
- 最後の 3 つの列はさまざまな機械学習タスクに利用できます。  _tip_amount_ 列には連続する数値が含まれ、回帰分析用の **label** 列として利用できます。 _tipped_ 列には yes/no 値のみが含まれ、二項分類に利用されます。 _tip_class_ 列には複数の **クラス ラベル** が含まれ、複数クラスの分類タスク用のラベルとして利用できます。
- ラベル列に使用される値はすべて _tip_amount_ 列に基づき、次のようなビジネス ルールが適用されます。
  
    |派生列名|Rule|
    |-|-|
     |tipped|tip_amount > 0 の場合、tipped = 1、それ以外では tipped = 0|
    |tip_class|クラス 0: tip_amount = $0<br /><br />クラス 1: tip_amount > $0 および tip_amount <= $5<br /><br />クラス 2: tip_amount > $5 および tip_amount <= $10<br /><br />クラス 3: tip_amount > $10 および tip_amount <= $20<br /><br />クラス 4: tip_amount > $20|

## <a name="create-plots-using-python-in-t-sql"></a>T-SQL で Python を使用してプロットを作成します。

視覚エフェクトは、データ、外れ値の分布を理解するため、このような強力なツールであるために、Python は、データの視覚化多くのパッケージを提供します。 **Matplotlib**モジュールは、ヒストグラム、散布、ボックス プロット、およびその他のデータ探索のグラフを作成するための多くの関数を含む一般的なライブラリです。

このセクションでは、ストアド プロシージャを使用してプロットを操作する方法を学習します。 保存する、 `plot` Python オブジェクトとして、 **varbinary**データ型、およびサーバーで生成されたプロットを保存します。

### <a name="storing-plots-as-varbinary-data-type"></a>varbinary データ型としてプロットを保存する

**Revoscalepy** SQL Server 2017 Machine Learning サービスに含まれているモジュールには、ライブラリ、RevoScaleR パッケージでの R ライブラリに似ていますが含まれています。 Python の該当するショートカットは、この例で使用する`rxHistogram`からデータに基づくヒストグラムをプロットする、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 容易にできるように、ラップする、ストアド プロシージャで_PlotHistogram_です。

ストアド プロシージャが返すシリアル化された Python`figure`オブジェクトのストリームとして**varbinary**データ。 バイナリ データを直接表示することはできませんが、逆シリアル化し、金額を表示するクライアントでの Python コードを使用してクライアント コンピューター上の画像ファイルを保存します。

### <a name="create-the-stored-procedure-plotspython"></a>Plots_Python ストアド プロシージャを作成します。

1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を新しく開きます**クエリ**ウィンドウです。

2.  チュートリアル用のデータベースを選択し、このステートメントを利用してプロシージャを作成します。 必要であれば、正しいテーブル名を使用するようにコードを変更してください。
  
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
**注:**

- 変数`@query`クエリ テキストを定義します (`'SELECT tipped FROM nyctaxi_sample'`)、スクリプトの入力変数の引数としての Python コード ブロックに渡される`@input_data_1`です。
- Python スクリプトが非常に単純な: **matplotlib** `figure`オブジェクトが、ヒストグラム、散布図のプロットに使用され、これらのオブジェクトは、シリアル化を使用して、`pickle`ライブラリです。
- Python グラフィックス オブジェクトは、Python にシリアル化する**パンダ**の出力データ フレーム。

### <a name="output-varbinary-data-to-viewable-graphics-file"></a>表示可能なグラフィックス ファイルに出力 varbinary データ

1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、次のステートメントを実行します。
  
    ```
    EXEC [dbo].[SerializePlots]
    ```
  
    **[結果]**
  
    *プロット*
    *0xFFD8FFE000104A4649 しています.* 
     *0xFFD8FFE000104A4649 しています.* 
     *0xFFD8FFE000104A4649 しています.* 
     *0xFFD8FFE000104A4649 しています.*

  
2.  クライアント コンピューターでは、サーバー名、データベース名、および適切な資格情報を置き換えて、次の Python コードを実行します。
  
    **SQL server 認証。**
    
        ```python
        import pyodbc
        import pickle
        import os
        cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSOWRD}')
        cursor = cnxn.cursor()
        cursor.execute("EXECUTE [dbo].[SerializePlots]")
        tables = cursor.fetchall()
        for i in range(0, len(tables)):
            fig = pickle.loads(tables[i][0])
            fig.savefig(str(i)+'.png')
        print("The plots are saved in directory: ",os.getcwd())
        ```  
    **Windows 認証。**

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

    > [!NOTE]
    > Python のバージョンが、クライアントとサーバーで同じことを確認してください。 また、Python ライブラリ (matplotlib) など、クライアントで使用しているが、サーバーにインストールされているライブラリに対する相対同じまたはそれ以降のバージョンであることを確認してください。


3.  接続が成功した場合は、次の結果が表示されます。
  
    *プロットがディレクトリに保存されます: xxxx*
  
4.  出力ファイルは、Python の作業ディレクトリに作成されます。 プロットを表示するには、Python の作業ディレクトリを開きます。 次の図は、クライアント コンピューターに保存された例プロットを示しています。
  
    ![Vs 運賃金額の量をヒント](media/sqldev-python-sample-plot.png "ヒント量 vs 運賃量") 

## <a name="next-step"></a>次の手順

[手順 4: T-SQL を使用してデータ機能を作成する](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>前の手順

[手順 2: PowerShell を使用して SQL Server にデータをインポートする](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)

