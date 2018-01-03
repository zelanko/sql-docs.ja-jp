---
title: "グラフおよび SQL と R (チュートリアル) を使用してプロットを作成 |Microsoft ドキュメント"
ms.date: 11/10/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: 5f70f0a6-fd4a-410f-9f44-1605503f77ec
caps.latest.revision: "16"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: f2e644f052ed2cf4fbfbabb11752a6e29a007b5b
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>グラフや SQL と R (チュートリアル) を使用してプロットを作成します。

このチュートリアルでは、プロットと SQL Server データを R を使用して、マップを生成する方法を説明します。 いくつかの方法を取得する、単純なヒストグラムを作成しより複雑なマップ プロットを作成します。

### <a name="create-a-histogram"></a>ヒストグラムを作成します。

1. [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) 関数を利用し、最初のプロットを生成します。  RxHistogram 関数オープン ソース R パッケージと同様の機能には、リモートの実行コンテキストで実行できます。

    ```R
    # Plot fare amount on SQL Server and return the plot
    start.time <- proc.time()
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")
    used.time <- proc.time() - start.time
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate plot.", sep=""))
    ```

2. この画像はお使いの開発環境の R グラフィックス デバイスで返されたものです。  たとえば、RStudio で、 **プロット** ウィンドウをクリックします。  [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]で、別個のグラフィックス ウィンドウが開きます。

    ![rxHistogram を使用した料金の金額のプロット](media/rsql-e2e-rxhistogramresult.png "rxHistogram を使用した料金の金額のプロット")

    > [!NOTE]
    > グラフ レイアウトが変化します。
    >  
    > これはため_inDataSource_上位 1000 行のみを使用します。 TOP を使用して行の順序は、データと結果のグラフが異なる場合があることを想定して、ORDER BY 句がない場合は決定的です。
    > この画像は約 10,000 行のデータを利用して生成されました。 行数を変えて、実験してみることをお勧めします。お使いの環境で結果を得るためにかかった時間をメモしてください。

### <a name="create-a-map-plot"></a>マップ プロットを作成します。

通常、データベース サーバーは、インターネット アクセスをブロックします。 これは不都合マップまたはプロットを生成するには、その他のイメージをダウンロードする必要がある R パッケージを使用する場合。 ただし、これには役に立つ、独自のアプリケーションを開発するときにする回避策があります。 基本的には、クライアントでは、マップの表現を生成し、SQL Server テーブルの属性として保存されている点で、マップをオーバーレイします。

1. R プロット オブジェクトを作成する関数を定義します。 ユーザー定義関数*mapPlot*タクシーのピックアップ場所を使用し、各場所から開始乗っての数をプロットする散布図を作成します。 これは **ggplot2** パッケージと  **ggmap** パッケージを利用します。この 2 つのパッケージは既にインストールされ、読み込まれているはずです。

    ```R
    mapPlot <- function(inDataSource, googMap){
        library(ggmap)
        library(mapproj)
        ds <- rxImport(inDataSource)
        p <- ggmap(googMap)+
        geom_point(aes(x = pickup_longitude, y =pickup_latitude ), data=ds, alpha =.5,
    color="darkred", size = 1.5)
        return(list(myplot=p))
    }
    ```

    + *MapPlot*関数は 2 つの引数を受け取ります。 RxSqlServerData、を使って以前定義した、クライアントからマップ表現が渡された既存のデータ オブジェクト。
    + 始まる行で、 *ds*変数、rxImport のため、以前に作成したデータ ソースからデータをメモリに読み込む*inDataSource*です。 (そのデータ ソースには、1000 を超える行が含まれています。 データ要素を持つマップを作成する場合は、別のデータ ソースを置き換えることができます。)
    + 使用するたびに**オープン ソース**R 関数、データをデータ フレームのローカル メモリに読み込む必要があります。 ただしを呼び出して、 [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport)関数の場合、リモート計算コンテキストのメモリで実行することができます。

2. コンピューティング コンテキストをローカルに変更し、マップの作成に必要なライブラリを読み込みます。

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + `gc` 変数は、ニューヨークにあるタイムズ スクウェアの一組の座標を保存します。

    + `googmap` で始まる行により、指定した座標を中心に据えるマップが生成されます。

3. SQL Server のコンピューティング コンテキストに切り替え、プロットの関数をラップすることによって、結果をレンダリング[rxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec)次に示すようにします。 RxExec 関数の一部である、 **RevoScaleR**パッケージ、およびリモート計算コンテキストでの任意の R 関数の実行をサポートしています。

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + マップ データを`googMap`リモートで実行される関数に引数として渡される*mapPlot*です。 マップが生成されるため、ローカル環境で、必要があります渡すことが関数に SQL Server のコンテキストでは、プロットを作成するためにします。

    + で始まる行`plot`実行、表示されたデータはシリアル化され、ローカルの R 環境に、R クライアントで表示することができます。

    > [!NOTE]
    > Azure の仮想マシンにおける SQL Server を使用している場合は、この時点でエラーが発生した可能性があります。 Azure での既定のファイアウォール ルールは、R コードでネットワーク アクセスをブロックするためです。 このエラーを解決する方法の詳細については、「 [Azure VM での R Services のインストール](../r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)です。

4. 出力プロットは次の図のようになります。 乗車場所が赤い点でマップ上に追加されます。 イメージは、によって異なります、どのようにさまざまな場所が使用したデータ ソースになります。

    ![カスタムの R 関数を使用したタクシーの乗車のプロット](media/rsql-e2e-mapplot.png "カスタムの R 関数を使用したタクシーの乗車のプロット")

## <a name="next-lesson"></a>次のレッスン

[R と SQL を使用してデータ機能を作成します。](/walkthrough-create-data-features.md)

## <a name="previous-lesson"></a>前のレッスン

[R を使用するデータを概要します。](/walkthrough-view-and-summarize-data-using-r.md)
