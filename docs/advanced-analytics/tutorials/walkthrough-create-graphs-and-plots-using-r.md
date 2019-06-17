---
title: グラフやプロットの SQL と R 関数の SQL Server Machine Learning を使用して作成します。
description: グラフや SQL Server で R 言語の関数を使用してプロットを作成する方法を示すチュートリアルです。
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: b988105733d8e3a9ee2edae344947cbf9d377e5d
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140385"
---
# <a name="create-graphs-and-plots-using-sql-and-r-walkthrough"></a>グラフやプロットの SQL と R (チュートリアル) を使用して作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このチュートリアルでは、SQL Server データと R を使用して、マップとプロットを生成する方法について説明します。 単純なヒストグラムを作成しより複雑なマップ プロットを作成します。

## <a name="prerequisites"></a>前提条件

この手順では、このチュートリアルで前の手順に基づいて継続的な R セッションを想定しています。 これらの手順で作成された接続文字列およびデータ ソース オブジェクトを使用します。 次のツールとパッケージは、スクリプトの実行に使用されます。

+ Rgui.exe R コマンドを実行するには
+ Management Studio を T-SQL の実行
+ googMap
+ ggmap パッケージ
+ mapproj パッケージ

## <a name="create-a-histogram"></a>ヒストグラムを作成します。

1. [rxHistogram](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxdatasource) 関数を利用し、最初のプロットを生成します。  RxHistogram 関数は、オープン ソース R パッケージと同様の機能を提供しますが、リモート実行コンテキストで実行できます。

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
    > グラフが異なるようでしょうか。
    >  
    > だ_inDataSource_上位 1000 行のみを使用します。 TOP を使用して行の順序は、データと、結果のグラフを異なる場合がありますが必要ですが、最初の ORDER BY 句がない場合は、決定的です。
    > この画像は約 10,000 行のデータを利用して生成されました。 行数を変えて、実験してみることをお勧めします。お使いの環境で結果を得るためにかかった時間をメモしてください。

## <a name="create-a-map-plot"></a>マップ プロットを作成します。

通常、データベース サーバーは、インターネットへのアクセスをブロックします。 これは不都合マップまたはプロットを生成する他のイメージをダウンロードする必要がある R パッケージを使用する場合。 ただし、役に立つ、独自のアプリケーションを開発する際にする回避策があります。 基本的に、クライアントでは、マップ表示を生成し、SQL Server テーブルの属性として格納されているポイントのマップをオーバーレイします。

1. R プロット オブジェクトを作成する関数を定義します。 カスタム関数*mapPlot*がタクシーの乗車場所を使用し、各場所から開始した乗車の数をプロットする散布図を作成します。 使用して、 **ggplot2**と**ggmap**パッケージは既にこの[インストールされ、読み込まれた](walkthrough-data-science-end-to-end-walkthrough.md#add-packages)します。

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

    + *MapPlot*関数は 2 つの引数を受け取ります。 RxSqlServerData、を使用して定義すると、クライアントから渡されたマップ表示を、既存のデータ オブジェクト。
    + 始まる行で、 *ds*変数 rxImport を使って、以前に作成したデータ ソースからデータをメモリに読み込む*inDataSource*します。 (そのデータ ソースには、1000 を超える行が含まれています。 データ ポイントを詳細マップを作成する場合は、別のデータ ソースを置き換えることができます)。
    + オープン ソース R 関数を使用するたびにデータをローカル メモリ内のデータ フレームに読み込む必要があります。 ただしを呼び出して、 [rxImport](https://docs.microsoft.com/r-server/r-reference/revoscaler/rximport)関数の場合、リモート コンピューティング コンテキストのメモリで実行することができます。

2. ローカル コンピューティング コンテキストを変更し、マップを作成するために必要なライブラリを読み込みます。

    ```R
    rxSetComputeContext("local")
    library(ggmap)
    library(mapproj)
    gc <- geocode("Times Square", source = "google")
    googMap <- get_googlemap(center = as.numeric(gc), zoom = 12, maptype = 'roadmap', color = 'color');
    ```

    + `gc` 変数は、ニューヨークにあるタイムズ スクウェアの一組の座標を保存します。

    + `googmap` で始まる行により、指定した座標を中心に据えるマップが生成されます。

3. SQL Server 計算コンテキストに切り替えるしでプロット関数をラップすることによって、結果をレンダリング[rxExec](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxexec)次のようにします。 RxExec 関数の一部である、 **RevoScaleR**パッケージ、およびリモート コンピューティング コンテキストで任意の R 関数の実行をサポートします。

    ```R
    rxSetComputeContext(sqlcc)
    myplots <- rxExec(mapPlot, inDataSource, googMap, timesToRun = 1)
    plot(myplots[[1]][["myplot"]]);
    ````

    + マップ データを`googMap`、リモートで実行される関数に引数として渡される*mapPlot*します。 マップは、ローカル環境で生成されたためする必要があります渡すことが関数に SQL Server のコンテキストでプロットを作成するためにします。

    + で始まる行`plot`R クライアントを表示できるように、実行、表示されたデータがローカルの R 環境にシリアル化します。

    > [!NOTE]
    > Azure の仮想マシンで SQL Server を使用する場合は、この時点でエラーを取得可能性があります。 Azure での既定のファイアウォール規則は、R コードでネットワーク アクセスをブロックした場合、エラーが発生します。 このエラーを解決する方法の詳細については、次を参照してください。 [Azure VM での Machine Learning のインストール (R) サービス](../install/sql-machine-learning-azure-virtual-machine.md)します。

4. 出力プロットは次の図のようになります。 乗車場所が赤い点でマップ上に追加されます。 イメージは異なる場所の数が使用したデータ ソースによってになります。

    ![カスタムの R 関数を使用したタクシーの乗車のプロット](media/rsql-e2e-mapplot.png "カスタムの R 関数を使用したタクシーの乗車のプロット")

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [R と SQL を使用してデータ機能を作成します。](walkthrough-create-data-features.md)
