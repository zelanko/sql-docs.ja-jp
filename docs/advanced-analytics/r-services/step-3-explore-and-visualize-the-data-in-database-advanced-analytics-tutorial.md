---
title: "手順 3: データの探索と視覚化 (高度な分析 (データベース内) のチュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
ms.assetid: 7fe670f3-5e62-43ef-97eb-b9af54df9128
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# 手順 3: データの探索と視覚化 (高度な分析 (データベース内) のチュートリアル)
データ科学ソリューションの開発には、通常、集中的なデータの探索とデータの視覚化が伴います。 この手順では、サンプル データを確認し、R 関数を利用していくつかのプロットを生成します。 R 関数は [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] に既に含まれています。このチュートリアルでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] から R 関数を呼び出す演習を行います。  
  
## データを確認する  
最初に、サンプル データを確認してください (まだ確認していない場合)。  
  
元のデータセットでは、タクシーの識別子と乗車記録が別々のファイルに入力されていましたが、 サンプル データの利用を簡単にするために、_medallion_、_hack_license_、_pickup_datetime_ 列で元のデータセットを結合しました。  レコードもサンプリングされており、元のレコード数の 1% だけが取得されています。 結果的にダウンサンプリングされたデータセットは 1,703,957 行と 23 列です。  
  
**タクシーの識別子**  
  
-   _medallion_ 列はタクシーの一意の識別子を表します。  
  
-   _hack_license_ 列には、タクシー運転手のライセンス番号が含まれます (匿名にしてあります)。  
  
**乗車と料金の記録**  
  
-   各乗車記録には、乗車場所、降車場所、走行距離が含まれています。  
  
-   各料金記録には、支払の種類、支払の合計額、チップ額など、支払情報が含まれています。  
  
-   最後の 3 つの列はさまざまな機械学習タスクに利用できます。  _tip_amount_ 列には連続する数値が含まれ、回帰分析用の **label** 列として利用できます。 _tipped_ 列には yes/no 値のみが含まれ、二項分類に利用されます。 _tip_class_ 列には複数の**クラス ラベル**が含まれ、複数クラスの分類タスク用のラベルとして利用できます。  
  
    このチュートリアルでは、二項分類タスクのみを紹介します。他の 2 つの機械学習タスク (回帰と複数クラスの分類) でもモデルの構築をお試しください。  
  
-   ラベル列に使用される値はすべて _tip_amount_ 列に基づき、次のようなビジネス ルールが適用されます。  
  
    |派生列名|Rule|  
    |-|-|  
     |tipped|tip_amount > 0 の場合、tipped = 1、それ以外では tipped = 0|  
    |tip_class|クラス 0: tip_amount = $0<br /><br />クラス 1: tip_amount > $0 および tip_amount <= $5<br /><br />クラス 2: tip_amount > $5 および tip_amount <= $10<br /><br />クラス 3: tip_amount > $10 および tip_amount <= $20<br /><br />クラス 4: tip_amount > $20|  
  
## T-SQL で R を使用してプロットを作成する  
データの分布や外れ値を理解する上で視覚化は強力なツールとなります。R はデータを視覚化するためのさまざまなパッケージを提供します。 R の標準オープンソース配布には、ヒストグラム、散布図、箱ひげ図、その他のデータ探索グラフを作成するためのさまざまな関数が含まれています。  
  
R は通常、グラフィック出力の R デバイスを利用して画像を作成します。 このデバイスの出力をキャプチャし、**varbinary** データ型で画像を保管し、アプリケーションでレンダリングできます。あるいは、サポートされているファイル形式 (.JPG や .PDF など) に画像を保存できます。  
  
このセクションでは、ストアド プロシージャを利用し、各種類の出力を使用する方法について学習します。  
  
-   varbinary データ型としてプロットを保存する  
  
-   サーバーでファイル (.JPG、.PDF) にプロットを保存する  
  
### varbinary データ型としてプロットを保存する  
`rxHistogram` ([!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で提供される拡張 R 関数の 1 つ) を利用し、[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリのデータに基づいてヒストグラムを描画します。 R 関数を簡単に呼び出すために、ストアド プロシージャ (_PlotHistogram_) でラップします。  
  
ストアド プロシージャは varbinary データのストリームとして画像を返し、直接見ることはできません。 ただし、**bcp** ユーティリティを利用すれば、varbinary データを取得し、クライアント コンピューターに画像ファイルとして保存できます。  
  
##### PlotHistogram ストアド プロシージャを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、新しいクエリ ウィンドウを開きます。  
  
2.  チュートリアル用のデータベースを選択し、このステートメントを利用してプロシージャを作成します。  
  
    ```  
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
  
    -   変数 `@query` によりクエリ テキスト (`'SELECT tipped FROM nyctaxi_sample'`) が定義され、スクリプト入力変数 `@input_data_1` の引数として R スクリプトに渡されます。  
  
    -   R スクリプトは非常に単純です。R 変数 (`image_file`) が定義され、画像が保存されます。それから、`rxHistogram` 関数が呼び出され、プロットが生成されます。  
  
    -   R デバイスは**オフ**に設定されます。  
  
        R では、高レベルの描画コマンドを送るとき、R は *device* という名前のグラフィックス ウィンドウを開きます。 ウィンドウのサイズ、色、その他の特徴を変更できます。あるいは、ファイルに書き込み、別の方法で出力を処理する場合、デバイスをオフにできます。  
  
    -   R グラフィックス オブジェクトは、出力のために R data.frame にシリアル化されます。 これは CTP3 の一時的な回避策です。  
  
##### 表示可能なグラフィックス ファイルに varbinary データを出力するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、次のステートメントを実行します。  
  
    ```  
    EXEC [dbo].[PlotHistogram]  
    ```  
  
**[結果]**  
  
*プロット*  
*0xFFD8FFE000104A4649...*  
  
2.  PowerShell コマンド プロンプトを開き、次のコマンドを実行します。引数として適切なインスタンス名、データベース名、ユーザー名、資格情報を指定します。  
  
    ```  
    bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>  
  
    ```  
  
    > [!NOTE]  
    > **bcp** のコマンド スイッチでは大文字と小文字が区別されます。  
  
3.  接続に成功した場合は、グラフィック ファイル形式に関する詳細情報を入力するように求められます。 プロンプトのたびに ENTER キーを押し、初期設定を適用します。ただし、次については変更します。  
  
    -   **フィールド プロットのプレフィックス長**に「0」を入力します。  
  
    -   後で再利用するために出力パラメーターを保存する場合、「**Y**」を入力します。  
  
    ```  
    Enter the file storage type of field plot [varbinary(max)]:  
    Enter prefix-length of field plot [8]: 0  
    Enter length of field plot [0]:  
    Enter field terminator [none]:  
  
    Do you want to save this format information in a file? [Y/n]  
    Host filename [bcp.fmt]:  
  
    ```  
  
**[結果]**  
  
*コピーを開始しています...*  
*1 行がコピーされました。*  
*ネットワーク パケット サイズ (バイト): 4096*  
*クロック タイム (ミリ秒)合計     : 3922   平均: (毎秒 0.25 行)*  
   
> [!TIP]  
 > フォーマット情報をファイル (bcp.fmt) に保存する場合、**bcp** ユーティリティによりフォーマット定義が生成されます。それを今後、同様のコマンドに適用できます。グラフィック ファイル フォーマットの選択を求められません。 フォーマット ファイルを使用するには、`-f bcp.fmt` をコマンド行の終わりに追加します。パスワード引数の後です。  
  
4.  出力ファイルは、PowerShell コマンドを実行した同じディレクトリに作成されます。 プロットを表示するには、ファイル plot.jpg を開きます。  
  
    ![taxi trips with and without tips](../../advanced-analytics/r-services/media/rsql-devtut-tippedornot.jpg "taxi trips with and without tips")  
  
### サーバーでファイル (jpg、pdf) にプロットを保存する  
R プロットをバイナリデータ型に出力するとアプリケーションでそれを利用するとき便利ですが、データの探索段階で、レンダリングされたプロットを必要とするデータ科学者にとってはあまり役に立ちません。 一般的に、データ科学者はデータ視覚化を複数行い、さまざまな観点からデータを考察します。  
  
簡単に表示できるグラフを生成するには、.JPG、.PDF、.PNG など、一般的な形式で R を出力するストアド プロシージャを利用する必要があります。 ストアド プロシージャでグラフィックが作成されたら、ファイルを開き、プロットを視覚化します。  
  
この手順では、新しいストアド プロシージャの _PlotInOutputFiles_ を作成します。このストアド プロシージャは、R プロット関数を利用し、ヒストグラムや散布図などを .JPG または .PDF 形式で作成する方法を示します。 グラフィックス ファイルはローカル ファイルに、つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのフォルダーに保存されます。  
  
##### PlotInOutputFiles ストアド プロシージャを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、新しいクエリ ウィンドウを開き、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを貼り付けます。  
  
    ```  
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
  
    -   ストアド プロシージャ内の SELECT クエリの出力が既定の R データ フレーム `InputDataSet` に保存されます。 さまざまな R プロット関数を呼び出し、実際のグラフィックス ファイルを生成できます。  
  
        埋め込み R スクリプトのほとんどがそのようなグラフィックス関数のオプションを表します。`plot` や `hist` などです。  
  
    -   すべてのフォルダーがローカル フォルダー _C:\temp\Plots\\_ に保存されます。  
  
        宛先フォルダーはストアド プロシージャの一部として R スクリプトに渡された引数により定義されます。  変数 `mainDir` の値を変更して宛先フォルダーを変更できます。  
  
2.  ステートメントを実行してストアド プロシージャを作成します。  
  
  
##### グラフィックス ファイルを生成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、次の SQL クエリを実行します。  
  
    ```  
    EXEC PlotInOutputFiles  
  
    ```  
  
**[結果]**  
  
*外部スクリプトからの STDOUT メッセージ:*  
*[1] Creating output plot files:[1]* *C:\\\temp\\\plots\\\rHistogram_Tipped_18887f6265d4.jpg[1]* *C:\\\temp\\\plots\\\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]* *C:\\\temp\\\plots\\\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf*  
  
2.  宛先フォルダーを開き、ストアド プロシージャの R コードにより作成されたファイルを確認します。 (ファイル名の番号はランダムに生成されます。)  
  
*  rHistogram_Tipped_*nnnn*.jpg: チップをもらった乗車 (1) の数とチップをもらわなかった乗車 (0) の数を比較して表示します。 このヒストグラムは、前の手順で生成したヒストグラムに似ています。  
  
*  rHistograms_Tip_and_Fare_Amount_*nnnn*.pdf: tip_amount 列と fare_amount 列の地の分布を表示します。  
  
        ![histogram showing tip_amount and fare_amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtfareamt.PNG "histogram showing tip_amount and fare_amount")  
  
*  rXYPlots_Tip_vs_Fare_Amount_*nnnn*.pdf: x 軸を料金、y 軸をチップ額とする散布図です。  
  
        ![tip amount plotted over fare amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtbyfareamt.PNG "tip amount plotted over fare amount")  
  
3.  ファイルを別のフォルダーに出力するには、ストアド プロシージャに埋め込まれている R スクリプトの `mainDir` 変数の値を変更します。  
  
    スクリプトを変更し、さまざまなフォーマットを出力したり、出力するファイルを増やしたりできます。  
  
## 次の手順  
[手順 4: T-SQL を使用してデータ機能を作成する](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## 前の手順  
[手順 2: PowerShell を使用して SQL Server にデータをインポートする](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## 参照  
[SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
