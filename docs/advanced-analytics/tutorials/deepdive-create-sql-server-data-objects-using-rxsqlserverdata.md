---
title: RxSqlServerData (SQL と R deep dive) を使用して SQL Server データ オブジェクトを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 12/14/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
- SQL Server 2017
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 84413df820a415ede57a029b24e16abf4181e54f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-and-r-deep-dive"></a>RxSqlServerData (SQL と R deep dive) を使用して SQL Server データ オブジェクトを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事の内容を使用する方法について、データ サイエンス Deep Dive のチュートリアルの一部である[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) SQL Server とします。

ここまでで作成した、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースにあり、データを操作するために必要なアクセス許可を持っています。 この手順では、データを使用することのできる R の一部のオブジェクトを作成します。

## <a name="create-the-sql-server-data-objects"></a>SQL Server のデータ オブジェクトを作成します。

関数を使用するこの手順で、 **RevoScaleR**パッケージを作成し、2 つのテーブルを作成します。 一方のテーブルはモデルのトレーニング用に使用し、他方のテーブルはスコア付けのために使用します。 この 2 つのテーブルには、模擬的なクレジット カード不正使用データが含まれます。

リモート テーブルを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター、呼び出し、 **RxSqlServerData**関数。

> [!TIP]
> R Tools for Visual Studio を使用している場合は、ツールバーから **[R Tools (R ツール)]** を選択し、 **[Windows (ウィンドウ)]** をクリックして R の変数をデバッグおよび表示するためのオプションを表示します。

### <a name="create-the-training-data-table"></a>トレーニング データ テーブルを作成します。

1. データベース接続文字列を R 変数に保存します。 ここでは、SQL Server の有効な ODBC 接続文字列の 2 つの例: 1 つの SQL ログインを使用して、Windows 統合認証用の 1 つです。

    **SQL ログイン**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"
    ```

    **Windows 認証**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name;Database=DeepDive;Trusted_Connection=True"
    ```

    インスタンス名、データベース名、ユーザー名、およびパスワードは必ず適切なものに変更してください。
  
2. 作成するテーブルの名前を指定し、R 変数に保存します。
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    インスタンスとデータベースの名前は接続文字列の一部として既に指定されているので、2 つの変数を組み合わせると、新しいテーブルの *"完全修飾"* 名は、 _instance.database.schema.ccFraudSmall_となります。
  
3.  データ ソース オブジェクトをインスタンス化する前に、 *rowsPerRead*パラメーターを指定する行を追加します。  *RowsPerRead* パラメーターは、各バッチで読み込まれるデータ行の数を制御します。
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    このパラメーターは省略できますが、メモリ使用量を管理し効率的な計算を行う上で重要な役割を果たします。  強化された分析機能のほとんど[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]チャンク内のデータを処理し、最終的な計算すべてのデータが読み取られたを返す、中間結果を格納します。
  
    このパラメーターの値が大きすぎる場合、そのような大規模なデータ チャンクを効率的に処理するのに十分なメモリは備えていないため、データ アクセスは遅くなる可能性があります。  一部のシステムでは、 *rowsPerRead* の値が小さすぎると、パフォーマンスが低下する可能性があります。 そのため、試してみることこの設定では、システムに大きなデータ セットを使用している場合にお勧めします。
  
    このチュートリアルでは、によって定義された既定のバッチ プロセス サイズを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]各チャンク内の行の数を制御するインスタンス。 変数にその値を保存`sqlRowsPerRead`です。
  
4.  最後に、新しいデータ ソース オブジェクトの変数を定義し、以前に定義した RxSqlServerData コンス トラクターに引数を渡します。 ここではデータ ソース オブジェクトが作成されるだけで、設定は行われないことに注意してください。
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

#### <a name="to-create-the-scoring-data-table"></a>スコア付け用のデータ テーブルを作成するには

同じ手順を使用して、同じプロセスを使用してスコア付けのデータを保持するテーブルを作成します。

1. スコア付けで使用するテーブルの名前を格納するための新しい R 変数 *sqlScoreTable*を作成します。
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. 2 番目のデータ ソース オブジェクトを定義する RxSqlServerData 関数の引数としてその変数を指定する*sqlScoreDS*です。
  
    ```R
    sqlScoreDS \<- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

R ワークスペースに変数として既に接続文字列およびその他のパラメーターを定義している、ために、簡単に別のテーブル、ビュー、またはクエリの新しいデータ ソースの作成です。

> [!NOTE]
> 関数は、クエリに基づいてデータ ソースのよりテーブル全体に基づくデータ ソースを定義するための別の引数を使用します。 これでは、SQL Server データベース エンジンが異なる方法でクエリを準備する必要があります。 このチュートリアルの後半では、SQL クエリに基づくデータ ソース オブジェクトを作成する方法を説明します。

## <a name="load-data-into-sql-tables-using-r"></a>R を使用する SQL テーブルにデータを読み込む

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルが作成されましたので、それらのテーブルには、適切な **Rx** 関数を使用してデータを読み込むことができます。

**RevoScaleR**パッケージには、さまざまなデータ ソースをサポートする関数が含まれています: テキスト データを使用して[RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata)データ ソース オブジェクトを生成します。 その他に、Hadoop データや ODBC データなどからデータ ソース オブジェクトを作成するための関数もあります。

> [!NOTE]
> ここでは、する必要があります**DDL 実行**データベースに対する権限。

### <a name="load-data-into-the-training-table"></a>トレーニングのテーブルにデータを読み込む

1. R 変数を作成*ccFraudCsv*、サンプル データを含む CSV ファイルのファイル パスを変数に割り当てるとします。
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    呼び出しに注意してください**rxGetOption**、これは、GET メソッドに関連付けられている[rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions)で**RevoScaleR**です。 このユーティリティを使用して設定し、既定の共有ディレクトリや計算で使用するプロセッサ (コア) の数など、ローカルおよびリモートの計算コンテキストに関連するオプションの一覧です。
    
    この特定の呼び出しは、コードを実行している場所に関係なく、適切なライブラリから、サンプルを取得します。 たとえば、SQL Server で関数を実行し、開発用コンピューターでパスがどのように違うかを確認してください。
  
2. 新しいデータを格納する変数を定義し、 **RxTextData** 関数を使用してテキスト データ ソースを指定します。
  
    ```R
    inTextData <- RxTextData(file = ccFraudCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer",
        "fraudRisk" = "integer"))
    ```
  
    引数 *colClasses* は重要です。 この引数は、テキスト ファイルから読み込まれたデータの各列に割り当てるデータ型を指定するために使用します。 この例では、すべての列がテキストとして扱われます。例外として、名前付きの列は整数として扱われます。
  
3. 一時停止するこの時点では、%12%n%n でデータベースを表示および[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]です。  データベース内のテーブルの一覧を更新します。
  
    、R のデータ オブジェクトは、ローカル ワークスペース内に作成されている、が、テーブルが作成されなかったことでを参照してください、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 また、データが読み込まれていませんテキスト ファイルから R 変数に代入します。
  
4. 次に、関数 [rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) を呼び出して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータを挿入します。
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
  
    接続文字列に問題がなければ、しばらくすると、次のような結果が表示されます。
  
      *Total Rows written: 10000, Total time: 0.466*

      *Rows Read: 10000, Total Rows Processed: 10000, Total Chunk Time: 0.577 seconds*
  
5. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、テーブルの一覧を更新します。 内のテーブルを右クリックすることも、各変数、正しいデータ型があり、正常にインポートされたことを確認する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]選択**上位 1000 行**です。

### <a name="load-data-into-the-scoring-table"></a>スコア付けのテーブルにデータを読み込む

1. データベースにスコアリングのために使用されるデータ セットを読み込むには、手順を繰り返します。
  
    まず、ソース ファイルへのパスを指定します。
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. **RxTextData** 関数を使用してデータを取得し、それを変数 *inTextData*に保存します。
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  **rxDataStep** 関数を呼び出して、現在のテーブルを新しいスキーマとデータで上書きします。
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - *inData* 引数では、使用するデータ ソースを定義します。
  
    - *OutFile* 引数では、データを保存する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のテーブルを指定します。
  
    - テーブルが既に存在し、使用しない場合、*上書き*オプションが切り詰めなしの結果が挿入されます。
  
ここでも、接続に成功した場合は、完了を示すメッセージと、テーブルへのデータ書き込みに要した時間が表示されます。

*Total Rows written: 10000, Total time: 0.384*

*Rows Read: 10000, Total Rows Processed: 10000, Total Chunk Time: 0.456 seconds*

## <a name="more-about-rxdatastep"></a>rxDataStep に関する詳細情報

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep) R データ フレームで複数の変換を実行できる強力な関数です。 データの変換先で必要な形式に変換する rxDataStep を使用することもできます。 この場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

引数の中で R 関数を使用して、データに対して変換を指定する必要に応じて、 **rxDataStep**です。 これらの操作の例については、このチュートリアルの後半で提供されます。

## <a name="next-step"></a>次の手順

[SQL Server データに対するクエリおよび変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)

## <a name="previous-step"></a>前の手順

[R を使用する SQL Server データを操作します。](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)
