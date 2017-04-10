---
title: "R を利用してグラフやプロットを作成する (データ サイエンスのエンド ツー エンド チュートリアル) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
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
ms.assetid: 5f70f0a6-fd4a-410f-9f44-1605503f77ec
caps.latest.revision: 16
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# R を利用してグラフやプロットを作成する (データ サイエンスのエンド ツー エンド チュートリアル)
このレッスンでは、R と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データを利用してプロットやマップを生成する方法について説明します。  サーバーで作成されたプロットを簡単に表示できます。また、グラフィックス オブジェクトをサーバーに渡すことができます。  
  
## <a name="creating-graphics"></a>グラフィックスの作成
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]では、モデルや結果と同様に、グラフィックス オブジェクトがコンピューターと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューティング コンテキストの間でシリアル化されます。

SQL Server 計算コンテキストを使用するとき、マップ表示をダウンロードできないことがあります。ほとんどの運用データベース サーバーでは、インターネット アクセスが完全に阻止されるためです。  そのため、プロットの 2 つ目のセットを作成するには、クライアントでマップ表示を生成し、*nyctaxi_sample* テーブルに属性として保存されているポイントをマップ上でオーバーレイします。   

これを行うは、最初に Google マップを呼び出し、マップ表示を作成します。次に SQL コンテキストにマップ表示を渡します。  
  
このパターンは、独自のアプリケーションの開発時に役立つことがあります。   
  
### <a name="create-a-histogram"></a>ヒストグラムの作成  
ヒストグラムを作成するには、先に作成した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ソースと、R Services で提供される `rxHistogram` 関数を利用します。  
  
1.  *rxHistogram* 関数を利用し、最初のプロットを生成します。  *rxHistogram* 関数は、オープン ソース R パッケージのそれと同様の機能を提供しますが、リモート実行コンテキストで実行できます。 
  
    ```R  
    #Plot fare amount on SQL Server and return the plot  
    start.time <- proc.time()  
    rxHistogram(~fare_amount, data = inDataSource, title = "Fare Amount Histogram")  
    used.time <- proc.time() - start.time  
    print(paste("It takes CPU Time=", round(used.time[1]+used.time[2],2), " seconds, Elapsed Time=", round(used.time[3],2), " seconds to generate features.", sep=""))    
    ```         
  
2.  この画像はお使いの開発環境の R グラフィックス デバイスで返されたものです。  たとえば、RStudio で、 **プロット** ウィンドウをクリックします。  [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)]で、別個のグラフィックス ウィンドウが開きます。  
  
    ![using rxHistogram to plot fare amounts](../../advanced-analytics/r-services/media/rsql-e2e-rxhistogramresult.png "using rxHistogram to plot fare amounts")  
  
    > [!NOTE]  TOP を利用した行の順序付けは ORDER BY 句なしでは非決定性となるため、かなり異なる結果が表示される場合があります。 行数を変えて、実験してみることをお勧めします。お使いの環境で結果を得るためにかかった時間をメモしてください。  この画像は ～ 10,000 行のデータを利用して生成されました。
  
### <a name="create-a-map-plot"></a>マップ プロットの作成  
この例では、コンピューティング コンテキストとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを利用してプロット オブジェクトを生成します。それからプロット オブジェクトをローカルのコンピューティング コンテキストに返し、レンダリングします。  
   
1.  まず、プロット オブジェクトを作成する関数を定義します。  

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
    + カスタム R 関数 *mapPlot* は、タクシーが客を乗せた場所を利用し、それぞれの場所から開始した乗車の数をプロットする散布図を作成します。 これは **ggplot2** パッケージと **ggmap** パッケージを利用します。この 2 つのパッケージは既にインストールされ、読み込まれているはずです。  
    + カスタム関数 *mapPlot* は引数を 2 つ取得します。*RxSqlServerData* を利用して先に定義した既存のデータ オブジェクトとクライアントから渡されたマップ表示です。    
    + *ds* 変数を利用し、前に作成したデータ ソース *inDataSource* からデータを読み込むことに注意してください。  オープン ソース R 関数を使用するときは、データをメモリのデータ フレームに読み込む必要があります。 それは **RevoScaleR** パッケージの *rxImport* 関数を利用して実行できます。  ただし、この関数は、先に定義された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンテキストにおいてメモリで実行されます。 つまり、この関数はローカル ワークステーションのメモリを利用しません。  
  
2.  次に、ローカルの R 環境でマップを作成するために必要なライブラリを読み込みます。  
  
    ```R  
    library(ggmap)  
    library(mapproj)  
    gc <- geocode("Times Square", source = "google")  
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color';    
    ```  
    + このコードは R クライアントで実行されます。 ライブラリの **ggmap** と **mapproj**が繰り返し呼び出されることに注意してください。 これは、前の関数定義がサーバー コンテキストで実行され、ライブラリがローカルで読み込まれていないためです。今度はプロット操作をワークステーションに戻します。  
  
    -   *gc* 変数は、ニューヨークにあるタイムズ スクウェアの一組の座標を保存します。  
  
    -   *googmap* で始まる行により、指定した座標を中心に据えるマップが生成されます。  
          
  
3.  プロット関数を実行し、ローカルの R 環境で結果をレンダリングします。 これを行うには、ここで示すように *rxExec* でプロット関数をラップします。  *rxExec* 関数は **RevoScaleR** パッケージに含まれ、リモート コンピューティング コンテキストで任意の R 関数の実行をサポートします。 
  
    ```R  
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)  
    plot(myplots[[1]][["myplot"]]);  
  
    ```  
    + 最初の行で、リモート実行される関数 *mapPlot* に引数 (*googMap*) としてマップ データが渡されることを確認できます。 これはマップがローカル環境で生成されたためです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のコンテキストでプロットを作成するために関数に渡す必要があります。   
  
        レンダリングされたデータはローカルの R 環境で再びシリアル化されます。RStudio またはその他の R グラフィックス デバイスの **プロット** ウィンドウを利用して表示できます。  
  
  
4.  出力プロットは次のようになります。マップ上の赤い点が乗車場所です。  
  
    ![plotting taxi rides using a custom R function](../../advanced-analytics/r-services/media/rsql-e2e-mapplot.png "plotting taxi rides using a custom R function")  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 3: データ機能の作成 (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-3-create-data-features-data-science-end-to-end-walkthrough.md)  
  
  
  
