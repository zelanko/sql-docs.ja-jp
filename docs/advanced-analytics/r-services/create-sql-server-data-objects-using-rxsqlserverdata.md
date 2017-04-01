---
title: "RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する | Microsoft Docs"
ms.custom: ""
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
ms.assetid: bcf5f7ff-795b-4815-b163-bcddd496efce
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を作成し、データを操作するのに必要なアクセス許可を取得したので、データを使用するためのオブジェクトを R で作成します (サーバーとワークステーションの両方で)。  
  
## SQL Server データ オブジェクトを作成する  
この手順では、R を使用して 2 つのテーブルを作成し、設定します。 この 2 つのテーブルには、模擬的なクレジット カード不正使用データが含まれます。 一方のテーブルはモデルのトレーニング用に使用し、他方のテーブルはスコア付けのために使用します。 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリモート コンピューター上にテーブルを作成するには、**RevoScaleR** パッケージに用意されている `RxSqlServerData` 関数を使用します。  

> [!TIP]
> R Tools for Visual Studio を使用している場合は、ツールバーから **[R Tools (R ツール)]** を選択し、**[Windows (ウィンドウ)]** をクリックして R の変数をデバッグおよび表示するためのオプションを表示します。
  
#### トレーニング用のデータ テーブルを作成するには  
  
1.  R 変数でデータベース接続文字列を指定します。 ここでは、SQL Server に対する有効な ODBC 接続文字列の例を 2 つ示します。1 つは SQL ログインを使用するもので、もう 1 つは Windows 統合認証 (推奨) を使用するものです。

    **SQL ログインを使用する**
    ```R  
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"   
    ```

    **Windows 統合認証を使用する**
    ```R  
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
    ```

    インスタンス名、データベース名、ユーザー名、およびパスワードは必ず適切なものに変更してください。  
  
2.  作成するテーブルの名前を指定し、R 変数に保存します。  
  
    ```R  
    sqlFraudTable <- "ccFraudSmall"       
    ```  
  
    インスタンスとデータベースの名前は接続文字列の一部として既に指定されているので、2 つの変数を組み合わせると、新しいテーブルの *"完全修飾"* 名は、_instance.database.schema.ccFraudSmall_ となります。  
  
3.  データ ソース オブジェクトをインスタンス化する前に、*rowsPerRead* パラメーターを指定する行を追加します。  *RowsPerRead* パラメーターは、各バッチで読み込まれるデータ行の数を制御します。  
  
    ```R  
    sqlRowsPerRead = 5000   
    ```  
  
    このパラメーターは省略できますが、メモリ使用量を管理し効率的な計算を行う上で重要な役割を果たします。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 内の拡張分析関数の大部分は、データをチャンク単位で処理し、中間結果を蓄積していきます。すべてのデータの読み込みが終了したら、最終的な計算結果を返します。  
  
    このパラメーターの値が大きすぎる場合、そのような大規模なデータ チャンクを効率的に処理するのに十分なメモリは備えていないため、データ アクセスは遅くなる可能性があります。  一部のシステムでは、*rowsPerRead* の値が小さすぎると、パフォーマンスが低下する可能性があります。  
  
    このチュートリアルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで定義されたバッチ処理サイズを使用して、各チャンク内の行数を制御し、その値を変数 *sqlRowsPerRead* に保存します。  実際のシステムで大規模なデータ セットを操作する場合は、この設定を試してみることをお勧めします。  
  
4.  最後に、新しいデータ ソース オブジェクトの変数を定義し、前に *RxSqlServerData* コンストラクターに対して定義した引数を渡します。 ここではデータ ソース オブジェクトが作成されるだけで、設定は行われないことに注意してください。  
  
    ```R  
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable, 
       rowsPerRead = sqlRowsPerRead)  
    ```  

  
#### スコア付け用のデータ テーブルを作成するには  

スコア付けデータを保持するテーブルも同じ方法を使用して作成します。  
  
1.  スコア付けで使用するテーブルの名前を格納するための新しい R 変数 *sqlScoreTable* を作成します。  
  
    ```R  
    sqlScoreTable <- "ccFraudScoreSmall"  
    ```  
  
2.  その変数を引数として *RxSqlServerData* 関数に渡して、2 つ目のデータ ソース オブジェクト *sqlScoreDS* を定義します。  
  
    ```R   
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead) 
    ```  
  
  
接続文字列およびその他のパラメーターは変数として R ワークスペースに定義済みであるため、異なるテーブル、ビュー、クエリ用に新しいデータ ソースを作成することは簡単です。異なるテーブル名を指定するだけでよいのです。  
  
このチュートリアルの後の方で、SQL クエリを使用してデータ ソース オブジェクトを作成する方法について説明します。  
  
## R を使用して SQL テーブルにデータを読み込む  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルが作成されましたので、それらのテーブルには、適切な **Rx** 関数を使用してデータを読み込むことができます。  
  
**RevoScaleR** パッケージには、さまざまなデータ ソースをサポートする関数が入っています。テキスト データの場合は、*RxTextData* を使用して、データ ソース オブジェクトを生成します。 その他に、Hadoop データや ODBC データなどからデータ ソース オブジェクトを作成するための関数もあります。  
  
> [!NOTE]  
> このセクションでは、データベースに対する Execute DDL アクセス許可が必要です。
  
#### トレーニング用のテーブルにデータを読み込むには  
  
1.  R 変数 *ccFraudCsv* を作成し、Microsoft R に付属するサンプル データを含む CSV ファイルへのパスを、変数に割り当てます。  
  
    ```R  
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")   
    ```  
  
    ユーティリティ関数 *rxGetOption* に注意してください。 この関数は **RevoScaleR** パッケージに入っています。ユーザーはこの関数を使用して、ローカルおよびリモートのコンピューティング コンテキストに関連するオプション (既定の共有ディレクトリ、計算で使用するプロセッサ (コア) の数など) を容易に設定し管理することができます。この関数は、コードを実行している場所に関係なく、正しいライブラリからサンプルを取得するので便利です。 たとえば、SQL Server で関数を実行し、開発用コンピューターでパスがどのように違うかを確認してください。
  
2.  新しいデータを格納する変数を定義し、*RxTextData* 関数を使用してテキスト データ ソースを指定します。  
  
    ```R  
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(   
        "custID" = "integer", "gender" = "integer", "state" = "integer",   
        "cardholder" = "integer", "balance" = "integer",    
        "numTrans" = "integer",   
        "numIntlTrans" = "integer", "creditLine" = "integer",    
        "fraudRisk" = "integer"))    
    ```  
  
    引数 *colClasses* は重要です。 この引数は、テキスト ファイルから読み込まれたデータの各列に割り当てるデータ型を指定するために使用します。 この例では、すべての列がテキストとして扱われます。例外として、名前付きの列は整数として扱われます。  
  
3.  この時点で、少し間を置いて、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でデータベースを確認することをお勧めします。  データベース内のテーブルの一覧を更新します。  
  
    ローカル ワークスペースには R データ オブジェクトが作成されているが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにはまだテーブルが作成されていないのがわかります。 テキスト ファイルから R 変数に実際に読み込まれたデータもありません。 
  
4.  次に、関数 *rxDataStep* を呼び出して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータを挿入します。  
  
    ```R  
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)   
    ```  
  
    接続文字列に問題がなければ、しばらくすると、次のような結果が表示されます。  
  
      *Total Rows written: 10000, Total time: 0.466*
      *Rows Read: 10000, Total Rows Processed: 10000, Total Chunk Time: 0.577 seconds*  
  
5.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、テーブルの一覧を更新します。 各変数に適切なデータ型が格納されていること、また各変数が正常にインポートされたことを確認するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でテーブルを右クリックして、**[上位 1000 行の選択]** を選択してもかまいません。  
  
#### スコア付け用テーブルにデータを読み込むには  
  
1.  同じ手順に従って、スコア付けに使用するデータ セットをデータベースに読み込みます。  
  
    まず、ソース ファイルへのパスを指定します。  
  
    ```R  
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")   
    ```  
  
2.  *RxTextData* 関数を使用してデータを取得し、それを変数 *inTextData* に保存します。  
  
    ```R  
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(   
        "custID" = "integer", "gender" = "integer", "state" = "integer",   
        "cardholder" = "integer", "balance" = "integer",    
        "numTrans" = "integer",   
        "numIntlTrans" = "integer", "creditLine" = "integer"))  
  
    ```  
  
3.  *rxDataStep* 関数を呼び出して、現在のテーブルを新しいスキーマとデータで上書きします。  
  
    ```R  
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)    
    ```  
  
    -   *inData* 引数では、使用するデータ ソースを定義します。  
  
    -   *OutFile* 引数では、データを保存する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のテーブルを指定します。  
  
    -   テーブルが既に存在しているために *"上書き"* オプションを使用しない場合は、切り捨てなしで結果が挿入されます。  
  
ここでも、接続に成功した場合は、完了を示すメッセージと、テーブルへのデータ書き込みに要した時間が表示されます。 

*Total Rows written: 10000, Total time: 0.384*
*Rows Read: 10000, Total Rows Processed: 10000, Total Chunk Time: 0.456 seconds*  
  
## rxDataStep に関する詳細情報  
*rxDataStep* は **RevoScaleR** パッケージの強力な関数であり、R データ フレームに対して複数の変換を実行し、データを宛先で必要とされる表現に変換できます。 この場合、宛先は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] です。  
  
また、*rxDataStep* に対する引数で R 関数を使用することにより、除外する列の指定、新しい列の追加、データ型の変更など、データに対する変換を指定することもできます。 これらの操作例については、[レッスン 4](../../advanced-analytics/r-services/lesson-4-analyze-data-in-local-compute-context-data-science-deep-dive.md) を参照してください。  
  
## 次の手順  
[SQL Server データに対するクエリおよび変更 (データ サイエンスの詳細情報)](../../advanced-analytics/r-services/query-and-modify-the-sql-server-data-data-science-deep-dive.md)  
  
## 前の手順  
[レッスン 1: R を使用した SQL Server データの操作 (データ サイエンスの詳細)](../../advanced-analytics/r-services/lesson-1-work-with-sql-server-data-using-r-data-science-deep-dive.md)  
  
