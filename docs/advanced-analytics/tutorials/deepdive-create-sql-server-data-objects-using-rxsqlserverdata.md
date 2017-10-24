---
title: "RxSqlServerData を使用した SQL Server のデータ オブジェクトの作成 | Microsoft Docs"
ms.custom: 
ms.date: 05/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: bcf5f7ff-795b-4815-b163-bcddd496efce
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a1da660f019ca7665735c3d9aeb352a37214924
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata"></a>RxSqlServerData を使用して SQL Server のデータ オブジェクトを作成する

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を作成し、データを操作するのに必要なアクセス許可を取得したので、データを使用するためのオブジェクトを R で作成します (サーバーとワークステーションの両方で)。

## <a name="create-the-sql-server-data-objects"></a>SQL Server データ オブジェクトを作成する

この手順では、R を使用して 2 つのテーブルを作成し、設定します。 この 2 つのテーブルには、模擬的なクレジット カード不正使用データが含まれます。 一方のテーブルはモデルのトレーニング用に使用し、他方のテーブルはスコア付けのために使用します。

リモート テーブルを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、コンピューターを使用して、 **RxSqlServerData**で提供される関数、 **RevoScaleR**パッケージです。

> [!TIP]
> R Tools for Visual Studio を使用している場合は、ツールバーから **[R Tools (R ツール)]** を選択し、 **[Windows (ウィンドウ)]** をクリックして R の変数をデバッグおよび表示するためのオプションを表示します。

### <a name="create-the-training-data-table"></a>トレーニング データ テーブルを作成します。

1. R 変数でデータベース接続文字列を指定します。 ここでは、SQL Server に対する有効な ODBC 接続文字列の例を 2 つ示します。1 つは SQL ログインを使用するもので、もう 1 つは Windows 統合認証 (推奨) を使用するものです。

    **SQL ログインを使用する**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=instance_name; Database=DeepDive;Uid=user_name;Pwd=password"
    ```

    **Windows 認証を使用する**
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
  
    このパラメーターは省略できますが、メモリ使用量を管理し効率的な計算を行う上で重要な役割を果たします。  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 内の拡張分析関数の大部分は、データをチャンク単位で処理し、中間結果を蓄積していきます。すべてのデータの読み込みが終了したら、最終的な計算結果を返します。
  
    このパラメーターの値が大きすぎる場合、そのような大規模なデータ チャンクを効率的に処理するのに十分なメモリは備えていないため、データ アクセスは遅くなる可能性があります。  一部のシステムでは、 *rowsPerRead* の値が小さすぎると、パフォーマンスが低下する可能性があります。
  
    このチュートリアルでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで定義されたバッチ処理サイズを使用して、各チャンク内の行数を制御し、その値を変数 *sqlRowsPerRead*に保存します。  実際のシステムで大規模なデータ セットを操作する場合は、この設定を試してみることをお勧めします。
  
4.  最後に、新しいデータ ソース オブジェクトの変数を定義し、以前に定義した RxSqlServerData コンス トラクターに引数を渡します。 ここではデータ ソース オブジェクトが作成されるだけで、設定は行われないことに注意してください。
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

#### <a name="to-create-the-scoring-data-table"></a>スコア付け用のデータ テーブルを作成するには

スコア付けデータを保持するテーブルも同じ方法を使用して作成します。

1. スコア付けで使用するテーブルの名前を格納するための新しい R 変数 *sqlScoreTable*を作成します。
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. 2 番目のデータ ソース オブジェクトを定義する RxSqlServerData 関数の引数としてその変数を指定する*sqlScoreDS*です。
  
    ```R
    sqlScoreDS \<- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

接続文字列およびその他のパラメーターは変数として R ワークスペースに定義済みであるため、異なるテーブル、ビュー、クエリ用に新しいデータ ソースを作成することは簡単です。異なるテーブル名を指定するだけでよいのです。

このチュートリアルの後の方で、SQL クエリを使用してデータ ソース オブジェクトを作成する方法について説明します。

## <a name="load-data-into-sql-tables-using-r"></a>R を使用して SQL テーブルにデータを読み込む

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルが作成されましたので、それらのテーブルには、適切な **Rx** 関数を使用してデータを読み込むことができます。

**RevoScaleR**パッケージには、さまざまなデータ ソースをサポートする関数が含まれています: テキスト データを使用して RxTextData データ ソース オブジェクトを生成します。 その他に、Hadoop データや ODBC データなどからデータ ソース オブジェクトを作成するための関数もあります。

> [!NOTE]
> このセクションでは、データベースに対する Execute DDL アクセス許可が必要です。

### <a name="load-data-into-the-training-table"></a>トレーニングのテーブルにデータを読み込む

1. R 変数を作成*ccFraudCsv*、サンプル データを含む CSV ファイルのファイル パスを変数に割り当てるとします。
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    ユーティリティ関数 **rxGetOption**に注意してください。 この関数は **RevoScaleR** パッケージに入っています。ユーザーはこの関数を使用して、ローカルおよびリモートのコンピューティング コンテキストに関連するオプション (既定の共有ディレクトリ、計算で使用するプロセッサ (コア) の数など) を容易に設定し管理することができます。この呼び出しは、サンプル コードを実行している場所に関係なく、適切なライブラリから取得するために便利です。 たとえば、SQL Server で関数を実行し、開発用コンピューターでパスがどのように違うかを確認してください。
  
2. 新しいデータを格納する変数を定義し、RxTextData 関数を使用して、テキスト データ ソースを指定します。
  
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
  
    ローカル ワークスペースには R データ オブジェクトが作成されているが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースにはまだテーブルが作成されていないのがわかります。 また、データが読み込まれていませんテキスト ファイルから R 変数に代入します。
  
4. 次に、関数 **rxDataStep** を呼び出して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルにデータを挿入します。
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
  
    接続文字列に問題がなければ、しばらくすると、次のような結果が表示されます。
  
      *Total Rows written: 10000, Total time: 0.466*

      *Rows Read: 10000, Total Rows Processed: 10000, Total Chunk Time: 0.577 seconds*
  
5. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、テーブルの一覧を更新します。 内のテーブルを右クリックすることも、各変数、正しいデータ型があり、正常にインポートされたことを確認する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]選択**上位 1000 行**です。

### <a name="load-data-into-the-scoring-table"></a>スコア付けのテーブルにデータを読み込む

1. 同じ手順に従って、スコア付けに使用するデータ セットをデータベースに読み込みます。
  
    まず、ソース ファイルへのパスを指定します。
  
    ```R
    ccScoreCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudScoreSmall.csv")
    ```
  
2. RxTextData 関数を使用してデータを取得し、変数に保存*inTextData*です。
  
    ```R
    inTextData <- RxTextData(file = ccScoreCsv,      colClasses = c(
        "custID" = "integer", "gender" = "integer", "state" = "integer",
        "cardholder" = "integer", "balance" = "integer",
        "numTrans" = "integer",
        "numIntlTrans" = "integer", "creditLine" = "integer"))
    ```
  
3.  新しいスキーマとデータで、現在のテーブルを上書きする rxDataStep 関数を呼び出します。
  
    ```R
    rxDataStep(inData = inTextData, sqlScoreDS, overwrite = TRUE)
    ```
  
    - *inData* 引数では、使用するデータ ソースを定義します。
  
    - *OutFile* 引数では、データを保存する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のテーブルを指定します。
  
    - テーブルが既に存在しているために *"上書き"* オプションを使用しない場合は、切り捨てなしで結果が挿入されます。
  
ここでも、接続に成功した場合は、完了を示すメッセージと、テーブルへのデータ書き込みに要した時間が表示されます。

*Total Rows written: 10000, Total time: 0.384*

*Rows Read: 10000, Total Rows Processed: 10000, Total Chunk Time: 0.456 seconds*

## <a name="more-about-rxdatastep"></a>rxDataStep に関する詳細情報

**RxDataStep**へのデータの変換先で必要な形式に変換する R データ フレームで複数の変換を実行できる強力な関数です。 この場合、宛先は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

変換は、rxDataStep 引数の中で R 関数を使用して、データに対しても指定できます。 これらの操作の後で例が表示されます。

## <a name="next-step"></a>次の手順

[クエリおよび SQL Server データの変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)

## <a name="previous-step"></a>前の手順

[R を使用する SQL Server データを操作します。](../../advanced-analytics/tutorials/deepdive-work-with-sql-server-data-using-r.md)


