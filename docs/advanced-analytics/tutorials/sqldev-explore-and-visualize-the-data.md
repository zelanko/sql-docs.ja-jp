---
title: レッスン 3 の探索と R と T-SQL (SQL Server Machine Learning) を使用してデータの視覚化 |Microsoft Docs
description: SQL Server に R を埋め込む方法を示すチュートリアルはストアド プロシージャと T-SQL 関数
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6b34de3c71629a1563bf0d480306680dc6253748
ms.sourcegitcommit: 320958d0f55b6974abf46f8a04f7a020ff86a0ae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703625"
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>レッスン 3: 探索し、データの視覚化
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、SQL Server で R を使用する方法に関する SQL 開発者向けのチュートリアルの一部です。

このレッスンでが、サンプル データを確認しを使用していくつかのプロットを生成し、 [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)から[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)および一般的な[Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist)基本 R での関数これらの R 関数が既に含まれている[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]します。

主な目的がから R 関数を呼び出す方法を示す[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャおよびアプリケーション ファイル形式で結果を保存します。

+ ストアド プロシージャを使用して作成**RxHistogram** varbinary データとして R プロットを生成します。 使用**bcp**バイナリ ストリームをイメージ ファイルにエクスポートします。
+ ストアド プロシージャを使用して作成**Hist** JPG、PDF の出力としての結果を保存し、プロットを生成します。

> [!NOTE]
> 視覚化は、データのシェイプと配布を理解するため、このような強力なツールであるために、R は、ヒストグラム、散布、ボックス プロット、およびその他のデータ探索グラフを生成するため関数およびパッケージの範囲を提供します。 R は通常をキャプチャしてとして格納できますが、グラフィック出力の R デバイスを使用してイメージを作成、 **varbinary**アプリケーションで表示するためのデータ型。 サポート ファイルの形式のいずれかに、イメージを保存することもできます (します。JPG、します。PDF など)。

## <a name="review-the-data"></a>データを確認します。

データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 まだ行っていない場合は、まずサンプル データの確認に少し時間がかかります。

元のデータセットでは、タクシーの識別子と乗車記録が別々のファイルに入力されていましたが、 ただし、サンプル データを使用しやすくするには、2 つの元のデータセットが結合されている列_medallion_、 _hack\_ライセンス_、および_pickup\_datetime_します。  レコードもサンプリングされており、元のレコード数の 1% だけが取得されています。 結果的にダウンサンプリングされたデータセットは 1,703,957 行と 23 列です。

**タクシーの識別子**
  
-   _medallion_ 列はタクシーの一意の識別子を表します。
  
-   _Hack\_ライセンス_列には、タクシー運転手のライセンスの数 (匿名化された) が含まれています。
  
**乗車と料金の記録**
  
-   各乗車記録には、乗車場所、降車場所、走行距離が含まれています。
  
-   各料金記録には、支払の種類、支払の合計額、チップ額など、支払情報が含まれています。
  
-   最後の 3 つの列はさまざまな機械学習タスクに利用できます。 _ヒント\_量_列が連続する数値が含まれていますととして使用できる、**ラベル**回帰分析用の列。 _tipped_ 列には yes/no 値のみが含まれ、二項分類に利用されます。 _ヒント\_クラス_列が複数**クラス ラベル**のため、多クラス分類タスク ラベルとして使用することができます。
  
    このチュートリアルでは、二項分類タスクのみを紹介します。他の 2 つの機械学習タスク (回帰と複数クラスの分類) でもモデルの構築をお試しください。
  
-   ラベル列に使用される値はすべてに基づいて、_ヒント\_量_これらのビジネス ルールを使用し、列。
  
    |派生列名|Rule|
    |-|-|
     |tipped|tip_amount > 0 の場合、tipped = 1、それ以外では tipped = 0|
    |tip_class|クラス 0: tip_amount = $0<br /><br />クラス 1: tip_amount > $0 および tip_amount <= $5<br /><br />クラス 2: tip_amount > $5 および tip_amount <= $10<br /><br />クラス 3: tip_amount > $10 および tip_amount <= $20<br /><br />クラス 4: tip_amount > $20|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>RxHistogram を使用してデータをプロットするストアド プロシージャを作成します。

使用して、プロットを作成する[rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram)で提供される拡張 R 関数のいずれかの[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)します。 この手順からのデータに基づいてヒストグラムをプロットする[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 この関数をラップするには、ストアド プロシージャで**PlotHistogram**します。

1. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクト エクスプ ローラーで右クリックし、 **NYCTaxi_Sample**データベースを展開**プログラミング**、順に展開**Stored Procedures**を表示する、レッスン 2 で作成されたプロシージャ。

2. 右クリック**PlotHistogram**選択**変更**ソースを表示します。 呼び出すには、この手順を実行できる**rxHistogram** tipped nyctaxi_sample テーブルの列に含まれるデータにします。

3. 必要に応じて、学習の演習では、次の例を使用してこのストアド プロシージャのコピーを作成します。 新しいクエリ ウィンドウを開き、ヒストグラムをプロットするストアド プロシージャを作成する次のスクリプトに貼り付けます。 この例の名前は**PlotHistogram2**名前の既存のプロシージャでの競合を回避するためにします。

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram2]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =  
      N'SELECT tipped FROM nyctaxi_sample'  
      EXECUTE sp_execute_external_script @language = N'R',  
                                         @script = N'  
       image_file = tempfile();  
       jpeg(filename = image_file);  
       #Plot histogram  
       rxHistogram(~tipped, data=InputDataSet, col=''lightgreen'',   
       title = ''Tip Histogram'', xlab =''Tipped or not'', ylab =''Counts'');  
       dev.off();  
       OutputDataSet <- data.frame(data=readBin(file(image_file, "rb"), what=raw(), n=1e6));  
       ',  
       @input_data_1 = @query  
       WITH RESULT SETS ((plot varbinary(max)));  
    END
    GO
    ```

ストアド プロシージャ**PlotHistogram2**の既存のストアド プロシージャと同じ**PlotHistogram**によって作成された、`RunSQL_SQL_Walkthrough.ps1`スクリプト。 
  
+ 変数 `@query` によりクエリ テキスト (`'SELECT tipped FROM nyctaxi_sample'`) が定義され、スクリプト入力変数 `@input_data_1`の引数として R スクリプトに渡されます。
  
+ R スクリプトは非常に単純な: R 変数 (`image_file`)、イメージを格納するように定義し、 **rxHistogram**関数が呼び出され、プロットを生成します。
  
+ 設定されている R デバイス**オフ**SQL Server の外部のスクリプトとしてこのコマンドを実行しているためです。 通常、R で高レベルのプロット コマンドを発行するときに R グラフィックス、ウィンドウを開きますと呼ばれる、*デバイス*します。 ウィンドウのサイズ、色、その他の特徴を変更できます。あるいは、ファイルに書き込み、別の方法で出力を処理する場合、デバイスをオフにできます。
  
+ R グラフィックス オブジェクトは、出力のために R data.frame にシリアル化されます。

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>ストアド プロシージャを実行し、bcp を使用してバイナリ データをイメージ ファイルにエクスポートするには

ストアド プロシージャは varbinary データのストリームとして画像を返し、直接見ることはできません。 ただし、 **bcp** ユーティリティを利用すれば、varbinary データを取得し、クライアント コンピューターに画像ファイルとして保存できます。
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、次のステートメントを実行します。
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **結果**
    
    *plot*
    *0xFFD8FFE000104A4649...*
  
2.  PowerShell コマンド プロンプトを開き、適切なインスタンス名、データベース名、ユーザー名、および引数としての資格情報を提供する、次のコマンドを実行します。 Windows id を使用してそれらを置き換えることができます **-u**と **-p**で **-t**します。
  
     ```text
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  TaxiNYC_Sample  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Bcp コマンド スイッチは大文字小文字を区別します。
  
3.  接続に成功した場合は、グラフィック ファイル形式に関する詳細情報を入力するように求められます。 

   プロンプトのたびに ENTER キーを押し、初期設定を適用します。ただし、次については変更します。
    
    -   **フィールド プロットのプレフィックス長**に「0」を入力します。
  
    -   後で再利用するために出力パラメーターを保存する場合、「 **Y** 」を入力します。
  
    ```
    Enter the file storage type of field plot [varbinary(max)]: 
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **結果**
    
    ```
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > フォーマット情報をファイル (bcp.fmt) に保存する場合、 **bcp** ユーティリティによりフォーマット定義が生成されます。それを今後、同様のコマンドに適用できます。グラフィック ファイル フォーマットの選択を求められません。 フォーマット ファイルを使用するには、 `-f bcp.fmt` をコマンド行の終わりに追加します。パスワード引数の後です。
  
4.  出力ファイルは、PowerShell コマンドを実行した同じディレクトリに作成されます。 プロットを表示するには、ファイル plot.jpg を開きます。
  
    ![チップありとチップなしのタクシー乗車](media/rsql-devtut-tippedornot.jpg "チップありとチップなしのタクシー乗車")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Hist と複数の出力形式を使用してストアド プロシージャを作成します。

通常、データ サイエンティストは、さまざまな観点から、データに関する洞察を取得する複数のデータ視覚エフェクトを生成します。 この例では、ストアド プロシージャなど、一般的な形式にバイナリ データをエクスポート、ヒストグラムを作成するのに Hist 関数を使用します。JPG、します。PDF と。PNG。 

1. 既存のストアド プロシージャを使用して、 **PlotInOutputFiles**ヒストグラム、や散布図など、およびその他の R グラフィックスを記述します。JPG とします。PDF 形式です。 `RunSQL_SQL_Walkthrough.ps1`作成**PlotInOutputFiles**し、データベースを追加します。 右クリックを使用して、**変更**ソースを表示します。

2. 必要に応じて、学習の演習では、プロシージャとしての独自のコピーを作成**PlotInOutputFiles2**、名前付けの競合を回避するために一意の名前。

    [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、新しく開きます**クエリ**ウィンドウ、および貼り付けでは、次に[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles2]  
    AS  
    BEGIN  
      SET NOCOUNT ON;  
      DECLARE @query nvarchar(max) =  
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'  
      EXECUTE sp_execute_external_script @language = N'R',  
      @script = N'  
       # Set output directory for files and check for existing files with same names   
        mainDir <- ''C:\\temp\\plots''  
        dir.create(mainDir, recursive = TRUE, showWarnings = FALSE)  
        setwd(mainDir);  
        print("Creating output plot files:", quote=FALSE)
        
        # Open a jpeg file and output histogram of tipped variable in that file.  
        dest_filename = tempfile(pattern = ''rHistogram_Tipped_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.jpg'',sep="")  
        print(dest_filename, quote=FALSE);  
        jpeg(filename=dest_filename);  
        hist(InputDataSet$tipped, col = ''lightgreen'', xlab=''Tipped'',   
            ylab = ''Counts'', main = ''Histogram, Tipped'');  
         dev.off();  

        # Open a pdf file and output histograms of tip amount and fare amount.   
        # Outputs two plots in one row  
        dest_filename = tempfile(pattern = ''rHistograms_Tip_and_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=7);  
        par(mfrow=c(1,2));  
        hist(InputDataSet$tip_amount, col = ''lightgreen'',   
            xlab=''Tip amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram, Tip amount'', xlim = c(0,40), 100);  
        hist(InputDataSet$fare_amount, col = ''lightgreen'',   
            xlab=''Fare amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram,   
            Fare amount'',   
            xlim = c(0,100), 100);  
       dev.off();  
  
        # Open a pdf file and output an xyplot of tip amount vs. fare amount using lattice;  
        # Only 10,000 sampled observations are plotted here, otherwise file is large.  
        dest_filename = tempfile(pattern = ''rXYPlots_Tip_vs_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=4);  
        plot(tip_amount ~ fare_amount,   
            data = InputDataSet[sample(nrow(InputDataSet), 10000), ],   
            ylim = c(0,50),   
            xlim = c(0,150),   
            cex=.5,   
            pch=19,   
            col=''darkgreen'',    
            main = ''Tip amount by Fare amount'',   
            xlab=''Fare Amount ($)'',   
            ylab = ''Tip Amount ($)'');   
        dev.off();',  
     @input_data_1 = @query  
     END
    ```
  
+ ストアド プロシージャ内の SELECT クエリの出力が既定の R データ フレーム `InputDataSet`に保存されます。 さまざまな R プロット関数を呼び出し、実際のグラフィックス ファイルを生成できます。 埋め込み R スクリプトのほとんどがそのようなグラフィックス関数のオプションを表します。`plot` や `hist` などです。
  
+ すべてのフォルダーがローカル フォルダー _C:\temp\Plots\\_ に保存されます。 宛先フォルダーはストアド プロシージャの一部として R スクリプトに渡された引数により定義されます。  変数 `mainDir`の値を変更して宛先フォルダーを変更できます。

+ ファイルを別のフォルダーに出力するには、ストアド プロシージャに埋め込まれている R スクリプトの `mainDir` 変数の値を変更します。 スクリプトを変更し、さまざまなフォーマットを出力したり、出力するファイルを増やしたりできます。

### <a name="execute-the-stored-procedure"></a>ストアド プロシージャを実行する

プロットをバイナリ データを JPEG、PDF ファイル形式にエクスポートするのには、次のステートメントを実行します。

```SQL
EXEC PlotInOutputFiles
```

**結果**
    
```
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

ファイル名に番号が既存のファイルに書き込むときにエラーが発生しないことを確認します。 ランダムに生成されます。

### <a name="view-output"></a>出力の表示 

プロットを表示するには、コピー先のフォルダーを開き、ストアド プロシージャで R コードで作成されたファイルを確認します。

1. STDOUT メッセージで示されているフォルダーを参照してください (例では、これは C:\temp\plots\)

2. 開いている`rHistogram_Tipped.jpg`チップをもらわなかった乗車とヒントを取得した乗車の数を表示します。 (このヒストグラムは、前の手順で生成したものと同様です)。

3. 開いている`rHistograms_Tip_and_Fare_Amount.pdf`料金の金額のプロット、チップの金額の分布を表示します。
    
  ![tip_amount と fare_amount を示すヒストグラム](media/rsql-devtut-tipamtfareamt.PNG "tip_amount と fare_amount を示すヒストグラム")

4. 開いている`rXYPlots_Tip_vs_Fare_Amount.pdf`x 軸と y 軸をチップ額の料金での散布図を表示します。

   ![チップの金額のプロット fare 量](media/rsql-devtut-tipamtbyfareamt.PNG "料金経由でチップの金額のプロット")

## <a name="next-lesson"></a>次のレッスン

[レッスン 3: T-SQL を使用してデータ機能を作成します。](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 1: NYC タクシーのデモ データの設定します。](sqldev-download-the-sample-data.md)
