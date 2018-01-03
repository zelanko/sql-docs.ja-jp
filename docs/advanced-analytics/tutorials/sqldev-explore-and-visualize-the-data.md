---
title: "レッスン 3: 探索し、データの視覚化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 7fe670f3-5e62-43ef-97eb-b9af54df9128
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a47e9d2b2bec007af27b8e8ce26d6a6c6f67c3f
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>レッスン 3: 探索し、データの視覚化

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

このレッスンでは、サンプル データを確認し、R 関数を使用していくつかのプロットを生成します。 これらの R 関数が既に含まれている[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]です。 R 関数を呼び出すことができます[!INCLUDE[tsql](../../includes/tsql-md.md)]です。

## <a name="review-the-data"></a>データを確認します。

データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 まず、時間がかかるサンプル データの確認をまだ行っていない場合。

元のデータセットでは、タクシーの識別子と乗車記録が別々のファイルに入力されていましたが、 ただし、サンプル データを使用しやすくするには、2 つの元のデータセットが結合されて、列に_medallion_、 _hack\_ライセンス_、および_ピックアップ\_datetime_です。  レコードもサンプリングされており、元のレコード数の 1% だけが取得されています。 結果的にダウンサンプリングされたデータセットは 1,703,957 行と 23 列です。

**タクシーの識別子**
  
-   _medallion_ 列はタクシーの一意の識別子を表します。
  
-   _Hack\_ライセンス_列には (匿名化された) タクシー運転免許証番号が含まれています。
  
**乗車と料金の記録**
  
-   各乗車記録には、乗車場所、降車場所、走行距離が含まれています。
  
-   各料金記録には、支払の種類、支払の合計額、チップ額など、支払情報が含まれています。
  
-   最後の 3 つの列はさまざまな機械学習タスクに利用できます。  _ヒント\_量_列は、連続する数値が含まれており、として使用できる、**ラベル**回帰分析のための列です。 _tipped_ 列には yes/no 値のみが含まれ、二項分類に利用されます。 _ヒント\_クラス_列が複数**クラス ラベル**のため多クラス分類タスクのラベルとして使用することができます。
  
    このチュートリアルでは、二項分類タスクのみを紹介します。他の 2 つの機械学習タスク (回帰と複数クラスの分類) でもモデルの構築をお試しください。
  
-   ラベル列として使用される値はすべてに基づいて、_ヒント\_量_これらのビジネス ルールを使用し、列。
  
    |派生列名|Rule|
    |-|-|
     |tipped|tip_amount > 0 の場合、tipped = 1、それ以外では tipped = 0|
    |tip_class|クラス 0: tip_amount = $0<br /><br />クラス 1: tip_amount > $0 および tip_amount <= $5<br /><br />クラス 2: tip_amount > $5 および tip_amount <= $10<br /><br />クラス 3: tip_amount > $10 および tip_amount <= $20<br /><br />クラス 4: tip_amount > $20|

## <a name="create-plots-using-r-in-t-sql"></a>T-SQL で R を使用してプロットを作成します。

データの分布や外れ値を理解する上で視覚化は強力なツールとなります。R はデータを視覚化するためのさまざまなパッケージを提供します。 R の標準オープンソース配布には、ヒストグラム、散布図、箱ひげ図、その他のデータ探索グラフを作成するためのさまざまな関数が含まれています。

R は通常、グラフィック出力の R デバイスを利用して画像を作成します。 このデバイスの出力をキャプチャし、 **varbinary** データ型で画像を保管し、アプリケーションでレンダリングできます。あるいは、サポートされているファイル形式 (.JPG や .PDF など) に画像を保存できます。

このセクションでは、ストアド プロシージャを利用し、各種類の出力を使用する方法について学習します。 全体的なプロセスは次のとおりです。

- Varbinary データとして、R プロットを生成するストアド プロシージャを作成します。

- プロットを生成し、イメージ ファイルに保存

- ストアド プロシージャを使用して、プロットのバイナリ データを JPG ファイルや PDF ファイルに変換するには

### <a name="create-the-stored-procedure-plothistogram"></a>PlotHistogram ストアド プロシージャを作成します。

1. 使用して、プロットを作成する`rxHistogram`で提供される強化された R 機能のいずれかの[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]からデータに基づくヒストグラムをプロットするには、[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 R 関数を簡単に呼び出すために、ストアド プロシージャ ( _PlotHistogram_) でラップします。

    [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を新しく開きます**クエリ**ウィンドウです。

2. チュートリアルのデータを含むデータベースでは、このステートメントを使用してプロシージャを作成します。

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram]
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

    必要であれば、正しいテーブル名を使用するようにコードを変更してください。
  
    -   変数 `@query` によりクエリ テキスト (`'SELECT tipped FROM nyctaxi_sample'`) が定義され、スクリプト入力変数 `@input_data_1`の引数として R スクリプトに渡されます。
  
    -   R スクリプトは非常に単純です。R 変数 (`image_file`) が定義され、画像が保存されます。それから、 `rxHistogram` 関数が呼び出され、プロットが生成されます。
  
    -   R デバイスは **オフ**に設定されます。
  
        R では、高レベルの描画コマンドを送るとき、R は *device*という名前のグラフィックス ウィンドウを開きます。 ウィンドウのサイズ、色、その他の特徴を変更できます。あるいは、ファイルに書き込み、別の方法で出力を処理する場合、デバイスをオフにできます。
  
    -   R グラフィックス オブジェクトは、出力のために R data.frame にシリアル化されます。

### <a name="generate-the-graphics-data-and-save-to-file"></a>グラフィックスのデータを生成し、ファイルに保存

ストアド プロシージャは varbinary データのストリームとして画像を返し、直接見ることはできません。 ただし、 **bcp** ユーティリティを利用すれば、varbinary データを取得し、クライアント コンピューターに画像ファイルとして保存できます。
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、次のステートメントを実行します。
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **結果**
    
    *プロット*
    *0xFFD8FFE000104A4649 しています.*
  
2.  PowerShell コマンド プロンプトを開き、次のコマンドを実行します。引数として適切なインスタンス名、データベース名、ユーザー名、資格情報を指定します。
  
     ```
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Bcp コマンド スイッチは、大文字小文字を区別します。
  
3.  接続に成功した場合は、グラフィック ファイル形式に関する詳細情報を入力するように求められます。 プロンプトのたびに ENTER キーを押し、初期設定を適用します。ただし、次については変更します。
  
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
  
### <a name="export-the-plot-data-to-a-viewable-file"></a>プロットのデータを表示可能なファイルにエクスポートします。

バイナリ データに、R プロットを出力する型が、アプリケーションで使用するための便利な場合がありますが、データ探索ステージ中に、レンダリングされたプロットする必要があるデータ サイエンティストに非常に有用ではありません。 一般的に、データ科学者はデータ視覚化を複数行い、さまざまな観点からデータを考察します。

ユーザーのグラフを生成するなどの一般的な形式で R の出力を作成するストアド プロシージャを使用することができます。JPG、します。PDF とします。PNG です。 ストアド プロシージャでグラフィックが作成されたら、ファイルを開き、プロットを視覚化します。

1. ストアド プロシージャの新規作成_PlotInOutputFiles_ヒストグラム、scatterplots、およびその他の R グラフィックスを記述する方法を示しています。JPG とします。PDF 形式です。

    [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を新しく開きます**クエリ**ウィンドウ、および貼り付けでは、次に[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles]  
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
  
    -   ストアド プロシージャ内の SELECT クエリの出力が既定の R データ フレーム `InputDataSet`に保存されます。 さまざまな R プロット関数を呼び出し、実際のグラフィックス ファイルを生成できます。
  
        埋め込み R スクリプトのほとんどがそのようなグラフィックス関数のオプションを表します。`plot` や `hist` などです。
  
    -   すべてのフォルダーがローカル フォルダー _C:\temp\Plots\\_ に保存されます。 宛先フォルダーはストアド プロシージャの一部として R スクリプトに渡された引数により定義されます。  変数 `mainDir`の値を変更して宛先フォルダーを変更できます。
  
2.  ステートメントを実行してストアド プロシージャを作成します。

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

    既存のファイルに書き込もうとしているときにエラーが表示されないことを確認してください。 ファイル名に番号がランダムに生成されます。

3. 表示するには、プロットをコピー先のフォルダーを開き、ストアド プロシージャで R コードで作成されたファイルを確認します。

    + ファイル`rHistogram_Tipped.jpg`ヒントがないなトリップとヒントを取得しましたトリップの数を示します。 (このヒストグラムは、前の手順で生成されるように、)。

    + ファイル`rHistograms_Tip_and_Fare_Amount.pdf`ヒント金額、運賃金額に対してプロットの分布を示します。
    
    ![tip_amount と fare_amount を示すヒストグラム](media/rsql-devtut-tipamtfareamt.PNG "tip_amount と fare_amount を示すヒストグラム")

    + ファイル`rXYPlots_Tip_vs_Fare_Amount.pdf`運賃量、x 軸と y 軸にヒント量 scatterplot が含まれています。

    ![ヒントの量をプロット運賃を超過](media/rsql-devtut-tipamtbyfareamt.PNG "運賃超過ヒント金額がプロットされます")

2.  ファイルを別のフォルダーに出力するには、ストアド プロシージャに埋め込まれている R スクリプトの `mainDir` 変数の値を変更します。 スクリプトを変更し、さまざまなフォーマットを出力したり、出力するファイルを増やしたりできます。

## <a name="next-lesson"></a>次のレッスン

[レッスン 4: T-SQL を使用してデータ機能を作成します。](../tutorials/sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>前のレッスン

[レッスン 2: PowerShell を使用して SQL server のデータをインポートします。](../r/sqldev-import-data-to-sql-server-using-powershell.md)
