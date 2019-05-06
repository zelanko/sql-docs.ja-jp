---
title: RevoScaleR RxSqlServerData - SQL Server Machine Learning を使用した SQL Server のデータ オブジェクトを作成します。
description: SQL Server で R 言語を使用してデータ オブジェクトを作成する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 45643dbcdc2876fe0794ddb731abe6334537169c
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510359"
---
# <a name="create-sql-server-data-objects-using-rxsqlserverdata-sql-server-and-revoscaler-tutorial"></a>RxSqlServerData (SQL Server と RevoScaleR チュートリアル) を使用した SQL Server のデータ オブジェクトを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

レッスン 2 ではデータベースの作成の継続: テーブルを追加して、データを読み込んでいます。 DBA が作成したは、データベースとログインの場合[レッスン 1 つ](deepdive-work-with-sql-server-data-using-r.md)RStudio などの R IDE を使用してテーブルを追加するなどの組み込みツールや**Rgui**します。

R から SQL Server に接続して**RevoScaleR**以下のタスクを実行する関数。

> [!div class="checklist"]
> * トレーニング データと予測のテーブルを作成します。
> * ローカルの .csv ファイルからテーブルにデータを読み込む

サンプル データは、シミュレートされたクレジット_カード不正使用データ (ccFraud データセット) の場合は、トレーニング セットとデータセットをスコア付けにパーティション分割します。 データ ファイルが含まれている**RevoScaleR**します。

R IDE を使用するか、 **Rgui**これらの検索を完了します。 この場所にある R 実行可能ファイルを使用することを確認するには。C:\Program Files\Microsoft\R Client\R_SERVER\bin\x64 (か Rgui.exe ツール、または C:\Program Files\Microsoft\R Client\R_SERVER を指す R IDE を使用している場合)。 [R クライアント ワークステーション](../r/set-up-a-data-science-client.md)これらの実行可能ファイルはこのチュートリアルの前提条件と見なされます。

## <a name="create-the-training-data-table"></a>トレーニング データのテーブルを作成します。

1. データベース接続文字列を R 変数に格納します。 SQL Server の有効な ODBC 接続文字列の 2 つの例を次に示します。 1 つの SQL ログインを使用して、Windows 統合認証用に 1 つ。 

   サーバー名、ユーザー名、および必要に応じてパスワードを変更してください。

    **SQL ログイン**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>; Database=RevoDeepDive;Uid=<user_name>;Pwd=<password>"
    ```

    **Windows 認証**
    ```R
    sqlConnString <- "Driver=SQL Server;Server=<server-name>;Database=RevoDeepDive;Trusted_Connection=True"
    ```

2. 作成するテーブルの名前を指定し、R 変数に保存します。
  
    ```R
    sqlFraudTable <- "ccFraudSmall"
    ```
  
    サーバー インスタンスとデータベース名は既に指定されて、接続文字列の一部として 2 つの変数を結合する場合があるため、*の完全修飾*、新しいテーブルの名前になります*instance.database.schema.ccFraudSmall*します。
  
3.  必要に応じて指定*rowsPerRead*各バッチで読み取られるデータの行の数を制御します。
  
    ```R
    sqlRowsPerRead = 5000
    ```
  
    このパラメーターは省略可能ですが、設定されることがより効率的な計算します。 拡張分析関数のほとんど**RevoScaleR**と**MicrosoftML**のチャンク単位でデータを処理します。 *RowsPerRead*パラメーターは、各チャンク内の行の数を決定します。
  
    適切なバランスを見つけるには、この設定を調整する必要があります。 値が大きすぎる場合は、データ アクセスがそのサイズのチャンク単位でデータを処理するための十分なメモリがない場合は低速可能性があります。 逆に、一部のシステムの場合の値*rowsPerRead*が小さすぎる、パフォーマンスも低速化することができます。
  
    最初の値としては、各チャンク (5,000 行) 内の行の数を制御するのにデータベース エンジンのインスタンスで定義された既定のバッチ処理サイズを使用します。 その値を変数に保存*sqlRowsPerRead*します。
  
4.  新しいデータ ソース オブジェクトの変数を定義し、以前に定義されている引数を渡す、 **RxSqlServerData**コンストラクター。 ここではデータ ソース オブジェクトが作成されるだけで、設定は行われないことに注意してください。 データの読み込みとは別の手順です。
  
    ```R
    sqlFraudDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlFraudTable,
       rowsPerRead = sqlRowsPerRead)
    ```

## <a name="create-the-scoring-data-table"></a>スコア付けデータ テーブルを作成します。

同じ手順を使用して、スコア付けを同じプロセスを使用してデータを保持するテーブルを作成します。

1. スコア付けで使用するテーブルの名前を格納するための新しい R 変数 *sqlScoreTable*を作成します。
  
    ```R
    sqlScoreTable <- "ccFraudScoreSmall"
    ```
  
2. その変数を引数として **RxSqlServerData** 関数に渡して、2 つ目のデータ ソース オブジェクト *sqlScoreDS*を定義します。
  
    ```R
    sqlScoreDS <- RxSqlServerData(connectionString = sqlConnString,
       table = sqlScoreTable, rowsPerRead = sqlRowsPerRead)
    ```

接続文字列とその他のパラメーターは、既に R ワークスペース内の変数として定義した、ため、異なるテーブル、ビュー、またはクエリを表す、新しいデータ ソースの再利用できます。

> [!NOTE]
> 関数はクエリに基づいてデータ ソースのよりもテーブル全体に基づくデータ ソースを定義するためのさまざまな引数を使用します。 これはため、SQL Server データベース エンジンは異なる方法でクエリを準備する必要があります。 このチュートリアルの後半では、SQL クエリに基づくデータ ソース オブジェクトを作成する方法について説明します。

## <a name="load-data-into-sql-tables-using-r"></a>R を使用して SQL テーブルにデータを読み込む

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルが作成されましたので、それらのテーブルには、適切な **Rx** 関数を使用してデータを読み込むことができます。

**RevoScaleR**パッケージには、データ ソースの種類に固有の関数が含まれています。 テキスト データを使用して[RxTextData](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxtextdata)をデータ ソース オブジェクトを生成します。 その他に、Hadoop データや ODBC データなどからデータ ソース オブジェクトを作成するための関数もあります。

> [!NOTE]
> このセクションでは、する必要があります**DDL 実行**データベースに対する権限。

### <a name="load-data-into-the-training-table"></a>トレーニング用のテーブルにデータを読み込む

1. R 変数では、作成*ccFraudCsv*、サンプル データを含む CSV ファイルのファイル パスを変数に割り当てます。 このデータセットに含まれる**RevoScaleR**します。 "SampleDataDir"は、キーワード、 **rxGetOption**関数。
  
    ```R
    ccFraudCsv <- file.path(rxGetOption("sampleDataDir"), "ccFraudSmall.csv")
    ```
  
    呼び出しに注意してください**rxGetOption**、これは、GET メソッドに関連付けられている[rxOptions](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxoptions)で**RevoScaleR**します。 このユーティリティを使用して設定し、オプションの一覧に関連する既定の共有ディレクトリ、計算で使用するプロセッサ (コア) の数など、ローカルおよびリモート計算コンテキスト。
    
    この特定の呼び出しでは、コードを実行している場所に関係なく、正しいライブラリからサンプルを取得します。 たとえば、SQL Server で関数を実行し、開発用コンピューターでパスがどのように違うかを確認してください。
  
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
  
3. 一時停止するこの時点では、説明でデータベースを確認および[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。 データベース内のテーブルの一覧を更新します。
  
    ローカル ワークスペースには、R データ オブジェクトが作成されて、テーブルが作成されなかったでを参照してください、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 また、データが読み込まれていませんテキスト ファイルから R 変数にします。
  
4. 関数を呼び出すことによって、データを挿入[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep)関数。
  
    ```R
    rxDataStep(inData = inTextData, outFile = sqlFraudDS, overwrite = TRUE)
    ```
    
    接続文字列に問題がなければ、しばらくすると、次のような結果が表示されます。
  
    *書き込まれた合計行数:以上 10000 以下、合計時間:0.466* *の読み取り行数。処理された合計行以上 10000 以下、:以上 10000 以下、チャンクの合計時間:0.577 秒*
  
5. テーブルの一覧を更新します。 内のテーブルを右クリックすることも、各変数が適切なデータ型とが正常にインポートされたことを確認する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]選択**上位 1000 行**します。

### <a name="load-data-into-the-scoring-table"></a>スコア付け用のテーブルにデータを読み込む

1. データベースにスコア付けに使用するデータ セットを読み込む手順を繰り返します。
  
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
  
    - テーブルが既に存在し、使用しない場合、*上書き*オプション、切り捨てることがなく結果が挿入されます。
  
ここでも、接続に成功した場合は、完了を示すメッセージと、テーブルへのデータ書き込みに要した時間が表示されます。

*書き込まれた合計行数:以上 10000 以下、合計時間:0.384*
*の読み取り行数。処理された合計行以上 10000 以下、:以上 10000 以下、チャンクの合計時間:0.456 秒*

## <a name="more-about-rxdatastep"></a>rxDataStep に関する詳細情報

[rxDataStep](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxdatastep)は、R データ フレームに対して複数の変換を実行できる強力な関数です。 RxDataStep を使用してデータを変換先で必要とされる表現に変換する。 この場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。

引数の中で R 関数を使用して、データに対して変換を指定する必要に応じて、 **rxDataStep**します。 これらの操作の例については、このチュートリアルの後半で提供されます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [SQL Server データに対するクエリおよび変更](../../advanced-analytics/tutorials/deepdive-query-and-modify-the-sql-server-data.md)