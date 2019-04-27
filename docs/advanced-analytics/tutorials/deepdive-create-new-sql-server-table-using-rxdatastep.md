---
title: RevoScaleR rxDataStep - SQL Server Machine Learning を使用した新しい SQL Server のテーブルを作成します。
description: SQL Server で R 言語を使用して SQL Server テーブルを作成する方法のチュートリアル。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1fb3f83cd3bbd39e3af4936ce8dfb8f16bad82d8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62641464"
---
# <a name="create-new-sql-server-table-using-rxdatastep-sql-server-and-revoscaler-tutorial"></a>RxDataStep (SQL Server と RevoScaleR チュートリアル) を使用した新しい SQL Server のテーブルを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このレッスンの一部である、 [RevoScaleR チュートリアル](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)を使用する方法の[RevoScaleR 関数](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)と SQL Server。

このレッスンで、インメモリ データ フレームの間でデータを移動する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンテキスト、およびローカル ファイル。

> [!NOTE]
> このレッスンでは、さまざまなデータ セットを使用します。 航空会社の遅延データセットとは、機械学習実験に広く使用されている公開データセットです。 この例で使用されるデータ ファイルの他の製品サンプルと同じディレクトリで利用できます。

## <a name="load-data-from-a-local-xdf-file"></a>ローカル XDF ファイルからデータを読み込む

このチュートリアルの前半で使用して、 **RxTextData**テキスト ファイルから R にデータをインポートする関数を使用して、 **RxDataStep**関数にデータを移動する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。

このレッスンでは、別のアプローチと、保存ファイルからデータを使用して、 [XDF 形式](https://en.wikipedia.org/wiki/Extensible_Data_Format)します。 XDF ファイルを使用してデータに簡単な変換を行った後、新しい変換後のデータを保存する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。

**XDF は何ですか。**

XDF 形式は、高次元データ用に開発された XML 標準として、ネイティブのファイル形式が使用[Machine Learning Server](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-xdf)します。 XDF は、R インターフェイスを使用したバイナリ ファイル形式です。行と列の処理と分析を最適化しています。  XDF 形式は、データの移動や、分析に有用なデータのサブセットを格納するために使用できます。

1. 計算コンテキストをローカル ワークステーションに設定します。 **この手順では、DDL のアクセス許可が必要です。**

    ```R
    rxSetComputeContext("local")
    ```
  
2. **RxXdfData** 関数を使用して新しいデータ ソース オブジェクトを定義します。 XDF データ ソースを定義するには、データ ファイルへのパスを指定します。  

    テキスト変数を使用してファイルへのパスを指定できます。 ただし、ここでは、ある便利なショートカットを使用することですが、 **rxGetOption**関数し、サンプルのデータ ディレクトリからファイル (AirlineDemoSmall.xdf) を取得します。
  
    ```R
    xdfAirDemo <- RxXdfData(file.path(rxGetOption("sampleDataDir"),  "AirlineDemoSmall.xdf"))
    ```

3. インメモリ データに対して [rxGetVarInfo](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxgetvarinfoxdf) を呼び出して、データセットの概要を表示します。
  
    ```R
    rxGetVarInfo(xdfAirDemo)
    ```

**結果**

```R
Var 1: ArrDelay, Type: integer, Low/High: (-86, 1490)
Var 2: CRSDepTime, Type: numeric, Storage: float32, Low/High: (0.0167, 23.9833)
Var 3: DayOfWeek 7 factor levels: Monday Tuesday Wednesday Thursday Friday Saturday Sunday
```

> [!NOTE]
> 
> ご覧のように、データを XDF ファイルに読み込むために他の関数を呼び出す必要がなく、データに対して **rxGetVarInfo** をすぐに呼び出すことができます。 XDF は既定の中間ストレージ メソッドであるためにです**RevoScaleR**します。 XDF ファイルに加えて、 **rxGetVarInfo**関数が複数のソースの種類になりました。

## <a name="move-contents-to-sql-server"></a>SQL Server にコンテンツを移動します。

ローカルの R セッションで作成した XDF データ ソースに移動できますこのデータをデータベース テーブルに格納する*DayOfWeek* 1 から 7 への値を持つ整数。

1. データ、およびリモート サーバーへの接続を格納するテーブルを指定する、SQL Server のデータ ソース オブジェクトを定義します。
  
    ```R
    sqlServerAirDemo <- RxSqlServerData(table = "AirDemoSmallTest", connectionString = sqlConnString)
    ```
  
2. 念のため、同じ名前のテーブルが既にが存在しが存在する場合、テーブルを削除するかどうかをチェックする手順が含まれます。 同じ名前の既存のテーブルでは、新しく作成されないできないようにします。
  
    ```R
    if (rxSqlServerTableExists("AirDemoSmallTest",  connectionString = sqlConnString))  rxSqlServerDropTable("AirDemoSmallTest",  connectionString = sqlConnString)
    ```
  
3. 使用してテーブルにデータを読み込む**rxDataStep**します。 この関数は、2 つのデータは既にデータ ソースを定義し、途中のデータを変換できます必要に応じて移動します。
  
    ```R
    rxDataStep(inData = xdfAirDemo, outFile = sqlServerAirDemo,
        transforms = list( DayOfWeek = as.integer(DayOfWeek),
        rowNum = .rxStartRow : (.rxStartRow + .rxNumRows - 1) ),
        overwrite = TRUE )
    ```
  
    これは非常に大きなテーブル、このような最終状態メッセージが表示されるまでまで待機します。*行の読み取り:処理された合計行は 200000、:600000*.
     
## <a name="load-data-from-a-sql-table"></a>SQL テーブルからデータを読み込む

テーブルのデータが存在する場合は、単純な SQL クエリを使用して読み込むことができます。 

1. 新しい SQL Server データ ソースを作成します。 入力は、先ほど作成し、データと共に読み込まれる、新しいテーブルに対するクエリです。 この定義の因子レベルを追加します、 *DayOfWeek*列を使用して、 *colInfo*引数**RxSqlServerData**します。
  
    ```R
    sqlServerAirDemo2 <- RxSqlServerData(
        sqlQuery = "SELECT * FROM AirDemoSmallTest",
        connectionString = sqlConnString,
        rowsPerRead = 50000,
        colInfo = list(DayOfWeek = list(type = "factor",  levels = as.character(1:7))))
    ```
  
2. 呼び出す**rxSummary**クエリ内のデータの概要を確認します。
  
    ```R
    rxSummary(~., data = sqlServerAirDemo2)
    ```

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [rxDataStep を使用したチャンク分析の実行](../../advanced-analytics/tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)